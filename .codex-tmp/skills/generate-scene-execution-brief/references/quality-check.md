# Quality Check

Run this check before returning a scene execution brief.

## Required Passes

1. One-scene scope
   - The output must describe exactly one scene.
   - It must not include briefs for other scenes.
   - It must not attempt whole-chapter transition planning or one-pass chapter drafting.
2. Prose boundary
   - The output must not contain finished prose paragraphs.
   - Dialogue entries must describe strategy, topic, function, or subtext, not full exchanges.
3. Upstream fidelity
   - Preserve the chapter detail outline's scene function, ending state, information release, and prohibitions.
   - Do not reorder the chapter or invent a new scene function.
4. Cognition and information
   - Viewpoint knowledge must not exceed upstream constraints.
   - Hidden information may appear only as trace, pressure, absence, misread signal, or reader tension if allowed.
   - Reader, viewpoint, and key support-character cognition are not blended.
5. Pressure and dialogue control
   - The brief names one protected pressure point.
   - The brief names one dominant joke, misread, or comic pressure when humor is part of the scene.
   - Dominant-character line win-rate is controlled where relevant.
   - Important support characters have an entrance emotion, a turn, and an exit state when their arc matters.
6. Prose readiness
   - A prose generation skill should be able to write the scene without inventing the action chain, conflict pressure, information control, or ending beat.

## Failure Fixes

|Failure|Fix|
|---|---|
|The brief covers multiple scenes|Split it and return only the requested scene.|
|The request is whole-chapter preparation|Route to a chapter execution pack workflow instead of using this skill.|
|The brief reads like prose|Convert lines into constraints, action beats, and presentation rules.|
|The brief changes the outline|Restore the outline's function and move the conflict to `待确认问题`.|
|The viewpoint knows too much|Downgrade to clue, suspicion, reader tension, or hidden information.|
|The scene is not writeable|Add concrete action chain, pressure source, dialogue strategy, and ending beat.|
|The scene can be compressed past its real conflict|Add `承压点保护` and name the non-skippable turn.|
|Dialogue becomes clean Q&A|Add `错频目的`, interruption, silence, dodge, failed repair, or line win-rate limits.|
