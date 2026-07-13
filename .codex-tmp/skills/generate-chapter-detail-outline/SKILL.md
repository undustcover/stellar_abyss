---
name: generate-chapter-detail-outline
description: "Generate, revise, or check chapter detail outline cards for the user's web-novel writing system. Use when Codex needs to turn a confirmed unit context package, chapter outline, and character/event/setting constraints into a detail_outline draft for one chapter, usually around 3500 Chinese characters and a flexible set of effective scenes, with scene order, action progression, information release, dialogue focus, pacing, emotional movement, ending state, character entry cognition, character motive risks, and downstream intent-control checkpoints; do not use for single-scene deep execution briefs, prose writing, or full character intent tracks."
---

# Generate Chapter Detail Outline

## Purpose

Create a chapter detail outline card that turns a confirmed chapter-level narrative plan into a reader-experience and character-intent risk structure for later execution-pack, intent-control, and prose generation.

Keep this skill between chapter outline and execution pack. It may decide scene order, action progression, information release, dialogue focus, pacing, emotional movement, ending state, and scene-level character entry conditions for a whole chapter. Its main job is to lock how a web-novel reader will be led through expectation, misread, pressure, reveal, laugh, discomfort, and hook while pre-marking character motive risks. It must not write prose paragraphs, complete dialogue, build full character intent tracks, or become a full scene execution sheet.

In the `总-分-总` chain, this skill is a `分` skill. It must obey the chapter creative control plan and produce only the plot-skeleton layer plus lightweight reader-experience traceability. It must not become a second creative control plan or a prose-performance contract.

## Interface Alignment

Align outputs with the `章节细纲接口` in:

```text
设计流程与方案/共创机制/模板接口规范_总分总正文生成链路.md
```

Required interface behavior:

- Must read: chapter creative control plan, chapter narrative expression contract, and necessary world/event/setting facts.
- May cite: high-level reader feeling and information boundaries from the chapter contract; division of labor and reference rules from the creative control plan; only necessary character/event/setting facts.
- Must not repeat: full chapter contract, prose-performance rules, character intent tracks, execution-pack dispatch, prose sentences, or finished dialogue.
- Outputs to: scene performance contract, chapter execution pack, character intent control, and prose draft generation.
- ASK_USER when: scene function changes author intent, scene order changes reader misdirection, reader-experience fields cannot be traced to confirmed sources, or character behavior motive is not credible.

## Template Fidelity Rule

