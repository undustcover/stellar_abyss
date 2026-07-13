# Input Contract

Use this file when generating, revising, or checking a whole-chapter execution pack.

## Read Order

1. Chapter creative control plan
   - Prefer `type: chapter_creative_control_plan`.
   - Use it as the authority for downstream division of labor, artifact references, conflict priority, ASK_USER triggers, and token boundaries.
2. Chapter narrative expression contract
   - Prefer `type: narrative_expression_contract`.
   - Use it as the authority for author intent, reader information boundary, POV filtering, hidden/revealed lines, misreading direction, and hard prohibitions.
   - Do not restate it in full inside the execution pack.
3. Chapter detail outline
   - Prefer `type: detail_outline`.
   - Use it as the authority for scene order, scene function, action movement, information release, emotional movement, dialogue focus, prohibitions, and ending state.
4. Scene performance contract
   - Prefer `type: scene_performance_contract`.
   - Use it only for prose-performance rule references, not plot changes.
5. Character intent result, if available
   - Prefer `type: character_intent_result`.
   - Formal template: `System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md`.
   - Use it only for coverage labels, risk labels, and short summaries.
   - If it is missing or does not cover a risk, mark the gap for backflow; do not fill character intent inside the execution pack.
6. Unit context package and chapter outline
   - Read only when the detail outline points to broader constraints or when chapter-level facts are missing.
   - Prefer confirmed or author-approved material.
7. Approved common rule files
   - Use only reusable rule files that belong to the skill, setting, event, or narrative system.
8. Author request for the current turn
   - Use for word target, tone, pacing, draft mode, or special emphasis.
   - Do not let it silently overwrite upstream world facts or information boundaries.

## Allowed Source Boundary

Generate the execution pack only from:

- chapter detail outlines;
- chapter creative control plans;
- chapter narrative expression contracts;
- scene performance contracts;
- character intent results, when available;
- confirmed unit context packages;
- chapter outline cards;
- character cards;
- event cards;
- setting cards;
- approved common rule files inside the system;
- explicit author requirements for the current task.

Do not use external prose drafts, comparison reports, finished sample text, or non-system writing material as generation input.

## Required Inputs

- One chapter creative control plan.
- One chapter narrative expression contract.
- One chapter detail outline or equivalent whole-chapter scene plan.
- One scene performance contract.
- Chapter target: unit, chapter, title or working title.
- Word target or range from the chapter creative control plan or explicit author instruction. If absent, record the gap in `待确认问题`; do not silently decide the total target.

## Optional Inputs

- Unit context package.
- Chapter outline card.
- Character intent result. If missing, record coverage as missing and route the gap back to `control-character-intent`.
- Prior or next chapter summary.
- Short excerpts from character, event, or setting cards.
- Author's preferred pacing, dialogue density, or revision focus.
- Approved reusable rule files that are part of the system.

## Conflict Handling

If inputs conflict, follow the chapter creative control plan's conflict priority and ASK_USER triggers. If no priority is available, ask the author instead of silently choosing. Record unresolved conflicts in `待确认问题`.

Common conflicts:

- Detail outline and unit context disagree about what a character knows.
- Narrative expression contract and detail outline disagree about what may be revealed.
- Scene performance contract requires a prose effect that would change plot, information boundary, or character motive.
- Scene ending states do not connect.
- The requested word target is too short or too long for the scene count.
- A scene requires a setting mechanism not confirmed upstream.
- The user asks for a reveal that the outline marks as hidden.
- Input package includes external prose drafts, comparison reports, finished sample text, or other non-system writing material as if it were generation context.

## Skill Boundary

Use this skill for whole-chapter prose preparation, scene-to-scene continuity, dispatch routing, and character-intent coverage tracking.

Do not use this skill to create the chapter creative control plan or scene performance contract.

Use `generate-scene-execution-brief` only after this pack marks a scene as high-risk or when the user explicitly requests one specified scene.

Use `control-character-intent` as a separate分工 skill. The execution pack may point back to it only when character-intent coverage is missing, conflicting, or needs author confirmation. Do not treat the execution pack as the trigger for default per-scene intent control.

## Source Pollution Handling

If the provided outline or context appears to contain finished jokes, finished dialogue, finished punchlines, comparison details, or other non-system writing material, remove the finished material from the pack. Preserve only allowed structure from the detail outline, or mark the source as contaminated in `待确认问题` when a clean rebuild is needed.
