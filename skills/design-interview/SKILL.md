---
name: design-interview
description: >-
  在独立工作区里按目标岗位与简历设计多轮、多主题的候选人侧模拟面试。设计前核对高信任资料，缺来源则检索写入
  RESOURCES.md，或记明缺口改问经历；默认交付 HTML interview pack，仅当用户显式要求题库 / bank 时另写题库。
  不把模型记忆里的经典面试题当依据。语言以
  NOTES.md 为准。Use when the user asks to design, continue, or practice a
  candidate-side mock interview for a target role.
disable-model-invocation: true
argument-hint: "目标岗位 Target role（可附公司与级别）"
---

# design-interview

在一个可持久化的**面试设计工作区**里，按目标岗位和候选人简历设计多轮、多主题的模拟面试。每一轮的 interview pack 默认只交付可打印的 HTML 对话稿，题干、证据标准、追问和口语参考答都保留在 HTML 内；仅当用户显式要求题库 / bank 时另写同编号题库。必做范围是候选人侧准备；评分表只用于重心校准，默认不写。

斜杠命令后面的文字是目标岗位。例如：`/design-interview 平台后端 · 中级`。

## 硬规则

- 工作区文件只写在选定的**面试工作区根**，不一定是调用目录。按下面「工作区选择」分支确定位置。`*-FORMAT.md` 与本文件同目录，只用来读格式。不要把面试文件写进技能安装目录或本技能仓库。
- 当前目录能看到 `skills/design-interview/SKILL.md` 时，停下来，请用户换目录。不要在技能仓库里默认建面试目录；显式路径落在本技能仓库内也拒绝写入。
- 设计任何一轮之前，先检查本轮来源；缺来源时只做一轮检索，把打开并采用的高信任 URL 写入 `RESOURCES.md`。检索失败写缺口，可以改问经历。已有来源够本轮使用、或已决定只问经历时，进入设计。设计中不再开启检索或多轮中途校验；内容完成后只做一次最终自检。模型记忆里的「经典面试题」不是来源。
- 每道题都要过下面的出题闸门。对不上岗位、又对不上简历、也没有资料来源的题删掉。
- 工作区语言跟 `NOTES.md` 的 `Language`。不要默认中文或英文。
- 每一轮默认只写 `./interviews/NNNN-theme.html`；仅当用户显式要求题库 / bank 时才另写 `./interviews/NNNN-theme.bank.md`。每题口语参考答写在 HTML 的 `<aside class="spoken">`。`./interviews/NNNN-theme.rubric.md` 默认不写，仅在下面写明的校准条件下出现。
- 需要跨会话交接时直接写 GitHub Issue，不落本地临时 handoff 文档。不写临时校验或草稿文件；`MISSION.md`、`RESUME.md`、`RESOURCES.md`、`NOTES.md` 和 session notes 等支撑文件仍可按需写入。
- 用下面七个设计要素校准一轮该问多深。不要使用「最近发展区」、zone of proximal development，也不要引入教学课、熟练度、社区智慧之类的框架。目录名是 `./interviews/`。
- 不写一整套供背诵的标准答案。证据标准和追问树仍是出题侧主字段：对话稿写面试官怎么问、答里要出现什么证据、追问怎么分支。每题另附一段短的口语参考答，给候选人当场练着说。它是练习草稿，不是书面满分稿，也不是背诵稿。
- 只收录用户有权使用的材料与公开高信任源。来路不明的内部题库不写入 `RESOURCES.md`。
- 覆盖已有面试工作区文件、换公司或改级别之前先跟用户确认；确认前不改 `MISSION.md` 或被覆盖文件。一个面试工作区只服务一个目标岗位；另一个岗位换一个目录。

## 两条路径

| 路径 | 根在哪 | 例子 |
| --- | --- | --- |
| 技能文件 | 本 `SKILL.md` 所在目录 | [MISSION-FORMAT.md](./MISSION-FORMAT.md) |
| 面试工作区 | 按下节选定的面试工作区根 | `./MISSION.md`、`./interviews/0001-theme.html` |

### 工作区选择

**面试工作区根**是面试产物所在的根：`MISSION.md`、`NOTES.md`、`RESUME.md`、`RESOURCES.md`、`./interviews/`、`./session-notes/`、`./assets/`、`./reference/` 都在这里。它不一定是调用目录。按以下分支选择，并在回复中说明选定位置：

