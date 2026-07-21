---
name: generate-chapter-prose-draft
description: "Generate, continue, assemble, revise, or check whole-chapter web-novel prose drafts as the final director skill in the user's novel-writing system. Use when Codex needs to write a complete chapter V1 by directly coordinating a chapter creative control plan, chapter narrative expression contract, chapter detail outline, scene performance contract, lightweight chapter execution pack, and chapter-level character intent result. Use after CONTINUE or RESUME for key fragments, maintain clean prose output, and preserve scene order, viewpoint, cognition limits, information hiding, character intent tracks, pacing, ending state, and author prohibitions; do not use for creating outlines, execution packs, scene performance contracts, intent decisions, single-scene briefs, or rewriting upstream world facts."
---

# Generate Chapter Prose Draft

## Purpose

Write or assemble one complete web-novel chapter draft as the final director skill. Coordinate the chapter creative control plan, narrative expression contract, chapter detail outline, scene performance contract, lightweight execution pack, and approved chapter-level character intent result.

Keep this skill after `co-create-narrative-expression`, `co-create-scene-performance-contract`, `generate-chapter-execution-pack`, and `control-character-intent`. It writes prose, but it must not redesign the chapter, add new canon, explain hidden mechanics, revise upstream cards, or make P0 character intent decisions by itself. If the user provides only a chapter detail outline, stop and ask for the missing upstream artifacts unless they explicitly ask for a rough draft.

The draft must not depend on separate post-processing skills to become readable. Reusable prose-quality controls live in `references/director-prose-quality-rules.md`; chapter-specific expression differences come from the scene performance contract.

In the `总-分-总` chain, this skill is the final `总`. It directly coordinates all confirmed independent artifacts under the chapter creative control plan. It must not make the chapter execution pack the only input, and it must not paste upstream tables, intent tracks, or analysis labels into the prose body.

## Interface Alignment

Align outputs with the `正文草稿模板接口` in:

```text
设计流程与方案/共创机制/模板接口规范_总分总正文生成链路.md
```

Formal delivery template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHAPTER-PROSE-DRAFT_正文草稿交付版模板.md
```

Required interface behavior:

- Must read: chapter creative control plan, chapter narrative expression contract, chapter detail outline, scene performance contract, chapter execution pack, `type: character_intent_result`, and chapter runtime state when available.
- May cite: confirmed upstream artifacts, current-fragment source material, creative-control conflict priority, and ASK_USER rules.
- Must not repeat: upstream template tables, process labels, intent tracks, analysis explanations, execution-pack structure phrases, or upstream summaries inside the prose body.
- Outputs to: draft file, prose evaluation, local repair, and necessary backflow to co-creation or intent control.
- ASK_USER when: upstream conflict cannot be resolved, intent control returns `ASK_USER`, drafting would change plot/information/person boundary/author aesthetic, or drafting would require non-system finished material.

## Template Fidelity Rule

The output product must follow the formal delivery template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHAPTER-PROSE-DRAFT_正文草稿交付版模板.md
```

`references/draft-template.md` is only the local skill reference mirror and pointer to that formal template.

Preserve YAML source fields, `## 正文`, and `## 生成备注`. For formal delivery, the generated instance may omit `## 模板接口` as allowed by the draft template, but it must not omit `## 生成备注` unless the author explicitly requests clean prose only. Do not add outline labels, scene tables, intent tracks, process notes, or upstream summaries inside `## 正文`.

## Workflow

1. Read `references/input-contract.md` before drafting.
2. Read `references/workflow-control.md` before generating, continuing, or assembling prose.
3. Confirm the inputs include `章节创作总控规划`, chapter narrative expression contract, chapter detail outline, scene performance contract when available, one lightweight `type: chapter_execution_pack`, and the relevant `type: character_intent_result`.
4. Confirm whether the current operation is `START_CHAPTER`, `WRITE_FRAGMENT`, `RESUME_FRAGMENT`, `ASSEMBLE_V1`, or `REVISE_FRAGMENT`.
5. Use the creative control plan as the authority for division of labor, conflict priority, ASK_USER triggers, and token boundaries.
6. Use the chapter narrative expression contract as the authority for author intent, reader information boundary, POV filtering, and hard prohibitions.
7. Use the chapter detail outline as the authority for scene order, scene function, plot movement, and ending state.
8. Use the scene performance contract as the authority for chapter-specific wording, rhythm, dialogue naturalness, narration boundaries, and anti-AI differences. Do not expect it to restate reusable prose-quality rules.
9. Use the chapter execution pack as the dispatch index for scene weights, generation order, transitions, risk routing, and character-intent coverage status.
10. Before prose, identify the pack's `人物意图覆盖状态`, `场景调度表`, `场景衔接表`, `高风险清单`, `场景演出契约引用`, and `正文生成顺序`, then cross-check them against the original creative control plan, chapter contract, outline, scene performance contract, and character intent result. Do not rely on the execution pack as the sole source.
11. Require a `CONTINUE` or `RESUME` action in the `character_intent_result` before writing any key fragment. If a P0 language or behavior intent decision is missing, return control to `control-character-intent` to update the character intent result instead of drafting.
12. Enforce the source boundary: draft only from the creative control plan, narrative expression contract, detail outline, scene performance contract, execution pack, approved character intent result, chapter runtime state, allowed upstream system inputs, and approved common rule files. Do not read or use external prose drafts, comparison reports, finished sample text, or any non-system source while drafting.
13. For revision or second-pass drafting, internally classify material as `保留`, `压缩`, `删除`, or `延后` before writing. Do not delete scene pressure, key objects, money/procedure pressure, support-character turns, or the main ending hook while reducing jokes.
14. Apply `references/prose-style-rules.md` and `references/director-prose-quality-rules.md` while drafting.
15. Draft by scene grade:
   - A scenes: write full pressure, action, misread, character reaction, and turn;
   - B scenes: carry state and transition quickly;
   - C scenes: release information through conflict, object, procedure, or necessity, then exit.
