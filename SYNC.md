# How to set it up

**On any computer (one time):**

1. Install Git.
2. Copy the whole project down:
   ```powershell
   cd $HOME\Documents
   git clone https://github.com/ArieJanVerboon/llm-wiki.git
Sign in to GitHub when it asks.
That's it — the factory (the n8n workflow) already lives online and is switched
on. Your computer is just for reading and editing the files.

How to use it every day
To make a new report: send the factory a topic. From your PC:

Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/research-ingest" -Method Post -ContentType "application/json" -Body '{"topic":"your topic here"}'
Wait a bit, and the report appears on your website.

To rebuild the index (if you tidied the master list by hand):

Invoke-RestMethod -Uri "https://inspreadables.app.n8n.cloud/webhook/rebuild-index" -Method Post -ContentType "application/json" -Body '{"trigger":"manual-rebuild"}'
To keep your two computers in sync — the golden rule:

☀️ Before you start working: git pull (get the newest files)
🌙 When you finish: git add . → git commit -m "what I did" → git push
Think of it like a shared Google Doc: always grab the latest before typing,
always save when done. (More detail in SYNC.md.)

🚫 What NOT to do
Don't put weird symbols in filenames — especially a colon : (also
\ / * ? " < > |). Windows hates them and refuses to download the file.
The factory now cleans these automatically, but if you name files by hand,
keep them simple.
Don't hand-edit the robot's files. Leave public/index.html and
public/manifest.json to the factory. If you want them changed, edit the
manifest's data and press the rebuild button — don't rewrite the index
yourself, or you'll get clashes.
Don't forget to git pull first. If you start editing with old files,
your git push gets rejected. (Fix: git pull --rebase then git push.)
Don't work inside C:\Windows\System32 or other system folders. Keep the
project in your Documents.
Don't put secret files in the repo — it may be public. Passwords and API
keys stay inside n8n's credential store, never in the folder.
Don't run git reset --hard casually. It throws away unsaved changes.
It's only safe when you know you have nothing local to lose.

