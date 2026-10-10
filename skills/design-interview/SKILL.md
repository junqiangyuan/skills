---
name: design-interview
description: >-
  在独立工作区里按目标岗位与简历设计多轮、多主题的候选人侧模拟面试。设计前先检索高信任资料写入
  RESOURCES.md，再成对写出 HTML 对话稿与题库；不把模型记忆里的经典面试题当依据。语言以
  NOTES.md 为准。Use when the user asks to design, continue, or practice a
  candidate-side mock interview for a target role.
disable-model-invocation: true
argument-hint: "目标岗位 Target role（可附公司与级别）"
---

# design-interview

在一个可持久化的**面试设计工作区**里，按目标岗位和候选人简历设计多轮、多主题的模拟面试。每一轮的产出单位是一套 interview pack：可打印的对话稿，加上同编号的题库。必做范围是候选人侧准备；评分表只用于重心校准，默认不写。

斜杠命令后面的文字是目标岗位。例如：`/design-interview 平台后端 · 中级`。

## 硬规则

- 工作区文件写在**调用本技能时的当前目录**。`*-FORMAT.md` 与本文件同目录，只用来读格式。不要把 `MISSION.md`、`./interviews/` 写进技能安装目录，也不要写进本技能仓库。
- 若当前目录里能看到 `skills/design-interview/SKILL.md`，停下来，请用户换一个专门的目录。
- 设计任何一轮之前，先检索，并把打开过的高信任来源写入 `RESOURCES.md`。模型记忆里的「经典面试题」不是来源。
- 每道题都要过下面的出题闸门。对不上岗位、又对不上简历、也没有资料来源的题删掉。
- 工作区语言跟 `NOTES.md` 的 `Language`。不要默认中文或英文。
- 每一轮同时写 `./interviews/NNNN-theme.html` 与 `./interviews/NNNN-theme.bank.md`。`./interviews/NNNN-theme.rubric.md` 仅在下面写明的情况下出现。
- 用下面七个设计要素校准一轮该问多深。不要使用「最近发展区」、zone of proximal development，也不要引入教学课、熟练度、社区智慧之类的框架。目录名是 `./interviews/`。
- 不写一整套供背诵的标准答案。证据标准和追问树仍是出题侧主字段：对话稿写面试官怎么问、答里要出现什么证据、追问怎么分支。每题另附一段短的口语参考答，给候选人当场练着说。它是练习草稿，不是书面满分稿，也不是背诵稿。
- 只收录用户有权使用的材料与公开高信任源。来路不明的内部题库不写入 `RESOURCES.md`。
- 换公司或改级别之前先跟用户确认，再改 `MISSION.md`。一个工作区只服务一个目标岗位；另一个岗位换一个目录。

## 两条路径

| 路径 | 根在哪 | 例子 |
| --- | --- | --- |
| 技能文件 | 本 `SKILL.md` 所在目录 | [MISSION-FORMAT.md](./MISSION-FORMAT.md) |
| 工作区 | 当前目录 | `./MISSION.md`、`./interviews/0001-theme.html` |

## 工作区文件

当前目录就是 Interview Design Workspace。缺的文件在第一次需要时再创建。

| 路径 | 作用 | 格式 |
| --- | --- | --- |
| `MISSION.md` | 目标岗位、公司/级别、为何要面、JD 要点 | [MISSION-FORMAT.md](./MISSION-FORMAT.md) |
| `RESOURCES.md` | 高信任资料清单。先有它，再出题 | [RESOURCES-FORMAT.md](./RESOURCES-FORMAT.md) |
| `RESUME.md` | 简历结构化摘要。出题必须对照 | [RESUME-FORMAT.md](./RESUME-FORMAT.md) |
| `NOTES.md` | 语言、时长、题型偏好 | 见下文 |
| `./interviews/NNNN-theme.html` | 一轮主题的可打印对话稿 | 见「单轮产出」 |
| `./interviews/NNNN-theme.bank.md` | 同一轮的题库 | 见「单轮产出」 |
| `./interviews/NNNN-theme.rubric.md` | 可选。评分与重心校准 | [RUBRIC-FORMAT.md](./RUBRIC-FORMAT.md) |
| `./session-notes/NNNN-theme.md` | 这一轮问了什么、答得如何、下一轮钩子 | [SESSION-NOTE-FORMAT.md](./SESSION-NOTE-FORMAT.md) |
| `./reference/*.html` | 跨轮复用的压缩速查 | 见「参考文档」 |
| `./assets/` | 共用样式与以后会复用的小组件 | 见「资产」 |

