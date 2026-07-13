# Quality Check

Before returning a control result, verify:

## Formal Template

- The output follows `System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md`.
- The formal YAML, headings, tables, and `待确认问题` are preserved.
- The result includes or intentionally marks the formal sections needed for the current scope.
- `执行包轻引用接口` contains only coverage tags, risk tags, short summaries, gaps, and suggested backflow.
- The execution-pack-facing section does not copy full intent tracks.

## Chapter Baseline

- Chapter-level character intent baselines are provided when generating a full chapter result.
- Baselines do not replace character cards or create long-term character facts.
- Any possible long-term rule is recorded only as a `long_term_rule_candidates` item.

## Intent Track

- The current key fragment is identified.
- Only relevant characters have tracks.
- Each track has a behavior goal and language goal when the character acts or speaks.
- The track explains why the character does not take a simpler action.
- Knowledge boundaries support the line or action.
- Forbidden content is explicit.

## CONTINUE

Return `CONTINUE` only if:

- character reasons for speaking and acting are clear;
- no P0 divergence remains;
- current information supports the intended line/action;
- the action creates a plausible consequence;
- the result can be handed to prose generation without inventing author intent.

## ASK_USER

Return `ASK_USER` if:

- a P0 language or behavior divergence remains;
- two valid choices create different character meanings;
- a simpler action has no character-level reason for being avoided;
- a line or action moves plot but may betray character.

The question must be specific, include a recommendation, and stop after asking.

## RESUME

Return `RESUME` only if:

- the author's answer has been normalized into a rule;
- affected scope is clear;
- runtime-state update blocks are provided;
- a resume point is named.

## Boundary Check

- Do not write prose.
- Do not create outlines or execution packs.
- Do not update character cards.
- Do not ask about ordinary wording or minor action.
- Do not treat the execution pack as the source of character intent.
- Do not generate full tracks for every ordinary scene by default.
- Do not remove formal template fields because a source is missing; mark the gap instead.
