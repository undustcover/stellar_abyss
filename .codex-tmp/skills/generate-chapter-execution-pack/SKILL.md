---
name: generate-chapter-execution-pack
description: "Generate, revise, or check whole-chapter execution packs for the user's web-novel writing system. Use when Codex needs to turn a chapter detail outline into a temporary chapter_execution_pack for one-pass chapter prose drafting, with chapter word target, scene weights, scene transitions, emotional and information progression, viewpoint continuity, prose constraints, high-risk scene flags, and prohibitions; do not use for creating chapter detail outlines, writing prose, or deeply refining one specified difficult scene."
---

# Generate Chapter Execution Pack

## Purpose

Create a temporary whole-chapter execution pack from a chapter detail outline so a later prose generation skill can draft the chapter with scene-level reader-experience direction in one pass.

Keep this skill between `generate-chapter-detail-outline` and prose generation. It does not create new plot structure; it converts an existing chapter outline into an executable chapter-level drafting plan with scene continuity, pacing, word allocation, reader-experience direction, and prose constraints.

## Workflow

1. Read `references/input-contract.md` before generating the pack.
2. Confirm the input is one chapter detail outline or equivalent whole-chapter scene plan.
3. Preserve the outline's scene order, scene functions, information boundaries, emotional movement, and ending state.
4. Enforce the source boundary: this skill may use only the chapter detail outline, confirmed narrative-system inputs, setting-system cards, event-database cards, and approved common rule files. It must not use external prose drafts, comparison reports, finished sample text, or any non-system source as generation material.
5. Convert the outline into a chapter-level execution pack:
   - chapter target and drafting stance
   - scene weights and approximate word budget
   - protected pressure points and non-skippable turns
   - scene entrance and exit states
   - transition handling
   - information and cognition progression
   - reader/viewpoint/support-character cognition separation
   - chapter style execution
   - life-pressure chain execution
   - misread semantic chain execution
   - comedy/drama execution strategy
   - single main ending hook and secondary afterbeat control
   - support-character emotional arc protection
   - core joke progression
   - dialogue breakpoints
   - reversal-material entry method
   - scene-level anti-AI, style, and humor controls
   - local replacement rules for failed scenes
   - prose controls for the whole chapter
   - high-risk scene flags for optional `generate-scene-execution-brief`
6. Use `references/execution-pack-template.md`.
7. Apply the prose rules in `references/prose-control.md`.
8. Mark each scene as A/B/C:
   - A core scene: must be written with full pressure, misread, character reaction, and visible turn;
   - B transition scene: short, state-carrying, no decorative expansion;
   - C information scene: compressed, conflict/action led, no explanation block.
9. Run `references/quality-check.md` before returning the pack.

## Boundaries

Do:

- Prepare the whole chapter for one-pass prose drafting.
- Manage scene-to-scene continuity, pacing, information release, and emotional progression.
- Protect core pressure scenes from being flattened during later joke reduction or pacing compression.
- Identify one main chapter hook and mark any lighter comic or emotional close as secondary.
- Convert outline-level style chains into concrete drafting controls for natural prose.
- Integrate de-AI, style consistency, and dialogue humor into scene direction before prose is generated.
- Generate comedy mechanisms, dialogue breakpoints, pressure-chain execution, and reversal-material entry methods as structural controls rather than finished prose.
- Protect word budget by assigning scene grades and word ranges before drafting.
- Mark scenes that may need a later single-scene execution brief, but do not expand every scene into a brief.
- Keep the pack temporary and task-facing.
- Put missing or conflicting input into `待确认问题`.

Do not:

- Generate finished prose paragraphs.
- Write full dialogue exchanges.
- Read, quote, summarize, or imitate external prose drafts, finished sample text, comparison reports, or non-system writing material.
- Put finished jokes, punchlines, dialogue, exact paragraph order, or signature expressions from non-system material into the execution pack.
- Create or revise the chapter detail outline's scene structure unless the user explicitly asks for revision.
- Deeply refine one specified difficult scene; use `generate-scene-execution-brief` for that.
- Create a plan that expects later whole-chapter revision skills to fix reader experience after prose generation.
- Save the pack as a permanent world fact card.

## Output Rule

Return one Markdown working pack with YAML frontmatter:

```yaml
type: chapter_execution_pack
system: narrative
status: draft
temporary: true
```

Use stable section headings from `references/execution-pack-template.md`.
