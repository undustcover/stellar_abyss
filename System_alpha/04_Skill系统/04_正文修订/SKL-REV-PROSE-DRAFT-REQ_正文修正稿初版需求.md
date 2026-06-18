---
type: skill_requirement
system: prose_revision
status: deprecated
title: 正文草稿到修正稿 Skill 初版需求（已废弃）
skill_group: revise-draft
created: 2026-06-18
deprecated: 2026-06-18
tags:
  - prose-revision
  - deprecated
---

# 正文草稿到修正稿 Skill 初版需求（已废弃）

## 一、废弃结论

经第三章修订测试和前两章对照复盘，正文质量的关键不在后置的“去 AI 化、文风校准、对白幽默化”顺序，而在生成前是否完成分场景导演。

因此独立的整章后处理流程废弃。以下三个测试 skill 已从 `.codex-tmp/skills` 删除：

```text
revise-draft-de-ai
revise-draft-style-calibration
revise-draft-dialogue-humor
```

对应能力并入前三个生成 skill：

```text
generate-chapter-detail-outline
-> generate-chapter-execution-pack
-> generate-chapter-prose-draft
```

## 二、新默认链路

正文默认链路调整为：

```text
章节细纲：锁读者体验曲线、场景导演目标
    ↓
章节执行包：分场景导演表、A/B/C 场景等级、字数预算
    ↓
正文生成：按导演表一次生成，内置去 AI 感、文风一致性、对白幽默
```

重点不是“生成草稿后再修漂亮”，而是生成前先判断每场要让读者怎么读：期待什么、误会什么、笑在哪里、压力在哪里、信息怎样释放、结尾钩子怎样留下。

## 三、返修保险

生成稿失败时，只保留轻量返修保险：

```text
草稿诊断 -> 定位失败场景 -> 分场景再导演 -> 正文局部替换
```

该流程只处理失败场景，不作为默认整章后处理链路。若只有一场读者体验失败，只替换该场或必要相邻段落；不得默认整章重写。

当前保留的测试区边界 skill：

```text
.codex-tmp/skills/revise-draft-common-rules
```

其职责已改为失败场景诊断和局部替换边界参考，不再协调三个独立修订 skill。

## 四、废弃原因

旧流程的问题：

1. 后置修订容易退化成句面润色，如长句变短、短句变长、替换连接词。
2. 三个修订 skill 会反复消费 token，却不一定改变读者体验。
3. 对网络小说来说，关键质量来自期待、误会、反差、冲突、节奏和钩子，而不是后置统一文风。
4. 如果生成前没有锁定读者体验路径，后面再修容易变成整章重写或拼接。

新流程的目标：

1. 把读者体验前置到章节细纲。
2. 把去 AI 感、文风、对白幽默前置到章节执行包的分场景导演表。
3. 让正文生成第一次就按场景目标写出来。
4. 用 A/B/C 场景等级和字数预算控制 token 与正文篇幅。
5. 只在失败场景上做局部替换。

## 五、后续处理

后续不再维护独立整章修订 skill 组。若第三章或后续章节继续暴露“草稿与修订稿几乎无差别”的问题，应优先回写：

1. `generate-chapter-detail-outline` 的读者体验曲线和场景导演目标；
2. `generate-chapter-execution-pack` 的分场景导演表、场景等级和字数预算；
3. `generate-chapter-prose-draft` 的按导演表一次生成和局部替换建议。
