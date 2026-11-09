<p align="center">
  <img src="assets/icon.png" width="128" alt="derust icon">
</p>

<h1 align="center">derust</h1>

<p align="center">A fast, free and open source alternative to CleanMyMac for macOS, written in Rust.</p>

![derust](docs/screenshot.png)

## Features

Requires macOS 11 or newer (Apple silicon and Intel).

- **System Junk**: caches, logs, Xcode leftovers and broken launch agents
- **Disk Explorer**: browse your whole disk by size and remove what you don't need
- **Applications**: uninstall apps together with their leftover files

Everything goes to the Trash, so nothing is lost by accident.

## Performance

Scans use `getattrlistbulk` and run in parallel on the performance cores. A full disk with about 2.3 million files takes around 10 seconds on an M4 Pro.

The release binary is about **7.5 MB**.

## Install

Download the latest `derust-<version>-macos.dmg` from the [Releases page](https://github.com/Kencho5/DeRust/releases/latest), open it, and drag derust to Applications.

The app is signed ad hoc and not notarized, so on first launch macOS may block it. Right-click the app, choose Open, then confirm.

## Building

Requires macOS, Rust 1.85+ (edition 2024) via rustup, and the Xcode Command Line Tools.

```sh
cargo build --release
./target/release/derust
```

To build a universal `derust.app` with a `.dmg` and `.zip`, run `./scripts/bundle.sh`. The result is written to `target/dist/`.

## Permissions

Grant Full Disk Access in System Settings → Privacy & Security for complete results. If you run the binary from a terminal, grant it to the terminal app instead.

## Why

This is something I built for myself to replace CleanMyMac, which is paid. I'm sharing it in case it's useful to anyone else.

## AI Usage

- **UI**: copied from my startup. A designer and I made it.
- **Scanning and categorization**: copied one to one from another project of mine that I wrote years ago. I reviewed it manually and changed the removal logic so files go to the Trash instead of being permanently deleted.
- **Iced UI implementation**: written with AI. This is the only part I haven't fully reviewed. It's a thin layer, and every removal goes through the Trash, so a mistake there is recoverable.

## License

[MIT](LICENSE). Space Grotesk is licensed under the [SIL Open Font License](assets/fonts/OFL.txt).
