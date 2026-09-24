# llm-wiki — Antifragile Research Knowledge Base

Automated research knowledge base produced by the **Antifragile Research
Pipeline** (n8n) and served as a static site via Cloudflare. Content is
curated on top of that pipeline as a Karpathy-pattern **LLM wiki**: raw
captures in `raw/` are read by an LLM agent and synthesized into durable,
cross-linked pages under `wiki/`, governed by the schema in `CLAUDE.md`.

**Status:** active. The pipeline and wiki schema are both in daily use; the
published site (`public/`) currently has no live entries yet (see
`public/manifest.json`).

As of 2026-08 the original single 41-node pipeline has been split into **three
independent, antifragile workflows**, so a failure in one stage never blocks the
others.

## Getting started

The pipeline already runs online (n8n); a local clone is only needed to read
or hand-edit files. Git and Windows Git Bash / Linux shell are the only
requirements.

```bash
git clone https://github.com/ArieJanVerboon/llm-wiki.git
cd llm-wiki
```

See **SYNC.md** for the daily `git pull` / `git push` routine and **HOWTO.md**
for how to trigger each flow.

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
| `raw/` | Unstyled source drafts (confidence >= 80, or manual captures) and ingest sources for the wiki layer. Working material — never edited, only appended to. | Internal |
| `raw/_seed/` | Initial seed source(s) the wiki schema is based on, e.g. `karpathy-llm-wiki.md`. | Internal |
| `raw/_archief/` | Older/archived raw sources. | Internal |
| `review/` | Items awaiting review (confidence 60-79). | Internal |
| `03_Failed/` | Outputs that failed automated parsing. | Internal |
| `wiki/` | Curated, LLM-maintained wiki pages synthesized from `raw/`: `entities/`, `concepts/`, `topics/`, `sources/`. | Internal |
| `templates/` | Page templates (`_entity.md`, `_concept.md`, `_topic.md`, `_source.md`, `_comparison.md`, `_log-entry.md`) used when creating new wiki pages. | Internal |
| `index.md` | Catalogue of every wiki page, grouped by type. Updated on every ingest / new page. | Internal |
| `log.md` | Append-only chronological log of `ingest` / `query` / `lint` / `schema` operations on the wiki. | Internal |
| `CLAUDE.md` | Schema for the LLM wiki: layer ownership, folder layout, and the ingest/query/lint operations an LLM agent follows. | Internal |
| `HOWTO.md` | Day-to-day usage: how to trigger each of the three flows. | Internal |
| `SYNC.md` | How to clone and keep the repo in sync across multiple computers. | Internal |
| `ELI10.md` | Plain-language walkthrough of the whole pipeline and setup. | Internal |

> The pipeline writes published output into `public/`. Everything outside
> `public/` is working material and is **not** served by the live site.

## The wiki layer

On top of the pipeline, `raw/` sources are curated into a persistent,
cross-linked wiki instead of being re-synthesized on every query. This follows
the pattern described in `raw/_seed/karpathy-llm-wiki.md` and is formalized in
`CLAUDE.md`:

- **Ingest** — read a new `raw/` source fully, write a summary page under
  `wiki/sources/`, update or create related pages under `wiki/entities/`,
  `wiki/concepts/` and `wiki/topics/` (with citations and `⚠ contradictie`
  markers where sources disagree), then update `index.md` and append to
  `log.md`.
- **Query** — answer questions from `index.md` and the relevant wiki pages,
  citing both the wiki page and its underlying source; valuable answers can be
  offered back as new wiki pages.
- **Lint** — periodic health check for contradictions, stale claims, orphaned
  pages, missing pages for well-covered concepts, and missing cross-references.

Pages use YAML frontmatter (`type`, `created`, `updated`, `sources`, `tags`)
and `[[wiki-link]]`-style cross-references, so the repository also works as an
Obsidian vault (see `.obsidian/`). Full conventions live in `CLAUDE.md`.

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
Invoke-RestMethod -Uri "<JOUW-N8N-URL>/webhook/rebuild-index" -Method Post -ContentType "application/json" -Body '{"trigger":"manual-rebuild"}'
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
