# doX LMU Overlays Releases

Public distribution repository for doX LMU Overlays automatic updates.

This repository does not contain the plugin source code or the normal installer
EXE. It provides the published update package used by the doX plugin inside
SimHub.

## How automatic updates work

The plugin reads `manifest.json` from the `main` branch. When a newer pack
version is available, the manifest points to an immutable ZIP asset in a
GitHub Release.

The active manifest contains:

- The pack version.
- The GitHub Release ZIP URL and SHA-256 checksum.
- The release page URL.
- Discord announcement text and the OverTake page URL used in Discord.

`packageUrl` is used only by the automatic updater. `discordUrl` is used only
by the Discord announcement and should point to the OverTake download page.

## Update package layout

```text
doX-update-<version>.zip
|- package.json
|- payload/
|  |- doX.LMU_SessionDataPlugin.dll
|  |- doX-LMU-Overlays.version
|  `- DashTemplates/
`- updater/
   `- doX-PackUpdater.exe
```

The updater is extracted to a temporary folder only when an update is applied.
It is not permanently installed in SimHub and does not run with Windows.

## Publishing a pack update

1. Build the update ZIP from the `doX LMU Installer` repository.
2. Create a GitHub Release with tag `v<version>`.
3. Upload `doX-update-<version>.zip` to that release.
4. Update `manifest.json` with the version, ZIP URL, SHA-256 checksum, release
   URL, OverTake URL, and release notes.
5. Commit the manifest after the release asset is available.

Updating `manifest.json` triggers the Discord workflow. To repeat an existing
announcement, run **Post update JSON to Discord** manually with
`force_post=true`.

OverTake remains the official page for release notes and manual installer
downloads.