# GitHub 仓库上传指南

目标仓库：

`https://github.com/tianxiayiran/zhiku`

## 方式一：网页上传

1. 打开 GitHub 仓库。
2. 点击 `Add file` → `Upload files`。
3. 上传本目录下的 `README.md`、`themes/`、`releases/` 和 `marketing/`。
4. 提交说明建议：

`Add Starship Command Deck DreamSkin 5.0.0`

## 方式二：Git 命令

```powershell
git clone https://github.com/tianxiayiran/zhiku.git
Set-Location zhiku

Copy-Item -Path "C:\Users\27837\Documents\Codex\codex智脑提升\github-repo-ready\*" -Destination . -Recurse -Force

git add .
git commit -m "Add Starship Command Deck DreamSkin 5.0.0"
git push origin main
```

## 推荐后续结构

```text
zhiku/
├─ README.md
├─ themes/
│  └─ starship-command-deck-night/
│     ├─ manifest.json
│     ├─ theme.json
│     ├─ theme.css
│     └─ background.webp
├─ releases/
│  └─ starship-command-deck-night-5.0.0.zip
└─ marketing/
   ├─ listing-zh-CN.md
   ├─ listing-en-US.md
   └─ studio-submit.md
```

## 发布后需要做的事

1. 在 DreamSkin Studio 提交审核。
2. 审核通过后，把 DreamSkin 主题详情页链接补进仓库 README。
3. 后续版本继续放在 `releases/`，不要覆盖旧版本。
4. 更新主题时同时更新 `manifest.json` 的版本、文件哈希和 `theme.json` 内容。
