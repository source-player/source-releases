# Privacy

**Short version: this app has no accounts, no telemetry, no analytics, and no
crash reporting. Nothing about what you watch is ever sent to the developer.**

## What the app connects to

The app only makes network requests needed to do what you asked it to do:

- **Your own playlist / IPTV servers** — the servers and playlist URLs you
  add are contacted directly to fetch channel lists, program guides, and
  streams. Nothing about them is shared with anyone else.
- **TMDB** (`api.themoviedb.org`, `image.tmdb.org`) — movie/show titles are
  looked up to fetch metadata, ratings, and poster art.
- **Source's key service** (`api.sourceplayer.app`) — asked for the app's built-in
  TMDB key every few days, and more often while it can't get a working one (when
  TMDB stops accepting the key, or the service can't be reached: about every 10
  minutes at first, then up to once an hour). The request carries the app's
  version and, like any request from the app, your IP address and the app's
  browser engine (its User-Agent). Nothing about what you watch is sent. Source
  keeps no logs of these requests. It isn't contacted while you have your own TMDB key in
  Settings → API keys.
- **OpenSubtitles** (`api.opensubtitles.com`) — searched when you play a
  movie or episode, to list available subtitles; a subtitle is downloaded only
  when you pick one. If you sign in to your own OpenSubtitles.com account in
  Settings → Subtitles, your username and password are sent to OpenSubtitles
  to sign in, and nowhere else.
- **GitHub** (`github.com`) — checked for app updates. Downloads come from
  the public releases page.
- **iptv-org** (`iptv-org.github.io`) — a public list of TV channels, fetched
  to fill in Live TV logos your playlist doesn't provide. Channel logos then
  load from wherever that list or your playlist points (often Wikimedia).
- **Cloudflare** (`1.1.1.1`) — a short request to check that you're online.
- **Devices on your network** — when you cast, the app finds Chromecast and
  AirPlay devices on your local network and streams to them directly.

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
