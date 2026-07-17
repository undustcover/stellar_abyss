# Quality Check

Run this check before returning a chapter prose draft.

Formal output template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHAPTER-PROSE-DRAFT_正文草稿交付版模板.md
```

## Required Passes

1. Draft scope
   - The output must be prose for one chapter.
   - It must not be an outline, execution pack, or analysis document.
   - It may be generated across approved key fragments, but final V1 must assemble into one complete chapter.
2. Director-source fidelity
   - Follow the chapter creative control plan's division of labor, conflict priority, ASK_USER triggers, and token boundaries.
   - Preserve author intent, reader information boundary, POV filtering, prohibitions, and hidden/revealed lines from the narrative expression contract.
   - Preserve scene order, scene function, plot movement, and ending state from the chapter detail outline.
   - Preserve scene weights, transitions, risk routing, and generation order from the lightweight chapter execution pack.
   - Follow wording, rhythm, dialogue naturalness, narration boundaries, and anti-AI controls from the scene performance contract.
   - Preserve confirmed character intent rules from runtime state and the `character_intent_result`.
3. Prose quality
   - The prose must stage action, pressure, dialogue, perception, and consequence.
   - It must not read like a summary of the pack.
4. Information safety
   - Do not reveal hidden information early.
   - Do not make the viewpoint character know more than allowed.
5. Structural cleanliness
   - The draft follows the formal `正文草稿交付版模板`.
   - No scene labels, tables, outline notes, or process instructions inside `## 正文`.
   - Put caveats and repair suggestions in `## 生成备注`.
   - Do not put character intent tracks inside `## 正文`.
6. New style-chain execution
   - The draft coordinates the narrative expression contract, detail outline, scene performance contract, execution pack, and character intent result instead of treating the execution pack as the only authority.
   - Humor comes from setup, escalation, landing, and echo rather than isolated quips.
   - Dialogue is not clean Q&A and does not turn characters into explainers.
   - Each scene has one dominant joke or misread, but keeps a concrete pressure point.
   - Strong characters do not win every line; sharp dialogue is tied to action, relationship pressure, misread, or information control.
   - Reader, viewpoint, and important support-character cognition remain separated.
7. Character intent result pass
   - Each key fragment was generated from a `character_intent_result` with `CONTINUE` or `RESUME`, or is marked as needing intent control.
   - Character dialogue serves current language intent, not author explanation.
   - Character behavior follows behavior goal, motive, and knowledge boundary.
   - If a character avoids the simpler action, the prose preserves a believable reason.
   - No unresolved `ASK_USER` was ignored.
8. Anti-AI pass
   - Remove over-explanation, polished but nonfunctional metaphor, authorial diagnosis, and summary-like scene expansion.
   - Narration does not explain the complete design by combining what a character did, did not do, and what it means when visible conduct can carry the relationship meaning.
   - Each key close-POV scene gives the viewpoint at least one effective participation beat that shapes reader reception; fast transitions are exempt and no per-paragraph quota is used.
   - Metaphors, descriptions, jokes, and internal reactions pass the character-swap test and remain connected to current scene material.
   - POV binding does not become repeated “saw/thought/felt” markers, continuous commentary, invented character history, or psychology after every action.
   - Keep information release inside conflict, action, pressure, misread signal, object trace, or consequence.
   - Summary humor was converted into scene material, not replaced by prettier narration.
   - Blunt or low-grade misread wording was softened into double-coded, tactful misunderstanding.
9. System-source boundary
   - The draft's generation inputs come only from the creative control plan, narrative expression contract, detail outline, scene performance contract, execution pack, character intent result, narrative system, setting system, event database, and approved common rule files.
   - External prose drafts, comparison reports, finished sample text, and non-system writing material were not used for concrete bridges, jokes, dialogue, punchlines, paragraph order, ending lines, or signature expressions.
   - The draft does not copy execution-pack structure phrases as finished prose.
   - `生成备注` includes `是否只使用系统资料生成`, `非系统资料污染风险`, `人物意图结果输入`, `章节运行态更新情况`, and `总导演整合能力评估`.
   - Any suspected pollution is identified as a risk rather than treated as proof of generation quality.
10. Revision-control pass
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
|The draft changes plot|Restore the detail outline and put the issue in `生成备注`.|
|A key fragment lacks character intent result coverage|Stop drafting and run `control-character-intent` to update the character intent result.|
|The draft ignores ASK_USER|Remove the generated fragment and return to the interruption point.|
|Dialogue explains author intent instead of character intent|Rebuild the fragment from the approved language intent track.|
|Behavior only serves plot|Return to behavior intent control or rewrite with motive, pressure, and consequence.|
|The draft sounds AI-like|Run a second pass: hide logic under action, roughen over-polished lines, break clean Q&A, and replace explanation with pressure or consequence.|
|Narration exposes the complete author design|Keep visible facts; remove negative-action and meaning explanations; let conduct, object handling, address, position, or consequence carry the design.|
|The POV only acts as a camera in a key scene|Add one effective participation beat from confirmed character knowledge, then return to action or dialogue.|
|A metaphor or internal reaction can be swapped between characters|Regenerate from confirmed character experience and current scene material, or remove it.|
|The Public-derived prevention mapping is stale|Report `SYNC-DRAFT-DEAI-001`; synchronize the mapped method before drafting, or stop and ask the author if system maintenance is not authorized.|
|The draft resembles non-system finished prose too closely|Replace finished jokes, dialogue, paragraph order, or ending lines with newly generated material from the pack's mechanisms, then mark the risk in `生成备注`.|
|The draft used external comparison material|Mark the test as contaminated in `生成备注` and regenerate from clean system inputs.|
|A strong character wins every exchange|Cut or roughen clever lines; move force into action, interruption, failed repair, or another character's pressure.|
|A revision deletes the scene's pressure|Restore the action, object, money/procedure pressure, or relationship turn; delete only decorative cleverness.|
|The ending hook is buried|Move the main hook back into focus and make comic afterbeats shorter or quieter.|
|Reader/viewpoint/support-character cognition collapses together|Rewrite the scene so knowledge appears as clue, pressure, misread, or support-character behavior rather than shared explanation.|
|A high-risk scene is skipped|Restore the non-skippable action, object, face, money/procedure, relationship, or information-boundary turn from the execution pack.|
|Inputs conflict without priority|Stop and ask the author unless the creative control plan already defines the priority.|
