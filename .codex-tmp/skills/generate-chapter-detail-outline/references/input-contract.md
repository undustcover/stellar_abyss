# Input Contract

Use this file when generating, revising, or checking a chapter detail outline.

## Read Order

1. Unit context package
   - Prefer `status: confirmed`.
   - Use it as the compressed source for unit-level character, event, setting, information-release, and prohibition constraints.
2. Chapter outline card
   - Use it as the authority for chapter function, chapter goal, related events, information release, foreshadowing, reader reward, ending hook, and prohibitions.
3. Necessary upstream summaries
   - Read only the needed character, event, and setting excerpts when the unit context or chapter outline explicitly requires them.
   - Use character cards for in-world state, cognition, behavior boundaries, and relationship constraints.
   - Use event cards for confirmed facts, causality, state changes, information layers, and logic limits.
   - Use setting cards for mechanisms, organizations, abilities, costs, and world rules.
4. Approved common rule files
   - Use only reusable rule files that belong to the skill, setting, event, or narrative system.
5. Author request for the current turn
   - Treat direct author instructions as task goals, but do not let them silently overwrite confirmed world facts.

## Allowed Source Boundary

Generate the outline only from:

- confirmed unit context packages;
- chapter outline cards;
- character cards;
- event cards;
- setting cards;
- approved common rule files inside the system;
- explicit author requirements for the current task.

Do not use external prose drafts, comparison reports, finished sample text, or non-system writing material as generation input.

## Required Inputs

- A chapter target: unit ID, chapter ID, title or working title.
- A unit context package or equivalent confirmed unit-level context.
- A chapter outline or at least a chapter function row from the unit outline.
- Any explicit author requirement for this chapter.

## Optional Inputs

- Existing draft detail outline to revise.
- Relevant prior or next chapter summaries.
- Short excerpts from character, event, or setting cards.
- Style or pacing preferences, only as constraints for the outline layer.
- Approved reusable rule files that are part of the system.

## Conflict Handling

If inputs conflict, do not resolve by inventing new canon. Record the issue in `待确认问题`.

Common conflicts:

- Unit context and chapter outline disagree about what the protagonist knows.
- Chapter outline needs an event outcome that the event card does not support.
- A scene requires a character to act outside their known behavior boundary.
- A setting mechanism is used without cost, limit, or confirmed rule.
- Author request asks for early revelation of information that upstream material marks as hidden.
- Input package includes external prose drafts, comparison reports, finished sample text, or other non-system writing material as if it were generation context.

## Compression Rule

Do not read or copy full upstream files by default. Extract only the facts that this chapter needs:

- current in-world state
- cognition boundary
- action boundary
- event fact used by the chapter
- information to release or hide
- setting limit
- chapter ending state

## Source Pollution Handling

If a provided input appears to include external prose drafts, finished jokes, finished dialogue, comparison details, or other non-system writing material, do not use that material. Record the issue in `输入依据` as excluded material and add a `待确认问题` row if the remaining allowed system inputs are insufficient.