`NNNN` 是四位递增编号，从 `0001` 起。词干匹配 `^[0-9]{4}-[a-z0-9]+(?:-[a-z0-9]+)*$`，编号后面是 ASCII 小写 kebab-case 的主题。中文主题把中文标题写在文件里面，slug 用短英文，例如 `0001-mcp-auth`。同一轮的 html、bank、可选 rubric、session note 共用这个词干。编号只增不复用。

## 每次怎么跑

先读已有的 `NOTES.md`、`MISSION.md`、`RESUME.md`、`RESOURCES.md`、最新的 `./session-notes/`、以及 `./interviews/` 里最大的编号。调用消息里已经给出的信息不要再问一遍。

### 首次

1. 确认当前目录是专门的工作区。
2. 用用户正在使用的语言补齐缺口：目标岗位（命令参数里已有则不用问）、公司与级别、为何要面、简历（粘贴或文件路径）、语言、单轮时长、偏项目深挖还是算法或其他权重、不要的题型。
3. 把语言写入 `NOTES.md`。用户明确指定的优先。否则整段请求明显是单一语言时，把该语言写入 `NOTES.md`，并告诉用户这是假设、可以改。请求本身中英混杂且用户没指定时，先问一句，再写任何面试稿。
4. 按格式写 `MISSION.md` 与 `RESUME.md`。简历里没出现的数字不要编。
5. 按 [RESOURCES-FORMAT.md](./RESOURCES-FORMAT.md) 检索并写 `RESOURCES.md`。检索没跑成时，只写缺口，不出技术事实题。
6. 用户这次就是要设计面试，且岗位与简历已经够用：写出 `0001`。用户只想搭工作区：写完上面的文件后停，并提议一个主题。

没有简历时，可以先写 `MISSION.md` 与 `RESOURCES.md`。除非用户明确要一场只按 JD 的筛查，否则先要简历，再写 `./interviews/`。只按 JD 的那一场，简历锚点写「未提供」。

### 每一轮

1. 从 `MISSION.md` 里尚未被 session notes 覆盖的要点、简历里的缺口、以及上一轮的下一轮钩子，选定**一个**主题。
2. 若 `RESOURCES.md` 还没有这条目标能力的高信任源，先搜再写。
3. 过出题闸门，然后成对写出 html 与 bank。
4. 对话稿链到已有的面试稿和 `./reference/`（相对路径）。
5. 告诉用户两个文件的路径、本轮主题、以及下一轮钩子。不要在对话里复述整份题库。当前环境能打开本地文件时，可以打开 HTML；不能打开就把路径给用户。

岗位画像决定主题权重。Agent / FDE 一类岗位优先编排、鉴权、评测、工程判断；纯算法只在 `MISSION.md` 或 `NOTES.md` 要求时才成为一轮。不要把 LeetCode 式题单当成默认循环。

### 轮末

即使这一轮只设计、没有对练，也写 `./session-notes/NNNN-theme.md`。对练过就按证据标准记下答得如何。同一轮再次对练时，在原笔记下追加，不新开编号。

用户要求换岗或改级别时，先确认，更新 `MISSION.md`，并写一条 `./session-notes/NNNN-mission-update.md`（用下一个编号，不配面试稿）。

### 跨轮

用 `NOTES.md` 与 session notes 决定下一轮是补洞还是加压一个新主题。钩子已经写明就照钩子走，不要每轮重新从「常见面试流程」排期。

## 哲学

高信任来源先进入 `RESOURCES.md`，题再从清单里长出来。

**出题闸门。** 每道题写进文件前：

1. **岗位锚点。** 它覆盖 `MISSION.md` 哪一条 JD 要点？对不上就删。
2. **简历锚点。** 它挖 `RESUME.md` 的哪一段？对不上、又确实是 JD 要求而简历没写的，难度档标成加压，不要写成候选人已经做过。
3. **资料锚点。** 追问里的技术事实由 `RESOURCES.md` 的哪一条支撑？没有就先搜。搜不到就把题改成只问候选人自己的经历，不补模型记得的知识点。

只问候选人自身经历、且不引入外部技术事实的开场，可以没有第 3 条，但必须有简历锚点。

两份来源不一致时，两份都引用，把追问放在这个取舍上。不要靠记忆选边。

匿名面经、榜单体「N 道经典题」、以及没有 URL 的印象，不作为出题依据。公司自己的招聘页、工程博客、手册，以及语言或产品的官方文档，才是高信任。

## 校准带

每一轮在对话稿和题库里都写明这七项。整轮落在简历撑得住、又向外探一点的中间带：热身确认锚点是真的，主攻打目标能力，加压只探一步（一个失败模式、一个简历里该有的数字、或一条还没讲过的 JD 约束）。