1. 调用目录能看到 `skills/design-interview/SKILL.md` 时，停下来，请用户换目录。不要在仓库里默认建面试目录。
2. 用户给出显式工作区路径（`workspace`）时，写入该路径。先核对实际位置及上级目录；若路径落在本技能仓库内（能看到 `skills/design-interview/SKILL.md` 作为仓库内容），拒绝写入，请用户给仓库外的路径。
3. 调用目录已是本技能面试工作区：有含 `Language` 字段的 `NOTES.md`，或已有符合本技能格式的 `MISSION.md` / `RESUME.md` / `RESOURCES.md`，且待写的同名文件没有明显用于别处，继续写在当前目录。改公司或级别仍先确认。
4. 调用目录已有同名 `MISSION.md`、`RESOURCES.md` 等，但对不上本技能工作区（没有上述标记，或内容明显是别的用途），在调用目录下新建独立子目录，例如 `interview-workspace`。短名已占用就换一个未占用的短名。只在子目录写面试文件，原文件字节不动。这一步不需要再问。
5. 调用目录没有上述冲突时，可将它选为面试工作区根。

## 工作区文件

下表路径都相对面试工作区根。缺的文件在第一次需要时再创建。生成的 HTML 或 Markdown 内部链接相对各自文件所在目录，例如面试稿的样式链接仍是 `../assets/base.css`。

| 路径 | 作用 | 格式 |
| --- | --- | --- |
| `MISSION.md` | 目标岗位、公司/级别、为何要面、JD 要点 | [MISSION-FORMAT.md](./MISSION-FORMAT.md) |
| `RESOURCES.md` | 高信任资料清单。先有它，再出题 | [RESOURCES-FORMAT.md](./RESOURCES-FORMAT.md) |
| `RESUME.md` | 简历结构化摘要。出题必须对照 | [RESUME-FORMAT.md](./RESUME-FORMAT.md) |
| `NOTES.md` | 语言、时长、题型偏好 | 见下文 |
| `./interviews/NNNN-theme.html` | 一轮主题的可打印对话稿 | 见「单轮产出」 |
| `./interviews/NNNN-theme.bank.md` | 可选。仅当用户显式要求题库 / bank 时写 | 见「单轮产出」 |
| `./interviews/NNNN-theme.rubric.md` | 可选。评分与重心校准 | [RUBRIC-FORMAT.md](./RUBRIC-FORMAT.md) |
| `./session-notes/NNNN-theme.md` | 这一轮问了什么、答得如何、下一轮钩子 | [SESSION-NOTE-FORMAT.md](./SESSION-NOTE-FORMAT.md) |
| `./reference/*.html` | 跨轮复用的压缩速查 | 见「参考文档」 |
| `./assets/` | 共用样式与以后会复用的小组件 | 见「资产」 |

`NNNN` 是四位递增编号，从 `0001` 起。词干匹配 `^[0-9]{4}-[a-z0-9]+(?:-[a-z0-9]+)*$`，编号后面是 ASCII 小写 kebab-case 的主题。中文主题把中文标题写在文件里面，slug 用短英文，例如 `0001-mcp-auth`。同一轮必须写 html 和 session note；bank、rubric 在触发时才写，存在的文件共用这个词干。编号只增不复用。

## 每次怎么跑

先按「工作区选择」确定面试工作区根，再读该根下已有的 `NOTES.md`、`MISSION.md`、`RESUME.md`、`RESOURCES.md`、最新的 `./session-notes/`、以及 `./interviews/` 里最大的编号。调用消息里已经给出的信息不要再问一遍。

### 首次

