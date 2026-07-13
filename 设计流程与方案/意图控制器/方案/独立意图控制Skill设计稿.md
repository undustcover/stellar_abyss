# 独立意图控制 Skill 设计稿

## 一、设计结论

系统需要一个独立的意图控制 Skill。

该 Skill 不是第四个正文生成 Skill，也不是新的大纲生成 Skill，而是一个控制层 / 协议层。

建议名称：

```text
control-character-intent
```

建议位置：

```text
.codex-tmp/skills/control-character-intent/
```

它负责：

```text
建立人物意图轨道
判断 CONTINUE / ASK_USER
执行中断提问
归一化作者回答
更新章节运行态
提供 RESUME 信息
```

它不负责：

```text
生成章节细纲
生成章节执行包
直接写正文
自动回写人物卡
修改世界事实
决定正文详略、留白、句段松紧和读者展示方式
修订已经生成的过满草稿
```

第三章第二次测试后的边界补充：

```text
control-character-intent 只判断人物为什么说、为什么做、为什么不采取更简单行动。

如果人物意图已经成立，但正文问题是内容太满、读者视角过滤失败、正确线索展示过清、AI感强、没有留白或阅读体验累，则不应继续归因给本 Skill。

这类问题应交给正文生成 Skill 的正文输出策略，或草稿后的作者意图修订流程。
```

---

# 二、触发场景

当用户或系统需要执行以下任务时，应使用本 Skill：

1. 正文生成前，需要检查人物为什么说、为什么做；
2. 正文生成中，需要为关键片段建立人物意图轨道；
3. 人物语言意图或行为意图存在分歧；
4. 作者直接改写人物意图轨道后，需要归一化为规则；
5. 需要将作者确认写入章节运行态；
6. 需要从中断点恢复正文生成；
7. 需要检查正文片段是否违反人物语言或行为意图。

---

# 三、Skill 本体结构

建议结构：

```text
control-character-intent/
├── SKILL.md
└── references/
    ├── input-contract.md
    ├── intent-track-template.md
    ├── interrupt-protocol.md
    ├── runtime-state-rules.md
    ├── resume-protocol.md
    └── quality-check.md
```

暂不需要 scripts。

原因：

```text
第一版重点是交互判断和写作控制协议，不是稳定机械转换。
```

---

# 四、SKILL.md 设计

## 4.1 Frontmatter

建议：

```yaml
---
name: control-character-intent
description: "Align, inspect, interrupt, and resume character language intent and behavior intent for the user's web-novel prose generation workflow. Use when Codex needs to build character intent tracks, decide CONTINUE or ASK_USER before a key prose fragment, normalize the author's intent corrections, update a per-chapter runtime state, or resume drafting after an intent interruption; do not use for creating outlines, execution packs, direct prose drafting, or rewriting character/world fact cards."
---
```

## 4.2 Body 核心内容

SKILL.md 应保持简洁，只写：

1. Purpose；
2. When to use；
3. Workflow；
4. Output actions；
5. Boundaries；
6. Which reference to read.

不要把所有需求文档全文塞进 SKILL.md。

---

# 五、References 设计

## 5.1 input-contract.md

定义可读取输入：

- 章节细纲；
- 章节执行包；
- 章节运行态；
- 人物卡长期语言和行为边界；
- 事件卡 / 设定卡事实限制；
- 当前已生成正文片段；
- 作者刚确认的意图修正。

同时定义禁止输入：

- 外部成品正文；
- 未确认参照稿；
- 非系统写作材料；
- 与当前章节无关的完整人物卡全文；
- 未经作者确认的长期人物结论。

## 5.2 intent-track-template.md

保存人物意图轨道模板：

```yaml
intent_checkpoint:
  chapter_id:
  scene_id:
  fragment_id:
  fragment_scope:
  risk_level:
  action: CONTINUE

character_intent_tracks:
  人物名:
    behavior_goal:
    behavior_motive:
    immediate_action:
    why_not_simpler_action:
    language_goal:
    language_strategy:
    emotional_pressure:
    knowledge:
      knows:
      does_not_know:
      assumes:
      suspects:
    forbidden:
    expected_effect_on_other:
    expected_consequence:
```

## 5.3 interrupt-protocol.md

定义 ASK_USER：

