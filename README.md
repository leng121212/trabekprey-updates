# TrabekPrey Updates

This repository hosts update metadata and GitHub Releases for the TrabekPrey desktop app.

## Files

- `version.json` is read by the desktop app to check for updates.
- Release assets should contain `TrabekPrey_TTS.exe`.

## Publish A New Update

1. Build the updater:

```powershell
Set-Location "D:\Desktop\VoxCPM2\Tools Text to Speech"
.\build_updater_nuitka.bat
```

2. Build the main app:

```powershell
.\build_nuitka.bat
```

3. Get the SHA256 of the final EXE:

```powershell
Get-FileHash ".\dist\TrabekPrey_TTS.exe" -Algorithm SHA256
```

4. Create a GitHub Release in this repository.

Example:

- Tag: `v2.0.1`
- Asset: `TrabekPrey_TTS.exe`

5. Update `version.json`.

Example:

```json
{
  "version": "2.0.1",
  "download_url": "https://github.com/leng121212/trabekprey-updates/releases/download/v2.0.1/TrabekPrey_TTS.exe",
  "sha256": "PASTE_SHA256_HERE",
  "notes": "Added GitHub auto update support."
}
```

6. Commit and push `version.json`.

The app reads this URL:

```text
https://raw.githubusercontent.com/leng121212/trabekprey-updates/main/version.json
```
