---
name: generate-chapter-prose-draft
description: "Generate, revise, or check whole-chapter web-novel prose drafts for the user's novel-writing system. Use when Codex needs to write one complete chapter draft from a chapter_execution_pack, optionally with a chapter detail outline or one high-risk scene brief, while preserving scene order, viewpoint, cognition limits, information hiding, dialogue strategy, pacing, ending state, and author prohibitions; do not use for creating outlines, execution packs, single-scene briefs, or rewriting upstream world facts."
---

# Generate Chapter Prose Draft

## Purpose

Write one complete web-novel chapter draft from a chapter execution pack that already contains scene-level reader-experience direction.

Keep this skill after `generate-chapter-execution-pack`. It writes prose, but it must not redesign the chapter, add new canon, explain hidden mechanics, or revise upstream cards. If the user provides only a chapter detail outline, recommend generating a chapter execution pack first unless they explicitly ask for a rough draft.

The draft must not depend on separate post-processing skills for de-AI cleanup, style consistency, or dialogue humor. Those controls should already be present in the execution pack and must be executed during first-pass prose generation.

## Workflow

1. Read `references/input-contract.md` before drafting.
2. Confirm the main input is one `type: chapter_execution_pack`, or an equivalent whole-chapter execution plan.
3. Use the pack as the authority for scene order, word target, scene weights, transitions, information control, cognition limits, and ending state.
4. Before drafting, identify the pack's `认知差执行表`, `生活压力链执行`, `误会语义链执行`, `喜剧/正剧执行策略`, `主钩子与轻收束控制`, `场景承压点保护`, `支持角色情绪弧线`, `关键对话断裂点`, `反杀材料进入方式`, `分场景导演表`, and `场景权重与字数预算`.
5. Enforce the source boundary: draft only from the execution pack, allowed upstream system inputs, and approved common rule files. Do not read or use external prose drafts, comparison reports, finished sample text, or any non-system source while drafting.
6. For revision or second-pass drafting, internally classify material as `保留`, `压缩`, `删除`, or `延后` before writing. Do not delete scene pressure, key objects, money/procedure pressure, support-character turns, or the main ending hook while reducing jokes.
7. Apply `references/prose-style-rules.md` while drafting.
8. Draft by scene grade:
   - A scenes: write full pressure, action, misread, character reaction, and turn;
   - B scenes: carry state and transition quickly;
   - C scenes: release information through conflict, object, procedure, or necessity, then exit.
9. Run an integrated scene-director pass: remove over-explanation, clean Q&A, isolated jokes, over-polished metaphors, prose that only expands the outline, over-winning character quips, blunt/low-grade misread wording, summary humor that was merely replaced by prettier narration, and any scene that grows beyond its grade without adding pressure.
10. If a scene fails, mark it for `局部替换建议` instead of rewriting the whole chapter. Do not expand every scene merely because one core scene is weak.
11. In `生成备注`, explicitly record whether only system sources were used, whether any non-system material pollution risk exists, and whether there are risks in character line win-rate, misread scale, main-hook focus, compressed pressure scenes, support-character emotional arc, word-budget drift, or scene-level reader experience.
12. Output with `references/draft-template.md`.
13. Run `references/quality-check.md` before returning the draft.

## Boundaries

Do:

- Draft the whole chapter in one pass unless the user explicitly asks for a section.
- Preserve scene transitions and whole-chapter reading flow.
- Write in-scene action, dialogue, perception, pressure, and consequence instead of outline summary.
- Make scenes slide through concrete life pressure, misread semantics, emotional purpose, and light reversal material.
- Create concrete expressions, dialogue, actions, objects, joke landings, and ending sentences during drafting from allowed inputs.
- Keep character knowledge within the execution pack and upstream constraints.
- Keep reader, viewpoint, and important support-character cognition separated according to the pack.
- Keep one primary joke or misread per scene, while preserving at least one concrete pressure point in action, object, procedure, money, or relationship.
- Control strong characters' line win-rate: sharp lines must push action, pressure a relationship, deepen a misread, or guard information. Otherwise use action, silence, interruption, or failure.
- Preserve the chapter's single main ending hook; lighter comic afterbeats must not steal focus from it.
- Keep within the execution pack's scene-grade word budget; spend words on A scenes, compress B/C scenes.
- Execute style consistency, de-AI feel, and dialogue humor as part of scene staging, not as separate cleanup layers.
- Suggest local replacement only for failed scenes.
- Mark unresolved input problems in `生成备注` rather than silently fixing canon.

Do not:

- Create or revise the chapter detail outline.
- Create or revise the chapter execution pack.
- Use this skill for one difficult scene only; use `generate-scene-execution-brief` for local refinement.
- Reveal hidden information earlier than allowed.
- Read, quote, summarize, imitate, or reconstruct external prose drafts, finished sample text, comparison reports, or non-system writing material during generation.
- Reuse finished jokes, finished dialogue, punchlines, paragraph order, ending lines, or signature expressions from non-system material.
- Treat execution-pack structure phrases as finished prose sentences.
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
