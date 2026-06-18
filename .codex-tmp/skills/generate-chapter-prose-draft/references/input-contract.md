# Input Contract

Use this file when generating, revising, or checking a whole-chapter prose draft.

## Read Order

1. Chapter execution pack
   - Prefer `type: chapter_execution_pack`.
   - Use it as the authority for word target, scene weights, transitions, cognition, information control, prose constraints, high-risk flags, and ending state.
2. Chapter detail outline
   - Use only to clarify scene function or upstream constraints already referenced by the execution pack.
3. Optional single-scene execution brief
   - Use only for one high-risk scene explicitly included by the user.
   - Do not require one for every scene.
4. Approved common rule files
   - Use only reusable rule files that belong to the skill, setting, event, or narrative system.
5. Author request for the current turn
   - Use for length, tone, rough/polished mode, or specific repair focus.
   - Do not let it silently override world facts or information boundaries.

## Allowed Source Boundary

Generate the draft only from:

- chapter execution packs;
- chapter detail outlines when needed for clarification;
- confirmed unit context packages;
- chapter outline cards;
- character cards;
- event cards;
- setting cards;
- approved common rule files inside the system;
- explicit author requirements for the current task.

Do not use external prose drafts, comparison reports, finished sample text, or non-system writing material as generation input.

## Required Inputs

- One chapter execution pack or equivalent whole-chapter execution plan.
- Chapter ID, title or working title.
- Word target. Default to around 3500 Chinese characters if absent.

## Optional Inputs

- Chapter detail outline.
- Unit context package.
- Prior or next chapter summary.
- One high-risk scene execution brief.
- Short excerpts from character, event, or setting cards.
- Approved reusable rule files that are part of the system.

## Missing Input Handling

If only a chapter detail outline is provided, recommend generating a chapter execution pack first. If the user explicitly asks for a rough draft anyway, draft conservatively and add the missing pack risk to `生成备注`.

If only raw cards are provided, do not generate a full chapter. Request or recommend chapter detail outline and chapter execution pack first.

## Conflict Handling

If inputs conflict, preserve the chapter execution pack unless the user explicitly asks to revise it. Record unresolved conflicts in `生成备注`.

Common conflicts:

- Execution pack and outline disagree about scene ending.
- A scene requires knowledge the viewpoint character does not have.
- Author asks for a reveal marked hidden.
- Requested length cannot fit all scene weights.
- A high-risk scene requires a setting detail not confirmed upstream.
- Input package includes external prose drafts, comparison reports, finished sample text, or other non-system writing material as if it were generation context.

## Source Pollution Handling

If non-system writing material is provided before drafting, exclude it from generation and record this in `生成备注`. If the execution pack itself contains suspected non-system finished material, avoid reproducing it as prose and mark the risk in `生成备注`.
