# ShadowLee Codex 桌宠

[中文](README.md) | [English](README.en.md)

这个仓库包含两个为 Codex Desktop 制作的自定义动态桌宠：

- `ShadowLee`：白发、蓝色发尾、黑色圆形耳饰的 Q 版布偶桌宠。
- `ShadowLeeGlasses`：戴墨镜的 ShadowLee 变体。

两个桌宠分别放在独立目录中，可以单独安装或同时安装。

## 预览

### ShadowLee

![ShadowLee contact sheet](previews/ShadowLee/contact-sheet.png)

### ShadowLeeGlasses

![ShadowLeeGlasses contact sheet](previews/ShadowLeeGlasses/contact-sheet.png)

## 安装

在 PowerShell 中选择要安装的桌宠：

```powershell
$pet = "ShadowLee"
# 或者：
# $pet = "ShadowLeeGlasses"

$dest = Join-Path $env:USERPROFILE ".codex\pets\$pet"
New-Item -ItemType Directory -Force -Path (Split-Path $dest) | Out-Null
Remove-Item -LiteralPath $dest -Recurse -Force -ErrorAction SilentlyContinue
Copy-Item -LiteralPath ".\pets\$pet" -Destination $dest -Recurse
```

安装后重启 Codex Desktop，或者刷新 pet selector，然后选择对应桌宠。

## 文件结构

```text
pets/
  ShadowLee/
    pet.json
    spritesheet.webp
  ShadowLeeGlasses/
    pet.json
    spritesheet.webp
previews/
  ShadowLee/
    contact-sheet.png
    review.json
    validation.json
  ShadowLeeGlasses/
    contact-sheet.png
    review.json
    validation.json
catalog.json
scripts/
```

## 校验

```powershell
python .\scripts\validate_catalog.py
```

预期输出：

```text
catalog ok: 2 pet(s)
```

## 规格

两个桌宠都遵循当前 Codex 自定义 pet spritesheet 规格：

- 格式：带透明通道的 WebP。
- 总尺寸：`1536x1872`。
- 网格：8 列 x 9 行。
- 单格尺寸：`192x208`。
- 未使用格子保持完全透明。

## 说明

- 两个桌宠都使用 OpenAI `hatch-pet` 工作流生成。
- `running-left` 由 `running-right` 镜像派生，以保持奔跑动作一致。
- 预览与 QA 文件位于 `previews/<pet-id>/`。
- 本仓库只包含本地 Codex Desktop 自定义 pet 包，不包含 Codex Desktop 应用本体。
