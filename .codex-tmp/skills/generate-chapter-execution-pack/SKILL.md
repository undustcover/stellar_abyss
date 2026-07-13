---
name: generate-chapter-execution-pack
description: "Generate, revise, or check lightweight whole-chapter execution packs for the user's web-novel writing system. Use when Codex needs to create a temporary chapter_execution_pack that schedules and indexes confirmed chapter artifacts for prose drafting under a chapter creative control plan, including source indexes, scene weights, generation order, transition handles, risk routing, and character-intent coverage status. Do not use for creating chapter detail outlines, writing prose, building full character intent tracks, recreating narrative-expression contracts, creating scene performance contracts, or deeply refining one specified difficult scene."
---

# Generate Chapter Execution Pack

## Purpose

Create a temporary whole-chapter execution pack that schedules and indexes confirmed chapter artifacts so the prose-generation skill can draft the chapter while preserving whole-chapter flow. Record character-intent coverage status and route uncovered gaps back to intent control when needed.

Keep this skill after the chapter creative control plan, chapter narrative expression contract, chapter detail outline, and scene performance contract exist. It does not create new plot structure, narrative expression rules, prose performance rules, or character intent tracks. It produces a lightweight dispatch document: source indexes, scene weights, generation order, transition handles, risk routing, and character-intent coverage status.

In the `总-分-总` chain, this skill is the dispatch `分` skill. It does not consolidate upstream artifacts into a master summary. Its value is routing: tell the prose-draft skill where to look, how to weight scenes, and which risks require which layer. It may point back to `control-character-intent` only as a gap/backflow route, not as a linear downstream step.

## Interface Alignment

Align outputs with the `章节执行包接口` in:

```text
设计流程与方案/共创机制/模板接口规范_总分总正文生成链路.md
```

Required interface behavior:

- Must read: chapter creative control plan, chapter narrative expression contract, chapter detail outline, scene performance contract, existing character intent result if available, and necessary character/event/setting facts.
- May cite: artifact paths/IDs, short labels, short dispatch summaries, scene IDs, risk points, scene weights, generation order, and routing rules.
- Must not repeat: full chapter contract, full outline, full scene performance contract, character-card text, event-card text, finished prose, full dialogue, or punchlines.
- Outputs to: prose draft generation, optional single-scene execution brief, and necessary backflow to character intent control.
- ASK_USER when: scene weight affects author aesthetic, main hook versus light afterbeat is unclear, character-intent coverage is unclear and affects consistency, or a single-scene brief decision would affect prose quality.

## Template Fidelity Rule

The output product must follow the formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHAPTER-EXECUTION-PACK_章节执行包模板.md
```

`references/execution-pack-template.md` is only a pointer and local compatibility note; it is not a separate competing template.

Preserve YAML fields, heading order, required tables, and section names. If an item cannot be filled from confirmed inputs, keep the field and write the issue under `待确认问题`. Do not remove the `读取产物索引`, `场景调度表`, `高风险清单`, `人物意图覆盖状态`, `正文生成顺序`, or `生成前检查清单` sections. Do not replace the template with a prose summary or a large upstream-content recap.

## Workflow

1. Read `references/input-contract.md` before generating the pack.
2. Confirm the inputs include `章节创作总控规划`, one chapter narrative expression contract, one chapter detail outline or equivalent whole-chapter scene plan, and one confirmed scene performance contract. For the current full-chain test stage, do not allow a rough/smoke pack exemption.
3. Preserve the creative control plan's division of labor, conflict priority, reference rules, and token boundaries.
4. Preserve the outline's scene order, scene functions, information boundaries, emotional movement, and ending state.
5. Enforce the source boundary: this skill may use only the chapter creative control plan, chapter narrative expression contract, chapter detail outline, scene performance contract, confirmed narrative-system inputs, setting-system cards, event-database cards, and approved common rule files. It must not use external prose drafts, comparison reports, finished sample text, or any non-system source as generation material.
6. Convert inputs into a lightweight chapter-level dispatch pack:
   - source artifact index
   - chapter target and drafting stance
   - scene weights and approximate word budget
   - protected pressure points and non-skippable turns by reference
   - scene entrance and exit states
   - transition handling
   - information and cognition risk routing
   - single main ending hook and secondary afterbeat control
   - key scene performance-contract references
   - local replacement routing for failed scenes
   - character intent coverage status
   - key behavior risks and coverage gaps
   - key dialogue risks and coverage gaps
   - decisions the model must not make for characters
   - items that must backflow to `control-character-intent` when coverage is missing
   - high-risk scene flags for optional `generate-scene-execution-brief`
7. Use `System_alpha/00_总控台/02_模板库/TPL-CHAPTER-EXECUTION-PACK_章节执行包模板.md` as the exact product shape. Read `references/execution-pack-template.md` only to confirm the formal-template pointer and renamed fields.
8. Apply only the dispatch-relevant prose rules in `references/prose-control.md`; do not copy prose-performance rules from the scene performance contract into the pack.
9. Mark each scene as A/B/C:
   - A core scene: must be written with full pressure, misread, character reaction, and visible turn;
   - B transition scene: short, state-carrying, no decorative expansion;
   - C information scene: compressed, conflict/action led, no explanation block.
10. Do not generate full character intent tracks. Record only coverage status, risk flags, and backflow needs; `control-character-intent` owns character intent decisions.
11. Before returning, check that every upstream reference is either a path/ID, a short label, or a short dispatch summary. If any section starts restating an upstream table or long paragraph, compress it into routing language.
12. Run `references/quality-check.md` before returning the pack.

## Boundaries

Do:

- Prepare the whole chapter for controlled key-fragment prose drafting and final whole-chapter assembly.
- Manage scene-to-scene continuity, pacing, information release, emotional progression, and source routing.
- Protect core pressure scenes from being flattened during later joke reduction or pacing compression.
- Identify one main chapter hook and mark any lighter comic or emotional close as secondary.
- Reference confirmed scene performance rules without restating them in full.
- Route scene performance rules by label or short summary; preserve the original contract as the authority.
- Protect word budget by assigning scene grades and word ranges before drafting.
- Mark scenes that may need a later single-scene execution brief, but do not expand every scene into a brief.
- Mark key dialogue and behavior risks, plus whether the existing character intent result covers them.
- Add an explicit `人物意图覆盖状态` section.
- Keep the pack temporary and task-facing.
- Put missing or conflicting input into `待确认问题`.

Do not:

- Generate finished prose paragraphs.
- Write full dialogue exchanges.
- Build full character intent tracks for key fragments.
- Decide P0 character language or behavior intent divergences on behalf of the author.
- Read, quote, summarize, or imitate external prose drafts, finished sample text, comparison reports, or non-system writing material.
- Put finished jokes, punchlines, dialogue, exact paragraph order, or signature expressions from non-system material into the execution pack.
- Create or revise the chapter detail outline's scene structure unless the user explicitly asks for revision.
- Create or revise the chapter creative control plan.
- Create or revise the scene performance contract.
- Copy full upstream artifacts into the execution pack.
- Rebuild the chapter creative control plan as a longer dispatch plan.
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

Use stable section headings from `System_alpha/00_总控台/02_模板库/TPL-CHAPTER-EXECUTION-PACK_章节执行包模板.md`.
