---
id: PLAN-CHAPTER-INTERFACE-001
type: skill_plan
module: source_draft
status: confirmed
version: "1.3"
updated: 2026-07-23
---

# 章节 Draft Brief 与统一运行日志

## 本轮目标

为独立章节对话建立两个默认章节级中间产物的最小接口，并使运行问题能够定位到具体输入、模块、控制单元、方法或执行层。

本方案不修改、迁移或安装测试 Skill，不生成正文，不恢复大型章节契约、总控规划或默认执行包。

## 一、章节 Draft Brief

### 职责

Brief 是生成前经过作者确认的章节入口，只保存本章相对稳定单元资料和章节结构新增的创作决定。它不复制单元上下文包、总体规划、章节大纲／细纲、人物卡或方法正文。

### 最小接口

```yaml
chapter_draft_brief:
  id:
  status: confirmed
  version:
  unit:
  chapter:
  source_refs:
    unit_context: { id:, version: }
    unit_plan: { id:, version: }
    chapter_outline:
    detail_outline:
    language_profile: { id:, version: }
  previous_chapter_handoff:
    source_chapter:
    continuation_anchor:
    must_carry: []
    handoff_question:
  creation_decision:
    author_goal:
    story_focus:
    pov:
      chapter_main:
      scene_exceptions: []
    reader_information:
      may_reveal: []
      must_hold: []
    ending_direction:
    hard_prohibitions: []
    method_refs: []
  unresolved_questions: []
```

### 字段边界

- `source_refs` 只记录实际版本，不摘要来源内容；不存在章节大纲或细纲时可以为空，但必须有一个可执行的章节结构来源；`language_profile` 引用作品级默认语域，章节没有特殊语言要求时不复制文风正文；
- `previous_chapter_handoff` 沿用已确认四字段接口，不扩表；首章允许整体为空；
- `creation_decision` 只记录作者对本章的目标、故事焦点、POV、信息边界、章末方向和硬禁区；
- `scene_exceptions` 只记录作者已经确认的场景边界例外或全景客观特例，不复制场景表，也不在当前阶段实现多人物 POV 路由；
- `method_refs` 只引用已经存在且经作者确认适用的方法；方法缺失不在 Brief 中临时编写；
- 会改变正文方向的 `unresolved_questions` 未解决时，Brief 不得标记 `confirmed`。

### 明确排除

Brief 不保存完整剧情摘要、场景顺序、人物意图轨道、事实包、完整文风规则、生成调度、检查清单或正文方案。作品级语言要求只保存版本引用；章节确有特殊偏离时，才在 `creation_decision` 中记录一句最小差异。

## 二、统一 Draft 运行日志

### 职责

运行日志记录一次 Draft 实际发生了什么，并为问题归因保存最短证据链。普通运行只有一份紧凑日志；高风险、恢复、测试或故障复现才链接详细运行记录、场景演出契约或章节执行包。

### 最小接口

```yaml
draft_run_log:
  id:
  status: completed | blocked | failed
  version:
  unit:
  chapter:
  run:
  input_refs:
    draft_brief: { id:, version: }
    resolved_sources: []
  routing:
    module_entry: MOD-SOURCE-DRAFT
    skills: []
    control_units: []
    methods: []
    knowledge_items: []
  audits:
    character_intent:
      result: PASS | ASK_USER
      applicable_state:
      findings: []
      question:
    hard_boundaries:
      result: PASS | FAIL
      failures: []
    product_review:
      result: PENDING_AUTHOR_REVIEW | ACCEPTED | FAILED
      note:
  interventions: []
  output:
    draft_ref:
    result: GENERATED | BLOCKED | FAILED
  issue_routes: []
```

### 记录规则

- `resolved_sources` 只记录本次实际读取的文件 ID 与版本，不复制内容；
- `skills`、`control_units`、`methods` 和 `knowledge_items` 只记录实际调用项及适用范围，不列出整个知识库；
- 候选但尚未接入的 Skill 或控制单元不得伪装成已执行；测试接入前可记录 `planned_only`；
- `PASS / FAIL` 只用于连续性、POV、信息隐藏、硬结果遗漏等客观边界；元素出现不得自动转换为产品质量 `PASS`；
- `product_review` 在作者明确判断前必须保持 `PENDING_AUTHOR_REVIEW`；
- 正常日志不保存逐场镜头表、画面风险矩阵或完整覆盖分析；高风险测试时可记录场景轻重、节点的 `advance / experience` 判断、现实变化和显形点，但不得扩展为作者步骤；
- `interventions` 只记录实际发生的作者询问、冲突裁决、方法缺口或按需工具启用；
- `issue_routes` 在生成失败或作者反馈后追加，每个问题必须指向一个首要定位点；证据不足时标记 `needs_diagnosis`，不得猜测归因。

### 问题定位条目

```yaml
issue_routes:
  - issue_id:
    symptom:
    evidence:
    locator_type: source_artifact | input_interface | module | skill | control_unit | method | execution | test
    locator_id:
    disposition: fix | inspect | ask_user | no_change
```

一个问题可以保留次要关联，但只能有一个首要 `locator_id`，避免多处同时加规则。

## 三、默认与按需边界

默认每章只有：

1. 一份 confirmed 章节 Draft Brief；
2. 一份对应本次生成的紧凑 Draft 运行日志。

下列内容不恢复为默认产物：大型章节叙事契约、章节创作总控规划、场景演出契约、章节执行包、完整人物意图轨道和详细运行实例。

它们只有在方法共创、复杂调度、跨窗口恢复、正式测试或故障复现时按需启用，并由统一日志记录启用原因和链接。

## 四、用户确认

2026-07-22，用户确认：

1. 采用上述 Brief 最小接口；
2. 采用上述统一日志最小接口及“每个问题一个首要定位点”；
3. 旧大型产物继续退出默认链路，只作为日志可链接的按需工具。

## 五、2026-07-23 增补确认

P0C3 能力隔离测试确认正文执行上下文需要去重，并接入作品级语言配置。作者确认网络文化知识先服务《stellar abyss》，作者条目默认立即可用。Brief 因此只增加 `language_profile` 版本引用；实际选择的网络文化条目只进入运行日志，不扩大作者前台步骤。

P0C3 第二次全章重建进一步确认：默认由 Codex 推断主导推进；次要内容在内部按依附、留痕、标签或延后分配表现权限；多个硬结果无法建立主次且各自需要独立高潮时必须请求作者裁决。上述裁决不新增作者必填表，运行审核也不再以元素覆盖代替产品判断。

上述主导推进、表现权限与风险矩阵在第三次重建中继续造成任务化执行，自 1.3 起退出默认接口，只保留为失败历史。Brief 恢复为稳定创作决定入口；场景轻重、推进／体验判断和现实显形属于正文模块内部即时选择，不新增字段。
