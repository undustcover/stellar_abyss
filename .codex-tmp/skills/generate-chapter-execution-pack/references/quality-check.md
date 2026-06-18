# Quality Check

Run this check before returning a chapter execution pack.

## Required Passes

1. Whole-chapter scope
   - The pack must cover one full chapter.
   - It must prepare for one-pass chapter prose drafting.
   - It must not become several separate scene execution briefs.
2. Upstream fidelity
   - Preserve the detail outline's scene order, functions, information boundaries, and ending state.
   - Do not add new plot events unless the user explicitly requests revision.
3. Scene continuity
   - Every scene should have an entrance, exit, and transition logic.
   - The chapter's emotional and information movement should be continuous.
4. Prose boundary
   - Do not write finished prose paragraphs.
   - Do not write full dialogue exchanges.
5. Risk routing
   - Mark high-risk scenes.
   - Recommend a single-scene execution brief only for specific high-risk scenes, not for every scene.
6. New drafting controls
   - The pack includes `章节文风执行`, `认知差执行表`, `生活压力链执行`, `误会语义链执行`, `喜剧/正剧执行策略`, `主钩子与轻收束控制`, `场景承压点保护`, `支持角色情绪弧线`, `核心笑点递进表`, `关键对话断裂点`, `反杀材料进入方式`, `去 AI 化改写要求`, and `生成前检查清单`.
   - The pack turns outline-level chains into executable prose controls instead of repeating the outline.
7. Hook, pressure, and arc control
   - The pack identifies exactly one main ending hook.
   - Core scenes have protected pressure points.
   - Important support characters have a minimal emotional arc.
   - Comedy reduction rules do not remove action, object, money/procedure, face, relationship, or information-boundary pressure.
8. System-source boundary
   - The pack's generation inputs come only from the detail outline, narrative system, setting system, event database, and approved common rule files.
   - External prose drafts, comparison reports, finished sample text, and non-system writing material are not used for concrete bridges, jokes, dialogue, punchlines, paragraph order, ending lines, or signature expressions.
   - `核心笑点递进表` defines structure slots rather than finished jokes.
   - `关键对话断裂点` defines break mechanics rather than full dialogue.
   - `生成前检查清单` explicitly checks system-source use and finished-material exclusion.

## Failure Fixes

|Failure|Fix|
|---|---|
|The pack reads like prose|Convert lines into drafting constraints, weights, and transition rules.|
|Scenes feel isolated|Add transition handles and state carryover.|
|Every scene has equal weight|Reassign word budget based on conflict, reveal, and emotional importance.|
|The pack expands one scene too deeply|Move details to a recommended single-scene execution brief.|
|The pack changes the outline|Restore the outline and record the issue in `待确认问题`.|
|Missing new drafting controls|Add the required style execution, pressure-chain, misread-chain, comedy/drama, dialogue-breakpoint, reversal-material, and anti-AI sections.|
|No main hook is named|Add `主钩子与轻收束控制`; choose one hook that pushes the next chapter and demote other endings.|
|A core scene can be compressed away|Add `场景承压点保护` and mark the non-skippable turn.|
|A support character only delivers information|Add `支持角色情绪弧线` with entrance emotion, turn, and exit state.|
|The pack contains punchlines or dialogue from non-system material|Remove finished material and restate only setup, escalation, landing slot, echo function, or dialogue break mechanism.|
|The pack used external comparison material as context|Mark the input as contaminated and rebuild from clean outline, cards, event database, setting system, and approved rules.|
