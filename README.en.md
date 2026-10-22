# 01 Launcher · Release repository (01-release)

This repository hosts **only** the version index and the installer of **01 Launcher** (closed-source; no source code here).

- The installer (139.5 MB) lives in **Releases** — GitHub's 100 MB limit applies to files in the git repository, but a single release asset can be up to 2 GB, so the zip is not committed.
- The repository itself only tracks `version-index.json` plus docs, which keeps clones small.
- ⚠️ **Proprietary software**: personal installation and use are permitted; copying, redistributing, reselling, decompiling, unpacking (including `app.asar`) or rebranding are **not**. See [LICENSE](LICENSE).

## Contents

| File | Purpose |
|---|---|
| `version-index.json` | Version index. The launcher reads it on startup to detect updates (URL is built into the app) |
| Release asset `01-launcher-x.y.z.zip` | The launcher itself — extract and run (**one single zip, no split volumes**) |

## Download & install (1.0.0)

1. Open **Releases** on the right → `v1.0.0` → download `01-launcher-1.0.0.zip` (139.5 MB, single file, no merging needed).
2. Extract to an **ASCII-only path** (e.g. `D:\01-comfyui`; avoid `C:\Program Files` and non-ASCII paths).
3. Run `01.exe` and follow the first-run wizard to pick the runtime and the ComfyUI folder.

**SHA-256 (recommended check after download)**

```
d65996ec74631e8b07c413c9ca88654da2c4b1801fbbef810ed48ffce8977c42
```

Windows (PowerShell):

```powershell
Get-FileHash .\01-launcher-1.0.0.zip -Algorithm SHA256
```

> A mismatch means the download was corrupted — delete it and download again.

## Index format

```json
{
  "schemaVersion": 1,
  "latest": {
    "version": "1.0.0",
    "url": "direct download URL (release asset)",
    "sha256": "installer SHA-256 (lowercase hex, 64 chars)",
    "notes": "release notes",
    "publishedAt": "2026-10-22",
    "mandatory": false
  }
}
```

## Releasing (maintainers)

1. Package → get `01-launcher-x.y.z.zip`;
2. Create a GitHub Release (tag e.g. `v1.0.0`) and upload the zip as an **asset**;
3. Update `version` / `url` / `sha256` / `notes` / `publishedAt` in `version-index.json` and commit;
4. On the user side: startup check → download → SHA-256 verify → restart & replace (models, nodes and settings are preserved).

Asset URL pattern:

```
https://github.com/<owner>/01-release/releases/download/<tag>/01-launcher-x.y.z.zip
```

## Version history

| Version | Date | Notes |
|---|---|---|
| 1.0.1 | 2026-10-22 | Fixed: startup update check wasted ~24 s (mirror prefix applied twice); installer download now retries across mirrors (ghproxy → gh-proxy → ghfast → direct). Improved: redesigned startup check screen (680×350 wide card, no full-screen red on failure, 5 s auto-enter), sidebar navigation now resets to the first page |
| 1.0.0 | 2026-10-22 | First release: download manager (resume / tri-state remove), workflow check & one-click repair, node/model/kernel/component managers, automatic launch-arg tuning, error-doctor noise filtering, folder mapping (revocable), launcher self-update |

## License & restrictions

**This is proprietary software, not open source.** Full terms in [LICENSE](LICENSE). In short:

| Allowed | NOT allowed (without written permission) |
|---|---|
| Install and run it on your own devices | Copy, publicly redistribute, resell or rent it |
| Keep a backup of the installer you downloaded | Decompile, disassemble or unpack it (including `app.asar`) and reuse the code or assets |
| Pass the **unmodified** installer plus this license to a friend | Rebrand it, modify it and publish it, or embed it in a commercial product |