16. Run an integrated scene-director pass using `references/director-prose-quality-rules.md`: remove over-explanation, complete-design narration, camera-only POV in key scenes, interchangeable associations, clean Q&A, isolated jokes, over-polished metaphors, prose that only expands the outline, over-winning character quips, blunt/low-grade misread wording, summary humor that was merely replaced by prettier narration, and any scene that grows beyond its grade without adding pressure.
17. If a fragment or scene fails, mark it for `局部替换建议` instead of rewriting the whole chapter. Do not expand every scene merely because one core scene is weak.
18. In `生成备注`, explicitly record whether only system sources were used, whether intent-control input was present, whether any non-system material pollution risk exists, and whether there are risks in complete-design narration, POV participation, character-swap associations, character line win-rate, misread scale, main-hook focus, compressed pressure scenes, support-character emotional arc, word-budget drift, or scene-level reader experience.
19. In `生成备注`, explicitly record whether the final draft coordinated all six artifacts: creative control plan, chapter contract, detail outline, scene performance contract, execution pack, and character intent result.
20. Output with `System_alpha/00_总控台/02_模板库/TPL-CHAPTER-PROSE-DRAFT_正文草稿交付版模板.md` as the exact product shape. Use `references/draft-template.md` only as the local mirror if the formal template is not directly opened in the current context.
21. Run `references/quality-check.md` before returning the draft.

## Boundaries

Do:

- Draft approved key fragments and assemble them into a whole chapter V1.
- Preserve whole-chapter reading flow even when generation spans multiple turns.
- Preserve scene transitions and whole-chapter reading flow.
- Write in-scene action, dialogue, perception, pressure, and consequence instead of outline summary.
- Make scenes slide through concrete life pressure, misread semantics, emotional purpose, and light reversal material.
- Create concrete expressions, dialogue, actions, objects, joke landings, and ending sentences during drafting from allowed inputs.
- Keep character knowledge within the narrative contract, detail outline, execution pack, intent result, and upstream constraints.
- Keep reader, viewpoint, and important support-character cognition separated according to the narrative contract and approved character intent result.
- Keep one primary joke or misread per scene, while preserving at least one concrete pressure point in action, object, procedure, money, or relationship.
- Control strong characters' line win-rate: sharp lines must push action, pressure a relationship, deepen a misread, or guard information. Otherwise use action, silence, interruption, or failure.
- Preserve the chapter's single main ending hook; lighter comic afterbeats must not steal focus from it.
- Keep within the execution pack's scene-grade word budget; spend words on A scenes, compress B/C scenes.
- Execute reusable style consistency, de-AI feel, and dialogue humor from the director prose-quality rules, then apply the scene performance contract only for chapter-specific differences.
- Directly consult the original upstream artifacts when the execution pack only provides a short dispatch label.
- Suggest local replacement only for failed scenes.
- Mark unresolved input problems in `生成备注` rather than silently fixing canon.
- Refuse to continue a key fragment when the character intent result has returned `ASK_USER`.

Do not:

- Create or revise the chapter detail outline.
- Create or revise the chapter execution pack.
- Create or revise the chapter creative control plan.
- Create or revise the scene performance contract.
- Use this skill for one difficult scene only; use `generate-scene-execution-brief` for local refinement.
- Make P0 character language or behavior intent decisions; route them to `control-character-intent`.
- Continue prose after an unresolved `ASK_USER`.
- Reveal hidden information earlier than allowed.
- Read, quote, summarize, imitate, or reconstruct external prose drafts, finished sample text, comparison reports, or non-system writing material during generation.
- Reuse finished jokes, finished dialogue, punchlines, paragraph order, ending lines, or signature expressions from non-system material.
- Treat execution-pack structure phrases as finished prose sentences.
- Treat execution-pack summaries as a replacement for the chapter contract, detail outline, scene performance contract, or character intent result.
- Replace a summary joke with a prettier summary instead of staging it through action, object, procedure, or relationship pressure.
- Collapse high-pressure scenes into "after a while" transitions when the pack requires visible conflict.
- Let a support character become only a helper, explainer, or vibe source without an emotional turn.
- Write process labels, outline tables, or explanatory scaffolding inside the prose body.
- Update character, event, or setting cards.
- Depend on deleted post-processing skills (`revise-draft-de-ai`, `revise-draft-style-calibration`, `revise-draft-dialogue-humor`) to make the prose readable later.
- Rewrite the whole chapter when only one scene fails; diagnose and replace locally.

## Output Rule

Return one Markdown draft with YAML frontmatter:

```yaml
type: draft
system: narrative
status: draft
```

Put the actual novel text under `## 正文`. Put warnings, assumptions, or follow-up repair notes under `## 生成备注`, never inside the prose.