1. 按「工作区选择」确定面试工作区根。需要独立子目录就直接新建；需要换出技能仓库就停在目录确认，不向仓库写面试文件。
2. 用用户正在使用的语言核对缺口。必要澄清见下节，只问依赖事实；目标岗位已在命令参数里则不重复问。公司、级别、完整 JD、动机、时长、权重、排除题型按「可降级」处理，不等整包补齐。
3. 把语言、时长、主攻偏好的已知值或假设写入 `NOTES.md`，按下节规则处理。中英混杂且未指定语言时，面试稿正文先不写，其他独立产物继续。
4. 按格式写 `MISSION.md` 与 `RESUME.md`。简历里没出现的数字不要编；`Resume source`、确认状态和多版本处理见 [RESUME-FORMAT.md](./RESUME-FORMAT.md)。先整理无争议内容，冲突只放「不确定」。
5. 按 [RESOURCES-FORMAT.md](./RESOURCES-FORMAT.md) 核对已有来源；缺来源时只做一轮检索并写 `RESOURCES.md`。检索没跑成时，只写缺口，不出技术事实题。达到检索停止线就进入设计，不在设计中重开检索。
6. 用户这次就是要设计或准备一轮，且岗位与简历已经够用：默认写出 `0001` 的 HTML 和 session note，完成下面的准备交付；仅当用户显式要求题库 / bank 时另写 bank。必要确认挡住部分题时，先交出独立完成项。用户只想搭工作区：写完上面的文件后停，并提议一个主题。

### 够用、必要澄清与可降级

**够用**是同时满足下面三条，可以开始设计；另有必要确认时，只暂停它挡住的部分：

1. 岗位名称的含义没有实质歧义。
2. 至少有一段无冲突的简历锚点，或用户明确要只按 JD 的筛查。
3. 公司、级别、完整 JD、动机、时长、权重、排除题型可以未齐；未齐项按下面降级，写入假设或「未知」，继续出能出的材料。

**必要澄清只暂停依赖该事实的出题，不暂停整次准备。** 同一回复交出已完成的降级产物：

- 岗位含义有实质歧义：只问会改变选题的含义。依赖该歧义的题不写；来源清单、无争议简历锚点、阻塞项仍留下。缺公司、级别或完整 JD 不自动算岗位说不清。
- 简历事实冲突且用户未指定权威版本：只问会改变本轮锚点的差异，按 `RESUME-FORMAT.md` 处理。无争议锚点上的经历题可以先写；冲突事实只在「不确定」，不进题面。
- 覆盖已有面试工作区文件，或改公司/级别：只确认拟覆盖的文件或该项变化，确认前不改相关文件，尤其不改 `MISSION.md`。
- 请求中英混杂且未指定语言：只问语言；面试稿正文不写，其他已完成项仍列出。
- 没有简历且用户未明确只要 JD 筛查：先要简历，再写 `./interviews/`。可先写 `MISSION.md` 与 `RESOURCES.md`。已有材料多版本不等于没有简历。只按 JD 的那一场，简历锚点写「未提供」。

**可降级，不要整单阻塞：**

- 公司未提供：`MISSION.md` 写「未知」。不得把另一家公司招聘页写成目标公司要求。引用公开岗位说明时，标为「参考岗位画像」，写明不是目标公司实际要求；`MISSION.md` 里摘出的 JD 要点带同一标签。仍须是打开过的高信任 URL。
- 级别未提供：字段写「未知」并继续。禁止自行升档，不禁止出题；参考岗位画像的级别不移作目标级别。
- 完整 JD 未提供：能用用户已给的要点就用；搜不到就改问经历。可用带标签的参考岗位画像，不用模型印象补「这类级别一定考」。
- 单一语言请求：用户未指定、且 `NOTES.md` 没有语言记录时，将该语言作为假设写入 `NOTES.md`，告知可改；已有记录沿用，用户明确指定的语言优先。
- 准备一轮且未给时长：算「直接设计」；笔记也未写时长时，把 35 分钟假设写入 `NOTES.md`，并告知可改。笔记未指定权重且简历有项目时，主攻项目深挖，把这项假设也记入 `NOTES.md`。语言、时长、主攻偏好三处假设分别记下。`Avoid` 为空不阻塞。
- 用户给了面试日期或截止时间：写入 `MISSION.md` 的约束；完成线仍是交出一轮可练材料，不是先收齐可选项。
- 动机未说明：记「用户未说明动机」，不编造成功标准或 offer。

### 等待态与准备交付

等待必要确认时，先保存能独立完成的产物，再在同一回复同时列出：

- **已完成：** 独立子目录（若需要）、已采用来源或明确缺口、无争议简历锚点、已记下的假设。列出文件路径；未能落盘的已采用 URL 至少列在这里。
- **待确认：** 实质岗位歧义、影响本轮的事实冲突、覆盖或改公司/级别；若缺语言、简历或安全写入目录，也列在这里。每项只问该事实。
- **未完成：** 被确认挡住的题、尚未写的 HTML、尚未写的 session note；仅当用户显式要求题库 / bank 时才列尚未写的 bank。明确是哪项确认挡住，不把可降级项列成阻塞。

