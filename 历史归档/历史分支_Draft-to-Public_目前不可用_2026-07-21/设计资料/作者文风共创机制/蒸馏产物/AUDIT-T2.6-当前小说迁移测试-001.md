---
id: AUDIT-T2_6-TEST-001
type: internal_test_preflight
status: pass
version: "0.1"
created: 2026-07-21
author_visible: false
test_case: STYLE-TEST-T2_6-001
---

# T2.6 当前小说迁移测试 001 反审计

## 输入

|字段|内容|
|---|---|
|人物|马木、马雯雯|
|关系来源|两人角色卡中的堂兄妹与前期轻视关系|
|当前任务|处理电梯检修时无法直接搬运的二手书桌|
|事实变化|从准备整桌搬运，转为现场拆卸|
|正史状态|非正史测试，不写回剧情|
|隔离|人物台词包成品表达、Draft/Public、第三章冻结 Draft、作者改写、参考原句|

## 门禁结果

|门禁|结果|说明|
|---|---|---|
|G1 都市标准说明文|PASS after rewrite|拆除马木三项并列汇报；配送限制由被催问后的普通回应与现场状态呈现|
|G2 人物模板展示|PASS after rewrite|删除背心外露和工作电话恰好打入，不主动展示落魄或职场压力|
|G3 乡土语材换皮|PASS|任务、关系阻力和物件系统均不同于 T2.5 两轮|
|G4 默认 AI 句式回落|PASS after rewrite|删除“补拍给谁看”式机锋；无对称金句、漂亮反差或事实讲透后的收束|
|G5 人物越界|PASS|马木只处理现场，不展示专业知识；马雯雯未提前改观|
|G6 装饰动作|PASS|签收、扶桌、查看螺丝、借工具均改变现场操作|
|G7 污染|PASS with disclosure|检索阶段暴露人物台词包部分内容，但正文未调用其成品表达；与参考原文、台词包、冻结 Draft 的连续 8/10/12 字符重合均为 0|

## 决定

```yaml
decision: PASS
blocking_gate: null
author_test_file: TEST-T2.6-当前小说语材迁移-001.md
```
