# DreamSkin Studio 投稿步骤

> 以下流程为 2026-09-27 实测所得，依据是 DreamSkin Studio 前端代码，不是猜测。

## 关键事实

- Studio 是**纯浏览器本地工具**，不上传图片、不在本地导入 ZIP。
- 唯一的投稿入口是 Studio 页面底部的 `发布到主题库` 按钮。
- 该按钮调用 `POST https://api.dreamskin.cc/v1/me/themes/package`，
  `multipart/form-data` 携带 `package`（ZIP 文件）、`rightsDeclaration`、可选 `license`。
- 服务端会再次校验主题包，返回 201 表示受理、422 表示校验未通过。
- 未登录时按钮提示 `请先登录再发布`；登录走 `https://api.dreamskin.cc/v1/auth/oauth/<provider>/start`。
- 当前 AI 无法代点该按钮，因为本机浏览器自动化通道不可用（`unsupported Codex auth method: apikey`）。这一步必须由本人操作。

## 操作步骤

1. 打开 `https://dreamskin.cc/studio` 并用 Google 或 GitHub 登录。
2. 在 `背景画面` 选择
   `dreamskin-submission\starship-command-deck-night\background.webp`
   （不要先选 ZIP，Studio 不接受 ZIP 导入）。
3. 十个颜色按下表填写；外观选 `深色`；安全区选 `左侧`；任务画面选 `环境`。
4. `Safe CSS` 面板粘贴
   `dreamskin-submission\starship-command-deck-night\theme.css` 的全部内容。
5. 主题名填 `星舰指挥台：夜航离港`，主题 ID 填 `starship-command-deck-night`。
6. 包信息按下方“投稿信息”填写，最低客户端版本填 `1.0.0`。
7. 确认左侧检查面板五项全部显示 `已通过`：背景图片、主题信息、文字对比度、包信息、Safe CSS。
8. 勾选 `我确认拥有或有权使用该主题的素材与样式，并同意平台审核`。
9. 点击 `发布到主题库`，出现 `已提交审核。` 即成功。
10. 到 `https://dreamskin.cc/account` 的创作者工作区查看审核状态。

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
- 主题 ID：`starship-command-deck-night`
- 版本：`5.0.0`
- 平台：Windows、macOS
- 能力：background、tokens、safe-css
- 发布者 ID：`tianxiayiran`
- 发布者显示名称：JG
- 许可证：`All Rights Reserved`
- AI 生成声明：是
- 来源说明：夜航离港背景为项目星舰视觉素材，可能包含 AI 生成与后期处理内容；公开发布前由作者确认素材来源与授权范围。

## 提交前必须确认

- 背景图拥有公开再分发权。这一条我无法替你核实，背景图来源只有你清楚。
- 允许 DreamSkin 站点展示、托管和分发背景图。
- AI 生成声明与实际制作过程一致。
- **主题 ID 归属**：首次成功发布的账号会永久拥有
  `starship-command-deck-night` 这个 ID。后续换账号发布同一 ID 会返回
  `该主题标识属于其他作者`。请用你打算长期持有的账号首次发布。
- 注意 GitHub 仓库属于 `coyivayuxa67-cmd`，而 manifest 里发布者 ID 写的是
  `tianxiayiran`。两者不一致不影响校验，但发布账号决定真实归属，建议统一。