The output product must follow the formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-NAR-DETAIL-OUTLINE_章节细纲模板.md
```

`references/outline-template.md` is only a pointer and local compatibility note; it is not a separate competing template.

Preserve the template's YAML fields, heading order, required tables, and section names. If a field cannot be filled from confirmed inputs, keep the field and put a concise pending item in `待确认问题`. Do not delete sections, rename headings, merge tables, or add free-form replacement structures unless the author explicitly asks to change the template itself.

## Workflow

1. Read the input contract in `references/input-contract.md` before generating an outline.
2. Read V1.3 narrative expression contracts before older unit context or chapter outline material when they exist:
   - chapter creative control plan;
   - chapter-level narrative expression contract;
   - related unit-level narrative expression contract, including explicitly temporary reference contracts;
   - volume-level contract only if it exists and is not merely a placeholder.
3. Treat the chapter creative control plan as the authority for downstream division of labor, conflict priority, ASK_USER triggers, and token boundaries. Treat author-confirmed chapter narrative expression contracts as the authority for expression, reader knowledge, POV filtering, misreading direction, bright-line/hidden-line development, expression mix, hard prohibitions, and backflow items. Do not let older outline wording override them.
4. Prefer `status: confirmed` unit context packages. If only draft or review material exists, mark the uncertainty in `待确认问题`.
5. Separate three layers:
   - World facts: character cards, event cards, setting cards, and confirmed timelines.
   - Narrative arrangement: chapter function, scene order, information release, reader cognition, and pacing.
   - Prose execution: paragraph language, full dialogue, sensory writing, and line-level style.
6. Generate only the narrative arrangement layer for a chapter detail outline. Scene count is not a quota: default to 3-5 effective scenes for a typical 3500-character web-novel chapter, allow 1-2 scenes for concentrated emotional/dialogue/pressure chapters, and expand to 5-7 scenes only for longer chapters, fast cuts, multi-thread movement, action escalation, or chapters with several necessary turns.
7. Enforce the source boundary: this skill may use only confirmed narrative-system inputs, setting-system cards, event-database cards, and approved common rule files. It must not use external prose drafts, comparison reports, finished sample text, or any non-system source as generation material.
8. Add the reader-experience and intent-preparation fields required by the new drafting chain:
   - `本章认知差控制`
   - `场景轻重与承压点`
   - `生活压力链`
   - `误会语义链`
   - `人物情绪入口/出口索引`
   - `可回收材料链`
   - `本章人物意图风险预埋`
   - scene-level `人物进入状态`
   - scene-level `人物行为风险`
   - scene-level `人物语言风险`
   - scene-level `意图控制器关注点`
9. Add `读者体验曲线` with explicit source markers:
   - what the reader expects at chapter start;
   - what each scene makes the reader suspect, laugh at, worry about, or misunderstand;
   - what information is withheld, shifted, or reinterpreted;
   - whether each reader-experience item comes from the chapter narrative expression contract, creative control plan, author confirmation, or system suggestion pending confirmation.
10. Before finalizing scene order, assign each scene a weight role:
   - core pressure scene: carries conflict, face, money, procedure, object, relationship, or irreversible information movement;
   - transition/setup scene: only moves location, mood, or setup and must stay short;
   - hook scene: preserves the next-chapter pressure without solving it.
11. Track reader, viewpoint, and key supporting-character cognition separately. A chapter may let the reader lead the viewpoint character by half a step only when upstream contracts allow it; otherwise obey the chapter contract's exact reader/POV boundary.
12. Do not write concrete style, anti-AI, full dialogue, or scene-director wording inside the outline. Route prose-expression needs to the scene performance contract and dispatch needs to the execution pack. If an item feels like wording, rhythm, dialogue naturalness, narration boundary, or anti-AI control, move it out of the outline.
13. Do not generate full key-fragment intent tracks. The outline only pre-marks character cognition, external goals, relationship pressure, and downstream risks.
14. Use the card shape in `System_alpha/00_总控台/02_模板库/TPL-NAR-DETAIL-OUTLINE_章节细纲模板.md`; preserve its headings and tables as the product structure. Read `references/outline-template.md` only to confirm the formal-template pointer and renamed fields.
15. Run the checks in `references/quality-check.md` before returning the result.

## Boundaries

Do:

- Preserve traceability to upstream unit context, chapter outline, event facts, character states, and setting limits.
- Preserve traceability to the chapter creative control plan for division of labor, conflict priority, ASK_USER rules, and token boundaries.
- Preserve traceability to narrative expression contracts for reader knowledge, POV filtering, misreading direction, bright-line/hidden-line movement, and hard prohibitions.
- Record what each effective scene must accomplish, not how the final prose should sound line by line.
- Track what the protagonist knows, what the reader knows, and what must remain hidden.
- Mark scene weight, pressure-bearing objects/actions, and the single main ending hook early enough for execution-pack and prose skills to protect them.
- Prepare enough pressure, cognition, scene-weight, and intent-risk structure for later scene performance, execution-pack, intent-control, and prose skills.
- Auto-identify structure, misread conditions, emotion movement, life pressure, comedy opportunities, and reversal-material opportunities from allowed inputs.
- Pre-mark character entry cognition, external goals, relationship pressure, language risks, behavior risks, and downstream intent-control focus.
- Put missing or conflicting input into `待确认问题`.

Do not:

- Generate novel prose, complete dialogue exchanges, or polished descriptive paragraphs.
- Generate full character intent tracks for key prose fragments.
- Decide P0 character language or behavior intent divergences on behalf of the author.
- Read, quote, summarize, or imitate external prose drafts, finished sample text, comparison reports, or non-system writing material.
- Import finished jokes, finished dialogue, finished punchlines, recognizable bridge order, or signature expressions from outside the setting, event, and narrative-system inputs.
- Rewrite world facts from character, event, or setting cards.
- Define character state by chapter, unit, or plot function; use in-world time or upstream world-state facts.
- Reveal hidden information earlier than the chapter outline or unit context allows.
- Override an author-confirmed chapter narrative expression contract with older source-outline wording.
- Replace the later chapter execution pack, single-scene execution brief, or prose generation skill.
- Decide prose-performance rules such as sentence rhythm, narration texture, dialogue fracture, or anti-AI wording.

## Output Rule

Return a complete Markdown card draft with YAML frontmatter:

```yaml
type: detail_outline
system: narrative
status: draft
```

Use stable section headings from `System_alpha/00_总控台/02_模板库/TPL-NAR-DETAIL-OUTLINE_章节细纲模板.md`. If a section cannot be completed from the inputs, keep the section and fill it with a concise pending question rather than inventing facts.
