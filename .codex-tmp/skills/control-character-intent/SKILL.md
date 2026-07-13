---
name: control-character-intent
description: "Align, inspect, interrupt, and resume character language intent and behavior intent for the user's web-novel prose generation workflow. Use when Codex needs to build character intent tracks, decide CONTINUE or ASK_USER before a key prose fragment, normalize the author's intent corrections, update a per-chapter runtime state, or resume drafting after an intent interruption; do not use for creating outlines, execution packs, direct prose drafting, or rewriting character/world fact cards."
---

# Control Character Intent

## Purpose

Control character language intent and behavior intent before and during prose drafting.

This skill is a control layer. It does not create outlines, create execution packs, write prose, or update character/world fact cards. It builds and checks character intent tracks, decides whether prose generation can continue, asks the author only for blocking intent divergences, normalizes the author's answer, and prepares runtime-state updates.

In the `总-分-总` chain, this skill is a `分` control skill. It produces or updates the chapter-level `人物意图结果` product. It receives the creative control plan, chapter contract, detail outline, scene performance rules, necessary character/event/setting facts, and optional execution-pack risk routing, then records chapter-level character intent baselines and only builds full tracks for P0/P1 key fragments. It must not evaluate whole-chapter prose style, rewrite scene performance rules, reorder plot, or draft prose.

## Interface Alignment

Align outputs with the `人物意图结果接口` in:

```text
设计流程与方案/共创机制/模板接口规范_总分总正文生成链路.md
```

Primary formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md
```

Required interface behavior:

- Must read: chapter creative control plan, chapter narrative expression contract, relevant detail-outline fragment, relevant scene performance rule, necessary character/event/setting facts, and execution-pack risk index if it already exists.
- May cite: chapter-level character baselines, current-fragment character knowledge, motive, pressure, relevant prose-facing rule translated into a language/behavior constraint, and high-risk fragment flags.
- Must not repeat: full scene performance contract, full outline, full execution pack, full character card, prose paragraphs, or author-unconfirmed intent.
- Outputs to: prose draft generation, chapter runtime state, execution-pack light reference, and author confirmation when blocked.
- ASK_USER when: character motive is not credible, a simpler action would obviously be available, language intent has multiple business meanings, scene performance requirements conflict with character facts, or generation cannot safely continue.

## Template Fidelity Rule

The output control result must follow the formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md
```

Use `references/intent-track-template.md` only as the subtemplate for the `关键片段意图轨道` section inside the formal `人物意图结果` product.

Preserve the formal template YAML, section headings, tables, checkpoint fields, character track fields, and action vocabulary: `CONTINUE`, `ASK_USER`, or `RESUME`. If a required field cannot be filled from confirmed inputs, do not remove the field or invent the answer. Return `ASK_USER` for blocking intent gaps, or mark a concise pending item in `待确认问题` or `章节运行态更新建议` when the gap is non-blocking and outside the current fragment.

## Workflow

1. Read the formal template `System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md`.
2. Read `references/input-contract.md` before building or updating a character intent result.
3. Establish the chapter-level character intent baseline when generating a full result.
4. Identify P0/P1 key fragments: important dialogue turn, behavior choice, misread escalation, information release, strong joke landing, relationship shift, scene entrance/exit, or action chain.
5. Read `references/intent-track-template.md` and build concise intent tracks only for characters needed by those key fragments.
6. Check language intent and behavior intent:
   - Why does the character speak?
   - Why does the character act?
   - Why not take the simpler action?
   - Does current knowledge support the line or action?
   - Would two valid choices create different character meanings?
7. Decide exactly one action:
   - `CONTINUE`: intent is clear enough for prose generation.
   - `ASK_USER`: a blocking language or behavior intent divergence exists.
   - `RESUME`: the author has answered and the runtime state can be updated.
8. Fill the formal template's `执行包轻引用接口` with coverage tags, risk tags, short summaries, gaps, and suggested backflow. Do not copy full intent tracks into execution-pack-facing text.
9. For `ASK_USER`, read `references/interrupt-protocol.md`, ask one focused question, and stop. Do not continue prose.
10. For author answers, read `references/resume-protocol.md` and normalize the answer into explicit rules, scope, and resume point.
11. For runtime updates, read `references/runtime-state-rules.md` and output the exact update block.
12. Use scene performance rules only by translating them into character-facing constraints, such as speaking mode, explanation limits, interruption behavior, or anti-AI naturalness checks. Do not judge or rewrite whole-chapter style.
13. Run `references/quality-check.md` before returning the control result.

## Output Actions

### CONTINUE

Return:

- the formal `人物意图结果` sections needed for this generation scope;
- chapter-level character intent baselines when producing a full chapter result;
- character intent tracks;
- execution-pack light-reference coverage tags and gaps;
- check result `CONTINUE`;
- any runtime rules inherited by the prose skill.

Do not write prose.

### ASK_USER

Return:

- confirmed facts;
- one blocking divergence;
- model recommendation;
- a minimal verification fragment;
- request for the author to choose or directly edit the intent track.

Stop after the question.

### RESUME

Return:

- normalized author decision;
- affected scope;
- runtime-state update block;
- resume point for the prose skill.

Do not rewrite previous prose.

## Boundaries

Do:

- Treat character language intent and behavior intent as P0 controls.
- Treat the chapter creative control plan as the authority for conflict priority and ASK_USER triggers.
- Use the scene performance contract only to constrain how a character can naturally speak or act in the current fragment.
- Let the author directly edit intent tracks.
- Keep temporary chapter intent in chapter runtime state.
- Preserve character-card boundaries: character cards contain long-term world-internal facts, not chapter-local intent.
- Ask only when the character's reason for speaking or acting is unclear.

Do not:

- Write novel prose.
- Create or revise chapter outlines or execution packs.
- Create or revise scene performance contracts.
- Decide whole-chapter prose style or anti-AI strategy.
- Automatically write temporary intent into character cards.
- Ask about wording, minor action, decorative detail, or general writing difficulty.
- Continue generation after `ASK_USER`.
- Use external finished prose, comparison reports, or non-system writing material as source input.
