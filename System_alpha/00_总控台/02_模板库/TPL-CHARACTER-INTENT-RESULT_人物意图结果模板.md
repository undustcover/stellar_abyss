---
type: template
template_for: character_intent_result
system: narrative
status: draft
title: 人物意图结果模板
---

# 人物意图结果模板

人物意图结果用于在总-分-总正文生成链路中记录章节级人物语言意图、行为意图、认知边界、动机基线、关键片段意图轨道、CONTINUE/ASK_USER/RESUME 和章节运行态更新建议。

它是分工产物之一，不是章节执行包的下游，不是章节执行包的前置流水线步骤，也不替代正文草稿生成 Skill。

人物意图结果主服务于正文草稿生成 Skill；章节执行包只可轻量引用其覆盖标签、风险标签、短摘要、缺口和回流建议。

## 文件命名

```text
INTENT-{单元编号}-{章节编号}_{章节名}_人物意图结果.md
```

示例：

```text
INTENT-P0-C03_这事好像比会所还怪_人物意图结果.md
```

## YAML

```yaml
---
id: INTENT-P0-C00
type: character_intent_result
system: narrative
status: draft
temporary: true
unit: P0
chapter: C00
title:
related_creative_control_plan:
related_narrative_expression_contract:
related_detail_outline:
related_scene_performance_contract:
related_execution_pack:
related_runtime_state:
rel: []
tags:
  - narrative
  - character-intent-result
---
```

# {章节编号} 人物意图结果：《{章节名}》

## 模板接口

|接口项|规则|
|---|---|
|模板职责|记录本章人物语言意图、行为意图、认知边界、动机基线、关键片段意图轨道、CONTINUE/ASK_USER/RESUME 和章节运行态更新建议|
|必须读取|章节创作总控规划；章节级叙事表达契约；章节细纲相关片段；场景演出契约相关规则；人物卡/事件卡/设定卡相关事实；章节执行包风险索引，若已存在|
|只可引用|总控规划分工规则；章节契约中的人物边界和信息边界；细纲场景编号/关系压力/认知变化；场景演出契约中与人物表达有关的规则标签；执行包标记的风险标签|
|禁止复述|完整细纲；完整场景演出契约；完整执行包；人物卡全文；正文段落；作者未确认的长期人物结论|
|输出给|正文草稿生成；章节运行态；章节执行包轻量引用；必要时回到作者确认|
|冲突处理|人物动机与剧情推进冲突时 ASK_USER；场景演出要求导致人物不符合人设时 ASK_USER；人物知道不该知道的信息时按章节契约和人物卡回退；只是句式自然化问题时，只转为语言策略约束，不改文风规则|
|ASK_USER 触发|人物为什么这样做不成立；人物为什么不采取更简单行动不成立；人物语言意图有多种业务含义；场景演出要求和人设冲突；是否继续生成需要作者裁决|
|Token 边界|生成章节级人物意图结果；只为 P0/P1 关键片段建轨，不逐场铺满普通场景，不复述其他分工产物|

## 总-分-总边界声明

|项目|规则|
|---|---|
|产物位置|人物意图结果是总-分-总结构中的分工产物之一，与章节细纲、场景演出契约、章节执行包并列服从章节创作总控规划|
|是否线性流水线|否。人物意图结果不是执行包下游，执行包也不是人物意图结果总包|
|可局部互参|可引用细纲场景编号、关系压力、认知边界；可引用场景演出契约中的人物表达相关规则标签；可引用执行包已标记的风险标签|
|禁止行为|不得吞入完整细纲、完整场景演出契约或完整执行包；不得把所有正文质量问题归因给人物意图；不得把人物动机解释成前台正文|
|覆盖不足处理|若人物意图覆盖不足，记录缺口、待确认分歧和回流建议，不静默补写作者未确认的人物意图|

## 输入依据

|来源|路径/ID|调用内容|用途|确认状态|
|---|---|---|---|---|
|章节创作总控规划|||||
|章节级叙事表达契约|||||
|章节细纲相关片段|||||
|场景演出契约相关规则|||||
|章节执行包风险索引|若未生成，填 `missing / 可跳过`||||
|人物卡/事件卡/设定卡|||||
|章节运行态|若未创建，填 `missing / 待创建`||||

> 输入边界：人物意图结果只调用系统资料和作者确认内容。外部正文草稿、对比报告、成品梗、成品对白、成品落点、标志性句式不得作为人物意图依据；若用户提供，只能在本表标记为“已排除/非系统资料”。

## 总体控制结论

|项目|结果|
|---|---|
|控制动作|CONTINUE / ASK_USER / RESUME|
|阻断性分歧||
|本章人物意图总规则||
|本章人物认知总边界||
|可交给正文生成|是 / 否|
|需回流作者确认|无 / 有|
|需更新章节运行态|无 / 有|

## 本章人物意图基线

|人物|本章外在目标|本章内在动机|关系压力|认知边界|语言基线|行为基线|禁区|
|---|---|---|---|---|---|---|---|
||||||||

> 本节记录本章差异化人物基线，不替代人物卡，不生成长期人物结论。长期规则候选只能写入“章节运行态更新建议”的 `long_term_rule_candidates`。

## 关键片段覆盖索引

|片段ID|场景|片段功能|涉及人物|风险等级|覆盖状态|轨道位置|
|---|---|---|---|---|---|---|
||||||||

