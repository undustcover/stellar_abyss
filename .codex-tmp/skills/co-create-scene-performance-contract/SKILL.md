---
name: co-create-scene-performance-contract
description: Co-create scene performance contracts for the user's novel-writing system. Use when Codex needs to discuss and confirm whole-chapter or key-scene prose expression rules before chapter execution-pack and prose drafting, especially wording, sentence rhythm, dialogue naturalness, narration boundaries, anti-AI feel, human-written texture, and key-scene written performance. Do not use for plot outlining, chapter narrative-expression boundaries, character intent tracks, single high-risk scene execution briefs, or final prose drafting.
---

# Co-create Scene Performance Contract

## Purpose

Run an author-led workshop for prose performance decisions before execution-pack and prose-draft generation.

This skill does not decide what happens in the chapter. It decides how confirmed material should feel on the page for this chapter or key scene: rhythm, diction, dialogue fracture, narration density, chapter-specific anti-AI risks, and scene-level written texture.

Reusable prose-quality rules belong to the final director layer, especially `generate-chapter-prose-draft/references/director-prose-quality-rules.md`. Do not copy general de-AI, dialogue-naturalization, humor, or sentence-shape rules into every scene performance contract. Only record differences, exceptions, intensified rules, or local prohibitions that the current chapter needs.

Keep this skill separate from `generate-scene-execution-brief`. A scene execution brief is a local executable constraint document for one difficult scene; this skill is a co-creation contract for prose expression and author aesthetic.

In the `总-分-总` chain, this skill is a `分` skill. It translates confirmed chapter intent and outline structure into prose-performance rules. It must not modify plot order, reveal boundaries, character motive, execution dispatch, or final prose.

## Interface Alignment

Align outputs with the `场景演出契约接口` in:

```text
设计流程与方案/共创机制/模板接口规范_总分总正文生成链路.md
```

Required interface behavior:

- Must read: chapter creative control plan, chapter narrative expression contract, chapter detail outline, author-confirmed prose aesthetic directions, and the director-layer reusable prose-quality rules when deciding whether a rule is common or chapter-specific.
- May cite: high-level reader feeling from the chapter contract; scene IDs, scene functions, and action movement from the outline; division of labor and token boundaries from the creative control plan.
- Must not repeat: full plot, full outline, character cards, character motive tracks, execution-pack dispatch, finished prose, full dialogue, or full punchlines.
- Outputs to: chapter execution pack, character intent control, and prose draft generation.
- ASK_USER when: author aesthetic direction, sample-sentence permission, narration/psychology scale, dialogue-naturalization direction, anti-AI risk judgment, or whether a rule should become reusable director-layer guidance is unclear.

## Template Fidelity Rule

The output product must follow the formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-SCENE-PERFORMANCE_场景演出契约.md
```

`references/performance-contract-template.md` is only the local skill reference mirror and pointer to that formal template.

Preserve YAML fields, heading order, required tables, and section names. If a field cannot be filled from confirmed inputs, keep the field and write the issue under `待确认问题`. Do not rename sections, remove checks, or add a parallel custom contract structure unless the author explicitly changes the template.

## Required Inputs

- `章节创作总控规划`;
- chapter narrative expression contract;
- chapter detail outline;
- optional existing execution pack draft;
- optional author-provided aesthetic directions for prose texture.
- reusable director-layer prose-quality rules, if available: `generate-chapter-prose-draft/references/director-prose-quality-rules.md`.

If the task lacks `章节创作总控规划`, stop and ask whether to create or locate it. Do not silently proceed with disconnected scene-performance rules.

## Hard Rules

- Ask the author when prose aesthetic, business intent, reader feeling, or style direction is unclear.
- Do not ask the author about technical file naming, table order, or default formatting unless it changes business meaning.
- Do not create or overwrite a scene performance contract before the author explicitly confirms the final summary.
- Do not restate the chapter outline, character cards, event cards, or narrative contract in full.
- Do not write finished prose, full dialogue, punchlines, or ending lines.
- Do not use the contract as a warehouse for reusable text-quality rules. If a rule applies across chapters, mark it as director-layer/backflow material instead of restating it as a local scene rule.
- Do not replace `control-character-intent`; this skill may flag a character-expression risk but must not decide a character's intent track.
- If prose-performance requirements would change plot action, reader information boundary, or character motive, do not absorb the change here. Route it back to the chapter detail outline, chapter narrative expression contract, character intent control, or ASK_USER according to the creative control plan.

## Workflow

### 1. Gather Inputs

Identify:

- target unit and chapter;
- `章节创作总控规划`;
- chapter narrative expression contract;
- chapter detail outline;
- scenes marked as important or high-risk by upstream material;
- author-provided examples or prohibitions for prose style.

If inputs conflict, follow the conflict priority in the chapter creative control plan. If no priority exists, ask the author.

### 2. Discuss Prose Performance in Natural Language

Use plain natural language first. Do not ask the author to fill tables.

Discuss:

- whole-chapter written texture;
- sentence rhythm and paragraph density;
- dialogue naturalness and interruption pattern;
- narration and psychological description boundary;
- environment/action/object usage;
- humor and serious-pressure balance at the language level;
- anti-AI risks;
- which items are reusable director-layer rules versus this chapter's local expression differences;
- key-scene expression differences.

### 3. Required Business Questions

Ask or confirm when not already clear:

- "本章文字读起来应该更紧、更松、更碎，还是更生活化?"
- "对白应该更像互相打断、各说各话、试探回避，还是更直接?"
- "旁白可以吐槽到什么程度?"
- "心理描写是压低、点到为止，还是允许短促显影?"
- "哪些表达会让你觉得 AI 味重?"
- "哪些场景需要特殊文字质感?"
- "是否允许提供示例句? 如果允许，示例句只能作为方向，不作为正文成品。"

### 4. Produce Confirmation Summary

Before creating files, summarize:

- whole-chapter prose performance baseline;
- key-scene performance differences;
- dialogue rules;
- narration and psychological-description rules;
- anti-AI prohibitions;
- reusable prose-quality items that should backflow to director-layer rules instead of entering the local contract;
- conflicts or missing author decisions;
- files that will be created or updated.

Ask the author to confirm explicitly. Do not proceed on silence.

### 5. Create Contract After Confirmation

Use `System_alpha/00_总控台/02_模板库/TPL-SCENE-PERFORMANCE_场景演出契约.md` as the exact product shape. Read `references/performance-contract-template.md` only as the local mirror if the formal template is not directly opened in the current context.

Default output type:

```yaml
type: scene_performance_contract
system: narrative
status: draft
temporary: true
```

## Output Requirements

The contract must be concise and differential:

- reference upstream files by path or ID;
- record only prose-performance decisions;
- record only chapter-specific prose-performance decisions; do not duplicate reusable director-layer prose-quality rules;
- keep full discussion out of the contract;
- include whole-chapter rules only when they affect drafting;
- include key-scene rules only for scenes that need special written treatment;
- route character motive and knowledge problems to `control-character-intent`;
- route one-scene executable staging problems to `generate-scene-execution-brief`.
- include a token-boundary check proving it did not copy the full outline, execution pack, or finished prose.

## Quality Check

Read `references/quality-check.md` before returning the contract.
