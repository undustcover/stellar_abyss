# Quality Check

Run this check before returning a chapter execution pack.

## Required Passes

1. Whole-chapter scope
   - The pack must cover one full chapter.
   - It must prepare for controlled key-fragment drafting and whole-chapter assembly.
   - It must not become several separate scene execution briefs.
2. Creative-control fidelity
   - The pack reads `章节创作总控规划`.
   - The pack follows its division of labor, reference rules, conflict priority, ASK_USER triggers, and token boundary.
   - The pack does not become a replacement creative control plan.
3. Upstream fidelity
   - Preserve the detail outline's scene order, functions, information boundaries, and ending state.
   - Do not add new plot events unless the user explicitly requests revision.
4. Scene continuity
   - Every scene should have an entrance, exit, and transition logic.
   - The chapter's emotional and information movement should be continuous.
   - Transition logic is written as state carryover and transition type, not as bridge prose or new plot actions.
5. Prose boundary
   - Do not write finished prose paragraphs.
   - Do not write full dialogue exchanges.
   - Do not write prose-ready hooks, finished ending lines, complete scene summaries, or bridge paragraphs.
6. Risk routing
   - Mark high-risk scenes.
   - Recommend a single-scene execution brief only for specific high-risk scenes, not for every scene.
7. Dispatch controls
   - The pack includes `读取产物索引`, `总控规划执行摘要`, `场景调度表`, `场景衔接表`, `高风险清单`, `场景演出契约引用`, `人物意图覆盖状态`, `可选单场景执行 Brief 路由`, and `生成前检查清单`.
   - The pack indexes and routes upstream artifacts instead of repeating them.
   - The pack includes `人物意图覆盖状态` with intent-result index, relationship-pressure coverage, cognition-boundary coverage, key behavior-risk coverage, key dialogue-risk coverage, forbidden model-decisions, and backflow needs.
   - The pack does not build full character intent tracks; it only records coverage status, risk flags, and backflow needs.
   - The pack passes the formal template's `越权排除检查`.
8. Hook, pressure, and arc control
   - The pack identifies exactly one main ending hook.
   - Core scenes have protected pressure points.
   - Important support characters have a minimal emotional arc.
   - Comedy reduction rules do not remove action, object, money/procedure, face, relationship, or information-boundary pressure.
9. System-source boundary
   - The pack's generation inputs come only from the detail outline, narrative system, setting system, event database, and approved common rule files.
   - External prose drafts, comparison reports, finished sample text, and non-system writing material are not used for concrete bridges, jokes, dialogue, punchlines, paragraph order, ending lines, or signature expressions.
   - `生成前检查清单` explicitly checks system-source use and finished-material exclusion.

## Failure Fixes

|Failure|Fix|
|---|---|
|The pack reads like prose|Convert lines into drafting constraints, weights, and transition rules.|
|The pack writes a prose hook or ending line|Replace it with a short hook function, state label, or route to prose drafting.|
|Scenes feel isolated|Add transition handles and state carryover.|
|Every scene has equal weight|Reassign word budget based on conflict, reveal, and emotional importance.|
|The pack expands one scene too deeply|Move details to a recommended single-scene execution brief.|
|The pack changes the outline|Restore the outline and record the issue in `待确认问题`.|
|Missing creative control plan|Stop and ask to create or locate `章节创作总控规划`; do not infer downstream interfaces silently.|
|The pack copies full upstream artifacts|Replace copied content with source index entries, short references, and dispatch rules.|
|Missing character-intent coverage status|Add `人物意图覆盖状态` with key dialogue/behavior risk coverage and backflow needs.|
|The pack builds full character intent tracks|Reduce them to coverage status, risk flags, and backflow needs; leave tracks to `control-character-intent`.|
|No main hook is named|Add it to `章节生成目标` or route the missing decision to `待确认问题`.|
|A core scene can be compressed away|Raise its scene grade or add a high-risk route instead of expanding the pack into scene prose.|
|A support character only delivers information|Flag the support-character risk for `control-character-intent` or downstream prose generation.|
|The pack contains punchlines or dialogue from non-system material|Remove finished material and restate only setup, escalation, landing slot, echo function, or dialogue break mechanism.|
|The pack used external comparison material as context|Mark the input as contaminated and rebuild from clean outline, cards, event database, setting system, and approved rules.|
