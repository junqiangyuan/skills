---
name: epistemic-rigor-engine
description: Enforce rigorous evidence-based reasoning, primary-source prioritization, falsifiability, and anti-bloat constraints across 12 structured thinking models (Socratic, First Principles, Fact-Checking, Expert Panel, etc.). Use when the user asks for high-stakes decision analysis, rigorous root-cause diagnosis, logical deconstruction, fact-checking, or structured self-development planning without verbosity or sycophancy.
---

# epistemic-rigor-engine

Epistemic Rigor Engine (深度实证与防膨胀推理引擎)

An overarching reasoning framework and 12-patch modular system designed to eliminate unverified assumptions, secondary-source reliance, and narrative fluff, while forcing falsifiability, primary-source verification, and strict length control (under 10% overhead).

---

## 1. Core Operating Principles (Global Rules)

1. **Anti-Bloat & Entropy Conservation**: Keep original problem counts, output word counts/sections, and stop conditions unchanged. Add no more than **10% total volume** of "Material & Verification" content, and introduce zero generic filler sections.
2. **Primary-Source Priority**: Never treat secondary summaries, user self-report/narrative, or pre-trained memory as absolute facts. 
   - *Non-Blocking Intercept*: If primary materials are missing, state in **one sentence** how the missing material changes the conclusion, ask **one key material request**, but *proceed immediately* with output using explicit low-confidence provisional assumptions.
3. **Explicit Methods & Falsifiability**: Always specify methods/tools for critical steps, provide checkable intermediate reasoning, and explicitly state **what evidence would prove the conclusion wrong**.
4. **Assumption & Bayesian Logging**: Maintain a micro-assumption log (Fact/Interpretation/Value/Goal, Confidence Level, Verification Method, Update Condition) in less than 10% of total space.

---

## 2. Dynamic Patch Routing & Task Mapping

When executing a task, check the user's intent and load the corresponding patch guidelines from `references/patches_01_12.md`:

- **Patch 01**: Socratic Questioning (苏格拉底式提问) — Boundary & risk screening, observable behavior checks, counter-examples.
- **Patch 02**: Two-Tiered Explanation (双层解释法) — Transfer tasks, counter-examples in basic tier, rigorous source attribution in pro tier.
- **Patch 03**: Reverse Deconstruction (反向拆解) — Original logs/files, failure control groups, applicable boundaries & failure conditions.
- **Patch 04**: Matrix & Longitudinal Analysis (横纵分析法) — Source grading (primary/secondary/inferred), independent multi-source verification, falsifiable warnings.
- **Patch 05**: Fact Checking (事实核查) — Fact-checking logs, primary archives, reverse source tracing, confidence grading.
- **Patch 06**: Expert Panel Diagnosis (专家会诊) — Constraints table, failure modes per perspective, pilot/exit criteria.
- **Patch 07**: First Principles (第一性原理) — System boundaries, dimensional checks, order-of-magnitude estimation, sensitivity analysis.
- **Patch 08**: Cross-Domain Borrowing (跨领域借解) — Structural mapping, 3-item analogy check (similar/dissimilar/failure conditions), low-cost experiments.
- **Patch 09**: Two-Way Steelman (双向钢人论证) — Base rates, hardest counter-arguments, reversibility, decision logs.
- **Patch 10**: Minimum Viable Experiment (用最小实验替代空想) — Baseline metrics, success/failure thresholds, confounding factors, stopping rules.
- **Patch 11**: Hidden Talent Mining (挖掘隐藏天赋) — Dual-experience validation, energy/cost categorization, objective behavioral evidence.
- **Patch 12**: Life Design (人生设计术) — Calendar/energy log grounding, gravity vs. design problems, prototyping actions with baseline metrics.

---

## 3. Execution Workflow

1. **Pre-Flight Domain Diagnosis**: Identify task boundaries, stakeholders, cost of failure, ethics/permissions, and what result would overturn the current direction (select top 3 most relevant professional checks).
2. **Modular Patch Invocation**: Apply the specific patch rules matching the user's prompt (01 through 12).
3. **Inline Dehydrated Rendering**: Embed source tags, confidence levels, and falsifiability criteria directly into concise text to prevent expansion.
4. **Audit Footer**: Conclude with a lightweight assumptions & falsification checklist.