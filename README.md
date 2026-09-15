# LinkDB

A single-file link archive/manager. Open `index.html` directly in a
browser or host it (e.g. GitHub Pages) — no build step. Data lives in a
[Supabase](https://supabase.com) Postgres project, and access is gated by
Google sign-in.

## Architecture

- **Data**: Supabase Postgres (`categories`, `tags`, `post_tags`, `posts`,
  `post_category`, `post_notes`, `meta`), loaded into memory on boot and
  kept in sync — every edit updates the UI immediately and pushes to
  Supabase in the background.
- **Auth**: Google OAuth via Supabase Auth, restricted to a single account
  both client-side and via Postgres Row Level Security.
- **Images**: each link has one screenshot, `images/<id>.jpg`, committed to
  this GitHub repo and served from `raw.githubusercontent.com`. The
  "Renew" button and Purge's image cleanup both go through a Supabase Edge
  Function (`renew-image`), which holds the GitHub write token
  server-side and talks to [thum.io](https://www.thum.io/) for the actual
  screenshot.

## Features

- Paste-to-import: add links in bulk, one URL per line
- Categories, tags, and per-link notes
- Sortable URL / Title / Tags (by category) columns; Title, Tags, and
  Notes cells cap at 250px tall with their own scrollbar for long content
- One-click "Renew" screenshot fetch; Purge also removes the link's image
  from GitHub
- Hide/restore links (soft delete) separate from permanent Purge
- Search across URL, title, notes, and tags
- Light/dark theme

## Usage

1. Open the hosted page (GitHub Pages) or `index.html` locally in any
   browser
2. Sign in with Google — only the account configured in Supabase's Row
   Level Security policies can read or write data
3. Use the ⇩ button to paste-import links, the ⏻ button to sign out

## Archive

Previous tagged versions are kept in [`Archive/`](./Archive) for reference.