已打开并采用的 URL 必须写入 `RESOURCES.md`，或至少出现在回复的已完成清单。检索失败写缺口，不用记忆填技术事实。

准备任务不被必要澄清挡住时，默认完成线是 `NNNN-theme.html`、对应 session note、`RESOURCES.md` 有本轮来源或写明缺口，并在内容完成后做一次最终「自检」。用户显式要求题库 / bank 时，完成线再加对应 bank。回复给出实际写出的文件路径及自检结果。只设计时 session note 写 `designed` 和「只设计，未作答」，不评分。

### 每一轮

1. 从 `MISSION.md` 里尚未被 session notes 覆盖的要点、简历里的缺口、以及上一轮的下一轮钩子，选定**一个**主题。
2. 若 `RESOURCES.md` 还没有这条目标能力的高信任源，只做一轮检索并写入来源或缺口；首次流程已检索过，不重复检索。目标能力已有采用的来源，或已决定改问经历时，就进入设计，不为低增量页面继续检索。
3. 过出题闸门，然后写出 HTML；仅当用户显式要求题库 / bank 时另写 bank，并与 HTML 保持同步。设计中不做多轮中途校验。
4. 对话稿链到已有的面试稿和 `./reference/`（相对路径）。
5. 写对应 session note，内容完成后做一次最终自检。告诉用户 HTML 与 session note 的路径、本轮主题、以及下一轮钩子；bank 仅在实际写出时给路径。不要在对话里复述整份材料。当前环境能打开本地文件时，可以打开 HTML；不能打开就把路径给用户。

岗位画像决定主题权重。Agent / FDE 一类岗位优先编排、鉴权、评测、工程判断；纯算法只在 `MISSION.md` 或 `NOTES.md` 要求时才成为一轮。不要把 LeetCode 式题单当成默认循环。

### 轮末

即使这一轮只设计、没有对练，也写 `./session-notes/NNNN-theme.md`。对练过就按证据标准记下答得如何。同一轮再次对练时，在原笔记下追加，不新开编号。

用户要求换岗或改级别时，先确认，更新 `MISSION.md`，并写一条 `./session-notes/NNNN-mission-update.md`（用下一个编号，不配面试稿）。

### 跨轮

用 `NOTES.md` 与 session notes 决定下一轮是补洞还是加压一个新主题。钩子已经写明就照钩子走，不要每轮重新从「常见面试流程」排期。

## 哲学

高信任来源先进入 `RESOURCES.md`，题再从清单里长出来。信息是否够用按上面的三条判断；必要澄清只挡依赖题。可降级缺口不挡整轮，但每道题仍要过下面的闸门。

**出题闸门。** 每道题写进文件前：

1. **岗位锚点。** 它覆盖 `MISSION.md` 哪一条 JD 要点？JD 缺失且已改问经历时，指向明确目标岗位下的本轮经历主题，并在 `MISSION.md` 记明 JD 缺口。参考岗位画像要保留标签，不当成目标公司要求。对不上就删。
2. **简历锚点。** 它挖 `RESUME.md` 的哪一段？对不上、又确实是 JD 要求而简历没写的，难度档标成加压，不要写成候选人已经做过。
3. **资料锚点。** 追问里的技术事实由 `RESOURCES.md` 的哪一条支撑？缺来源在设计前的一轮检索中处理；设计时仍没有来源，就记缺口，把题改成只问候选人自己的经历，或删掉无来源的技术事实题，不重开检索，不补模型记得的知识点。

只问候选人自身经历、且不引入外部技术事实的开场，可以没有第 3 条，但必须有简历锚点。

**检索停止线：** 本轮目标能力已有采用的来源，或已经决定改问经历，就进入设计，不再为低增量页面继续检索。

两份来源不一致时，两份都引用，把追问放在这个取舍上。不要靠记忆选边。

匿名面经、榜单体「N 道经典题」、以及没有 URL 的印象，不作为出题依据。公司自己的招聘页、工程博客、手册，以及语言或产品的官方文档，才是高信任。

## 校准带

