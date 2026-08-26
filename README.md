# llm-wiki — Antifragile Research Knowledge Base

Automated research knowledge base produced by the **Antifragile Research
Pipeline** (n8n) and served as a static site via Cloudflare.

As of 2026-08 the original single 41-node pipeline has been split into **three
independent, antifragile workflows**, so a failure in one stage never blocks the
others.

## The three workflows

| Flow | Trigger | What it does | Writes to |
|------|---------|--------------|-----------|
| **A — Manual Capture** | New row in the Google Sheet | LLM-free capture of items you add by hand. Normalizes, de-duplicates against Zotero, then files the item. | `raw/` + Zotero (`ingested:raw`) |
| **B — Perplexity Research Capture** | Webhook `POST /webhook/perplexity-research` | Runs Perplexity deep research on a topic, scores it with a Claude confidence gate, and routes by confidence. | `raw/` / `review/` / `03_Failed/` + Zotero |
| **C — Publish & Index Rebuild** | Webhook `POST /webhook/rebuild-index` | Turns an approved payload into a house-styled HTML page + PDF, then rebuilds `manifest.json` and `index.html`. | `public/published/`, `public/manifest.json`, `public/index.html` |

### Confidence gate (Flow B)

- **>= 80** -> filed to `raw/`, tagged `ingested:raw`
- **60-79** -> filed to `review/`, tagged `ingested:review`
- **< 60** -> discarded (no file written)
- **unparseable evaluator output** -> raw text saved to `03_Failed/` so nothing is ever lost

> Each flow is separate on purpose. If Perplexity is slow or the PDF service is
> down, the other flows keep working. This is the "antifragile" split.

## Repository layout

| Path | Purpose | Public? |
|------|---------|---------|
| `public/` | **The live site.** Cloudflare serves this folder as the site root. | Yes (served by Cloudflare) |
| `public/index.html` | Generated research index (grouped by section). **Do not edit by hand** — it is regenerated from the manifest. | Yes |
| `public/manifest.json` | **Source of truth** for the index. One entry per published document. Edit this to add/remove/hide/re-title/re-tag entries. | Yes |
| `public/published/` | Published research pages (`<slug>.html`) and their PDFs (`<slug>.pdf`). | Yes |
| `raw/` | Unstyled source markdown drafts (confidence >= 80, or manual captures). Working material. | Internal |
| `review/` | Items awaiting review (confidence 60-79). | Internal |
| `03_Failed/` | Outputs that failed automated parsing. | Internal |
| `HOWTO.md` | Day-to-day usage: how to trigger each of the three flows. | Internal |
| `SYNC.md` | How to clone and keep the repo in sync across multiple computers. | Internal |

> The pipeline writes published output into `public/`. Everything outside
> `public/` is working material and is **not** served by the live site.

## How the index works

`public/manifest.json` is the single source of truth. Each manifest entry looks
like:

```json
{
  "title": "Antifragility in Supply Chains",
  "slug": "2026-08-25-antifragility-in-supply-chains",
  "path": "published/2026-08-25-antifragility-in-supply-chains.html",
  "pdf": "published/2026-08-25-antifragility-in-supply-chains.pdf",
  "summary": "Systems that gain from disruption...",
  "confidence": 82,
  "date": "2026-08-25",
  "section": "Risk",
  "subsection": "Supply Chains",
  "tags": ["risk", "logistics"],
  "status": "raw",
  "hidden": false
}
```

- `section` / `subsection` — control grouping in the index. Missing section -> shown under **Unsorted**.
- `tags` — displayed as labels (not used for grouping).
- `status` — `raw` items show in the main index.
- `hidden: true` — keeps the file in the repo but removes it from the index.

`public/index.html` is regenerated from the manifest every time Flow C publishes
a new document and whenever a manual rebuild is triggered.

### Manual edits

Edit `public/manifest.json` directly (add an entry, set `hidden: true`, change
section/tags, reorder, etc.), then trigger a rebuild so `public/index.html`
regenerates:

```powershell
Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -Method Post -ContentType "application/json" -Body '{"trigger":"manual-rebuild"}'
```

The response reports `published_count` and `entry_count` and confirms the
commit. The rebuild also backfills any `public/published/*.html` that is not yet
in the manifest (into "Unsorted").

## Working across multiple computers

GitHub is the single source of truth; each computer is a disposable local clone,
and the pipeline also commits here automatically. See **SYNC.md** for the
clone + daily `git pull` / `git push` routine, and **HOWTO.md** for how to
trigger each flow.

## Deployment

Cloudflare is connected to this repo and auto-deploys on every commit. Build
output directory: `public`. No build command (static HTML).
