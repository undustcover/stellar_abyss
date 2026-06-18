# Input Contract

Use this file when generating, revising, or checking a single high-risk scene execution brief.

## Read Order

1. Target chapter detail outline
   - Use the `type: detail_outline` card as the main source.
   - Extract only the selected scene, chapter-level constraints, information control, dialogue focus, emotional movement, and ending treatment.
2. Target scene identifier
   - Accept a scene number, scene heading, or scene function.
   - If no exact scene is identified, stop and ask for the target scene.
3. Unit context or chapter outline constraints
   - Use these only when the detail outline points to a broader constraint.
   - Prefer confirmed or author-approved material.
4. Author request for this scene
   - Treat it as task intent, but do not let it silently override confirmed world facts or the chapter detail outline.

## Required Inputs

- A chapter detail outline or equivalent scene-level outline.
- Exactly one target scene.
- Any known chapter-level prohibitions or information hiding rules.

## Optional Inputs

- Unit context package.
- Chapter outline card.
- Short excerpts from character, event, or setting cards.
- Author's preferred tone, pacing, dialogue density, or prose target for the scene.

## Conflict Handling

If inputs conflict, keep the chapter detail outline's scene function unless the author explicitly says to revise it. Do not invent canon or repair upstream cards inside this skill.

Record conflicts in `待确认问题` when:

- The target scene cannot be identified.
- The scene requires a character to know unavailable information.
- The author request asks for prose that violates an information hiding rule.
- The scene ending differs from the chapter detail outline.
- A required action depends on an unconfirmed setting mechanism.

## One-Scene Rule

Generate exactly one scene execution brief per invocation. If asked for an entire chapter, whole-chapter prose preparation, or multi-scene continuity, route the task to a chapter execution pack workflow instead of generating scene briefs. If no chapter execution pack skill exists yet, state that this task needs a chapter-level execution pack rather than this single-scene brief.

## Trigger Boundary

Use this skill for:

- one specified high-risk scene
- local repair of a difficult scene
- climax, reversal, information reveal, complex dialogue, or emotional beat

Do not use this skill for:

- default chapter generation
- preparing all scenes in a chapter
- scene-to-scene continuity across a whole chapter
- one-pass 3500-character chapter drafting
