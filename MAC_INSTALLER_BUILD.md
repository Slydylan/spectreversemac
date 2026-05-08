# Spectreverse Simulator Deck — macOS Installer Build

This repository contains the macOS desktop-packaged Spectreverse Simulator Deck.

The app is still the same browser-native simulator payload: `index.html`, `src/`, `data/`, `runtime_config.json`, and the Electron local static server wrapper in `electron/main.cjs`.

## Build outputs

The GitHub Actions workflow builds two macOS variants:

| Artifact | Use for |
|---|---|
| `spectreverse-mac-arm64` | Apple Silicon Macs: M1, M2, M3, M4, later Apple chips |
| `spectreverse-mac-x64` | Older Intel Macs |

Inside each artifact zip, expect a `.dmg` and a `.zip` build. The `.dmg` is the normal Mac installer-style package. The `.zip` contains the `.app` bundle directly.

## How to build in GitHub

1. Put all project files at the repository root.
2. Commit `.github/workflows/build-mac-installer.yml`.
3. Open GitHub → Actions → Build Mac Installer.
4. Click Run workflow.
5. Download either `spectreverse-mac-arm64` or `spectreverse-mac-x64` from the completed workflow run.

## How a Mac user installs it

For the `.dmg`:

1. Download the correct artifact.
2. Unzip the GitHub artifact.
3. Open the `.dmg`.
4. Drag `Spectreverse Simulator Deck.app` into `Applications` if prompted.
5. Open it from Applications.

## Unsigned app warning

This build is intentionally unsigned and not notarized. A tester may need to right-click the app and choose Open, then confirm the warning. This is expected for a local unsigned test build. For broad public distribution, add Apple Developer signing and notarization.

## Local build on a Mac

```bash
npm ci
npm run check
npm run desktop:build:mac
```

For one architecture:

```bash
npm run desktop:build:mac:arm64
npm run desktop:build:mac:x64
```

## What is preserved from the Windows build

- Same simulator code.
- Same Electron local server wrapper.
- Same autonomy governor.
- Same nested phenomena memory layer.
- Same high-cap structure ecology.
- Same browser/GitHub Pages-compatible source layout.

## Notes

- Apple Silicon users should test the `arm64` build first.
- Intel users should test the `x64` build.
- The `.dmg` is the cleanest thing to send to a normal Mac tester.
- Do not send `latest*.yml` or `.blockmap` files for a one-off manual test.
