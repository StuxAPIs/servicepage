# Changelog

All notable changes to Service Page are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Date Versioning](https://datevers.ing) since v26.10.23 (`YY.MM.DD`, the UTC release date, with `-1`, `-2`… for later releases the same day); earlier releases used [Semantic Versioning](https://semver.org/).

## v26.10.23-1

### Added

- Discord link previews: every page except the 404 page carries a `discord:component-embed` block in its `<head>`, in the StuxAPIs purple (`#BF7FF9`) with the StuxAPIs icon. The home page says what this placeholder is and links to StuxAPIs; the changelog, the legal hub and the other pages get their own preview. The blocks are pre-built and committed by `python scripts/build-discord-embeds.py`, page text is escaped so it shows as plain text, a preview over Discord's 3,000-byte limit is left out, and the page title and description stay as the fallback
- A full favicon set generated from the StuxAPIs icon: `favicon.ico` (16, 32 and 48px), `apple-touch-icon.png` (on a white background, so iOS doesn't fill it with black) and `site.webmanifest` with 192px, 512px and maskable 512px icons, linked from every page, the 404 page included
- `tests/site.sh`, which checks every Discord preview (valid JSON, under 3,000 bytes, none on the 404 page), the favicon files and sizes, the manifest, and the icon tags in every `<head>`; CI now runs it and `tests/version.sh`

## v26.10.23

### Added

- `tests/version.sh`, which checks that `VERSION.md` is a valid Date Version, a real calendar date not in the future, and the same as the newest entry in this changelog

### Changed

- Switched from Semantic Versioning to [Date Versioning](https://datevers.ing): releases are numbered by their UTC release date as `YY.MM.DD`, with `-1`, `-2`… for later releases the same day. This release follows v1.0.7
- `commit.sh` and `commit.bat` refuse a `VERSION.md` that isn't a valid Date Version or is dated in the future (UTC), and warn when it's dated before today
- `README.md` and `CONTRIBUTING.md` describe Date Versioning and the release steps

## v1.0.7

### Changed

- The favicon follows the browser's light or dark theme: the deep icon (`icon-dark.png`) on light and the bright one (`icon-light.png`) on dark, straight from the brand's media host, so a brand colour change is just a new file there
- The logos and icons in the Markdown docs (README and the like) follow GitHub's light or dark theme, using each brand's `logo-light`/`logo-dark` and `icon-light`/`icon-dark` files

## v1.0.6

### Changed

- README footer now matches the StuxAPIs `.github` footer ("Built & Maintained by StuxAPIs…" and "StuxAPIs is a part of the Stux.Group brand of businesses"), like every other StuxAPIs repository

## v1.0.5

### Changed

- The footer's copyright year is worked out automatically: the start year alone in the first year, then START–CURRENT

## v1.0.4

### Changed

- The copyright line reads Stux.Group instead of Stux Group Ltd

## v1.0.3

### Changed
- Changelog badges now use the fixed shared palette — Added green, Changed blue, Fixed orange, Removed red, Security purple, Deprecated grey — as tinted pills, with darker variants in light mode
- `###` sections within each release are sorted into that same fixed order (Added, Changed, Fixed, Removed, Security, Deprecated) at render time, whatever order `CHANGELOG.md` lists them in; unknown types go last

## v1.0.2

### Fixed
- The footer's changelog/version link (and other footer links) turned accent-purple once visited — `a:visited` carries a pseudo-class, giving it higher CSS specificity than the plain `footer a` selector meant to keep footer links muted, so it kept winning regardless of source order. Every affected footer link now also styles `footer a:visited` explicitly.

## v1.0.1

### Fixed
- GitHub Pages was using the legacy branch-deploy build system, which can silently stop auto-deploying with no error recorded anywhere (discovered on SeasonalOverlaysLibrary — its live site served stale content for over an hour with no visible failure). Switched to GitHub Actions-based Pages deployment (`.github/workflows/pages.yml`), making every deploy an ordinary, observable CI run instead.

## v1.0.0

### Added

- Initial release: a placeholder page shown when a StuxAPIs service hasn't
  been set up yet, with self-hosted Fredoka font (matching Kittens and other
  StuxAPIs products), a "Boring Legal Stuff" legal hub (`legal.html` +
  `legal/`), `changelog.html` that fetches and renders `CHANGELOG.md` at
  runtime, a version indicator fetched live from `VERSION.md`, cross-origin
  `postMessage` title sync, `dev-server.sh` / `dev-server.bat`, and a custom
  `404.html` error page
