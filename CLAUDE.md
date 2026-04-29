# Game Projects Workspace

This folder is a **vibe coding workspace** for building small, standalone browser/JS games.

## Starting a new game

When the user describes a game to build, before writing any code:

1. **Derive a short slug** from the game description (2-4 words, lowercase, hyphen-separated). Examples: `snake-game`, `space-shooter`, `2048-clone`.
2. **Create a subdirectory** named `<slug>-YYYY-MM-DD` using today's date. Example: `snake-game-2026-04-22`.
3. **Initialize a git repo** inside that directory:
   ```bash
   git init <slug>-YYYY-MM-DD
   cd <slug>-YYYY-MM-DD
   git config user.name "mahfujar"
   git config user.email "mahfujar.rahman@lobstr.io"
   ```
4. Build the game inside that directory.
5. After the initial working version is done, create an initial commit:
   ```bash
   git add .
   git commit -m "init: <short game description>"
   ```
6. **Create a README.md** in the game directory with the live surge URL:
   ```markdown
   # <Game Name>
   <one line description>
   **Live:** https://<slug>.surge.sh
   ```
7. **Push to GitHub** immediately after the initial commit — create a public repo named `<slug>` and push:
   ```bash
   gh repo create <slug> --public --description "<short description>" --source . --remote origin --push
   ```
   - `gh` CLI is installed and authenticated as `mahfujarrahman` — no confirmation needed
7. **Deploy to surge.sh** immediately after the initial commit (no local server needed):
   ```bash
   npx surge . <slug>.surge.sh
   ```
   - surge is already authenticated as `mahfujar.rahman@lobstr.io` — no login prompt needed
   - The domain follows the pattern `<slug>.surge.sh` (e.g. `palette-thief-game.surge.sh`)
   - After deploy, share the live URL with the user

## Autonomy

**Do not ask for permission** for any of these standard operations — just do them:
- Creating directories, files, git repos
- Committing changes
- Creating GitHub repos and pushing (`gh` authenticated as `mahfujarrahman`)
- Deploying to surge.sh (authenticated as `mahfujar.rahman@lobstr.io`)
- Redeploying after changes

Only pause if something is genuinely ambiguous about what the user wants built.

## Redeploying

To redeploy after changes, run from inside the game directory:
```bash
npx surge . <slug>.surge.sh
```

## Platform notes

This workspace is used on both **macOS** and **Windows**. Keep all instructions cross-platform:

- Use `npx surge` (works on both — Node/npm must be installed)
- **macOS**: Node installed via Homebrew at `/opt/homebrew/bin/node`
- **Windows**: Node installed via official installer or `winget install OpenJS.NodeJS`; `npx` available in any terminal (CMD, PowerShell, Git Bash)
- Avoid macOS-only commands (`brew`, `open`, etc.) unless guarded by OS check
- All file paths in game code must use relative paths (forward slashes work in both browsers and surge)

## Project conventions

- Each game lives in its own subdirectory with its own `.git` repo.
- Keep games self-contained: single HTML file + assets, or minimal Node/bundler setup.
- Prefer vanilla JS/HTML/CSS unless the user specifies a framework.
- Git identity for every repo: `mahfujar <mahfujar.rahman@lobstr.io>`

## Folder structure

```
game/
  CLAUDE.md              ← this file
  snake-game-2026-04-22/ ← each game in its own dated, git-tracked folder
  space-shooter-2026-04-25/
  ...
```
