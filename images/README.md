# images

Per-link screenshot thumbnails, one file per link: `<ID>.jpg` (the same 10-character
ID shown in the app's ID column — MD5 of the link's URL, first 10 hex chars).

Populated by the app's "Renew" button, which calls a Supabase Edge Function that
fetches a fresh screenshot from thum.io and commits it here via the GitHub API
(the commit token lives server-side as an Edge Function secret, never in the
browser). The app reads images straight from this folder via
`raw.githubusercontent.com`.
