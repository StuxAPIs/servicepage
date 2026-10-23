<p align="center">
  <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stuxapis.net/logo-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stuxapis.net/logo-dark.png"><img src="https://global.media.stuxapis.net/logo-dark.png" height="100" alt="StuxAPIs Logo"></picture>
</p>

# Service Page

A clean and simple placeholder page for a StuxAPIs service that hasn't been set up yet.

## Overview

This repository contains a lightweight HTML page shown in place of a StuxAPIs service that hasn't been configured yet. It points visitors back to StuxAPIs and gives them a way to get in touch.

## Features

- 📄 Simple, clean HTML structure
- ⚡ Lightweight and fast-loading
- 🎨 Ready to customize
- 📱 Responsive design
- 🚀 Deployed at [servicepage.stuxapis.net](https://servicepage.stuxapis.net)

## Getting Started

1. Clone the repository:
   ```bash
   git clone https://github.com/StuxAPIs/servicepage.git
   ```

2. Open `index.html` in your browser or deploy to your hosting provider

## Customization

Edit the HTML files to:
- Update the message
- Add your branding and logo
- Customize colors and styling
- Include additional links

## Deployment

This project uses GitHub Pages and can be automatically deployed to your desired domain.

The live version is deployed at [servicepage.stuxapis.net](https://servicepage.stuxapis.net).

## Link previews and icons

Every page except the 404 page carries a Discord link preview (a `discord:component-embed` script in its `<head>`), built by `python scripts/build-discord-embeds.py`. The favicon set (`favicon.ico`, `apple-touch-icon.png`, `site.webmanifest` and the icons in `assets/img/`) is linked from every page. `bash tests/site.sh` checks both.

## Versioning

This project uses [Date Versioning](https://datevers.ing): each release is numbered by its UTC release date as `YY.MM.DD` (for example `26.10.23`), with `-1`, `-2`… for later releases the same day. See [CHANGELOG.md](CHANGELOG.md) for what changed in each release.

## License

This project is open source and available for use and modification.

---

*Built & Maintained by <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stuxapis.net/icon-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stuxapis.net/icon-dark.png"><img src="https://global.media.stuxapis.net/icon-dark.png" height="14" alt="StuxAPIs" valign="middle"></picture> [StuxAPIs](https://github.com/StuxAPIs), Hosted by <img src="https://github.com/Stuxedo.png" height="14" alt="Stuxedo" valign="middle"> [Stuxedo](https://stuxedo.com).    
StuxAPIs is a part of the <picture><source media="(prefers-color-scheme: dark)" srcset="https://global.media.stux.group/icon-light.png"><source media="(prefers-color-scheme: light)" srcset="https://global.media.stux.group/icon-dark.png"><img src="https://global.media.stux.group/icon-dark.png" height="14" alt="Stux.Group" valign="middle"></picture> Stux.Group brand of businesses.*
