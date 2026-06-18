---
name: generate-scene-execution-brief
description: "Generate, revise, or check a single high-risk scene execution brief for the user's novel-writing system. Use only when Codex needs to refine one explicitly specified difficult scene, such as a climax, reversal, complex dialogue, information reveal, emotional beat, or local prose repair, into a temporary scene_execution_brief with viewpoint lock, cognition limits, action chain, conflict pressure, information release and concealment, dialogue strategy, narration controls, pacing, prohibitions, and ending beat; do not use for whole-chapter prose preparation, multi-scene chapter flow, or default chapter generation."
---

# Generate Scene Execution Brief

## Purpose

Create one temporary scene execution brief from one explicitly specified high-risk scene in a chapter detail outline.

Keep this skill as a local refinement tool between chapter-level preparation and prose generation. It translates one difficult scene's function into executable constraints for later prose writing. It must not become the default whole-chapter preparation path, write final prose, write complete dialogue, or restructure the chapter.

## Workflow

1. Read `references/input-contract.md` before generating the brief.
2. Confirm the user has specified exactly one target scene by number, title, or scene function.
3. If the user asks for whole-chapter prose preparation, multi-scene flow, or one-pass chapter drafting, do not expand all scenes here; use or recommend a chapter execution pack workflow instead.
4. If the user provides a full chapter detail outline without a target scene, ask for the target scene instead of generating all scene briefs.
5. Convert the target scene into prose constraints:
   - must write
   - may imply
   - must hide
   - must not write as
   - reader/viewpoint/support-character cognition split
   - protected pressure point
   - dominant joke or misread slot
   - support-character emotional turn when relevant
6. Apply the strong prose controls in `references/prose-control.md`.
7. Use the card shape in `references/execution-brief-template.md`.
8. Run `references/quality-check.md` before returning the brief.

## Boundaries

Do:

- Preserve the chapter detail outline's scene function, action movement, information boundary, emotional movement, and ending state.
- Lock viewpoint, cognition, available evidence, dialogue purpose, narration mode, and pacing for the scene.
- Preserve the scene's protected action, object, procedure, face, relationship, or information-boundary pressure.
- Control dialogue win-rate when a sharp or dominant character could flatten the scene.
- Keep the brief usable by a later prose generation skill without requiring it to invent core action or information movement.
- Treat this as a magnifying glass for complex scenes, not as the default way to process every scene in a chapter.
- Put missing or conflicting input into `待确认问题`.

Do not:

- Generate finished prose paragraphs.
- Write full dialogue exchanges.
- Change the scene order, chapter function, event facts, character state, or setting rules.
- Prepare whole-chapter scene transitions or one-pass chapter drafting constraints.
- Let a character know information that upstream material has not made available.
- Save the brief as a permanent world fact card.

## Output Rule

Return one Markdown working brief with YAML frontmatter:

```yaml
type: scene_execution_brief
system: narrative
status: draft
```

Use stable section headings from `references/execution-brief-template.md`. If the inputs do not identify exactly one scene, return a short `待确认问题` instead of producing multiple briefs.
