# Input Contract

Use this file when generating, revising, or checking a chapter detail outline.

## Read Order

1. Chapter creative control plan
   - Prefer `type: chapter_creative_control_plan`.
   - Use it as the authority for downstream division of labor, artifact references, conflict priority, ASK_USER triggers, and token boundaries.
   - Do not use it to invent plot, prose style, or world facts.
2. Narrative expression contracts
   - Read the chapter-level narrative expression contract first when it exists.
   - Read the related unit-level narrative expression contract when it exists, including temporary reference contracts created for V1.3 calibration.
   - Volume-level narrative expression contracts may remain placeholders in the current iteration; if missing or placeholder-only, note this but do not block chapter outline generation.
   - Use narrative expression contracts as the authority for reader knowledge, POV filtering, misreading direction, bright-line/hidden-line development, expression mix, hard prohibitions, and unit-contract backflow items.
   - Do not use narrative expression contracts to rewrite world facts from character, event, or setting cards.
3. Unit context package
   - Prefer `status: confirmed`.
   - Use it as the compressed source for unit-level character, event, setting, information-release, and prohibition constraints.
4. Chapter outline card
   - Use it as the authority for chapter function, chapter goal, related events, information release, foreshadowing, reader reward, ending hook, and prohibitions.
   - If the chapter outline or source outline conflicts with an author-confirmed narrative expression contract, follow the contract for expression and information-display decisions, and record the old outline wording as superseded.
5. Necessary upstream summaries
   - Read only the needed character, event, and setting excerpts when the unit context or chapter outline explicitly requires them.
   - Use character cards for in-world state, cognition, behavior boundaries, and relationship constraints.
   - Use event cards for confirmed facts, causality, state changes, information layers, and logic limits.
   - Use setting cards for mechanisms, organizations, abilities, costs, and world rules.
6. Approved common rule files
   - Use only reusable rule files that belong to the skill, setting, event, or narrative system.
7. Author request for the current turn
   - Treat direct author instructions as task goals, but do not let them silently overwrite confirmed world facts.

## Allowed Source Boundary

Generate the outline only from:

- chapter creative control plans;
- author-confirmed chapter narrative expression contracts;
- related unit narrative expression contracts, including explicitly marked temporary reference contracts;
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
- A chapter creative control plan, when the total-split-total workflow has produced one.
- A chapter-level narrative expression contract, when the V1.3 workflow has produced one.
- A related unit-level narrative expression contract or equivalent unit-level expression reference, when available.
- A unit context package or equivalent confirmed unit-level context.
- A chapter outline or at least a chapter function row from the unit outline.
- Any explicit author requirement for this chapter.

## Optional Inputs

- Existing draft detail outline to revise.
- Co-creation discussion logs, only when needed to trace author intent behind a narrative expression contract.
- Relevant prior or next chapter summaries.
- Short excerpts from character, event, or setting cards.
- Style or pacing preferences, only as constraints for the outline layer.
- Approved reusable rule files that are part of the system.

## Conflict Handling

If inputs conflict, follow the chapter creative control plan's conflict priority and ASK_USER triggers when available. If no priority is available, do not resolve by inventing new canon; record the issue in `待确认问题` or ask the author when the conflict blocks scene design.

Common conflicts:

- Chapter narrative expression contract and older source outline disagree about reader knowledge, POV filtering, title meaning, or what the chapter is "about".
- Chapter creative control plan and any other input disagree about artifact priority, ASK_USER triggers, or token boundary.
- Unit narrative expression contract and chapter narrative expression contract disagree; follow the chapter contract for this chapter and record the issue as a backflow item if it affects multiple chapters.
- Narrative expression contract appears to contradict character/event/setting facts; preserve world facts and record the conflict in `待确认问题`.
- Unit context and chapter outline disagree about what the protagonist knows.
- Chapter outline needs an event outcome that the event card does not support.
- A scene requires a character to act outside their known behavior boundary.
- A setting mechanism is used without cost, limit, or confirmed rule.
- Author request asks for early revelation of information that upstream material marks as hidden.
- Input package includes external prose drafts, comparison reports, finished sample text, or other non-system writing material as if it were generation context.

## Compression Rule

Do not read or copy full upstream files by default. Extract only the facts that this chapter needs:

- expression differences from the chapter narrative expression contract
- division of labor, conflict priority, ASK_USER triggers, and token boundary from the chapter creative control plan
- unit-level expression baseline
- reader knowledge boundary
- POV filtering boundary
- misreading direction
- bright-line and hidden-line movement
- hard prohibitions
- unit-contract backflow items
- current in-world state
- cognition boundary
- action boundary
- language boundary
- relationship pressure
- character motive gaps
- event fact used by the chapter
- information to release or hide
- setting limit
- chapter ending state

## Source Pollution Handling

If a provided input appears to include external prose drafts, finished jokes, finished dialogue, comparison details, or other non-system writing material, do not use that material. Record the issue in `输入依据` as excluded material and add a `待确认问题` row if the remaining allowed system inputs are insufficient.