| 要素 | 英文 | 怎么定 |
| --- | --- | --- |
| 目标能力 | target capability | 本轮只验证 1–2 个能力 |
| 简历锚点 | resume anchor | `RESUME.md` 里的具体项目或指标，用来开场深挖 |
| 岗位锚点 | job anchor | `MISSION.md` / JD 里本轮必须覆盖的点 |
| 难度档 | difficulty band | 热身 → 主攻 → 加压 |
| 证据标准 | evidence criteria | 答好时要出现什么：取舍、主链路、异常兜底、可量化效果 |
| 追问树 | follow-up tree | 2–3 层。过浅怎么往下，偏了怎么拉回锚点，够深怎么加压一问 |
| 下一轮钩子 | next-round hook | 一句话，写入 session note，驱动下一主题 |

追问要指回具体锚点，例如简历里的某项指标或 JD 里的某条职责。不要用「再说细一点」充一层。

## 单轮产出

一场是一个主题，默认可在 `NOTES.md` 的时长内做完（笔记没写时长时，先问；用户让你直接设计且没给时长，则按 35 分钟写入 `NOTES.md` 并说明这是假设）。默认题量：热身 1 题，主攻 2–4 题，加压 1 题。`NOTES.md` 写了不要热身时，可以不设热身。

内容形状（证据清单，不是代写答案）：

- **项目深挖：** 是什么、为何做、个人贡献与数据。笔记偏项目、或笔记未指定且简历里有项目时，主攻用这个形状。
- **技术题：** trade-off、主链路实现、长尾与兜底。
- **具体问题要能听到：** 描述 → 原因 → 方案 → 可量化效果。
- **第一印象：** 1–2 个来自简历指标的亮点，不巡礼整份题库。

### 口语参考答

每题必有。写在 bank 该题下的固定小节，并在 HTML 同一题的 `<aside class="spoken">` 里放同一段。给候选人开口练，不出题人拿它打分。

- **像在答。** 用说得出口的句子，连接词可以有。不要公文腔，也不要把证据标准改成条目念出来。
- **短。** 大约口播 30–90 秒。热身更短，可以不到 30 秒。主攻可以靠近上限，略长一点也可以。不要写成一篇写全的文章。
- **只写简历里有的。** 事实和数字以 `RESUME.md` 为准，没有的不编。讲不完、留下取舍都可以。不是满分样稿。
- **标签写明不是背诵稿。** `Language` 为 `zh` 时，bank 小节标题用 `口语参考答（候选人视角 · 非背诵稿）`，HTML 强标签用「口语参考答 · 非背诵稿」。`en` 时 bank 用 `Spoken sketch (candidate side · not a script to memorize)`，HTML 用 “Spoken sketch · not a script to memorize”。`mixed` 跟该题所用语言。
- **不替代主字段。** 证据标准、追问树照旧写全。口播对不齐证据标准时，改口播或改题，不要把口播写成另一套标准答案。

### HTML 对话稿

自包含、可打印、无内联样式、无远程资源。`<html lang>` 按语言取 `zh-CN` 或 `en`。样式只链 `../assets/base.css`。类名用下面这套，方便多轮看起来像同一套材料。

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>0001 · {主题}</title>
  <link rel="stylesheet" href="../assets/base.css" />
</head>
<body>
<main>
  <p class="kicker">Interview 0001</p>
  <h1>{主题}</h1>
  <p class="meta">{岗位} · {时长} · {语言}</p>
  <p class="read-first">先读 <a href="{primary-url}">{来源标题}</a></p>
  <section class="highlights">
    <h2>第一印象</h2>
    <ul>
      <li>{亮点，来自简历}</li>
    </ul>
  </section>
  <section class="calibration">
    <h2>本轮校准</h2>
    <dl>
      <dt>目标能力</dt><dd>{1–2 个}</dd>
      <dt>简历锚点</dt><dd>{RESUME 位置}</dd>
      <dt>岗位锚点</dt><dd>{MISSION / JD}</dd>
      <dt>难度档</dt><dd>热身 → 主攻 → 加压</dd>
      <dt>证据标准</dt><dd>{本轮共同标准}</dd>
      <dt>追问树</dt><dd>过浅 / 偏了 / 够深</dd>
      <dt>下一轮钩子</dt><dd>{一句话，与文末相同}</dd>
    </dl>
  </section>
  <section class="band band-warmup" id="warmup">
    <h2><span class="tag">热身</span> {小节标题}</h2>
    <article class="turn" id="q1">
      <p class="who">面试官</p>
      <p class="prompt">{问题}</p>
      <aside class="listen"><strong>证据</strong> {要听到的要点}</aside>
      <ol class="followups">
        <li><span>过浅</span> {追问}</li>
        <li><span>偏了</span> {拉回哪个锚点}</li>
        <li><span>够深</span> {加压一问}</li>
      </ol>
      <aside class="spoken">
        <strong>口语参考答 · 非背诵稿</strong>
        <p>{与 bank 同一段口播。热身更短。只使用简历已有事实和数字。}</p>
      </aside>
      <p class="cite">依据：<a href="{url}">{标题}</a> · RESUME · MISSION</p>
    </article>
  </section>
  <!-- band-main、band-pressure 同样结构。题号 q1、q2… 与 bank 一致 -->
  <section class="sources">
    <h2>依据</h2>
    <ul>
      <li><a href="{url}">{标题}</a> — {用在哪一题}</li>
    </ul>
  </section>
  <footer class="hook">下一轮钩子：{一句话}</footer>
