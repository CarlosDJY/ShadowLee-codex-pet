# ShadowLee Codex Pet

Fan-made animated custom pet for the Codex desktop app.

## Preview

![ShadowLee contact sheet](previews/ShadowLee/contact-sheet.png)

## Install

Install ShadowLee manually:

```powershell
$pet = "ShadowLee"
$dest = Join-Path $env:USERPROFILE ".codex\pets\$pet"
New-Item -ItemType Directory -Force -Path (Split-Path $dest) | Out-Null
Remove-Item -LiteralPath $dest -Recurse -Force -ErrorAction SilentlyContinue
Copy-Item -LiteralPath ".\pets\$pet" -Destination $dest -Recurse
```

Then restart Codex Desktop or refresh the pet selector.

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
