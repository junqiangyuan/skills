# Session note 格式

Session notes 在 `./session-notes/`。文件名与那一轮相同：`0001-theme.md`。岗位或级别变更没有对应面试稿时，用下一个编号加 `-mission-update`：`0002-mission-update.md`。

它们驱动下一轮是补洞还是换主题。不是日记，也不记录「学过了什么概念」。

## 模板

```md
# 0001 · {主题}

- 状态: designed | practiced
- 日期: {YYYY-MM-DD}
- 面试稿: [interviews/0001-theme.html](../interviews/0001-theme.html)
- 题库: [interviews/0001-theme.bank.md](../interviews/0001-theme.bank.md)

## 问了什么
- Q1 {一句话}
- Q2 {一句话}

## 答得如何
{designed：只设计，未作答。practiced：对照证据标准，哪题打到、哪题没有。不改写成标准答案。}

## 补洞
- {下一轮该补的具体缺口}

## 加压
- {已经稳、可以再探一步的点}

## 下一轮钩子
{一句话。与面试稿、题库里的钩子相同。}
```

同一轮再次对练，在文件末尾追加：

```md
## 再练 · {YYYY-MM-DD}
{相对上次，证据标准上变了什么。需要的话改写文末钩子，并同步 html 与 bank。}
```

## 英文标题

`# 0001 · {theme}` · `- Status` 取值仍为 `designed` 或 `practiced` · `## What was asked` · `## How the answers landed` · `## Fill` · `## Press` · `## Next-round hook` · `## Practiced again · {date}`

## 规则

- **一轮一条主笔记。** 再练不新开编号。
- **钩子只有一句，并且三处一致：** 本笔记、HTML 文末、bank 文末。
- **未对练不要虚构表现。** 状态写 `designed`，答得如何写「只设计，未作答」。
- **重心偏了就写出来。** 一句即可，例如「主攻滑向通用缓存题，岗位锚点没覆盖到」。这会触发下一轮考虑写 rubric。
- **使命变更笔记**只记确认过的变化、原因，以及哪些旧题因此作废。不在这条笔记里出新题。
