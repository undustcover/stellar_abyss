---
name: co-create-narrative-expression
description: Run author-led narrative expression workshops for novel writing, especially V1.3 chapter-level narrative expression contracts and chapter creative control plans. Use when Codex needs to discuss a chapter's expression direction, reader knowledge, POV filtering, misreading system, bright-line/hidden-line development, author intent, downstream skill division of labor, or whether confirmed chapter decisions should become a narrative expression contract plus chapter creative control plan. In the current iteration, support chapter mode only; volume and unit contracts may be referenced as placeholders or temporary references but must not be formally developed by this skill.
---

# Co-create Narrative Expression

## Scope

Use this skill to run a chapter-level narrative expression workshop before creating a chapter narrative expression contract and a lightweight `章节创作总控规划`.

The narrative expression contract records chapter author intent and narrative boundaries. The creative control plan records downstream division of labor, interface rules, mutual references, conflict priority, and token boundaries. Do not merge them into one large document.

This skill is the first `总` in the `总-分-总` prose-generation chain. It creates the interface layer that later `分` skills must obey. It must not create plot outlines, prose-performance rules, execution dispatch, character intent tracks, or prose drafts.

Current supported mode:

- `chapter`: discuss, confirm, and then create a chapter-level narrative expression contract, a chapter creative control plan, and a co-creation discussion log.

Current unsupported modes:

- `volume`: keep as placeholder or existing reference only.
- `unit`: keep as placeholder or temporary reference only. Do not develop the formal unit-level workflow here.

## Hard Rule

Do not create or overwrite a chapter narrative expression contract, chapter creative control plan, or co-creation log before the author actively confirms the final discussion summary.

Author confirmation must be explicit. Accept confirmations such as:

- "确认"
- "可以落地"
- "生成契约"
- "按这个写"

If the author keeps correcting, supplementing, rejecting, or asking questions, continue discussion. Do not create files yet.

## Priority Order

When sources conflict, use this priority:

1. Author's current-session explicit feedback.
2. Existing temporary or confirmed unit-level narrative expression contract.
3. Source outline or P0 outline.
4. Older system assumptions.

Never mechanically inherit source-outline wording when the author has corrected the chapter-level expression direction.

## Interface Alignment

Use the repository-wide interface standard from:

```text
设计流程与方案/共创机制/模板接口规范_总分总正文生成链路.md
```

The chapter narrative expression contract must align with the `章节级叙事表达契约接口`.

The chapter creative control plan must align with the `章节创作总控规划接口`.

For the creative control plan:

- Must read: confirmed chapter workshop conclusions and the chapter narrative expression contract.
- May cite: contract ID/path, author-intent boundaries, downstream artifact names, conflict rules, ASK_USER triggers, token limits.
- Must not repeat: complete plot, scene details, character cards, event cards, prose-performance rules, finished prose, dialogue, or punchlines.
- Outputs to: chapter detail outline, scene performance contract, chapter execution pack, character intent control, and prose draft generation.
- ASK_USER when: downstream responsibilities, author aesthetic direction, reader information boundary, or business conflict priority is unclear.

## Template Fidelity Rule

After author confirmation, generated files must preserve the repository template structure unless the author explicitly approves a template change.

Use these templates as the source of truth for headings, YAML fields, and required tables:

- `System_alpha/00_总控台/02_模板库/TPL-NAR-CHAPTER_章节级叙事表达契约.md`
- `System_alpha/00_总控台/02_模板库/TPL-CHAPTER-CREATIVE-CONTROL_章节创作总控规划.md`
- `System_alpha/00_总控台/02_模板库/TPL-COCREATE-LOG_共创讨论记录.md`

The creative control plan must preserve the formal `related_director_prose_quality_rules` field when the chapter uses the total-split-total prose chain. This field only registers the director-layer prose-quality reference path and must not copy reusable prose-quality rules into the plan.

When a field cannot be completed, keep the field and write a concise pending item under `待确认问题`; do not delete or rename required sections. Do not add large custom sections outside the template just because the current chapter has extra discussion material.

## Workflow

### 1. Gather Inputs

Identify:

- target unit and chapter;
- source outline;
- related temporary or confirmed unit contract;
- existing chapter contract, if any;
- forbidden sources;
- relevant character cards only when needed for character boundaries.

If any source is forbidden by the user, do not read it.

### 2. Start With Natural Language Discussion

Use plain natural language, not tables, when asking the author to decide or correct the chapter direction.

Present a discussion draft in the chat with these sections:

1. "我理解本章不是..."
2. "我理解本章是..."
3. "读者本章能知道..."
4. "读者本章不能知道..."
5. "POV 人物能感到..."
6. "本章最容易跑偏的是..."
7. "我判断需要回流单元契约的是..."

Also include a natural-language expression mix when relevant:

- 明线如何推进;
- 暗线如何推进;
- 喜剧、现实压力、异常感、信息揭示、留白、情绪压迫的大致强弱。

