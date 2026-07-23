---
id: SKL-REGISTRY-MODULES
type: skill_module_registry
system: skill_control
status: active
version: "0.2"
created: 2026-07-22
updated: 2026-07-22
---

# Skill 模块注册表

本文件只登记模块边界、入口和运行状态，不复制模块内部规则。模块是否登记、控制单元是否存在、测试 Skill 是否已接入是三件不同的事。

## 当前模块

|模块 ID|模块|入口|定位地图|阶段|运行时状态|
|---|---|---|---|---|---|
|`MOD-SOURCE-DRAFT`|源头 Draft|`../03_正文生成/01_源头Draft/00_模块总控/MOD-SOURCE-DRAFT_源头Draft模块说明.md`|`../03_正文生成/01_源头Draft/00_模块总控/MAP-SOURCE-DRAFT-001_生产与问题定位地图.md`|首个模块化样板建设中|未接入测试 Skill|

## 状态解释

- `样板建设中`：可以建立目录、索引、候选控制单元和测试设计，但不代表规则已经晋升。
- `未接入测试 Skill`：当前 `.codex-tmp/skills/generate-chapter-prose-draft/` 不读取本模块，不能把模块文件当作现行 Skill 行为说明。
- 模块只有通过真实章节验证、用户确认和治理门禁后，才可进入正式化或安装阶段。

## 注册规则

新增模块时只登记稳定的问题域，并至少给出：模块入口、定位地图、需求来源、控制单元索引、当前阶段和运行时状态。没有证据时不得把方案、经验或方法论登记成已生效控制单元。
