# AGENTS.md

本文件是本仓库**唯一**的 skill 规范入口。**Godex** 与 **Cloud Agent** 共用这一份。不要另写第二套顶层规范（并列的仓级说明、第二份 `AGENTS` 类文件都不算）。README 只链到这里。

长模板和资料索引放外链，不把教程全文贴进本文件或 skill。

- 写法（只作链接，不收录正文）：[Extra08 如何写出好的 Skill](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra08-%E5%A6%82%E4%BD%95%E5%86%99%E5%87%BA%E5%A5%BD%E7%9A%84Skill.md)、[Agent Skills 概述](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/overview)、[Agent Skills 最佳实践](https://docs.anthropic.com/en/docs/agents-and-tools/agent-skills/best-practices)
- 差距分析索引：[摘要](https://docs.google.com/document/d/1JFUG_jxEphvmYKUBQwhLASfP9On-OwV516NN15vVT-4/edit)、[全文](https://docs.google.com/document/d/1icvtjjMrJAdAeItFAEA-WyaeX-pdy0N1aujT4937kF0/edit)、[Drive](https://drive.google.com/drive/folders/14fczqOLB5USHT_G4FDrMauVPFOnr_RBx)

## 布局与命名

每个 skill 一个目录，入口文件名固定：

```text
skills/<name>/SKILL.md
```

- `<name>` 只含小写字母、数字、连字符，最长 64，且与 frontmatter 的 `name` 相同。
- 格式、资产、脚本可以放在同一目录，由 `SKILL.md` 按需指向。引用保持从 `SKILL.md` 一层可达。
- 人类分析长文（例如 `docs/issue-3-analysis.md`）**不是** skill 内容，不要新挂进 `skills/<name>/`。这类文件不是必跑内容。

## SKILL.md

每个 skill 目录必须有 `SKILL.md`。文首 YAML frontmatter 必须包含 `name` 和 `description`：

```yaml
---
name: <name>
description: >-
  这个 skill 做什么，以及何时触发。触发边界写在 description。
---
```

- `description` 非空，最长 1024 字符。写清做什么、何时用。触发边界放在 `description`，不要只写在正文。
- 正文只留本仓库才有的流程、约束和格式。宜短（约 500 行内）。超过只作提醒，不在本文件里强制瘦身。

## 禁区

- **不写个人密钥。** 不把密钥、token、口令、私钥以明文放进 skill。
- **不抄教学噪音。** 不把教程腔、概念科普写进 skill。
- **模型已会的不进 Skill。** 模型已经知道的 API、常规写法和通用知识不要写进来。

## PR / 合入验收

验收**不只看 diff**。合入前对照本文件，并核对下面的已知全局债。禁区里脚本扫不到的部分（教学噪音、模型已会的内容）靠人眼对照本节，不能只看改动行。

### 已知全局债

- `skills/design-interview/docs/issue-3-analysis.md` 是人类分析稿，不是 skill 必跑内容。不要再往 skill 目录里加同类辅文档。
- `design-interview` 的行为规则、题号与口语同步不在本规范的机械检查里（完整 validate-pack 另案）。文件偏长可以指出，不因此强制瘦身。
