# ShadowLee Codex 桌宠

[中文](README.md) | [English](README.en.md)

ShadowLee 是一个为 Codex Desktop 制作的自定义动态桌宠。角色基于白发、蓝色发尾、黑色圆形耳饰的 Q 版布偶形象生成，包含 Codex 所需的完整动画状态。

## 预览

![ShadowLee contact sheet](previews/ShadowLee/contact-sheet.png)

## 安装

在 PowerShell 中运行：

```powershell
$pet = "ShadowLee"
$dest = Join-Path $env:USERPROFILE ".codex\pets\$pet"
New-Item -ItemType Directory -Force -Path (Split-Path $dest) | Out-Null
Remove-Item -LiteralPath $dest -Recurse -Force -ErrorAction SilentlyContinue
Copy-Item -LiteralPath ".\pets\$pet" -Destination $dest -Recurse
```

安装后重启 Codex Desktop，或者刷新 pet selector，然后选择 `ShadowLee`。

## 文件结构

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

## 校验

```powershell
python .\scripts\validate_catalog.py
```

预期输出：

```text
catalog ok: 1 pet(s)
```

## 规格

该桌宠遵循当前 Codex 自定义 pet spritesheet 规格：

- 格式：带透明通道的 WebP。
- 总尺寸：`1536x1872`。
- 网格：8 列 x 9 行。
- 单格尺寸：`192x208`。
- 未使用格子保持完全透明。

## 说明

- `running-left` 由 `running-right` 镜像派生，以保持奔跑动作一致。
- 预览与 QA 文件位于 `previews/ShadowLee/`。
- 本仓库只包含本地 Codex Desktop 自定义 pet 包，不包含 Codex Desktop 应用本体。
