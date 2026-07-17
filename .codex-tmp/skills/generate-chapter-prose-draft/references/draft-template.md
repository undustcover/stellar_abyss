# Draft Template

Formal template source:

```text
System_alpha/00_总控台/02_模板库/TPL-CHAPTER-PROSE-DRAFT_正文草稿交付版模板.md
```

This reference is a local mirror for `generate-chapter-prose-draft`. The formal template in `System_alpha/00_总控台/02_模板库` is authoritative. Use this template for a `type: draft` chapter prose delivery file.

```markdown
---
id: DRAFT-P00-C00
type: draft
system: narrative
status: draft
title:
unit: P00
chapter: C00
source_creative_control_plan:
source_narrative_expression_contract:
source_detail_outline:
source_scene_performance_contract:
source_execution_pack:
source_character_intent_result:
source_runtime_state:
rel: []
tags:
  - narrative
  - draft
---

# 章节标题

## 模板接口

|接口项|规则|
|---|---|
|模板职责|承载最终小说正文、上游来源索引和生成备注；正文生成 Skill 作为总导演统一调用各产物|
|必须读取|章节创作总控规划；章节级叙事表达契约；章节细纲；场景演出契约；章节执行包；人物意图结果；章节运行态；导演层可复用文本质量规则；Public 去 AI 化方法的 Draft 预防映射|
|只可引用|已确认上游产物；当前生成片段所需资料；总控规划中的冲突优先级和 ASK_USER 规则|
|禁止复述|任何上游模板表格；过程标签；意图轨道；分析说明；章节执行包结构短语；上游产物摘要|
|输出给|正文文件；正文评估；局部返修；必要时回流到共创或人物意图控制|
|冲突处理|根据总控规划处理冲突；没有优先级且涉及业务判断时 ASK_USER；不静默改世界事实；不静默改变作者审美|
|ASK_USER 触发|上游产物冲突无法裁决；人物意图结果返回 ASK_USER；需要改变剧情、信息边界、人物边界或作者审美；正文生成需要使用非系统成品材料|
|Token 边界|正文只写正文；生成备注只写风险、缺口、追踪和返修建议，不复制上游产物|

## 正文

正文内容写在这里。

## 生成备注

### 输入状态

|项目|内容|
|---|---|
|章节创作总控规划||
|章节级叙事表达契约||
|章节细纲||
|场景演出契约||
|章节执行包||
|人物意图结果||
|章节运行态||
|Public 去 AI 预防映射|方法 ID@版本|
|去 AI 预防映射同步状态|current / stale|
|是否只使用系统资料生成|是 / 否 / 存在污染风险|
|非系统资料污染风险||

### 总导演整合情况

|项目|内容|
|---|---|
|章节创作总控规划执行情况||
|章节级叙事表达契约执行情况||
|章节细纲执行情况||
|场景演出契约执行情况||
|章节执行包调度执行情况||
|人物意图结果执行情况||
|导演层文本质量规则执行情况||
|总导演整合能力评估||

### 风险与缺口

|项目|内容|
|---|---|
|上游冲突处理||
|输入缺口||
|人物意图结果输入|CONTINUE / RESUME / ASK_USER / 缺失|
|角色语言字段缺口||
|角色语言越界风险||
|人物同质化风险||
|为什么不采取更简单行动检查||
|疑似AI感句子||
|说明式完整设计旁白风险||
|关键场景 POV 参与风险||
|人物联想换人测试风险||
|人物联想场景关联风险||
|解释过度风险||
|叙事说明书化风险||
|疑似硬梗||
|对话配合问答风险||
|漂亮比喻过度风险||
|幽默冲淡正剧情绪风险||
|认知差执行风险||
|主钩子聚焦风险||
|轻收束抢主钩子风险||
|承压场面被压缩风险||
|支持角色情绪弧线风险||
|高风险场面跳过风险||
|章节运行态更新情况||

### 建议返修

|问题|位置/范围|建议处理|
|---|---|---|
||||
```

## Prose Body Rule

Only the novel text goes under `## 正文`. Do not insert outline labels, scene numbers, tables, analysis notes, or comments inside the prose body unless the author explicitly wants annotated drafting.

For a formal delivery draft, the `## 模板接口` section may be removed from the generated instance; keep `## 正文` and `## 生成备注` unless the author asks for a clean author-reading version.

## Notes Rule

Put non-prose material under `## 生成备注`. Keep notes concise and actionable.

## Anti-AI Notes Rule

If no risk is found for a row, write `未发现明显风险`. Do not invent problems. If a risk is found, cite a short phrase or describe the location, then give a repair direction.

## Source Notes Rule

For `是否只使用系统资料生成`, write one of: `是`, `否`, or `存在污染风险`. For `非系统资料污染风险`, explain whether any finished joke, dialogue, punchline, paragraph order, ending line, or signature expression may come from external prose drafts, comparison reports, or other non-system writing material. For `人物意图结果输入`, state whether prose was generated from a `character_intent_result` with `CONTINUE` or `RESUME`, or whether the result was `ASK_USER`/missing. For `Public 去 AI 预防映射`, record every mapped `method ID@version`; for `去 AI 预防映射同步状态`, record `current` or `stale` and never silently generate when stale. For `章节运行态更新情况`, state whether confirmed intent rules were written or should be written to runtime state. For `总导演整合能力评估`, state whether the draft successfully coordinated the creative control plan, narrative expression contract, detail outline, scene performance contract, execution pack, character intent result, director prose-quality rules, Public-derived prevention mapping, and approved system inputs.
