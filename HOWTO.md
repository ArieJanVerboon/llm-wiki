# How to use the Knowledge Factory

The factory (three n8n workflows) already lives online and is switched on. Your
computer is just for reading and editing the files. There are three ways to feed
it.

## 1. Capture something manually — Flow A

Add a new row to the Google Sheet:

`https://docs.google.com/spreadsheets/d/1oNeUWK5Hz1TnBWby-Lx7P9lC17WWZER9f2XabCzQ9QQ/edit`

Flow A picks up the new row automatically, de-duplicates it against Zotero, and
files it into `raw/`. No AI is involved — it captures exactly what you typed.

## 2. Research a topic with AI — Flow B

Send the factory a topic from your PC:

```powershell
Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/perplexity-research" -Method Post -ContentType "application/json" -Body '{"topic":"your topic here"}'
```

Perplexity runs deep research, a Claude confidence gate scores the result, and it
is filed automatically:

- score **>= 80** -> `raw/`
- score **60-79** -> `review/`
- score **< 60** -> discarded
- unparseable -> `03_Failed/`

Deep research can take a few minutes. You can also pass `"url"` instead of
`"topic"` for de-duplication on a source link.

## 3. Publish an approved report + rebuild the site — Flow C

When a draft is ready to go live, send it to the publisher:

```powershell
$body = @{
  title      = "Antifragility in Supply Chains"
  summary    = "The core so-what in two or three sentences."
  confidence = 82
  markdown   = "## Full report body in Markdown..."
  section    = "Risk"
  subsection = "Supply Chains"
  tags       = @("risk","logistics")
} | ConvertTo-Json
Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -Method Post -ContentType "application/json" -Body $body
```

Flow C builds a house-styled HTML page and a PDF, commits both to
`public/published/`, then rebuilds `manifest.json` and `index.html`.

## 4. Rebuild the index only

If you tidied `public/manifest.json` by hand and just want the index
regenerated (no new document):

```powershell
Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -Method Post -ContentType "application/json" -Body '{"trigger":"manual-rebuild"}'
```

## Keeping computers in sync — the golden rule

- Before you start working: `git pull` (get the newest files)
- When you finish: `git add .` -> `git commit -m "what I did"` -> `git push`

Think of it like a shared document: always grab the latest before typing, always
save when done. Full detail in **SYNC.md**.
