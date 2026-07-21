---
id: REPORT-T3-V0_2-M07-001
type: candidate_validation_report
status: validated_not_formalized
version: "0.1"
created: 2026-07-21
runtime_eligible: false
source_mechanism: M07
source_cases:
  - STYLE-TEST-T3-V0_2-COGNITIVE-007
  - STYLE-TEST-T3-V0_2-COGNITIVE-NEAR-008
  - STYLE-TEST-T3-V0_2-COGNITIVE-NEAR-008-R1
  - STYLE-TEST-T3-V0_2-COGNITIVE-FAR-009
---

# T3 V0.2 句长与认知转向验证结论 V0.1

## 一、作者结果

|层级|人物与任务|作者结果|
|---|---|---|
|首测|马木—马雯雯；搬家误判转为消杀准备|A|
|近迁移原稿|陈科—陈艾艾；冰箱损坏判断转为抽屉除冰|C|
|近迁移局部修订|补足陈艾艾进入任务的观察、确认和物件触发|A|
|远迁移|马木—陈艾艾；手机被人捡走判断转为可能留在公交车|A|

## 二、当前小说窄候选

> 人物可以根据连续可见或可核对的信息形成暂时判断；较长句负责把观察与生活经验接起来，较短信息只在新事实出现时切断上一判断，随后文本恢复普通句长和现场行动。

## 三、跨实例保持项

1. 暂时判断符合人物当下已有信息，不靠故意降智。
2. 事实修正由消杀设备、结冰抽屉或公交停靠规律支持。
3. 短信息只负责确认或转向，不承担机锋和胜负。
4. 修正后继续搬物、接水或联系终点站，不写“原来如此”。
5. 句长随认知任务变化，不把短、断、利落当统一风格。

## 四、近迁移失败新增的强制边界

认知修正后，系统不能直接把下一步行动切给另一个人物。

行动主体必须通过以下至少一项进入任务：

- 看见新的物件状态；
- 开口确认进度或分工；
- 接到对方当前要求；
- 收到刚发生的环境反馈。

008 原稿中陈艾艾从旁观直接切到端盆、扎袋和接水，因此获 C；R1 补入观察、询问、鱼袋松开和确认空盆位置后获 A。该失败证据优先于三次通过结论，不能删除。

## 五、失败边界

- 为反转隐藏人物已经看见的信息；
- 用漂亮反差或角色机锋完成纠正；
- 修正后写主题总结或解释人物偏见；
- 行动主体无观察、确认或反馈就突然接管任务；
- 固定复制“长观察—短问答—新事实”的段落外形。

## 六、状态决定

```yaml
current_novel_candidate: validated
formalized: false
runtime_eligible: false
draft_public_authorized: false
next_validation: M02_voice_from_relationship_task
```
