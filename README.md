# LinkDB

A single-file, offline-first link archive/manager. Open `linkdb.html` directly
in a browser — no server, no build step, no external dependencies. Data is
stored in a local SQLite database (via sql.js) that you connect to or export
from the app itself.

## Features

- Paste-to-import: add links in bulk, one URL per line
- Categories, tags, and per-link notes
- Local image thumbnails per link, with a one-click "Renew" screenshot fetch
- Search across ID, URL, title, notes, and tags
- Light/dark theme

## Usage

1. Download [`linkdb.html`](./linkdb.html)
2. Open it in a Chromium-based browser (Chrome/Edge — needed for the File
   System Access API used to connect/save a local `.sqlite` file)
3. Use the menu (☰) to open or create a database file

## Archive

Previous tagged versions are kept in [`Archive/`](./Archive) for reference.
