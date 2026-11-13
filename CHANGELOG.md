# Changelog

All notable changes to regionpage-v1 are documented here.

Since v26.10.23 this project uses [Date Versioning](https://datevers.ing) (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used Semantic Versioning.

## v26.11.13-1

### Fixed

- **Registered office country.** The Imprint page now gives the full registered office, ending in "United Kingdom": 124 City Road, London, EC1V 2NX, England, United Kingdom.

## v26.11.13

### Changed

- **New registered office.** The Imprint page now shows Stux Group Ltd's new registered office, 124 City Road, London, EC1V 2NX, England (it was 82a James Carter Road, Mildenhall). The company number and "Registered in England and Wales" are unchanged.

## v26.11.12

### Fixed

- **The commit script's push hint** now names the current branch (`test`) and the release tag, and reminds you to open the pull request into `main`. It used to say to push to `main`.

## v26.11.07

### Changed

- **All rights reserved.** The License section now reads "Copyright (c) 2026 Stux.Group. All rights reserved. This repository is not licensed for reuse or redistribution", and a `LICENSE` file says the same.

## v26.11.06

### Changed

- **Work happens on `test`.** Changes reach `main` only through a pull request from `test` (CI now runs on pushes to `test` too), and releases are made and tagged on `test`. CONTRIBUTING has a Branches section, and the README's Versioning section says so.

## v26.10.26

### Security

- CI uses Node.js 24 instead of the end-of-life Node.js 20, which has no fix for the Brotli decoder vulnerability CVE-2026-111497

## v26.10.23-1

### Added

- A Discord link preview: every page except the 404 page carries a `discord:component-embed` in its `<head>` (pre-built JSON, kept under Discord's 3,000-byte limit) showing the server regions with a link to their live status, in Stuxedo's colours with its icon. The Open Graph fallback is unchanged
- A full favicon set at the site root: `favicon.ico` (16, 32 and 48 px), `apple-touch-icon.png`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` and `site.webmanifest`, all made from Stuxedo's own icon, and the matching tags in every page's `<head>` (the region wrapper's tags point at the full `https://regionpage-v1.stuxedo.net/` address, since it is hosted on each region's own site)
- `tests/site.sh`, which checks every embed is valid JSON under 3,000 bytes with no stray `$1`, that the 404 page has none, that the favicon files exist at the right sizes, and that every `<head>` carries the tag set
- `.htmlvalidate.json` relaxes `valid-id` so the validator accepts the embed's required `discord:component-embed` id
- The local dev server (`dev-server.sh` / `dev-server.bat`) serves `site.webmanifest` as `application/manifest+json`, as GitHub Pages does

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.4
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.4

### Changed

- Live server status comes from Stuxedo's own status page, [status.stuxedo.net](https://status.stuxedo.net) (`Stuxedo/Status`), instead of Stux.Group's: the servers moved there on 9 October 2026 with their history and slugs, so every badge works as before. The "Live status from" link points there too

## v1.0.3

### Fixed

- The footer's copyright line had a second, hidden copy of the © icon inside its screen-reader text; it's gone, leaving the visible icon and a plain "©" for screen readers. Nothing changes on screen

## v1.0.2

### Fixed

- The footer no longer says "Stuxedo is operated by Stux.Cloud, which is operated by Stux Group Ltd."; that belongs on the Imprint, which still says who operates the page. The copyright line names Stuxedo instead of Stux.Group ("© 2026 Stuxedo. All rights reserved."), matching the live pages

## v1.0.1

### Fixed

- The imprint said this page is published as Stuxedo, "which is operated by Stuxedo, which is operated by" Stux Group Ltd, repeating itself; it now reads "published as Stuxedo, which is operated by" Stux Group Ltd

## v1.0.0

### Added

- Archived [Stuxedo/regionpage](https://github.com/Stuxedo/regionpage) at commit `988fda7` (`v1.0.1`), the last state before Stuxedo's rebrand to the tuxedo-cat logo (neon `#4bf708` on dark, deep `#032f14` on light), preserving history up to that point as this repository's own `main` branch

### Changed

- Served from `regionpage-v1.stuxedo.net` instead of `regionpage.stuxedo.net` (CNAME, canonical URLs, sitemap and robots.txt)
- Logo, icon and favicon now point at the archived assets under `https://global.media.stuxedo.com/v1/` instead of the live Stuxedo brand assets, which have been replaced
- README and CONTRIBUTING describe this repository as an archive
