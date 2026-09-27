# 发布记录

## 当前公开版本

| 项 | 值 |
| --- | --- |
| 主题名 | 星舰指挥台：夜航离港 |
| slug / themeId | `starship-command-deck` |
| 版本 | `5.0.0` |
| 线上版本 ID | `ver_50bbdac26bffa67b58c7` |
| 作者 | `yiran` / `usr_fea84bc4fb492297d8c7` |
| 提交时间 | 2026-09-27T11:57:43Z |
| 审核时间 | 2026-09-27T11:57:49Z（`system:ai-moderation`） |
| 状态 | `approved` |
| 下载 / 收藏 | 822 / 4（沿用旧版本，未重置） |
| 线上包 SHA256 | `e63568514cded7d10eea263b7cd89c271a3ab59eac5caad53b3302a107d30b40` |
| 线上包大小 | 564708 字节 |
| 背景图 SHA256 | `9f39aca876ef5e7dd51cc1f2de0481ecd9e974452ee639f71c22f8fdd0bb0084` |

客户端应用链接：

`dreamskin://apply?version=ver_50bbdac26bffa67b58c7`

## 版本历史

| 版本 | 版本 ID | 状态 | 背景图 |
| --- | --- | --- | --- |
| `5.0.0` | `ver_50bbdac26bffa67b58c7` | approved | `bg-1-earth-night-8k.webp` 地球夜景 |
| `3.3.7` | `ver_48a679cbbecc66a965a0` | disabled | `bg-4-earth-ring-8k.webp` 环地 |
| `2.4.8` | 未记录 | disabled | 未记录 |

## 本次发布方式

按“更新已有主题”处理：向 `POST /v1/me/themes/package` 提交 themeId 为
`starship-command-deck` 的新包，服务端把它作为该主题的新版本，
审核通过后自动接替旧版本，slug、下载数与收藏数全部沿用。

注意：线上包由 DreamSkin Studio 重新打包，因此
`packageSha256` 与本仓库 `releases/` 里的 ZIP 不同
（Studio 会重排 `theme.json` 的键顺序并重新压缩）。
两者的 `background.webp` 与 `theme.css` 哈希完全一致。

## 复核方式

```powershell
curl.exe -s "https://api.dreamskin.cc/v1/themes?q=starship"
curl.exe -s -L -o live.zip "https://api.dreamskin.cc/v1/themes/ver_50bbdac26bffa67b58c7/download"
Get-FileHash live.zip -Algorithm SHA256
```
