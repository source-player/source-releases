# Privacy

**Short version: this app has no accounts, no telemetry, no analytics, and no
crash reporting. Nothing you do in it is ever sent to the developer.**

## What the app connects to

The app only makes network requests needed to do what you asked it to do:

- **Your own playlist / IPTV servers** — the servers and playlist URLs you
  add are contacted directly to fetch channel lists, program guides, and
  streams. Nothing about them is shared with anyone else.
- **TMDB** (`api.themoviedb.org`, `image.tmdb.org`) — movie/show titles are
  looked up to fetch metadata, ratings, and poster art.
- **OpenSubtitles** (`api.opensubtitles.com`) — searched when you play a
  movie or episode, to list available subtitles; a subtitle is downloaded only
  when you pick one. If you sign in to your own OpenSubtitles.com account in
  Settings → Subtitles, your username and password are sent to OpenSubtitles
  to sign in, and nowhere else.
- **GitHub** (`github.com`) — checked for app updates. Downloads come from
  the public releases page.

Requests to these services are governed by their own privacy policies.

## What's stored, and where

Everything the app stores stays on your device:

- Playlist definitions and server credentials (stored unencrypted in the
  app's local storage — treat your device accordingly).
- Your OpenSubtitles.com username and password, if you sign in — kept in the
  operating system's credential store (Windows Credential Manager or the macOS
  Keychain). Signing out deletes them.
- Watch history, resume positions, and favorites.
- Metadata and image caches.
- A local log file (`app.log`) for troubleshooting; it never leaves your
  machine, and server credentials are redacted from it.

Uninstalling the app (and removing its app-data folder) removes all of it.

## Questions

Open an issue at <https://github.com/source-player/source-releases/issues>.
