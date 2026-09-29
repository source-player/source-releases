# Third-Party Licenses

This application ("source") bundles and redistributes prebuilt open-source
components. This file lists every distributed component with its license and
upstream home. The authoritative license text for each component is the one
in its upstream repository/release; this file is a notice index, not a
replacement for those texts.

Source code for every component listed here is available from the linked
upstream project. For the GPL/LGPL-licensed components, copies of the exact
corresponding sources are also available on request — open an issue at
<https://github.com/source-player/source-releases/issues>.

---

## Application framework

| Component | License | Upstream |
|---|---|---|
| Tauri (v2, incl. plugins: dialog, process, updater) | MIT OR Apache-2.0 | <https://github.com/tauri-apps/tauri> |
| wry (vendored fork in `vendor/wry`) | MIT OR Apache-2.0 | <https://github.com/tauri-apps/wry> |
| tauri-runtime-wry (vendored fork in `vendor/tauri-runtime-wry`) | MIT OR Apache-2.0 | <https://github.com/tauri-apps/tauri> |
| Rust crate dependencies | predominantly MIT OR Apache-2.0 (see `src-tauri/Cargo.lock`) | crates.io |

## Frontend assets

| Component | License | Upstream |
|---|---|---|
| Lucide icons | ISC | <https://github.com/lucide-icons/lucide> |
| Inter font | SIL OFL 1.1 | <https://github.com/rsms/inter> |
| JetBrains Mono font | SIL OFL 1.1 | <https://github.com/JetBrains/JetBrainsMono> |
| Open Sans font | SIL OFL 1.1 | <https://github.com/googlefonts/opensans> |
| IBM Plex Sans + IBM Plex Mono fonts | SIL OFL 1.1 | <https://github.com/IBM/plex> |
| Space Grotesk font | SIL OFL 1.1 | <https://github.com/floriankarsten/space-grotesk> |
| Space Mono font | SIL OFL 1.1 | <https://github.com/googlefonts/spacemono> |
| Atkinson Hyperlegible font | SIL OFL 1.1 | <https://www.brailleinstitute.org/freefont/> |
| Fira Code font | SIL OFL 1.1 | <https://github.com/tonsky/FiraCode> |
| Cascadia Code font | SIL OFL 1.1 | <https://github.com/microsoft/cascadia-code> |
| Geist + Geist Mono fonts | SIL OFL 1.1 | <https://github.com/vercel/geist-font> |
| Instrument Sans font | SIL OFL 1.1 | <https://github.com/Instrument/instrument-sans> |
| Figtree font | SIL OFL 1.1 | <https://github.com/erikdkennedy/figtree> |
| Manrope font | SIL OFL 1.1 | <https://github.com/sharanda/manrope> |
| Rubik font | SIL OFL 1.1 | <https://github.com/googlefonts/rubik> |
| Lexend font | SIL OFL 1.1 | <https://github.com/googlefonts/lexend> |
| Chakra Petch font | SIL OFL 1.1 | <https://github.com/cadsondemak/Chakra-Petch> |
| Oxanium font | SIL OFL 1.1 | <https://github.com/sevmeyer/oxanium> |
| DM Mono font | SIL OFL 1.1 | <https://github.com/googlefonts/dm-mono> |
| Source Code Pro font | SIL OFL 1.1 | <https://github.com/adobe-fonts/source-code-pro> |
| Martian Mono font | SIL OFL 1.1 | <https://github.com/evilmartians/mono> |
| Victor Mono font | SIL OFL 1.1 | <https://github.com/rubjo/victor-mono> |
| Recursive font | SIL OFL 1.1 | <https://github.com/arrowtype/recursive> |
| Kode Mono font | SIL OFL 1.1 | <https://github.com/isaozler/kode-mono> |
| Share Tech Mono font | SIL OFL 1.1 | <https://fonts.google.com/specimen/Share+Tech+Mono> |
| VT323 font | SIL OFL 1.1 | <https://github.com/phoikoi/VT323> |
| TMDB logo | TMDB brand asset, used per TMDB attribution requirements | <https://www.themoviedb.org/about/logos-attribution> |

