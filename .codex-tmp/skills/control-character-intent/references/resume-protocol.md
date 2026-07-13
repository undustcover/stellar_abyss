# Resume Protocol

Use this protocol after the author answers an `ASK_USER` interruption or directly edits an intent track.

## Steps

1. Convert the answer into a precise rule.
2. Identify affected scope:
   - current fragment;
   - current scene;
   - chapter remainder;
   - long-term rule candidate.
3. Prepare runtime-state update blocks.
4. State the resume point.
5. Hand control back to the prose generation skill.

## Required Format

已确认：
- ...

影响范围：
- ...

章节运行态更新：

YAML update block:

- resolved_intents / resolved_divergences / pending_divergences / long_term_rule_candidates

可从以下断点继续：
- ...

## Rules

- Do not repeat prior prose.
- Do not restart the chapter.
- Do not silently change confirmed earlier text.
- Do not write the next prose fragment unless the user explicitly asks this skill to combine control and drafting.
- Do not update character cards.