```markdown
## 人物意图中断：需要确认一个关键分歧

### 已确认

### 当前分歧

### 我的判断

### 最小验证片段

请确认 A、B，或直接改写人物意图轨道。
```

并规定：

```text
触发 ASK_USER 后不得继续生成正文。
```

## 5.4 runtime-state-rules.md

定义如何写入章节运行态：

- resolved_intents；
- resolved_divergences；
- pending_divergences；
- draft_fragments；
- long_term_rule_candidates。

重点规则：

```text
临时人物意图不得自动写回人物卡。
```

## 5.5 resume-protocol.md

定义恢复格式：

```markdown
已确认：
- ...

影响范围：
- ...

已更新章节运行态。

继续当前正文片段：
```

## 5.6 quality-check.md

定义检查：

- 人物为什么说是否明确；
- 人物为什么做是否明确；
- 为什么不采取更简单行动是否成立；
- 台词是否只为解释信息；
- 行为是否只为推动剧情；
- 作者确认是否已归一化；
- 运行态是否更新；
- 是否误写人物卡。

---

# 六、工作流

## 6.1 建立人物意图轨道

输入：

- 当前关键片段；
- 章节执行包；
- 章节运行态；
- 必要人物卡摘要。

输出：

```text
人物意图轨道
CONTINUE 或 ASK_USER
```

## 6.2 判断是否中断

强制中断：

```text
人物语言意图不明
人物行为意图不明
人物为什么不采取更简单行动无法解释
人物认知无法支撑对白或行为
台词会塑造出不同人物形象
行为会显著改变人物关系或情节走向
```

## 6.3 作者改写轨道

作者可以直接改：

```text
不是证明项目可靠，而是证明自己不是被人骗的蠢货。
```

系统必须转换为：

```text
陈科当前语言目标是维护自尊，避免承认判断失误；后续对白不能变成客观项目说明。
```

## 6.4 更新运行态

作者确认后写入：

```yaml
resolved_intents:
  - id:
    character:
    type:
    decision:
    normalized_rule:
    scope:
```

## 6.5 恢复生成

输出 RESUME 信息给正文生成 Skill。

本 Skill 不直接写正文主体。

---

# 七、与现有 Skill 的关系

## 7.1 与 generate-chapter-detail-outline

细纲 Skill 提供：

- 关键人物；
- 基础认知；
- 外在目标；
- 关系压力；
- 潜在意图风险。

意图控制 Skill 负责在正文生成前展开为人物意图轨道。

## 7.2 与 generate-chapter-execution-pack

执行包 Skill 提供：

- 关键对白风险；
- 关键行为风险；
- 禁止替人物决定项；
- 意图控制器建议检查片段。

意图控制 Skill 负责判断是否中断。

## 7.3 与 generate-chapter-prose-draft

正文生成 Skill 接收：

- CONTINUE；
- ASK_USER；
- RESUME；
- 已确认人物意图轨道；
- 章节运行态规则。

正文生成 Skill 根据轨道写正文。

---

# 八、第一版输出格式

## 8.1 CONTINUE

```markdown
## 人物意图轨道

...

## 检查结果

CONTINUE：不存在需要作者确认的人物语言或行为分歧。
```

## 8.2 ASK_USER

```markdown
## 人物意图中断：需要确认一个关键分歧

...
```

## 8.3 RESUME

```markdown
已确认：
- ...

影响范围：
- ...

已更新章节运行态。

可从以下断点继续：
- ...
```

---

# 九、开发验收

独立意图控制 Skill 第一版通过开发验收，至少满足：

1. 能读取章节执行包和章节运行态；
2. 能输出人物意图轨道；
3. 能判断 CONTINUE / ASK_USER；
4. 能在 ASK_USER 后停止正文生成；
5. 能接受作者直接改写轨道；
6. 能归一化作者回答；
7. 能给出章节运行态更新内容；
8. 能输出 RESUME 信息；
9. 不直接写正文；
10. 不自动回写人物卡；
11. 不把正文表现问题误判为人物意图分歧；
12. 能在检查结果中提示“本问题属于正文输出策略 / 作者意图修订”，但不直接执行正文修订。

---

# 十、开发启动判断

可以启动。

启动前必须先创建 Skill 本体，而不是继续只改正文生成 Skill。

原因：

```text
意图控制是跨阶段控制层。
如果只放进正文生成 Skill，会导致职责混杂，难以测试和复用。
```
