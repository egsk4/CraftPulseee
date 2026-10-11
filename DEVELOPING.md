# Developing CraftPulse

## Prerequisites

- Rust stable and Cargo
- A system tray / desktop session for running the app
- On Linux, X11 and `xprop` are used to inspect window titles

## Commands

```sh
cargo test
cargo clippy --all-targets -- -D warnings
cargo build --release
```

The settings page is embedded from `web/settings.html`; rebuild the binary after changing it. Configuration data lives outside the executable under the platform configuration directory.

The CI workflow compiles Linux, Windows, and macOS targets. The Discord RPC worker is intentionally detached from the tray event loop so a blocked IPC call cannot prevent the user from quitting.