每一轮在 HTML 对话稿里写明这七项；用户显式要求题库 / bank 时，题库也保留这七项并与 HTML 一致。整轮落在简历撑得住、又向外探一点的中间带：热身确认锚点是真的，主攻打目标能力，加压只探一步（一个失败模式、一个简历里该有的数字、或一条还没讲过的 JD 约束）。

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

一场是一个主题，默认可在 `NOTES.md` 的时长内做完。用户要求设计或准备一轮，且用户与笔记都未给时长时，按 35 分钟写入 `NOTES.md` 并说明这是假设；不为时长暂停准备。默认题量：热身 1 题，主攻 2–4 题，加压 1 题。`NOTES.md` 写了不要热身时，可以不设热身。

内容形状（证据清单，不是代写答案）：

- **项目深挖：** 是什么、为何做、个人贡献与数据。笔记偏项目、或笔记未指定且简历里有项目时，主攻用这个形状。
- **技术题：** trade-off、主链路实现、长尾与兜底。
- **具体问题要能听到：** 描述 → 原因 → 方案 → 可量化效果。
- **第一印象：** 1–2 个来自简历指标的亮点，不巡礼整份题库。

### 口语参考答

每题必有，主位置是 HTML 该题的 `<aside class="spoken">`。仅在用户显式要求题库 / bank 且另写 bank 时，才在 bank 该题下的固定小节放同一段。给候选人开口练，不出题人拿它打分。

- **像在答。** 用说得出口的句子，连接词可以有。不要公文腔，也不要把证据标准改成条目念出来。
- **短。** 大约口播 30–90 秒。热身更短，可以不到 30 秒。主攻可以靠近上限，略长一点也可以。不要写成一篇写全的文章。
- **只写简历里有的。** 事实和数字以 `RESUME.md` 为准，没有的不编。讲不完、留下取舍都可以。不是满分样稿。
- **标签写明不是背诵稿。** `Language` 为 `zh` 时，HTML 强标签用「口语参考答 · 非背诵稿」；`en` 时用 “Spoken sketch · not a script to memorize”。仅在另写 bank 时，bank 小节标题分别用 `口语参考答（候选人视角 · 非背诵稿）` 或 `Spoken sketch (candidate side · not a script to memorize)`。`mixed` 跟该题所用语言。
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
        <p>{候选人口播。热身更短。只使用简历已有事实和数字。}</p>
      </aside>
      <p class="cite">依据：<a href="{url}">{标题}</a> · RESUME · MISSION</p>
    </article>
  </section>
  <!-- band-main、band-pressure 同样结构。题号 q1、q2…；另写 bank 时与其题号一致 -->
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

### 可选题库 `NNNN-theme.bank.md`

仅当用户显式要求题库 / bank 时写，默认不生成。HTML 是默认内容主位置；另写题库时，与 HTML 题号、顺序、锚点、七个校准要素、证据标准、追问树、口语参考答和下一轮钩子一致。改一边时同步另一边。

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

`NOTES.md` 在面试工作区根。没有就创建。假设写在对应字段，并在 `Other` 记明哪些是假设、用户可改。`Avoid` 可以留空。

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

HTML、session note 及本轮来源或缺口等内容完成后，只做一次最终自检，不做多轮中途校验：

- 本轮目标能力在 `RESOURCES.md` 里有本次用得上的来源，或写明缺口、明确只问个人经历；HTML 的来源与岗位、简历锚点能对应
- 没有一道题的唯一出处是「经常会问」
- 七个校准要素在 HTML 里都有
- HTML 每题有 `<aside class="spoken">`，并用对应语言标明不是背诵稿
- 这段是短口播：像现场在答，热身更短，其余大约 30–90 秒；没有简历以外的数字；没有写成条目式范文或满分稿
- HTML 每题的证据标准与追问树仍在，没有被口语参考答换掉
- HTML 与 session note 词干相同；未触发「评分表」的请求或校准条件就没有 rubric
- 语言与 `NOTES.md` 一致
- 追问树有拉回分支
- session note 里有下一轮钩子，与 HTML 一致；没对练就写 `designed` 和「只设计，未作答」，不评分
- 默认没有 bank 或临时文件；仅当用户显式要求题库 / bank 时，另核对 bank 与 HTML 的词干、题号、顺序、锚点、七个校准要素、证据标准、追问树、口语参考答和钩子同步
