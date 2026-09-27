# DreamSkin Studio 投稿步骤

> 以下流程为 2026-09-27 实测所得，依据是 DreamSkin Studio 前端代码，不是猜测。

## 关键事实

- Studio 是纯浏览器本地工具，图片与编辑都在本机处理；只有点发布时才上传。
- **Studio 支持直接导入主题 ZIP。** 2026-09-27 实测：导入
  `starship-command-deck-5.0.0.zip` 后，主题名、ID、版本、平台、
  发布者、许可证、AI 声明、来源摘要、十个颜色、Safe CSS、theme.json
  全部恢复，六项就绪检查一次全绿。导入时会询问“导入会覆盖当前草稿，继续吗？”。
- 唯一的投稿入口是“导出”页签底部的 `发布到主题库` 按钮。
- 该按钮调用 `POST https://api.dreamskin.cc/v1/me/themes/package`，
  `multipart/form-data` 携带 `package`（ZIP）、`rightsDeclaration`、可选 `license`。
- 服务端会再次校验，返回 201 表示受理、422 表示校验未通过。
- 未登录时按钮为禁用状态并显示“请先登录再发布。”
- 登录走 `https://api.dreamskin.cc/v1/auth/oauth/<provider>/start`（已确认支持 Google）。

## 最简操作步骤

1. 打开 `https://dreamskin.cc/studio` 并登录。
2. 点页头 `导入`，选择
   `github-repo-ready\releases\starship-command-deck-5.0.0.zip`，
   在弹窗里确认覆盖草稿。
3. 切到 `导出` 页签，确认六项都是 `已通过`：
   背景图片、主题信息、theme.json 源码、文字对比度、Safe CSS、包信息。
   主题信息那一行应显示 `星舰指挥台：夜航离港 · starship-command-deck`。
4. 勾选 `我确认拥有或有权使用该主题的素材与样式，并同意平台审核`。
5. 点 `发布到主题库`，出现 `已提交审核。` 即成功。
6. 到 `https://dreamskin.cc/account` 的创作者工作区查看审核状态。

> 因为 themeId 与已发布的“星舰指挥台”相同，服务端会把它作为**该主题的新版本**
> 处理：审核期间旧的 3.3.7 继续保持公开，审核通过后由 5.0.0 接替，
> slug、下载数、收藏都不会丢。

> 如果不用导入，也可以手动重建：`背景画面` 选 `background.webp`，
> 外观选 `深色`，安全区选 `左侧`，任务画面选 `环境`，
> 十个颜色按下表填写，把 `theme.css` 全文贴进 `Safe CSS`，再填包信息。

## 颜色值

| 字段 | 值 |
| --- | --- |
| background | `#04121d` |
| panel | `#071924` |
| panelAlt | `#0b3044` |
| accent | `#19d8ff` |
| accentAlt | `#8feeff` |
| secondary | `#9ab8c7` |
| highlight | `#00eaa5` |
| text | `#d7edf5` |
| muted | `#759cad` |
| line | `#1e7890` |

## 投稿信息

- 主题名：星舰指挥台：夜航离港
- 主题 ID：`starship-command-deck`
- 版本：`5.0.0`
- 平台：Windows、macOS
- 能力：background、tokens、safe-css
- 发布者 ID：`tianxiayiran`
- 发布者显示名称：JG
- 许可证：`All Rights Reserved`
- AI 生成声明：是
- 来源说明：夜航离港背景为项目星舰视觉素材，可能包含 AI 生成与后期处理内容；公开发布前由作者确认素材来源与授权范围。

## 提交前必须确认

- 允许 DreamSkin 站点展示、托管和分发背景图。
- AI 生成声明与实际制作过程一致。
- **主题 ID 归属**：首次成功发布的账号会永久拥有该 ID，换账号会返回
  `该主题标识属于其他作者`。请用打算长期持有的账号首次发布。
- GitHub 仓库属于 `coyivayuxa67-cmd`，而 manifest 里发布者 ID 是
  `tianxiayiran`。两者不一致不影响校验，但发布账号决定真实归属。

## 已发布记录

2026-09-27 已完成 `5.0.0` 发布，公开主题库当前显示：

| 项 | 值 |
| --- | --- |
| 主题 | 星舰指挥台：夜航离港 |
| slug / themeId | `starship-command-deck` |
| 版本 | `5.0.0` |
| 线上版本 ID | `ver_50bbdac26bffa67b58c7` |
| 状态 | `approved`（提交后约 6 秒由 `system:ai-moderation` 通过） |
| 下载 / 收藏 | 822 / 4（沿用旧版本，未重置） |

## 更早的版本

同一作者账号此前的公开版本：

| 项 | 值 |
| --- | --- |
| 主题 | 星舰指挥台 |
| slug / themeId | `starship-command-deck` |
| 版本 | `3.3.7` |
| 发布版本 ID | `ver_48a679cbbecc66a965a0` |
| 作者 | `yiran` / `usr_fea84bc4fb492297d8c7` |
| 首次提交 | 2026-09-11 |
| 背景图 | `bg-4-earth-ring-8k.webp`（环地），SHA256 `426a52ca…` |
| 当前状态 | `disabled`，已被 5.0.0 接替 |

本次投稿 `starship-command-deck` 5.0.0 用的是**另一张**图
`bg-1-earth-night-8k.webp`（地球夜景），SHA256 `9f39aca8…`，
与已发布的环地图不是同一个文件，视觉上是全新的夜航离港场景。

更新已发布主题的正确做法是**发布同 themeId 的新版本**：
`POST /v1/me/themes/package`，包内 themeId 填 `starship-command-deck`。
创作者工作区里的 `重新送审`（`POST /v1/me/themes/<id>/resubmit`）
**不带请求体**，只是把已有的一次提交重新排队，不能上传新内容。

备选包 `starship-command-deck-night-5.0.0.zip` 的 themeId 是
`starship-command-deck-night`，会另起一个新条目，当前未采用。
