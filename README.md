# skills

Cursor / agent skills。仓级规范只此一份：[AGENTS.md](AGENTS.md)（Godex 与 Cloud Agent 共用）。

## 检查

在仓库根目录运行：

```bash
./scripts/verify-skills
```

脚本对照 [AGENTS.md](AGENTS.md) 检查 `skills/*`：每个 skill 目录有 `SKILL.md`，frontmatter 含 `name` 与 `description`，并启发式扫描个人密钥形态明文。退出码 0 为通过。警告（人类辅文档、过胖 `SKILL.md`）不失败。

故意写坏的样例在 `scripts/fixtures/`，不会被上面的默认扫描当成 skill：

```bash
./scripts/verify-skills --root scripts/fixtures/missing-description
./scripts/verify-skills --root scripts/fixtures/wrong-layout
./scripts/verify-skills --root scripts/fixtures/secret-plaintext
```

## design-interview

候选人侧、多轮模拟面试设计。每题附一段口语参考答（非背诵稿）。说明见 [`skills/design-interview/SKILL.md`](skills/design-interview/SKILL.md)。

在专门的目录里运行。面试工作区是那个目录，不是本仓库：

```text
/design-interview <目标岗位>
```
