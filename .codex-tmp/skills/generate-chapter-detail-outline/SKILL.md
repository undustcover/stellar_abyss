---
name: generate-chapter-detail-outline
description: "Generate, revise, or check chapter detail outline cards for the user's web-novel writing system. Use when Codex needs to turn a confirmed unit context package, chapter outline, and character/event/setting constraints into a detail_outline draft for one chapter, usually around 3500 Chinese characters and a flexible set of effective scenes, with scene order, action progression, information release, dialogue focus, pacing, emotional movement, ending state, and prohibitions; do not use for single-scene deep execution briefs or prose writing."
---

# Generate Chapter Detail Outline

## Purpose

Create a chapter detail outline card that turns a confirmed chapter-level narrative plan into a reader-experience structure for later execution-pack and prose generation.

Keep this skill between chapter outline and execution pack. It may decide scene order, action progression, information release, dialogue focus, pacing, emotional movement, and ending state for a whole chapter. Its main job is to lock how a web-novel reader will be led through expectation, misread, pressure, reveal, laugh, discomfort, and hook. It must not write prose paragraphs, complete dialogue, or become a full scene execution sheet.

## Workflow

1. Read the input contract in `references/input-contract.md` before generating an outline.
2. Prefer `status: confirmed` unit context packages. If only draft or review material exists, mark the uncertainty in `待确认问题`.
3. Separate three layers:
   - World facts: character cards, event cards, setting cards, and confirmed timelines.
   - Narrative arrangement: chapter function, scene order, information release, reader cognition, and pacing.
   - Prose execution: paragraph language, full dialogue, sensory writing, and line-level style.
4. Generate only the narrative arrangement layer for a chapter detail outline. Scene count is not a quota: default to 3-5 effective scenes for a typical 3500-character web-novel chapter, allow 1-2 scenes for concentrated emotional/dialogue/pressure chapters, and expand to 5-7 scenes only for longer chapters, fast cuts, multi-thread movement, action escalation, or chapters with several necessary turns.
5. Enforce the source boundary: this skill may use only confirmed narrative-system inputs, setting-system cards, event-database cards, and approved common rule files. It must not use external prose drafts, comparison reports, finished sample text, or any non-system source as generation material.
6. Add the reader-experience bridge fields required by the new drafting chain:
   - `章节文风模式`
   - `人物语言调用`
   - `场景文风分配`
   - `本章认知差控制`
   - `场景轻重与承压点`
   - `生活压力链`
   - `误会语义链`
   - `人物情绪链`
   - `反杀材料链`
7. Add `读者体验曲线` and `场景导演目标`:
   - what the reader expects at chapter start;
   - what each scene makes the reader suspect, laugh at, worry about, or misunderstand;
   - what information is withheld, shifted, or reinterpreted;
   - which scene is allowed to carry the primary comedy/misread;
   - which scene must stay short to protect word budget.
8. Before finalizing scene order, assign each scene a weight role:
   - core pressure scene: carries conflict, face, money, procedure, object, relationship, or irreversible information movement;
   - transition/setup scene: only moves location, mood, or setup and must stay short;
   - hook scene: preserves the next-chapter pressure without solving it.
9. Track reader, viewpoint, and key supporting-character cognition separately. A chapter may let the reader lead the viewpoint character by half a step, but must not let the viewpoint character know hidden facts early.
10. Do not outsource de-AI, style consistency, or dialogue humor to later revision skills. Mark the intended handling at scene level so execution pack and prose drafting can carry it before text exists.
11. Use the card shape in `references/outline-template.md`.
12. Run the checks in `references/quality-check.md` before returning the result.

## Boundaries

Do:

- Preserve traceability to upstream unit context, chapter outline, event facts, character states, and setting limits.
- Record what each effective scene must accomplish, not how the final prose should sound line by line.
- Track what the protagonist knows, what the reader knows, and what must remain hidden.
- Mark scene weight, pressure-bearing objects/actions, and the single main ending hook early enough for execution-pack and prose skills to protect them.
- Prepare enough style-facing structure for a later execution pack and prose draft to avoid AI-like outline expansion.
- Auto-identify structure, misread conditions, emotion movement, life pressure, comedy opportunities, and reversal-material opportunities from allowed inputs.
- Put missing or conflicting input into `待确认问题`.

Do not:

- Generate novel prose, complete dialogue exchanges, or polished descriptive paragraphs.
- Read, quote, summarize, or imitate external prose drafts, finished sample text, comparison reports, or non-system writing material.
- Import finished jokes, finished dialogue, finished punchlines, recognizable bridge order, or signature expressions from outside the setting, event, and narrative-system inputs.
- Rewrite world facts from character, event, or setting cards.
- Define character state by chapter, unit, or plot function; use in-world time or upstream world-state facts.
- Reveal hidden information earlier than the chapter outline or unit context allows.
- Replace the later chapter execution pack, single-scene execution brief, or prose generation skill.

## Output Rule

Return a complete Markdown card draft with YAML frontmatter:

```yaml
type: detail_outline
system: narrative
status: draft
```

Use stable section headings from `references/outline-template.md`. If a section cannot be completed from the inputs, keep the section and fill it with a concise pending question rather than inventing facts.
