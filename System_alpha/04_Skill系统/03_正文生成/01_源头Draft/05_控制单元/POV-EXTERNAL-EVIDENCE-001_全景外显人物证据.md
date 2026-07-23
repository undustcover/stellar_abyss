---
id: POV-EXTERNAL-EVIDENCE-001
type: control_unit
module: source_draft
status: candidate
version: "0.1"
updated: 2026-07-22
trigger: panoramic_scene_with_characters
scope: scene_or_bounded_section
priority: high
freedom: hard
conflicts_with: []
depends_on: []
runtime_binding: none
---

# 全景外显人物证据

## 目标

让全景客观场景中的人物仍以可观察、可判断的方式存在，避免宏大叙述退化为事件说明或人物名册。

## 触发条件

启用 `POV-PANORAMIC-001`，且场景中人物的压力、关系位置、选择或代价对当前故事重要时启用。

## 控制动作

按当前境况选择少量有信息价值的外显证据，例如：

- 站位、移动、动作中断或动作失误；
- 表情、呼吸、视线落点与身体反应；
- 语言、语气、音量、停顿、改口与沉默；
- 对关键物件的拿、放、藏、递、丢或保护；
- 与他人的距离、服从、对抗、回避、保护或协作；
- 公开选择及其可见后果。

证据应帮助读者判断人物承受的压力、处境、关系位置或可能选择，但不替读者下心理结论。

## 禁止越界

- 不把外显证据改写成确定的内心解释；
- 不平均给所有人物分配细节；
- 不按摄像机清单逐项记录无关动作；
- 不规定必须使用某个动作、物件或身体反应。

## 创作自由

具体证据、密度、落点和读者可推断程度由生成者根据场面选择。允许留下多义性，只要人物没有从故事中消失。

## 成功证据

- 至少一个核心人物通过外显证据获得可感处境；
- 证据与当前事件、压力或关系直接相关；
- 读者可以推断，但文本没有代替读者确定内心；
- 人物细节没有遮蔽全景段落的组织中心。

## 失败码

- `CHARACTER_BECAME_INVENTORY`：人物仅作为姓名或位置被罗列；
- `EVIDENCE_BECAME_MIND_READ`：外显动作被直接翻译为确定心理；
- `CAMERA_CHECKLIST`：细节平均、机械且不服务当前境况；
- `EVIDENCE_OVERLOAD`：人物细节破坏全景组织中心。

## 当前运行状态

本单元尚未接入 Draft 测试 Skill，只作为样板候选供后续测试方案引用。
