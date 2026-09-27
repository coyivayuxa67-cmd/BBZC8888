# 星舰指挥台主题资源

这个仓库用于保存 DreamSkin 投稿包、发布版本和宣传资料。

## 目录

- `themes/starship-command-deck/`：**当前投稿源文件**，themeId 为
  `starship-command-deck`，用于更新已发布的主题
- `releases/starship-command-deck-5.0.0.zip`：**当前投稿 ZIP**
- `themes/starship-command-deck-night/`、`releases/starship-command-deck-night-5.0.0.zip`：
  备选包，themeId 为 `starship-command-deck-night`，会另起一个新条目，暂未使用
- `marketing/`：中文/英文宣传文案、Studio 投稿步骤和 GitHub 上传指南
- `codexpp/starship-command-deck.user.js`：Codex++ 完整版用户脚本（自带六张内嵌背景）
- `assets/`：六张 8K 背景原图（WebP，合计 13.00 MB），供脚本的回退地址与后续轻量版使用

## 两个渠道，两套东西

这个仓库同时保存两个渠道的产物，互不通用：

| 渠道 | 产物 | 能力 |
| --- | --- | --- |
| DreamSkin（官方客户端静态主题） | `releases/starship-command-deck-5.0.0.zip` | 单张背景、配色、Safe CSS。已上架 |
| Codex++（用户脚本） | `codexpp/starship-command-deck.user.js` | 六背景切换、六款舷窗、流星、外星飞船、任务树、输入舱动效 |

DreamSkin 包是静态视觉，**不要**把用户脚本提交到 DreamSkin 主题库。
Codex++ 脚本也不能用 DreamSkin 包替代，两者格式完全不同。

## Codex++ 用户脚本

`codexpp/starship-command-deck.user.js` 版本 `5.0.1`，约 18.3 MB，
六张背景以 base64 内嵌，安装后不依赖外部图床。

仓库中该文件的 SHA256 为
`25c9ea21b76ceccfb53e673cce829e7ef2d3a23f9cc7a7aca32f1e3819eb9dc3`，
与 `raw.githubusercontent.com` 上提供的字节一致。

原始 RC 的元数据指向空的 `tianxiayiran/zhiku`，本版本已改为本仓库，
并补上了 `@downloadURL` 与 `@updateURL`，支持 Codex++ 的脚本更新检查：

```text
@downloadURL https://raw.githubusercontent.com/coyivayuxa67-cmd/BBZC8888/main/codexpp/starship-command-deck.user.js
@updateURL   https://raw.githubusercontent.com/coyivayuxa67-cmd/BBZC8888/main/codexpp/starship-command-deck.user.js
```

注意：仓库里的这份是发布用产物。本机 Codex++ 实际加载的是
`%APPDATA%\Codex++\user_scripts\星舰指挥台主题.js`（当前为 `4.8.7-smaller-meteor`，
使用本地路径加载资源），两者相互独立，覆盖安装前请先备份。

### Release

已发布 `v5.0.1`：

`https://github.com/coyivayuxa67-cmd/BBZC8888/releases/tag/v5.0.1`

附件两个：

| 附件 | 大小 | 说明 |
| --- | --- | --- |
| `starship-command-deck.user.js` | 18310475 字节 | Codex++ 用户脚本 |
| `starship-command-deck-dreamskin-5.0.0.zip` | 527238 字节 | DreamSkin 静态主题包 |

**下载路径实测（2026-09-27，国内网络）**

`github.com/<owner>/<repo>/releases/download/...` 与 `releases/latest/download/...`
三次测试全部超时：TCP 连接建立、请求已发出，但 15 到 21 秒内收到 0 字节。
同环境下这几个是正常的：

| 路径 | 结果 |
| --- | --- |
| `raw.githubusercontent.com` | 200，18MB 完整下载成功 |
| `cdn.jsdelivr.net/gh/...` | 200 |
| `release-assets.githubusercontent.com` | 可达 |
| `api.github.com/.../releases/assets/<id>`（带 token） | 可下载 |

结论：Release 页面适合展示与海外用户，**国内用户请走 raw 或 jsDelivr**：

```text
https://raw.githubusercontent.com/coyivayuxa67-cmd/BBZC8888/main/codexpp/starship-command-deck.user.js
https://cdn.jsdelivr.net/gh/coyivayuxa67-cmd/BBZC8888@main/codexpp/starship-command-deck.user.js
```

脚本里的 `@downloadURL` / `@updateURL` 指向 raw，正是因为这个路径实测可用。

### 关于仓库体积

18MB 的脚本直接提交进 git，意味着以后每发一版历史都会增加约 18MB。
后续版本建议只发 Release 附件（或 jsDelivr 从 tag 取），不再提交进 git。

### 回退资源

5.0.1 的 `ASSET_BASES` 依次是：本地覆盖值 →
`raw.githubusercontent.com` → `jsDelivr` → `github raw`。
这三条远程地址都指向本仓库的 `assets/` 目录，已补齐六张 WebP
（合计 13,626,964 字节），地址实测可用，不再是死链。

正常加载走内嵌数据，回退只在解码异常时才用到。
补齐这批资源还有一个用处：将来可以做一个约 143 KB 的轻量脚本，
图片走 CDN 缓存，这样每次升级不必重新下载 18MB。

## 当前主题

**星舰指挥台：夜航离港**

从地球夜景启航的未来舰桥静态主题。包含一张 8K WebP 背景、深色语义色和经过 DreamSkin Safe CSS 校验的组件样式。

已于 2026-09-27 发布为 `5.0.0`，作为已有主题 `starship-command-deck`
的更新版本上线，slug、下载数与收藏数均沿用。详见 `PUBLISHED.md`。

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
