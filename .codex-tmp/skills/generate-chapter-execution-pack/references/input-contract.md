# Input Contract

Use this file when generating, revising, or checking a whole-chapter execution pack.

## Read Order

1. Chapter detail outline
   - Prefer `type: detail_outline`.
   - Use it as the authority for scene order, scene function, action movement, information release, emotional movement, dialogue focus, prohibitions, and ending state.
2. Unit context package and chapter outline
   - Read only when the detail outline points to broader constraints or when chapter-level facts are missing.
   - Prefer confirmed or author-approved material.
3. Approved common rule files
   - Use only reusable rule files that belong to the skill, setting, event, or narrative system.
4. Author request for the current turn
   - Use for word target, tone, pacing, draft mode, or special emphasis.
   - Do not let it silently overwrite upstream world facts or information boundaries.

## Allowed Source Boundary

Generate the execution pack only from:

- chapter detail outlines;
- confirmed unit context packages;
- chapter outline cards;
- character cards;
- event cards;
- setting cards;
- approved common rule files inside the system;
- explicit author requirements for the current task.

Do not use external prose drafts, comparison reports, finished sample text, or non-system writing material as generation input.

## Required Inputs

- One chapter detail outline or equivalent whole-chapter scene plan.
- Chapter target: unit, chapter, title or working title.
- Any known word target. Default to around 3500 Chinese characters if absent.

## Optional Inputs

- Unit context package.
- Chapter outline card.
- Prior or next chapter summary.
- Short excerpts from character, event, or setting cards.
- Author's preferred pacing, dialogue density, or revision focus.
- Approved reusable rule files that are part of the system.

## Conflict Handling

If inputs conflict, preserve the chapter detail outline unless the user explicitly asks to revise it. Record unresolved conflicts in `待确认问题`.

Common conflicts:

- Detail outline and unit context disagree about what a character knows.
- Scene ending states do not connect.
- The requested word target is too short or too long for the scene count.
- A scene requires a setting mechanism not confirmed upstream.
- The user asks for a reveal that the outline marks as hidden.
- Input package includes external prose drafts, comparison reports, finished sample text, or other non-system writing material as if it were generation context.

## Skill Boundary

Use this skill for whole-chapter prose preparation and scene-to-scene continuity.

Use `generate-scene-execution-brief` only after this pack marks a scene as high-risk or when the user explicitly requests one specified scene.

## Source Pollution Handling

If the provided outline or context appears to contain finished jokes, finished dialogue, finished punchlines, comparison details, or other non-system writing material, remove the finished material from the pack. Preserve only allowed structure from the detail outline, or mark the source as contaminated in `待确认问题` when a clean rebuild is needed.
