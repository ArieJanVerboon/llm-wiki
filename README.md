# llm-wiki — Antifragile Research Knowledge Base

Automated research knowledge base produced by the **Antifragile Research
Ingestion Pipeline** (n8n) and served as a static site via Cloudflare.

## Repository layout

| Path | Purpose | Public? |
|------|---------|---------|
| `public/` | **The live site.** Cloudflare serves this folder as the site root. | Yes (served by Cloudflare) |
| `public/index.html` | Generated research index (grouped by section). **Do not edit by hand** — it is regenerated from the manifest. | Yes |
| `public/manifest.json` | **Source of truth** for the index. One entry per published document. Edit this to add/remove/hide/re-title/re-tag entries. | Yes |
| `public/published/` | Published research pages (`<slug>.html`) and their PDFs (`<slug>.pdf`). | Yes |
| `raw/` | Unstyled source markdown/HTML drafts. Working material. | Internal |
| `review/` | Items awaiting review (confidence 60–79). | Internal |
| `03_Failed/` | Outputs that failed automated parsing. | Internal |
| `SYNC.md` | How to clone and keep the repo in sync across multiple computers. | Internal |

> The pipeline writes published output into `public/`. Everything outside
> `public/` is working material and is **not** served by the live site.

## How the index works

`public/manifest.json` is the single source of truth. Each manifest entry looks like:

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
section / subsection — control grouping in the index. Missing section → shown under Unsorted.
tags — displayed as labels (not used for grouping) and searchable.
status — raw items show in the main index; review items appear in a collapsed "In review" section.
hidden: true — keeps the file in the repo but removes it from the index.
public/index.html is regenerated from the manifest every time the pipeline
publishes a new document and whenever the manual rebuild is triggered.

Manual edits
Edit public/manifest.json directly (add an entry, set hidden: true, change
section/tags, reorder, etc.).

Trigger a rebuild so public/index.html regenerates from the manifest:

Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -Method Post -ContentType "application/json" -Body '{"trigger":"manual-rebuild"}'
The response reports published_count and entry_count, and confirms the
commit. The rebuild also backfills any public/published/*.html that is
not yet in the manifest (into "Unsorted").

Working across multiple computers
GitHub is the single source of truth; each computer is a disposable local
clone, and the pipeline also commits here automatically. See SYNC.md
for the clone + daily git pull / git push routine and how to avoid conflicts
with the pipeline's generated files.

Deployment
Cloudflare is connected to this repo and auto-deploys on every commit.
Build output directory: public. No build command (static HTML).


Small note: this README has a `json` code block *inside* it. When you paste into VS Code that's totally fine — it's part of the file. Just make sure you grab everything from `# llm-wiki...` down to the last `static HTML).` line. Save it as `README.md` in your `llm-wiki` folder, then commit as before:

```powershell
git pull
git add README.md
git commit -m "Update README"
git push
 
