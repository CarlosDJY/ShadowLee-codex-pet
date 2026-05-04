# ShadowLee Codex Pet

[中文](README.md) | [English](README.en.md)

ShadowLee is a custom animated pet for Codex Desktop. The character is based on a white-haired chibi plush design with blue hair tips and black round ear buns, packaged with the full animation set expected by Codex.

## Preview

![ShadowLee contact sheet](previews/ShadowLee/contact-sheet.png)

## Install

Run this in PowerShell:

```powershell
$pet = "ShadowLee"
$dest = Join-Path $env:USERPROFILE ".codex\pets\$pet"
New-Item -ItemType Directory -Force -Path (Split-Path $dest) | Out-Null
Remove-Item -LiteralPath $dest -Recurse -Force -ErrorAction SilentlyContinue
Copy-Item -LiteralPath ".\pets\$pet" -Destination $dest -Recurse
```

Then restart Codex Desktop or refresh the pet selector, and choose `ShadowLee`.

## Files

```text
pets/
  ShadowLee/
    pet.json
    spritesheet.webp
previews/
  ShadowLee/
    contact-sheet.png
    review.json
    validation.json
catalog.json
scripts/
```

## Validate

```powershell
python .\scripts\validate_catalog.py
```

Expected result:

```text
catalog ok: 1 pet(s)
```

## Contract

The spritesheet follows the current Codex custom pet contract:

- Format: WebP with alpha.
- Dimensions: `1536x1872`.
- Grid: 8 columns x 9 rows.
- Cell size: `192x208`.
- Unused cells are fully transparent.

## Notes

- `running-left` was derived by mirroring `running-right` to preserve gait consistency.
- Preview and QA files are stored under `previews/ShadowLee/`.
- This repository only contains a local Codex Desktop custom pet package. It does not include Codex Desktop itself.