Do not ask the author to fill out tables during discussion.

### 3. Required Business Questions

Always ask or confirm:

- "本章不是要写成什么?"
- "本章真正要达成什么表达?"
- "明线推进是什么?"
- "暗线推进是什么?"
- "读者本章能知道什么?"
- "读者本章不能知道什么?"
- "POV 人物能感到什么，不能感到什么?"
- "本章最容易跑偏的方向是什么?"
- "是否有需要回流单元契约的事项?"

Reader-leading degree is not a fixed required question. Ask it only if the chapter discussion requires deciding whether readers lead, match, or trail the POV character.

### 4. Classify Author Feedback

Classify author feedback into these buckets:

- bright-line development;
- hidden-line development;
- reader information boundary;
- POV cognition boundary;
- misreading direction;
- character's chapter function;
- expression mix;
- title semantics;
- hard prohibitions;
- unit-contract backflow.

If the author corrects a local detail, actively expand the impact area. For example, if the author says a character's first impression should be "会所熟客", ask whether this also forbids that character from acting as an anomaly explainer in this chapter.

### 5. Produce a Confirmation Summary in Chat

Before creating files, summarize in the chat:

- confirmed chapter expression;
- confirmed reader knowledge boundary;
- confirmed POV filtering;
- confirmed misreading system;
- confirmed bright-line and hidden-line roles;
- confirmed character chapter functions;
- hard prohibitions;
- downstream skill division of labor;
- required cross-references between later artifacts;
- conflict priority and ASK_USER triggers for downstream generation;
- unit-contract backflow items, or "暂无";
- files that will be created or updated after confirmation.

Ask the author to actively confirm. Do not proceed on silence or ambiguous approval.

### 6. Create Files Only After Confirmation

After explicit author confirmation, create exactly three chapter workshop outputs:

1. chapter narrative expression contract;
2. chapter creative control plan;
3. co-creation discussion log.

Use the repository's templates when available:

- `System_alpha/00_总控台/02_模板库/TPL-NAR-CHAPTER_章节级叙事表达契约.md`
- `System_alpha/00_总控台/02_模板库/TPL-CHAPTER-CREATIVE-CONTROL_章节创作总控规划.md`
- `System_alpha/00_总控台/02_模板库/TPL-COCREATE-LOG_共创讨论记录.md`

The creative control plan must not repeat plot, scene details, character cards, event cards, or finished prose. It is an interface and coordination document, not a chapter outline or execution pack.

Default output path for test chapters:

```text
<chapter-test-directory>/V1.3校准/
```

For P0C3, this is:

```text
测试文本/正文测试/第一单元/skills第三章测试/V1.3校准/
```

For later chapters, create or use each chapter's own `V1.3校准/` directory.

### 7. Handle Unit Contract Backflow

Do not automatically modify the temporary unit contract while creating the two chapter outputs.

Mark backflow when:

- a chapter-level rule applies to multiple chapters;
- the author correction contradicts the temporary unit contract;
- the chapter information boundary affects later chapters;
- a character expression boundary should apply across the unit.

Record backflow in:

- chapter contract: "待回流上级契约事项";
- co-creation log: "待回流事项".

Modify the temporary unit contract only as a separate step after the author asks for or confirms that update.

## Output Requirements

The chapter contract should be concise and differential:

- inherit unit-level rules;
- write only chapter-specific differences;
- avoid duplicating unit-wide rules;
- structure final machine-readable details in tables;
- keep author quotes and raw discussion out of the contract.

The chapter creative control plan should:

- coordinate downstream skill responsibilities;
- require later artifacts to reference each other without copying full content;
- define which layer handles author intent, plot skeleton, prose performance, character intent, execution scheduling, and prose drafting;
- register the director-layer reusable prose-quality rules as a prose-draft reference when relevant, without copying those rules into the creative control plan;
- define conflict priority and when downstream skills must ask the author;
- keep token boundaries explicit.
- include a clear continuation marker for downstream work: current chapter, related artifact paths, next expected skill, and whether P0C3 testing is still blocked.

The co-creation log should preserve:

- what the system proposed;
- what the author corrected;
- what was confirmed;
- what was rejected;
- what entered the contract;
- what stayed only as discussion context;
- what should backflow to the unit contract.

## Failure Modes

If a chapter contract already exists but lacks author confirmation:

- treat it as `system_draft` or unconfirmed;
- do not continue downstream to outline generation;
- run the workshop and create/update the co-creation log after confirmation.

If the author identifies a process mistake:

- acknowledge the process failure;
- classify whether it is missing skill enforcement, missing template fields, or missing business rules;
- fix the workflow before continuing downstream.

If the task asks for a unit or volume contract:

- state that this skill currently supports chapter mode only;
- use existing placeholders or temporary references if needed;
- do not develop formal unit or volume flow unless the user explicitly switches scope.
