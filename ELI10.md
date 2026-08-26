
# 🏭 Your Research Knowledge Factory — Explained Like You're 10

## What we built

Imagine a **magic factory** that turns questions into finished, good-looking
research reports and puts them on a website — all by itself.

You drop a topic in one end. Out the other end comes:

- A tidy research report (written by AI),
- A pretty web page and a PDF of it,
- A spot on your website's index so people can find it.

Here are the factory's main machines:

1. **The front door (Webhook).** You send it a topic. The factory wakes up.
2. **The "have we done this already?" check (Zotero).** Like a librarian who
   checks if the book already exists, so you don't make the same report twice.
3. **The researcher (Perplexity).** Reads the internet and writes a deep report.
4. **The judge (Anthropic AI).** Reads the report and gives it a **confidence
   score** (0–100), like a teacher grading homework.
5. **The sorting hat (Switch).** Based on the grade, it decides:
   - **80+** → publish it (it's great!)
   - **60–79** → put it in the "needs a human to check" pile (`review/`)
   - **Below 60** → toss it (trash)
   - **Couldn't read it** → put it in the "broken" pile (`03_Failed/`)
6. **The decorator (House Style).** Wraps good reports in your orange-and-slate design.
7. **The printer (API2PDF).** Makes a PDF.
8. **The publisher (GitHub).** Saves everything into your `llm-wiki` folder online.
9. **The index maker.** Rebuilds the website's table of contents (`index.html`)
   from a master list (`manifest.json`) so everything is browsable.

Then **Cloudflare** takes the finished website online at your public address.

And your **two computers** are just copies of the same box of files — GitHub is
the real "master copy" everyone shares.

---

## How to set it up

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