> 覆盖状态可填：`covered` / `partial` / `missing` / `ASK_USER` / `not_applicable`。只为 P0/P1 关键片段建立轨道，普通低风险片段不强制铺满。

## 关键片段意图轨道

### {片段ID} {片段名}

```yaml
intent_checkpoint:
  chapter_id:
  scene_id:
  fragment_id:
  fragment_scope:
  resume_point:
  risk_level:
  action: CONTINUE
  source_creative_control_plan:
  source_narrative_expression_contract:
  source_detail_outline:
  source_scene_performance_contract:
  source_execution_pack:
  source_character_cards:

character_intent_tracks:
  人物名:
    behavior_goal:
    behavior_motive:
    immediate_action:
    why_not_simpler_action:
    language_goal:
    language_strategy:
    emotional_pressure:
    knowledge:
      knows:
        -
      does_not_know:
        -
      assumes:
        -
      suspects:
        -
    forbidden:
      -
    expected_effect_on_other:
    expected_consequence:
```

### 字段规则

|字段|规则|
|---|---|
|behavior_goal|人物当前想完成什么|
|behavior_motive|这个目标为什么对人物重要，而不是对大纲重要|
|immediate_action|当前片段准备采取的具体行动|
|why_not_simpler_action|人物为什么不直接问、直接走、直接拒绝、直接解释、直接报警或直接解决问题|
|language_goal|人物本轮开口想实现什么|
|language_strategy|人物选择怎样说：试探、遮掩、确认、回避、施压、缓和、玩笑、否认、夸大或转移|
|emotional_pressure|恐惧、羞耻、愤怒、自尊、急迫、尴尬、谨慎或表演性镇定如何影响言行|
|knowledge|人物此刻知道、不知道、误以为、怀疑什么|
|forbidden|人物当前绝不能说、知道、推断或做什么|
|expected_effect_on_other|人物希望或预期对方理解什么、误解什么或采取什么行动|
|expected_consequence|这句话或这个动作会怎样改变局面|

## 场景演出契约转译

|场景/片段|演出规则标签|转译为人物语言/行为约束|不处理内容|
|---|---|---|---|
|||||

> 这里只把文字演出规则转成“人物怎么说/怎么做”的约束：将用词规则转为语言策略，将对白自然化要求转为说话方式约束，将旁白/心理边界转为“人物不能像解释设定”，将去 AI 化要求转为人物行为和语言的自然化检查。不得评价整体文风，不得重写场景演出契约。

## 执行包轻引用接口

|覆盖类别|覆盖标签|风险标签|短摘要|缺口|建议回流|
|---|---|---|---|---|---|
|关系压力覆盖||||||
|认知边界覆盖||||||
|关键行为风险覆盖||||||
|关键对白风险覆盖||||||

> 本节只给章节执行包引用。执行包只能引用标签、风险标签、短摘要、缺口和回流建议，不得复制完整意图轨道，不得替人物意图结果补写轨道。

## ASK_USER / RESUME 记录

### 待确认分歧

|分歧ID|风险等级|人物|问题|阻断原因|必须确认前置点|建议问法|
|---|---|---|---|---|---|---|
||||||||

### 已确认分歧

|分歧ID|人物|作者决定|归一化规则|影响范围|恢复点|
|---|---|---|---|---|---|
|||||||

> 触发 ASK_USER 后，不得继续生成相关正文片段。作者确认后，先归一化为规则，再更新章节运行态，并从恢复点继续。

## 章节运行态更新建议

```yaml
resolved_intents:
  - id:
    source_checkpoint:
    character:
    type: language_intent # language_intent / behavior_intent / cognition / relationship / reader_info
    decision:
    normalized_rule:
    scope: 当前片段 # 当前片段 / 当前场景 / 本章后续 / 长期规则候选
    confirmed_by_author:
    created_at:

resolved_divergences:
  - id:
    risk_level:
    divergence_type:
    character:
    question:
    author_decision:
    model_recommendation:
    final_rule:
    affected_scope:
    resume_point:

pending_divergences:
  - id:
    risk_level:
    divergence_type:
    character:
    blocking_reason:
    must_ask_before:
    resume_point:

long_term_rule_candidates:
  - id:
    source:
    character:
    candidate_rule:
    reason:
    target_file:
    status: pending_review
```

> 章节运行态只保存章节内临时人物意图、作者确认规则、分歧记录、恢复点和长期规则候选。不得自动回写人物卡。

## 质量检查

|检查项|结果|
|---|---|
|是否读取章节创作总控规划||
|是否服从章节级叙事表达契约||
|是否只局部引用细纲、场景演出契约、执行包||
|是否没有复述完整上游产物||
|是否覆盖关键人物关系压力||
|是否覆盖关键认知边界||
|是否覆盖关键行为风险||
|是否覆盖关键对白风险||
|为什么不采取更简单行动是否成立||
|是否存在 ASK_USER 阻断||
|是否没有写正文||
|是否没有自动回写人物卡||
|是否只调用系统资料||
|是否排除非系统成品梗/成品对白/成品落点||

## 归档规则

|项目|规则|
|---|---|
|产物性质|章节级临时控制产物|
|正文完成后处理|正文确定后可归档；其中被作者确认且有长期价值的规则只进入长期规则候选，不自动回写人物卡|
|是否进入长期世界事实|否|
|可保留价值|人物言行控制依据、ASK_USER/RESUME 记录、运行态更新建议、后续正文生成追踪|

## 待确认问题

|问题|影响范围|建议处理|
|---|---|---|
|||||
