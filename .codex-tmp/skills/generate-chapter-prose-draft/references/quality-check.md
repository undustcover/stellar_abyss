# Quality Check

Run this check before returning a chapter prose draft.

## Required Passes

1. Draft scope
   - The output must be prose for one chapter.
   - It must not be an outline, execution pack, or analysis document.
2. Pack fidelity
   - Preserve scene order, scene weights, transitions, cognition limits, information control, prohibitions, and ending state from the chapter execution pack.
3. Prose quality
   - The prose must stage action, pressure, dialogue, perception, and consequence.
   - It must not read like a summary of the pack.
4. Information safety
   - Do not reveal hidden information early.
   - Do not make the viewpoint character know more than allowed.
5. Structural cleanliness
   - No scene labels, tables, outline notes, or process instructions inside `## 正文`.
   - Put caveats and repair suggestions in `## 生成备注`.
6. New style-chain execution
   - The draft uses the pack's cognition-difference table, life-pressure chain, misread semantic chain, main-hook control, pressure-point protection, support-character emotional arc, dialogue breakpoints, and reversal-material entry method.
   - Humor comes from setup, escalation, landing, and echo rather than isolated quips.
   - Dialogue is not clean Q&A and does not turn characters into explainers.
   - Each scene has one dominant joke or misread, but keeps a concrete pressure point.
   - Strong characters do not win every line; sharp dialogue is tied to action, relationship pressure, misread, or information control.
   - Reader, viewpoint, and important support-character cognition remain separated.
7. Anti-AI pass
   - Remove over-explanation, polished but nonfunctional metaphor, authorial diagnosis, and summary-like scene expansion.
   - Keep information release inside conflict, action, pressure, misread signal, object trace, or consequence.
   - Summary humor was converted into scene material, not replaced by prettier narration.
   - Blunt or low-grade misread wording was softened into double-coded, tactful misunderstanding.
8. System-source boundary
   - The draft's generation inputs come only from the execution pack, narrative system, setting system, event database, and approved common rule files.
   - External prose drafts, comparison reports, finished sample text, and non-system writing material were not used for concrete bridges, jokes, dialogue, punchlines, paragraph order, ending lines, or signature expressions.
   - The draft does not copy execution-pack structure phrases as finished prose.
   - `生成备注` includes `是否只使用系统资料生成`, `非系统资料污染风险`, and `自动生成能力评估`.
   - Any suspected pollution is identified as a risk rather than treated as proof of generation quality.
9. Revision-control pass
   - For revision drafts, the internal `保留/压缩/删除/延后` choice did not remove required pressure scenes.
   - The main ending hook remains visible and is not displaced by a lighter comic afterbeat.
   - Important support characters show an emotional turn instead of staying as helpers, explainers, or atmosphere.

## Failure Fixes

|Failure|Fix|
|---|---|
|The draft reads like an outline|Rewrite into present-moment action, dialogue, pressure, and consequence.|
|The draft explains hidden mechanics|Replace explanation with trace, pressure, absence, or misread signal.|
|The viewpoint knows too much|Downgrade to suspicion, clue, reader tension, or unknown pressure.|
|Scenes feel disconnected|Add transition carryover from the execution pack.|
|The draft changes plot|Restore the pack and put the issue in `生成备注`.|
|The draft sounds AI-like|Run a second pass: hide logic under action, roughen over-polished lines, break clean Q&A, and replace explanation with pressure or consequence.|
|The draft resembles non-system finished prose too closely|Replace finished jokes, dialogue, paragraph order, or ending lines with newly generated material from the pack's mechanisms, then mark the risk in `生成备注`.|
|The draft used external comparison material|Mark the test as contaminated in `生成备注` and regenerate from clean system inputs.|
|A strong character wins every exchange|Cut or roughen clever lines; move force into action, interruption, failed repair, or another character's pressure.|
|A revision deletes the scene's pressure|Restore the action, object, money/procedure pressure, or relationship turn; delete only decorative cleverness.|
|The ending hook is buried|Move the main hook back into focus and make comic afterbeats shorter or quieter.|
|Reader/viewpoint/support-character cognition collapses together|Rewrite the scene so knowledge appears as clue, pressure, misread, or support-character behavior rather than shared explanation.|
|A high-risk scene is skipped|Restore the non-skippable action, object, face, money/procedure, relationship, or information-boundary turn from the execution pack.|
