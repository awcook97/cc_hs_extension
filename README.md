# HubSpot CompanyCam Extension Releases

This public repository is the distribution channel for the extension.

Source code lives in the private development repository.
Release artifacts are built locally, then uploaded here as GitHub Release assets.

## What Lives Here

- Public release tags and assets
- Firefox update feed (`updates.json`)
- Latest signed Firefox package (`firefox/latest/hubspot-companycam-viewer.xpi`)
- Issue templates for bugs/features

## One-Time Setup (Repo Settings)

1. Enable GitHub Pages for this repo.
2. Set Pages source to `main` branch root.
3. Confirm this URL works:
- `https://awcook97.github.io/cc_hs_extension/updates.json`

4. Add repository secrets:
- `CWS_CLIENT_ID`
- `CWS_CLIENT_SECRET`
- `CWS_REFRESH_TOKEN`
- `CWS_PUBLISHER_ID`
- `CWS_EXTENSION_ID`
- `AMO_API_KEY`
- `AMO_API_SECRET`

## Per Release

1. In the private source repo, build assets locally:
- `bash build.sh release`

2. In this public repo, create release tag `vX.Y.Z`.

3. Upload these files from the private repo `build/` folder to that release:
- `hubspot-companycam-viewer-X.Y.Z-standard_dev.zip`
- `hubspot-companycam-viewer-X.Y.Z-firefox.xpi`

4. Publish the release.

5. Workflow `.github/workflows/publish.yml` runs and does:
- Chrome Web Store upload + publish
- Firefox signing
- `updates.json` + `firefox/latest/hubspot-companycam-viewer.xpi` update
