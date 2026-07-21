---
id: REPORT-T3-T4-V0_2-001
type: phase_completion_report
status: complete
version: "0.1"
created: 2026-07-21
runtime_eligible: false
---

# T3—T4 V0.2 作者实例测试与迁移校准结论 V0.1

## 一、阶段结论

FLOW 中的 T3“将蒸馏结果转换为作者测试”和 T4“作者首次介入与迁移校准”已经在 V0.2 连续交互测试中共同完成。

四个优先机制均经过：

1. 当前小说人物与全新局部任务首测；
2. 作者原始判断；
3. 必要时一次有根因的局部修订；
4. 不同人物或任务的近迁移；
5. 更换关系形态或回应方式的远迁移；
6. G1—G7 反审计与连续字符污染检查。

## 二、候选结果

|来源机制|当前小说候选效果|作者路径|状态|
|---|---|---|---|
|M03 被问题激活的说明|背景只在当前问题需要时进入，并立刻改变操作或判断|A / A / A|validated_not_formalized|
|M04 目标—操作—反馈动作链|目标通过具体操作推进，反馈触发下一步，不堆装饰动作|A / A / A|validated_not_formalized|
|M07 功能性句长与断点|句长随观察和认知转向变化；主体切换必须被触发|A / C→A / A|validated_not_formalized|
|M02 以关系任务生成对白|人物声音受任务、利益、情绪、关系和交流方式共同约束|C→A / A / A|validated_not_formalized|

## 三、失败证据优先保留

- 008 原稿：认知修正后直接切换行动主体，人物被系统分配动作。
- 010 原稿：任务正确但关系和情绪被抽空，周睿退化为教师式指导者。

两项失败均经一次根因明确的局部修订后获 A。修订结果只确认对应边界有效，不把修订后的问答、物件和台词保存为模板。

## 四、权限边界

```yaml
T3_complete: true
T4_complete: true
candidate_count: 4
formalized_rule_count: 0
runtime_eligible: false
whole_chapter_rewrite_authorized: false
frozen_draft_modified: false
next_stage: T5
```

T5 应先选择第三章失败实例的小片段，将真实失败与四个候选机制对照并复验。不能因为 T3—T4 完成就直接把候选批量套入整章，也不能重新生成冻结 Draft。