</main>
</body>
</html>
```

`Language` 为 `en` 时，可见标题用 Target capability、Resume anchor、Job anchor、Difficulty band、Evidence criteria、Follow-up tree、Next-round hook，以及 Warmup / Main / Pressure、Interviewer、Evidence。追问标签用 Shallow / Drifted / Strong enough。口语参考答的强标签用 “Spoken sketch · not a script to memorize”。`mixed` 时按 `NOTES.md` 里写的哪一部分用哪种语言。准备稿里证据和追问保持可见，方便候选人知道要打到哪里。口语参考答放在追问之后，不取代这两项。

### 题库 `NNNN-theme.bank.md`

与 HTML 题号、顺序、锚点一致。改一边时同步另一边。

```md
# 0001 · {主题}

- 目标能力 target capability:
- 简历锚点 resume anchor:
- 岗位锚点 job anchor:
- 难度档 difficulty band:
- 语言:
- 建议时长:
- 先读:

## Q1 · {短标题}

- 档: 热身 | 主攻 | 加压
- 问:
- 证据标准 evidence criteria:
- 追问树 follow-up tree:
  - 过浅:
  - 偏了:
  - 够深:
- 依据:

### 口语参考答（候选人视角 · 非背诵稿）

{口播正文，与 HTML 该题 aside 相同。大约 30–90 秒；热身更短。只使用简历已有事实和数字。可以不完整。}

## 下一轮钩子 next-round hook
```

### 评分表

默认不写。仅当用户要求评分或校准，或上一则 session note 写明重心偏了，或你无法判断本轮权重是否仍贴着 `MISSION.md` 时，才写 `NNNN-theme.rubric.md`。它是 agent 与用户对齐重心的文件：写明权重，请用户改。格式见 [RUBRIC-FORMAT.md](./RUBRIC-FORMAT.md)。用户没对练过就不要替他们打分。

## NOTES.md

工作区根目录。没有就创建。

```md
# Notes

## Language
zh | en | mixed
<!-- mixed 时写清：哪一部分用哪种语言 -->

## Duration
<!-- 分钟 -->

## Emphasis
<!-- 项目深挖 / 算法 / 系统设计 / 行为题，可写权重 -->

## Avoid
<!-- 不要的题型 -->

## Other
```

## 资产

工作区还没有 `./assets/base.css` 时，把本技能目录下的 [assets/base.css](./assets/base.css) **复制**进去，再让对话稿和参考页链接它。不要链接技能安装路径。第二轮还会用到的样式或小组件再放进 `./assets/`，不要在每份 HTML 里各写一份。

## 参考文档

同一骨架要在两轮以上重复时，压成 `./reference/*.html`（题型骨架、trade-off 清单、STAR 形状、岗位关键词、术语表）。同样链接 `../assets/base.css`，同样只写有来源的内容。第一轮不要预造一整套参考库。行为题才需要 STAR 形状。术语表一旦写下，后续各轮沿用这些说法。

## 自检

保存前核对：

- 本轮目标能力在 `RESOURCES.md` 里有本次用得上的来源，或明确只问个人经历
- 没有一道题的唯一出处是「经常会问」
- 七个要素在 HTML 与 bank 里都有，且一致
- 每题 bank 有「口语参考答（候选人视角 · 非背诵稿）」小节（英文轮用对应英文标题），HTML 同题有 `<aside class="spoken">`，两边是同一段
- 这段是短口播：像现场在答，热身更短，其余大约 30–90 秒；没有简历以外的数字；没有写成条目式范文或满分稿
- 证据标准与追问树仍在，没有被口语参考答换掉
- 两个主文件词干相同；没要求校准就没有 rubric
- 语言与 `NOTES.md` 一致
- 追问树有拉回分支
- session note 里有下一轮钩子；没对练就标明只设计、未作答