## Media engine — Windows (LGPL build)

| Component | License | Upstream |
|---|---|---|
| libmpv (`libmpv-2.dll`, **LGPL build** — mpv `-Dgpl=false`, statically-linked LGPL FFmpeg) | **LGPLv2.1-or-later** (mpv) with statically-linked LGPLv3 FFmpeg; no GPL-only components | <https://mpv.io> |

**Provenance (this is also the "corresponding source" pointer required by the LGPL):**

- Prebuilt by the **zhongfly/mpv-winbuild** CI (the auto-updating fork of
  shinchiro/mpv-winbuild-cmake), which publishes ready-made LGPL libmpv
  artifacts.
- Release tag: **`2026-07-17-94335ab87a`**, asset
  `mpv-dev-lgpl-x86_64-20260717-git-94335ab87a.7z`
  (SHA256 `6014aa0e6d8e98cdba90f5288295a7105d7d14ab0ca906f51465eeb478d5fea0`).
  Upstream prunes old releases, so release builds install a byte-identical copy of that
  artifact's contents from the developer's own archive (`win-libmpv-lgpl-2026-07-17-94335ab87a.zip`,
  SHA256 `4caa6903d0081de63052aa94b828492f93ab9ad36152b4687fa70c89096292dd`); the engine
  version string is verified on install.
- Engine version string: `mpv v0.41.0-878-g94335ab87`.
- Corresponding source: <https://github.com/zhongfly/mpv-winbuild> (build
  recipe) → mpv <https://github.com/mpv-player/mpv> and FFmpeg
  <https://ffmpeg.org> at the pinned commits. Also available on request via
  the issue tracker.

The single `libmpv-2.dll` statically links LGPL/permissive libraries only:
LGPL FFmpeg (built **without** `--enable-gpl`), libass (ISC), dav1d
(BSD-2-Clause), libplacebo (LGPL), SVT-AV1 (BSD), and friends. **No GPL-only
components** — x264, x265, and Rubber Band are deliberately excluded (verified
by binary inspection of the shipped DLL, 2026-07-17). x264/x265 are *encoders*
a player never uses; pitch-preserving speed is handled by mpv's built-in
`scaletempo2` (LGPL), not Rubber Band. The libmpv client API header is ISC.

## Media engine — macOS (LGPL build)

| Component | License | Upstream |
|---|---|---|
| libmpv (`libmpv.dylib`, **LGPL build** — mpv `-Dgpl=false`) | LGPL-2.1-or-later | <https://mpv.io> |
| FFmpeg (libavcodec, libavfilter, libavformat, libavutil, libswresample, libswscale) | LGPL-2.1-or-later (built **without** `--enable-gpl`) | <https://ffmpeg.org> |
| dav1d (AV1 decoder) | BSD-2-Clause | <https://code.videolan.org/videolan/dav1d> |
| libass | ISC | <https://github.com/libass/libass> |
| FreeType | FTL (BSD-style, with credit) | <https://freetype.org> |
| FriBidi | LGPL-2.1-or-later | <https://github.com/fribidi/fribidi> |
| HarfBuzz | MIT (Old MIT) | <https://github.com/harfbuzz/harfbuzz> |
| Mbed TLS (libmbedtls, libmbedcrypto, libmbedx509) | Apache-2.0 | <https://github.com/Mbed-TLS/mbedtls> |
| libpng | PNG Reference Library License v2 | <http://www.libpng.org/pub/png/libpng.html> |
| uchardet | MPL-1.1 (tri-licensed MPL/GPL/LGPL) | <https://www.freedesktop.org/wiki/Software/uchardet/> |
| libxml2 | MIT | <https://gitlab.gnome.org/GNOME/libxml2> |

**Provenance (this is also the "corresponding source" pointer required by the LGPL):**

- Prebuilt by **media-kit/libmpv-darwin-build**, which publishes ready-made LGPL
  libmpv builds for macOS (the same builds used by the `media_kit` Flutter plugin).
