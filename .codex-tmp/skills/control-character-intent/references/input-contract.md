# Input Contract

## Required Input

Use the smallest sufficient set:

- chapter creative control plan;
- chapter narrative expression contract;
- relevant chapter detail outline sections;
- relevant scene performance contract rule for the current fragment or chapter-level baseline;
- necessary character-card summaries for long-term language habits, behavior boundaries, knowledge boundaries, and relationship state;
- relevant event or setting fact limits;
- current key fragment description or resume point when building a P0/P1 fragment track;
- chapter runtime state, if it exists;
- chapter execution pack risk index, if it already exists;
- immediately preceding generated prose summary or fragment.

When generating a full chapter-level `人物意图结果`, also read the formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md
```

## Allowed Input

- confirmed narrative-system inputs;
- confirmed setting-system cards;
- event-database cards;
- approved common writing rule files;
- author answers from the current alignment flow.

## Forbidden Input

Do not use:

- external finished prose drafts;
- comparison reports as generation material;
- non-system writing notes as character behavior facts;
- full unrelated character-card content;
- unconfirmed long-term character conclusions;
- finished jokes, finished dialogue, punchlines, paragraph order, or signature expressions from non-system material.

## Source Priority

1. Author's latest explicit answer in the current intent flow.
2. Chapter creative control plan for conflict priority, ASK_USER triggers, and token boundaries.
3. Chapter narrative expression contract for information and POV boundaries.
4. Chapter runtime state.
5. Character/event/setting world facts.
6. Chapter detail outline.
7. Scene performance contract only as character-facing language/behavior constraints.
8. Chapter execution pack risk index, if present.
9. Approved prose-control rules.

When sources conflict, do not silently choose if the choice changes character language intent or behavior intent. Return `ASK_USER`.

## Scene Performance Use Boundary

Use the scene performance contract only to translate prose-facing rules into fragment-level character constraints:

- dialogue naturalness -> speaking mode, interruption, evasion, hesitation, or pressure;
- narration/psychology boundary -> what the character must not explain or consciously infer;
- anti-AI rule -> behavior or language should stay rough, partial, interrupted, or action-led.

Do not evaluate whole-chapter style, rewrite the performance contract, or copy its full table into an intent result.

## Execution Pack Boundary

The execution pack is optional input for this skill. Use it only for risk labels, coverage gaps, scene IDs, and backflow notes that already exist.

Do not treat the execution pack as the source of character intent. Do not let execution-pack gaps force new tracks unless the creative control plan, chapter contract, detail outline, or character facts also show a P0/P1 intent risk.
