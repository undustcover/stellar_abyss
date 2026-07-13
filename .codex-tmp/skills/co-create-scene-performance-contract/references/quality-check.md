# Quality Check

Run this check before returning a scene performance contract.

## Required Passes

1. Source fit
   - The contract references `章节创作总控规划`.
   - It does not proceed if no creative control plan exists or if its absence is unresolved.
2. Scope
   - The contract controls prose performance, not plot structure.
   - It does not rewrite the chapter detail outline or narrative expression contract.
3. Anti-repetition
   - The contract does not restate upstream plot, character cards, event cards, or setting cards.
   - It references source artifacts by path, ID, or short decision labels.
   - It references reusable director-layer prose-quality rules by rule name or short tag only, without copying the full common rule text.
4. Prose boundary
   - It does not write finished prose paragraphs.
   - It does not provide full dialogue exchanges, punchlines, or ending lines.
5. Role routing
   - Character motive, behavior, or knowledge problems are routed to `control-character-intent`.
   - One difficult executable scene-staging problem is routed to `generate-scene-execution-brief`.
   - Chapter-level author intent conflicts are routed back to `co-create-narrative-expression`.
   - Plot-order or scene-action changes are routed to the chapter detail outline rather than absorbed here.
6. Token control
   - Whole-chapter rules are concise.
   - Key-scene rules are only included when needed.
   - Discussion history is not copied into the contract.

## Failure Fixes

|Failure|Fix|
|---|---|
|Contract repeats the outline|Replace plot retelling with prose-performance rules and source references.|
|Contract decides character motive|Move the issue to `control-character-intent`.|
|Contract writes sample prose as final text|Remove finished lines and restate only rhythm, texture, or expression direction.|
|Every scene is expanded|Keep whole-chapter baseline plus only key-scene differences.|
|No creative control plan is referenced|Stop and ask to create or locate `章节创作总控规划`.|
|Contract copies director-layer common rules|Replace copied rule text with rule names or short tags and keep only chapter-specific differences.|
