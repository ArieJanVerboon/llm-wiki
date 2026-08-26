# Syncing across computers

GitHub is the single source of truth. Each computer is a disposable local clone,
and the factory (the n8n workflows) also commits here automatically. Keep the two
in sync with a simple daily routine.

## One-time setup (on any computer)

1. Install Git.
2. Clone the project:
   ```powershell
   cd $HOME\Documents
   git clone https://github.com/ArieJanVerboon/llm-wiki.git
   ```
3. Sign in to GitHub when prompted.

That's it. The factory already runs online; your computer is just for reading and
editing files. For how to actually trigger the flows, see **HOWTO.md**.

## The golden rule

- Before you start working: `git pull` (get the newest files)
- When you finish: `git add .` -> `git commit -m "what I did"` -> `git push`

Always grab the latest before typing, always save when done — the factory may
have committed new research since you last pulled.

## What NOT to do

- **Don't put weird symbols in filenames** — especially a colon `:` (also
  `\ / * ? " < > |`). Windows refuses to download such files. The factory now
  cleans these automatically, but keep hand-made names simple.
- **Don't hand-edit the robot's files.** Leave `public/index.html` and
  `public/manifest.json` to the factory. To change them, edit the manifest data
  and trigger a rebuild (see HOWTO.md) — don't rewrite `index.html` yourself, or
  you'll get merge clashes.
- **Don't forget to `git pull` first.** If you start from stale files, your
  `git push` gets rejected. Fix: `git pull --rebase` then `git push`.
- **Don't work inside `C:\Windows\System32`** or other system folders. Keep the
  project in your Documents.
- **Don't put secret files in the repo** — it may be public. Passwords and API
  keys stay inside n8n's credential store, never in the folder.
- **Don't run `git reset --hard` casually.** It throws away unsaved changes.
