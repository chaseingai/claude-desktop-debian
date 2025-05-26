# Repository Reference: claude-desktop-debian

This repository contains shell scripts that repackage the Windows version of **Claude Desktop** so it can run on Debian-based distributions or as an AppImage.

## Key Files

- `build.sh` – main entry point. Detects architecture, installs dependencies, downloads the Windows installer and extracts resources, replaces the native module with a stub, then delegates to packaging scripts.
- `scripts/build-deb-package.sh` – creates a `.deb` package with icons, launcher, and post-install steps.
- `scripts/build-appimage.sh` – builds an AppImage by creating an AppDir, bundling Electron, and generating `AppRun` and metadata.
- GitHub workflows in `.github/workflows/` build packages on CI and publish releases when a `v*` tag is pushed.

## Building Manually

From `README.md`:

```bash
# Clone and build (defaults to .deb)
./build.sh

# Build an AppImage and keep intermediate files
./build.sh --build appimage --clean no
```

The build script downloads and unpacks the Windows installer, substitutes the native module and repackages everything. See README for details.

## Useful README Sections

- The project is an *unofficial* build script for Debian/Ubuntu systems and provides packaging instructions. 【F:README.md†L18-L20】【F:README.md†L38-L61】
- Steps performed during the build are listed. 【F:README.md†L147-L174】

## Architecture Detection

`build.sh` detects `amd64` or `arm64` and sets download URLs accordingly. 【F:build.sh†L4-L26】

## End of Build Output

Upon completion the script prints installation instructions for the generated package. 【F:build.sh†L472-L512】