- Release **`v0.7.2`**, asset `libmpv-libs_v0.7.2_macos-arm64-video-full.tar.gz`.
  The **`video-full`** variant is the LGPL one; the `encodersgpl` variant is GPL
  (it bundles x264) and is deliberately **not** used.
- Corresponding source: <https://github.com/media-kit/libmpv-darwin-build> (build
  recipe) → mpv <https://github.com/mpv-player/mpv> and FFmpeg <https://ffmpeg.org>
  at the pinned versions. Also available on request via the issue tracker.
- Installed by `scripts/fetch-macos-libmpv-lgpl.sh`; see `docs/setup/libmpv-macos.md`.

These 18 dylibs are **LGPL or permissive only** — no GPL components. x264, x265,
and Rubber Band are deliberately absent (verified by inspecting the shipped
dylibs, 2026-07-17): x264/x265 are *encoders* a player never uses, and
pitch-preserving speed is handled by mpv's built-in `scaletempo2` (LGPL). The
libmpv client API header is ISC.

## Media engine — Windows Chromecast media plane (bundled FFmpeg sidecars)

| Component | License | Upstream |
|---|---|---|
| FFmpeg (`ffmpeg.exe`, `ffprobe.exe`, bundled as Tauri sidecar binaries) | **LGPL-2.1-or-later / LGPL-3.0-or-later** (BtbN's `win64-lgpl` build — no `--enable-gpl`) | <https://ffmpeg.org> |

These are the same FFmpeg tools used by casting's local media server (`cast_server/`, see
[docs/architecture/casting.md](docs/architecture/casting.md)) to probe source media and, when a
Chromecast can't decode a file as-is, remux or hardware-transcode it on the fly. They are
distinct from the FFmpeg code statically linked into libmpv above — these ship as **separate,
unmodified executable files** invoked as ordinary child processes (never linked into the app
binary), so this is a "mere aggregation" use, not the closer-coupling case the libmpv sections
document provenance for regardless.

**Provenance:**

- Prebuilt by **BtbN/FFmpeg-Builds**, which publishes ready-made LGPL Windows FFmpeg binaries.
- Build: `ffmpeg-n8.1.2-34-g9b6c8969e0-win64-lgpl-8.1.zip` from the pinned release tag
  `autobuild-2026-08-03-14-02` at <https://github.com/BtbN/FFmpeg-Builds/releases> — installed
  (and its LGPL configuration verified) by `tools/fetch-ffmpeg-win.sh`, which pins the tag and
  the archive's SHA-256 and refuses any GPL-configured artifact. BtbN prunes old auto-builds,
  so release builds install a byte-identical copy of that archive's `ffmpeg.exe`/`ffprobe.exe`
  from the developer's own archive (`win-ffmpeg-lgpl-autobuild-2026-08-03-14-02.zip`, SHA256
  `4784d2abc45dd7ecf3b1ae8949e5c266166d138d780ff4ae4f00f6375b4da500`); the LGPL check runs on install.
- Version string (from `ffmpeg -version`): **`n8.1.2-34-g9b6c8969e0-20260803`**.
- Built with `--disable-libx264 --disable-libx265` and no other GPL-only components (`--enable-gpl`
  is not set) — verified via the build's own `-version` banner, which lists its `configure` flags.
- Corresponding source: <https://ffmpeg.org> (upstream FFmpeg) at the pinned commit encoded in the
  version string above, via the BtbN build recipe: <https://github.com/BtbN/FFmpeg-Builds>. Also
  available on request via the issue tracker.
