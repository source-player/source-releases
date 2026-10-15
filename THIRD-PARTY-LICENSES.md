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
| Rust crate dependencies | predominantly MIT OR Apache-2.0 | crates.io |

## Frontend assets

| Component | License | Upstream |
|---|---|---|
| Lucide icons | ISC | <https://github.com/lucide-icons/lucide> |
| Fluent Emoji (Flat), Microsoft — the Explorer's emoji icons (`public/emoji/`) | MIT | <https://github.com/microsoft/fluentui-emoji> |
| Twemoji graphics — the Explorer's flag emoji (`public/emoji/1f1*.svg`), © Twitter, Inc. and other contributors | CC-BY 4.0 | <https://github.com/jdecked/twemoji> |
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
- Release tag: **`2026-09-12-14f2d48cbc`**, asset
  `mpv-dev-lgpl-x86_64-20260912-git-14f2d48cbc.7z`
  (SHA256 `455965297ba3f5906a63cd2b219442685be45528a1fe806e4b228147881e41cb`).
  Upstream prunes old releases, so release builds install a byte-identical copy of that
  artifact's contents from the developer's own archive (`win-libmpv-lgpl-2026-09-12-14f2d48cbc.zip`,
  SHA256 `d7d444c12adb942dffd7934bcb02c8b53e14e606c2d919e6f7ea76aacffceaa7`); the engine
  version string and the LGPL configuration are verified on install.
- Engine version string: `mpv v0.41.0-1044-g14f2d48cb`.
- Corresponding source: <https://github.com/zhongfly/mpv-winbuild> (build
  recipe) → mpv <https://github.com/mpv-player/mpv> and FFmpeg
  <https://ffmpeg.org> at the pinned commits. Also available on request via
  the issue tracker.

The single `libmpv-2.dll` statically links LGPL/permissive libraries only:
LGPL FFmpeg (built **without** `--enable-gpl`), libass (ISC), dav1d
(BSD-2-Clause), libplacebo (LGPL), SVT-AV1 (BSD), and friends. **No GPL-only
components** — x264, x265, and Rubber Band are deliberately excluded (verified
by binary inspection of the shipped DLL, 2026-07-17 and again 2026-10-03 for the current pin,
and checked automatically on every install). x264/x265 are *encoders*
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

These 18 dylibs are **LGPL or permissive only** — no GPL components. x264, x265,
and Rubber Band are deliberately absent (verified by inspecting the shipped
dylibs, 2026-07-17): x264/x265 are *encoders* a player never uses, and
pitch-preserving speed is handled by mpv's built-in `scaletempo2` (LGPL). The
libmpv client API header is ISC.

## Media engine — Windows Chromecast media plane (bundled FFmpeg sidecars)

| Component | License | Upstream |
|---|---|---|
| FFmpeg (`ffmpeg.exe`, `ffprobe.exe`, bundled as Tauri sidecar binaries) | **LGPL-3.0-or-later** (`--enable-version3`, no `--enable-gpl`, no `--enable-nonfree`) | <https://ffmpeg.org> |

These are the same FFmpeg tools used by casting's local media server to probe source media and, when a
Chromecast can't decode a file as-is, remux or hardware-transcode it on the fly. They are
distinct from the FFmpeg code statically linked into libmpv above — these ship as **separate,
unmodified executable files** invoked as ordinary child processes (never linked into the app
binary), so this is a "mere aggregation" use, not the closer-coupling case the libmpv sections
document provenance for regardless.

**Provenance:**

- Built by us from unmodified upstream FFmpeg source inside
  **BtbN/FFmpeg-Builds**' `win64-lgpl-8.1` Docker image (pinned by digest), which
  supplies the mingw-w64 toolchain and the statically linked LGPL/permissive dependencies listed
  below. Configured `--disable-everything` and then only the components casting uses (every
  decoder/demuxer/protocol is kept; encoders, muxers and filters are cut to the cast pipeline), so
  the binaries are ~38 MB each instead of the stock build's 113 MB. The exact `configure` line is
  in each binary's own `-version` banner.
- Release builds install the archive `win-ffmpeg-lgpl-n8.1.2-34-g9b6c8969e0-source-slim3.zip` from
  the developer's own archive, pinned by SHA-256; the install refuses any GPL- or
  nonfree-configured artifact (or one missing a component casting depends on).
- Version string (from `ffmpeg -version`): **`n8.1.2-34-g9b6c8969e0-source-slim3`**. The
  same binaries also make local-folder thumbnails (one JPEG frame per video; HDR frames are
  tone-mapped with zimg).
