---
id: PLAN-HANDOFF-001
type: skill_plan
module: source_draft
status: confirmed
version: "1.0"
updated: 2026-07-22
---

# 前章承接最小接口

## 目标

`previous_chapter_handoff` 只为防止新章丢失上一章结尾的必要状态。它是 Draft 生成时的内部接口，不是用户表单、独立创作产物或新增前台步骤。

## 最小字段

```yaml
previous_chapter_handoff:
  source_chapter: 上一章正式版本或路径
  continuation_anchor: 时间、地点、在场人物和最后动作
  must_carry: []
  handoff_question:
```

- `source_chapter`：防止读取错误版本。
- `continuation_anchor`：用一句话说明新章从何时、何地、哪些人和哪个动作继续。
- `must_carry`：只列下一章不能凭空消失的未完成状态，例如待回应对话、关键物件、情绪余温或现实压力；没有则为空，不要求分类齐全。
- `handoff_question`：上一章带给读者的一个主要问题；没有明确问题时允许为空。

## 默认执行

开始生成下一章时，由 LLM 从上一章正式正文内部提取以上四项并直接用于生成。只有出现正式版本冲突、承接内容与用户新目标冲突或无法可靠判断时，才询问用户。

当前不增加 Python、缓存、独立运行记录或用户确认步骤。若真实测试以后证明重复读取造成明显 Token 浪费，再单独评估是否把文件定位、缓存或格式校验交给轻量 Harness。

## 边界

- 不把四个字段继续拆成固定子表；
- 不要求每项都有内容；
- 不把具体续写桥段写入交接信息；
- 不在当前阶段修改或接入 Draft 测试 Skill。
