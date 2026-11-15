# Contributing to regionpage-v1

Thank you for your interest in contributing! This repository is an archived, pinned snapshot of the original green regionpage design, so its scope is intentionally narrow.

## Scope

This is **not** the actively developed template. That's [Stuxedo/regionpage](https://github.com/Stuxedo/regionpage). This repo preserves the `v1` look as-is. Contributions here should keep the existing design working, not change it:

- Fixing broken links, encoding issues, or browser-compatibility bugs
- Keeping the page renderable as browsers and standards evolve

New features, redesigns, or styling changes belong in the live `regionpage` repository instead.

## Running it locally

Run `./dev-server.sh` (or `dev-server.bat` on Windows) and open the printed URL. Add `--lan` to open it from a phone or another device on your network: it listens on every interface instead of `127.0.0.1` only and prints the addresses to open (usually the `192.168.x.x` one).

## Branches and going live

- **`main` is what's live.** Nothing is pushed to it directly: it only changes when a pull request from `staging` is merged. Merging into it deploys the site to GitHub Pages.
- **`staging` is the last check before live.** It only changes when a pull request from `test` is merged. It needs CI to pass. Nothing deploys from it.
- **Work happens on `test`**, or on a feature branch off `test` that's merged back into it. Releases are made on `test` too; `commit.sh` / `commit.bat` refuse to run on `staging` or `main`.
- **Going live:** push `test` with its tag, open a pull request into staging (`gh pr create --base staging --head test`), check staging once it's merged, then open one from staging into main (`gh pr create --base main --head staging`). Leo reviews and merges both.

## Versioning

This project uses [Date Versioning](https://datevers.ing). To release:

1. Add a `## vYY.MM.DD` entry at the top of `CHANGELOG.md`, with its sections in this order: Added, Changed, Fixed, Removed, Security, Deprecated.
2. Set `VERSION.md` to the same bare version (no `v`): today's **UTC** date as `YY.MM.DD`, or `YY.MM.DD-1`, `-2`… for later releases the same UTC day. Never a future date. Use UTC, not local time: just after midnight in the UK it is still the previous day in UTC.
3. Run `bash tests/version.sh` and `bash tests/site.sh`.
4. Run `./commit.sh` (or `commit.bat` on Windows). It checks the version, commits and tags `vYY.MM.DD`, and never pushes.
