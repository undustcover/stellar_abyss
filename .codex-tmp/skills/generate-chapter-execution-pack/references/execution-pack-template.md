# Chapter Execution Pack Template Pointer

The formal chapter execution pack template is the source of truth:

```text
System_alpha/00_总控台/02_模板库/TPL-CHAPTER-EXECUTION-PACK_章节执行包模板.md
```

When generating a `type: chapter_execution_pack`, use that formal template's YAML fields, heading order, table names, and boundary notes exactly.

Do not use older local test structures that contain:

- `人物意图控制接口` as if the execution pack triggers or owns intent control;
- full character intent tracks;
- copied scene performance rules;
- copied chapter outline tables;
- prose-ready dialogue, finished jokes, punchlines, or ending lines.

Use the formal replacements:

|Old/local wording|Formal wording|
|---|---|
|人物意图控制接口|人物意图覆盖状态|
|意图控制器建议检查片段|需回流人物意图控制的问题|
|建议字数|建议字数/篇幅范围|
|输出给人物意图控制|必要时回流人物意图控制|

The execution pack must remain a dispatch index: source paths, scene grades, weight ranges, generation order, transition states, risk routing, scene-performance rule labels, and character-intent coverage status.

Route missing or insufficient character intent coverage back to `control-character-intent`; do not fill the missing intent inside the execution pack.

Additional formal-template boundary:

- `章节生成目标` only records state labels or very short goals from confirmed upstream artifacts; do not write complete plot summaries, prose hook lines, or finished ending lines.
- `场景衔接表` only records state carryover and transition type; do not write bridge prose or new plot actions.
- `正文生成顺序` only records ordering and dispatch reasons; do not write prose plans or complete scene summaries.
- The formal template's `越权排除检查` must pass before returning the pack.
