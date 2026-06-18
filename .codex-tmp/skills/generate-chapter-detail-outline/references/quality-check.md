# Quality Check

Run this check before returning a chapter detail outline.

## Required Passes

1. Traceability
   - Each core fact should point back to unit context, chapter outline, event card, character card, setting card, or author instruction.
   - If traceability is missing, add a row to `待确认问题`.
2. Boundary
   - The outline must not rewrite world facts.
   - The outline must not define character state by chapter or unit.
   - The outline must not generate prose paragraphs or complete dialogue.
3. Information control
   - Protagonist knowledge and reader knowledge must not exceed upstream constraints.
   - Hidden information may appear as surface behavior, consequence, misunderstanding, pressure, or absence, but not as confirmed knowledge.
4. Scene usefulness
   - Each scene needs a goal, action movement, conflict or pressure, information movement, emotional movement, and ending state.
   - Remove scenes that only restate prior material.
   - For a typical 3500-character web-novel chapter, prefer 3-5 effective scenes; allow 1-2 core scenes for concentrated chapters and 5-7 light scenes for long, fast-cut, multi-thread, action-heavy, or turn-heavy chapters.
   - Treat scene count as a pacing choice, not a hard target. Do not add scenes merely to satisfy a number.
5. Prose readiness
   - A later prose generation skill should be able to write from the outline without inventing the chapter's core action, information release, or ending state.
   - A later chapter execution pack should be able to manage scene transitions without expanding every scene into a separate execution brief.
6. New prose-generation bridge fields
   - The outline includes `章节文风模式`, `人物语言调用`, `场景文风分配`, `本章认知差控制`, `场景轻重与承压点`, `生活压力链`, `误会语义链`, `人物情绪链`, and `反杀材料链`.
   - These sections contain reusable structure, not first-draft prose.
   - If chapter style mode or character language data is missing, the gap is marked in `待确认问题`.
7. Cognition and pressure control
   - Reader, viewpoint, and important support-character knowledge are separated.
   - Each core scene has a protected pressure point; transition scenes are marked as compressible.
   - The ending names one main hook, and lighter afterbeats are not allowed to displace it.
8. System-source boundary
   - The outline's generation inputs come only from the narrative system, setting system, event database, and approved common rule files.
   - External prose drafts, comparison reports, finished sample text, and non-system writing material are not listed as generation inputs.
   - Any provided non-system writing material is marked as excluded.
   - The outline's comedy and misread entries are structure/opportunity descriptions, not finished prose material.

## Failure Fixes

|Failure|Fix|
|---|---|
|The outline reads like prose|Replace paragraphs with scene function, action beat, and information movement.|
|The outline changes canon|Move the change to `待确认问题` and preserve the upstream fact.|
|A character knows too much|Downgrade the content to suspicion, misread signal, environmental clue, or reader-only tension if allowed.|
|The chapter lacks movement|Add a concrete action and state change to each scene.|
|The outline is too long|Compress repeated facts into `输入依据` and keep scene rows functional.|
|Missing prose-generation bridge fields|Add the required style, language, pressure, misread, emotion, and reversal-material sections before returning.|
|No scene weight or pressure point is assigned|Add `场景轻重与承压点`; mark which scenes are core, transitional, or hook-bearing.|
|Reader/viewpoint/support-character cognition is blended|Add `本章认知差控制` and downgrade hidden facts to clue, pressure, absence, or misread signal.|
|The ending has several competing hooks|Choose one main hook and mark any comic or emotional afterbeat as secondary.|
|The outline contains finished jokes or dialogue from non-system material|Remove the finished material, restate only the structural opportunity, and mark the source as excluded.|
|The outline used an external comparison report as generation context|Strip the specific bridge/order/joke details and rebuild from chapter outline, cards, event database, setting system, and approved rules only.|
