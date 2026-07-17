---
id: ITERATION-P00-C03-PUBLIC-01
type: draft_to_public_module_iteration
system: author_aesthetic_public_reconstruction_test
status: implementation_complete
version: "1.1"
title: 第三章 Draft→Public 模块迭代记录
created: 2026-07-16
updated: 2026-07-16
unit: P00
chapter: C03
source_task: TASK-P00-C03-DRAFT-TO-PUBLIC-01
rel:
  - 测试文本/正文测试/第一单元/skills第三章测试/第三次测试/10-表达重构候选方法-第3章
tags:
  - module-iteration
  - public-skill
  - architecture-decision
---

# 第三章 Draft→Public 模块迭代记录

## 一、ASK-I 解决记录

|字段|内容|
|---|---|
|节点|ASK-I|
|作者选择|A 推荐边界包|
|结果|resolved|
|确认内容|十条方法可跨场景测试；旁白只处理重复结论；混合基调必须指定第一基调；L3／L4 可改变读者获知顺序但不改变事实发生顺序|
|后续许可|进入 T4 Skill 承载决策|
|仍然禁止|跳过正式迁移、跳过 Skill 实施、直接生成整章 Public|

## 二、T4 Public Skill 承载决策

### 2.1 方案比较

|方案|现有职责|与 Public 的冲突|结论|
|---|---|---|---|
|A 新建 `reconstruct-draft-to-public`|尚不存在，可按 V0.3 定义独立职责|无既有职责冲突；增加一个专用 Skill|selected|
|B 扩展 `revise-draft-common-rules`|只处理最小失败场景或 beat，明确不是默认整章修订链|Public 需要全章冻结、九片段审计、L0—L4、全章装配和三类门禁，会破坏局部修复边界|rejected|
|C 扩展 `generate-chapter-prose-draft`|负责上游材料驱动的首次完整 Draft 生成|会混淆首次生成与 Draft→Public 二阶段表达重构，并削弱污染隔离|rejected|

### 2.2 决策

选择方案 A：新建独立 `reconstruct-draft-to-public` Skill。

没有触发 ASK-J，原因：

1. 现有局部修复 Skill 已明确禁止承担默认整章修订；
2. 现有 Draft Skill 已明确承担首次完整生成；
3. Public 的冻结表、作者介入地图、L0—L5、片段重构卡和三类门禁形成独立完整职责；
4. 将 Public 并入 B 或 C 都会产生已经能够由现有边界自动裁决的职责冲突。

### 2.3 新 Skill 最小职责

- 冻结 Input Draft 与污染隔离；
- 建立合格层冻结表和作者介入地图；
- 按功能片段审计并选择 L0—L4；
- 读取正式审美库、表达重构方法库和必要喜剧方法；
- 将审美原则转换为片段重构任务；
- 执行 L2 句式重写、L3 段落重组和 L4 片段表达重构；
- 运行事实与边界、作者审美、修改深度三类门禁；
- 只重做失败片段，再完成全章装配；
- 遇到 ASK-A—ASK-J 时立即停止。

### 2.4 明确不承担

- 首次 Draft 生成；
- 细纲、执行包、人物意图或场景事实修复；
- 未经作者批准的 L5；
- 作者目标稿模仿；
- 将失败 Public 当作新版本底稿；
- 自动回写未经作者确认的审美规则。

## 三、实施结果

作者确认安装位置：项目本地。

已创建：

- `.codex-tmp/skills/reconstruct-draft-to-public/SKILL.md`
- `.codex-tmp/skills/reconstruct-draft-to-public/references/public-workflow.md`
- `.codex-tmp/skills/reconstruct-draft-to-public/references/quality-gates.md`
- `System_alpha/04_Skill系统/03_正文生成/表达重构方法论库/README_表达重构方法论库.md`
- `System_alpha/04_Skill系统/03_正文生成/表达重构方法论库/LIB-EXPRESSION-P0_表达重构方法论库.md`
- `System_alpha/04_Skill系统/03_正文生成/表达重构方法论库/CHANGELOG_表达重构方法论库.md`

同步更新：

- `设计流程与方案/INDEX_设计流程与方案.md`
- `07-TASK-Draft-to-Public测试与迭代-第3章.md`
- `CURRENT_作者审美链工作状态.md`

当前状态：`implementation_complete`

下一步：验证完成后进入 T5 高风险片段冒烟测试。

## 四、验证结果

|检查|结果|
|---|---|
|Skill Creator `quick_validate.py`|pass：`Skill is valid!`|
|Skill frontmatter|pass：仅包含 `name` 与 `description`|
|Skill TODO 残留|pass：无 TODO|
|正式方法条目数量|pass：10|
|每条方法等级、机制、失败边界与深度检查|pass：10／10|
|设计总索引可达|pass|
|CURRENT 可续接|pass|
|正式库是否包含作者原句或第三章成品方案|pass：未包含|

验证说明：本机 Python 缺少校验脚本依赖的 `PyYAML`，使用只服务本次前置字段解析的临时本地 shim 运行官方校验脚本；验证完成后 shim 已删除，未成为项目依赖。

T4 最终状态：`passed`

## 五、T5.1 F04 冒烟测试

|字段|内容|
|---|---|
|测试产物|`11-S3盘问片段表达重构测试.md`|
|修改等级|L4|
|主方法|EXPRESSION-P0-010|
|辅助方法|EXPRESSION-P0-001、002|
|第一基调|父女关系压力|
|作者介入|未触发|
|事实与边界门禁|pass|
|作者审美门禁|pass|
|修改深度门禁|pass|
|测试结论|passed|

### 问题记录

|字段|内容|
|---|---|
|问题 ID|ISSUE-C03-PUBLIC-005|
|发现阶段|T5.1|
|片段 ID|F04|
|问题表现|原片段由标准问答、风险清单、强角色连续胜利和旁白结论链支配|
|问题层级|对白／段落／表达路径／审美决策|
|修改等级|L4|
|主归因模块|MOD-KB-EXPRESSION|
|次要影响模块|MOD-SKILL-PUBLIC|
|是否需要作者介入|no|
|拟修改文件|无|
|修改内容|现有正式方法和 Skill 已足以完成重构，不新增规则|
|复验对象|F04 原失败片段|
|复验结果|pass|
|是否回写 CURRENT／INDEX|CURRENT yes；INDEX no|

T5.1 未发现知识缺失、Skill 漏执行或模板记录缺口，因此不进行无证据系统迭代。