- Statically linked libraries: dav1d (BSD-2-Clause), libass (ISC) with Fontconfig (MIT-style),
  libunibreak (zlib), FreeType (FTL), HarfBuzz (MIT) and FriBidi (LGPL-2.1-or-later), libxml2
  (MIT), zlib (zlib), liblzma (0BSD), libiconv (LGPL-2.1-or-later), GMP (LGPL-3.0-or-later), SRT
  (MPL-2.0) with OpenSSL (Apache-2.0), oneVPL dispatcher (MIT), zimg 3.0.6 (WTFPL — the `zscale`
  filter; not on FFmpeg's GPL, nonfree or version3 library lists); nv-codec-headers (MIT) and the
  AMF headers (MIT) are headers only.
- No GPL-only components: `--enable-gpl` and `--enable-nonfree` are not set, and libx264/libx265
  are not built.
- Corresponding source: upstream FFmpeg <https://github.com/FFmpeg/FFmpeg> at commit
  `9b6c8969e05b4f0b29f0f85cd501be6b3e582e6b` (`n8.1.2-34-g9b6c8969e0`, branch `release/8.1`),
  built with the dependency recipes of <https://github.com/BtbN/FFmpeg-Builds>. Also available
  on request via the issue tracker.
- No source modifications; the binaries are invoked as separate OS processes (never dynamically
  or statically linked into `src-tauri`'s own binary).

## Media engine — macOS casting media plane (bundled FFmpeg sidecars)

| Component | License | Upstream |
|---|---|---|
| FFmpeg 8.1.2 (`ffmpeg` / `ffprobe` sidecar executables, built `--disable-gpl`) | **LGPL-2.1-or-later** | <https://ffmpeg.org> |
| dav1d 1.5.4 (AV1 decoder, statically linked) | BSD-2-Clause | <https://code.videolan.org/videolan/dav1d> |
| libass 0.17.5 (subtitle renderer, statically linked) | ISC | <https://github.com/libass/libass> |
| FreeType 2.14.3 (statically linked) | FTL (BSD-style, with credit) | <https://freetype.org> |
| FriBidi 1.0.16 (statically linked) | LGPL-2.1-or-later | <https://github.com/fribidi/fribidi> |
| HarfBuzz 14.3.0 (statically linked) | MIT-derived ("Old MIT") | <https://github.com/harfbuzz/harfbuzz> |
| zimg 3.0.6 (the `zscale` filter for HDR thumbnails, statically linked; sidecars built from Oct 2026) | WTFPL | <https://github.com/sekrit-twc/zimg> |

Same role as the Windows sidecars above (probe + remux/transcode for casting), same
"mere aggregation" relationship to the app: separate, separately-invoked executables,
never linked into `src-tauri`'s binary. Unlike Windows there is no off-the-shelf LGPL
macOS FFmpeg build, so these are compiled from source.

**Provenance:**

- Built from unmodified upstream release tarballs, pinned to every version listed above
  **and each tarball's SHA-256**; the build refuses to install a result whose `-version`
  banner shows `--enable-gpl`/`--enable-nonfree` or any x264/x265 reference — the same
  check the Windows sidecars get.
- Configured `--disable-gpl` (shown in the binary's own `-version` configuration line);
  no GPL components are compiled in. Hardware H.264 encoding uses Apple's VideoToolbox
  system framework; TLS uses Apple's SecureTransport system framework; fonts resolve via
  CoreText (no fontconfig).
- The third-party libraries in the table are **statically linked into the sidecar
  executables** (which link only macOS system frameworks and `/usr/lib` beyond that);
  all are LGPL-compatible permissive licenses except FriBidi, which is itself LGPL.
- Corresponding source: the upstream release tarballs of the versions in the table above
  (ffmpeg.org, VideoLAN, GitHub releases, Savannah). Also available on request via the
  issue tracker.

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
sources). Accordingly,
under the LGPL you may replace them with your own modified builds, and may
reverse engineer and modify the application as necessary to debug such
modifications — see Section 3 of the `LICENSE` file, which preserves these
rights explicitly.

License texts: LGPL-2.1 <https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html>
· LGPL-3.0 <https://www.gnu.org/licenses/lgpl-3.0.html>.

Complete corresponding source for the LGPL components is available from the
pinned upstream sources identified in the four "Provenance" blocks above, or on
request via the issue tracker.
