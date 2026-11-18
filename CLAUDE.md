# The Exiled Crown (castle builder review game)

This repo holds the game's code and art for Mr. Scott's Google Apps Script web app.

## Layout
- `code/Index.html` - the whole game page (menus, 3D view, rules). Paste into Apps Script file "Index".
- `code/Code.gs` - server code (Sheet reads and writes, reports). Paste into Apps Script file "Code.gs".
- Image files at the repo root (e.g. `test_crest.png`) are loaded by the live game from jsDelivr / raw.githubusercontent on the `main` branch. Do not rename or move them without updating `ART_MANIFEST` in Index.html and `ART_BASE_URLS` in Code.gs.

## Branches (how builds reach students)
- Code.gs `doGet` downloads `code/Index.html` from GitHub on every page load, so Index.html changes need no pasting or redeploying. The "Index" file inside Apps Script is only a fallback if GitHub is unreachable. Code.gs changes are still pasted by hand and deployed as a new version.
- `main` = newest build. Mr. Scott tests it with the web app link plus `?test=1` at the end.
- `live` = what students get from the plain link. Only update `live` from `main` after Mr. Scott tests and says it is ready.
- clasp cannot run from the Claude cloud workspace (script.googleapis.com is blocked there), which is why this loader exists.

## Working rules
- This repo is the source of truth for the code. Edit the files here in place (do not retype them), test, then commit and push to `main`.
- After pushing, also save the same files into the Claude Project docs `code/Index.html` and `code/Code.gs` so Project chats stay in sync.
- The design plan and build record live in the Claude Project ("Castle Builder Review Game Design Plan", "claude/Build Chat Plan and Setup Record").
- Mr. Scott does not code: give one step per message, complete files to paste, and wait for "done".
- Test headless before delivering: three.js r128 from npm (`three@0.128.0`), Chrome at /usr/bin/google-chrome via puppeteer, intercept the cdnjs request.
- Public repo: never commit student names, emails, the Sheet link, or backup codes.
