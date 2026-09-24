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

Add a new row to the **Research Topics** tab of the same Google Sheet. Columns:

- `topic` or `prompt` (one is required; `prompt` replaces the default research question)
- optional: `url`, `section`, `subsection`, `tags` (comma-separated)

n8n checks the tab every minute. Perplexity runs deep research, a Claude confidence gate scores the result, and it
is filed automatically:

- score **>= 80** -> `raw/`
- score **60-79** -> `review/`
- score **< 60** -> discarded
- unparseable -> `03_Failed/`

Deep research can take a few minutes. Topics already in Zotero are skipped.

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
Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/publish-document" -Method Post -ContentType "application/json" -Headers @{ 'X-Webhook-Token' = $env:N8N_WEBHOOK_TOKEN } -Body $body
```

Flow C builds a house-styled HTML page and a PDF, commits both to
`public/published/`, then rebuilds `manifest.json` and `index.html`.

## 4. Rebuild the index only

If you tidied `public/manifest.json` by hand and just want the index
regenerated (no new document):

```powershell
Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -Method Post -ContentType "application/json" -Headers @{ 'X-Webhook-Token' = $env:N8N_WEBHOOK_TOKEN } -Body '{"trigger":"manual-rebuild"}'
```

## Keeping computers in sync — the golden rule

- Before you start working: `git pull` (get the newest files)
- When you finish: `git add .` -> `git commit -m "what I did"` -> `git push`

Think of it like a shared document: always grab the latest before typing, always
save when done. Full detail in **SYNC.md**.

## Webhook-sleutel

Alle webhooks vereisen de header `X-Webhook-Token` (n8n Header Auth). Zet de sleutel eenmalig per computer als Windows-omgevingsvariabele (sleutel staat in de wachtwoordmanager onder `n8n-webhook-token`):

```powershell
[Environment]::SetEnvironmentVariable('N8N_WEBHOOK_TOKEN', '<sleutel>', 'User')
```

Open daarna een nieuw PowerShell- of Git Bash-venster (in VS Code: VS Code herstarten). Controle: `$env:N8N_WEBHOOK_TOKEN.Length` (PowerShell) of `echo ${#N8N_WEBHOOK_TOKEN}` (Git Bash) moet `40` geven.

Git Bash-variant van een aanroep:

```bash
curl -X POST "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -H "Content-Type: application/json" -H "X-Webhook-Token: $N8N_WEBHOOK_TOKEN" -d '{"trigger":"manual-rebuild"}'
```