- No source modifications; the binaries are used exactly as downloaded, invoked as separate OS
  processes (never dynamically or statically linked into `src-tauri`'s own binary).

## Media engine — macOS casting media plane (bundled FFmpeg sidecars)

| Component | License | Upstream |
|---|---|---|
| FFmpeg 8.1.2 (`ffmpeg` / `ffprobe` sidecar executables, built `--disable-gpl`) | **LGPL-2.1-or-later** | <https://ffmpeg.org> |
| dav1d 1.5.4 (AV1 decoder, statically linked) | BSD-2-Clause | <https://code.videolan.org/videolan/dav1d> |
| libass 0.17.5 (subtitle renderer, statically linked) | ISC | <https://github.com/libass/libass> |
| FreeType 2.14.3 (statically linked) | FTL (BSD-style, with credit) | <https://freetype.org> |
| FriBidi 1.0.16 (statically linked) | LGPL-2.1-or-later | <https://github.com/fribidi/fribidi> |
| HarfBuzz 14.3.0 (statically linked) | MIT-derived ("Old MIT") | <https://github.com/harfbuzz/harfbuzz> |

Same role as the Windows sidecars above (probe + remux/transcode for casting), same
"mere aggregation" relationship to the app: separate, separately-invoked executables,
never linked into `src-tauri`'s binary. Unlike Windows there is no off-the-shelf LGPL
macOS FFmpeg build, so these are compiled from source.

**Provenance:**

- Built from unmodified upstream release tarballs by `scripts/build-macos-ffmpeg-lgpl.sh`,
  which pins every version listed above **and each tarball's SHA-256**, and refuses to
  install a result whose `-version` banner shows `--enable-gpl`/`--enable-nonfree` or any
  x264/x265 reference — the same refusal model as `tools/fetch-ffmpeg-win.sh`.
- Configured `--disable-gpl` (shown in the binary's own `-version` configuration line);
  no GPL components are compiled in. Hardware H.264 encoding uses Apple's VideoToolbox
  system framework; TLS uses Apple's SecureTransport system framework; fonts resolve via
  CoreText (no fontconfig).
- The third-party libraries in the table are **statically linked into the sidecar
  executables** (which link only macOS system frameworks and `/usr/lib` beyond that);
  all are LGPL-compatible permissive licenses except FriBidi, which is itself LGPL.
- Corresponding source: the pinned upstream release tarballs named in
  `scripts/build-macos-ffmpeg-lgpl.sh` (ffmpeg.org, VideoLAN, GitHub releases,
  Savannah). Also available on request via the issue tracker.

## Services (attribution)

- **TMDB** — this application uses TMDB and the TMDB APIs but is not
  endorsed, certified, or otherwise approved by TMDB.
  <https://www.themoviedb.org>
- **OpenSubtitles** — subtitle search and downloads are provided by
  OpenSubtitles. <https://www.opensubtitles.com>

## LGPL notice

**No GPL-licensed components are distributed with this application.** On both
platforms the media engine is an **LGPL** build of libmpv (mpv `-Dgpl=false`
linked against an LGPL FFmpeg); the GPL-only pieces — x264, x265, Rubber Band —
are deliberately excluded. This was verified by inspecting the shipped binaries
on each platform (2026-07-17). Both platforms also bundle a separate LGPL FFmpeg
build (`ffmpeg.exe`/`ffprobe.exe` on Windows; `ffmpeg`/`ffprobe` on macOS) as
casting sidecar executables — no `--enable-gpl`, no GPL-only components either.

The LGPL components are redistributed as **unmodified, dynamically loaded shared
libraries** (`libmpv-2.dll` on Windows; `libmpv.dylib` and its sibling dylibs in
the app bundle's `Frameworks` folder on macOS) or, for the FFmpeg sidecars,
**separately-invoked executables** (`ffmpeg.exe`/`ffprobe.exe` on Windows,
`ffmpeg`/`ffprobe` on macOS, run as ordinary child processes, never linked into
the app binary; the macOS pair is compiled from unmodified pinned upstream
sources by `scripts/build-macos-ffmpeg-lgpl.sh`). Accordingly,
under the LGPL you may replace them with your own modified builds, and may
reverse engineer and modify the application as necessary to debug such
modifications — see Section 3 of the `LICENSE` file, which preserves these
rights explicitly.

License texts: LGPL-2.1 <https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html>
· LGPL-3.0 <https://www.gnu.org/licenses/lgpl-3.0.html>.

Complete corresponding source for the LGPL components is available from the
pinned upstream builds identified in the two "Provenance" blocks above, or on
request via the issue tracker.
