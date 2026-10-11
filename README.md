# CraftPulse

CraftPulse is a small, tray-only Discord Rich Presence companion for the ArtCraft creative apps. It detects PhotoCraft, VectorCraft, FilmCraft, LightCraft, PdfCraft, EffectCraft, and DesignCraft, then shows the current document and activity in Discord.

## Install

Download the Windows build at `target/x86_64-pc-windows-gnu/release/craftpulse.exe`, or build for your platform with:

```sh
cargo build --release
```

Run CraftPulse once. It appears in the system tray without opening a main window. Left-click the tray icon to open settings; right-click for settings and Quit.

Discord must be running. Rich Presence artwork keys are configured in the ArtCraft Discord application's Rich Presence assets. The default keys are `photocraft`, `vectorcraft`, `filmcraft`, `lightcraft`, `pdfcraft`, `effectcraft`, `designcraft`, and `artcraft`.

## Privacy and settings

Settings are stored in the OS config directory under `CraftPulse/config.toml` and reloaded when edited. The settings page listens on a random loopback port and requires a per-run token. Project names can be hidden globally, per application, or with `hide_patterns` regular expressions.

Applications can write optional hints to `CraftPulse/hints/<app>.json`, for example `photocraft.json`:

```json
{"action":"Exporting","document":"Poster"}
```

Write the file atomically (write a temporary file then rename it). Values are capped at 100 characters and hints older than 120 seconds are ignored.

## Build

```sh
cargo test
cargo clippy --all-targets -- -D warnings
cargo build --release --target x86_64-pc-windows-gnu
```
