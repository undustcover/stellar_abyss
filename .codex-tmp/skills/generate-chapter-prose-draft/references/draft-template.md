# Draft Template

Use this template for a `type: draft` chapter prose file.

```markdown
---
id: DRAFT-P00-C00
type: draft
system: narrative
status: draft
title:
unit: P00
chapter: C00
source_pack:
rel: []
tags:
  - narrative
  - draft
---

# 章节标题

## 正文

正文内容写在这里。

## 生成备注

|项目|内容|
|---|---|
|输入缺口||
|文风模式执行情况||
|文风模式与剧情冲突||
|角色语言字段缺口||
|角色语言越界风险||
|人物同质化风险||
|疑似AI感句子||
|疑似硬梗||
|解释过度风险||
|对话配合问答风险||
|漂亮比喻过度风险||
|叙事说明书化风险||
|幽默冲淡正剧情绪风险||
|认知差执行风险||
|角色台词胜率风险||
|误会尺度风险||
|主钩子聚焦风险||
|轻收束抢主钩子风险||
|承压场面被压缩风险||
|支持角色情绪弧线风险||
|高风险场面跳过风险||
|是否只使用系统资料生成||
|非系统资料污染风险||
|自动生成能力评估||
|需要作者判断的梗||
|建议返修||
```

## Prose Body Rule

Only the novel text goes under `## 正文`. Do not insert outline labels, scene numbers, tables, analysis notes, or comments inside the prose body unless the author explicitly wants annotated drafting.

## Notes Rule

Put non-prose material under `## 生成备注`. Keep notes concise and actionable.

## Anti-AI Notes Rule

If no risk is found for a row, write `未发现明显风险`. Do not invent problems. If a risk is found, cite a short phrase or describe the location, then give a repair direction.

## Source Notes Rule

For `是否只使用系统资料生成`, write one of: `是`, `否`, or `存在污染风险`. For `非系统资料污染风险`, explain whether any finished joke, dialogue, punchline, paragraph order, ending line, or signature expression may come from external prose drafts, comparison reports, or other non-system writing material. For `自动生成能力评估`, state whether the draft's life pressure, misread semantics, dialogue breakpoints, humor, and anti-AI pass were generated from the skill chain and allowed system inputs.
