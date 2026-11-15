<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stuxapis.net/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stuxapis.net/logo-dark.png"><img src="https://global.media.stuxapis.net/logo-dark.png" height="80" alt="StuxAPIs Logo"></picture>
</p>

# Contributing to Service Page

This is a single-file HTML template, open for use and modification per the
[License](README.md#license) section. This document is for anyone working on
the template itself (not a downstream deployment).

## Local setup

There's no build step or dependencies — just clone the repo and run
`./dev-server.sh [port]` (or `dev-server.bat [port]` on Windows), which starts
a local static server pointed at the directory. Then open
`http://127.0.0.1:8000`. Add `--lan` to open it from a phone or tablet on the same network: the server then listens on all interfaces instead of `127.0.0.1` only, and prints the addresses to open (usually the `192.168.x.x` one).

## Project conventions

- Static HTML pages (`index.html`, `legal.html` + `legal/`, `changelog.html`, `404.html`) — no framework, no build step, no backend.
- Keep it lightweight and dependency-free; the Fredoka font is self-hosted under `assets/fonts/` (matching other StuxAPIs products like Kittens), not pulled from a third-party CDN.
- `changelog.html` fetches and renders `CHANGELOG.md` at runtime — don't hand-duplicate changelog content into it.
- General contact uses `hello@stuxapis.net`; legal-page contact uses `legal@stuxapis.net`.
- This is a single page, not a soonpage/maintenancepage pair — a service either has been set up or it hasn't; there's no separate "under maintenance" state to design for.
- Match the existing code style: no comments explaining *what* the markup does, only *why* when something is genuinely non-obvious.

## Branches and going live

- **`main` is what's live.** Nothing is pushed to it directly: it only changes when a pull request from `staging` is merged. Merging deploys the site to GitHub Pages.
- **`staging` is the last check before live.** It only changes when a pull request from `test` is merged.
- **Work happens on `test`**, or on a branch off `test` that's merged back into it. Releases are committed and tagged on `test`; `commit.sh` / `commit.bat` refuse to run on `staging` or `main`.
- **Going live:** push `test` with its tag (`git push origin test --tags`), open a pull request into staging (`gh pr create --base staging --head test`), check staging once it's merged, then open one from staging into main (`gh pr create --base main --head staging`). Both pull requests need CI to pass and are reviewed and merged by Leo.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh` and `bash tests/site.sh`. If you change a page's `<title>` or description, run `python scripts/build-discord-embeds.py` first to refresh its Discord preview.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.

## Before committing

- Open `index.html` in a browser and check it renders correctly
- Check the page at common viewport widths (mobile/tablet/desktop) since it's meant to be responsive
