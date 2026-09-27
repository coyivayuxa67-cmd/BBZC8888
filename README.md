# 星舰指挥台主题资源

这个仓库用于保存 DreamSkin 投稿包、发布版本和宣传资料。

## 目录

- `themes/starship-command-deck/`：**当前投稿源文件**，themeId 为
  `starship-command-deck`，用于更新已发布的主题
- `releases/starship-command-deck-5.0.0.zip`：**当前投稿 ZIP**
- `themes/starship-command-deck-night/`、`releases/starship-command-deck-night-5.0.0.zip`：
  备选包，themeId 为 `starship-command-deck-night`，会另起一个新条目，暂未使用
- `marketing/`：中文/英文宣传文案、Studio 投稿步骤和 GitHub 上传指南

## 当前主题

**星舰指挥台：夜航离港**

从地球夜景启航的未来舰桥静态主题。包含一张 8K WebP 背景、深色语义色和经过 DreamSkin Safe CSS 校验的组件样式。

## 两个包的区别

两个包的背景图、配色、Safe CSS 完全相同，只有 themeId 不同：

| 包 | themeId | 效果 |
| --- | --- | --- |
| `starship-command-deck-5.0.0.zip` | `starship-command-deck` | 更新已有的“星舰指挥台”（保留下载数与收藏） |
| `starship-command-deck-night-5.0.0.zip` | `starship-command-deck-night` | 主题库里另起一个新条目 |

已发布的“星舰指挥台”当前为 `3.3.7`，2026-09-11 上线，822 次下载、4 次收藏。
本次投稿按“更新已有主题”处理，因此使用前者。

## 安装

使用 DreamSkin 客户端的普通 ZIP 导入功能选择：

`releases/starship-command-deck-5.0.0.zip`

DreamSkin Studio 也支持直接导入该 ZIP（页头“导入”按钮），导入后主题名、
ID、版本、平台、发布者、许可证、AI 声明、来源摘要、配色、Safe CSS 与
theme.json 会全部恢复，六项就绪检查一次通过。

## 兼容

- DreamSkin Skin API v1
- macOS / Windows 官方 Codex Desktop
- 不支持 Codex++ 用户脚本

## 说明

DreamSkin 版是静态视觉主题。六背景切换、六款舷窗、流星、外星飞船、任务树和输入舱动态效果属于 Codex++ 完整用户脚本版，不包含在 DreamSkin 包内。
