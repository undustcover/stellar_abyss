---
id: ITERATION-P00-C03-PUBLIC-01
type: draft_to_public_module_iteration
system: author_aesthetic_public_reconstruction_test
status: system_public_frozen
version: "1.6"
title: 第三章 Draft→Public 模块迭代记录
created: 2026-07-16
updated: 2026-07-17
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

## 六、T5.1 作者复核与修订

F04 首版虽通过既有门禁，但作者复核确认其与全章轻喜底色不符：陈艾艾过于急躁，马木成为严肃问题解决机器，陈科缺少“不知被骗而认真自洽”的滑稽与尴尬。

处理结果：

- 撤销 F04 V1.0 的 `passed`；
- 在相同事实与边界下重新生成 V1.1；
- 第一基调调整为生活化轻喜；
- 陈科改为服软解释并持续自洽；
- 马木改用现实生活例子作幽默对照；
- 陈艾艾改为冷硬、短句、少动作；
- 作者已确认修订版通过；
- F04 三类门禁最终状态均为 `pass`。

## 七、T5.2 F05—F06 冒烟测试

|字段|内容|
|---|---|
|测试产物|`12-S4工作人员回拉表达重构测试.md`|
|修改等级|L4|
|主方法|EXPRESSION-P0-010|
|辅助方法|EXPRESSION-P0-006、011（作者校准后由 003 调整）|
|第一基调|生活化轻喜|
|次级读感|正常服务产生的低危不安|
|事实与边界门禁|pass|
|修改深度门禁|pass|
|作者审美门禁|pass；作者确认|
|当前状态|passed|

## 八、T5.2 去 AI 化作者校准与系统回写

作者对 F05—F06 连续确认三类退化：

1. 旁白同时说明人物做了什么、没做什么和作者意图，现场动作失去证明作用；
2. 马雯雯作为限知 POV 只有看见过程，缺少能绑定读者视界的即时参与；
3. “忘东西有面子／顺手铺椅子”等联想可以换给任何人物，不来自马雯雯的社畜经验，也未紧扣当前服务场景。

主归因模块：`MOD-KB-EXPRESSION`。

系统修改：

- 新增正式方法 `EXPRESSION-P0-011 限知 POV 参与链与人物专属联想`；
- 将方法写入 Public Skill 常见问题路由；
- 在作者审美门禁新增说明式旁白、POV 参与、换人测试和场景关联检查；
- F05—F06 的辅助方法由 `003、006` 调整为 `006、011`；
- 不修改 Draft 生成流程，该链路由作者另行处理。

F05—F06 正文 V1.3 已完成三步校准并获作者确认；三类门禁最终状态均为 `pass`。

## 九、Public 去 AI 化回流 Draft 预防

作者确认 Public 去 AI 化方法需要进入 Draft 生成流程，并要求建立持续同步机制。

架构判断：`可行，采用单一权威源 + Draft 预防映射`。

已实施：

- 正式方法 `EXPRESSION-P0-011` 增加 `方法版本 1.0` 与 `Draft预防映射: yes`；
- 新建 Draft 映射 `public-derived-anti-ai-prevention.md`；
- Draft Skill 每次生成前必须比较 `方法 ID@版本`；
- 版本失配标记 `SYNC-DRAFT-DEAI-001`，不得静默继续；
- 同步 Draft 导演层规则、质量门禁、正式交付模板和本地模板镜像；
- Draft 生成备注新增映射版本、同步状态、说明式旁白、POV 参与、换人测试与场景关联字段；
- 正式方法库 README 和 CHANGELOG 增加跨阶段同步协议；
- 设计总索引增加映射入口。

职责边界：Draft 只执行预防版，不搬入 Public 的 L3／L4 事后重构；同步只迁移抽象规则，不读取或复用 Public 成品正文。

下一复验：使用下一次干净 Draft 生成或专门 Draft 冒烟测试，验证同类问题是否在首次生成时被拦截。

## 十、T6 问题迭代与原片段复验汇总

### 10.1 F05—F06 问题记录

|字段|内容|
|---|---|
|问题 ID|ISSUE-C03-PUBLIC-006|
|发现阶段|T5.2|
|片段 ID|F05—F06|
|问题表现|说明式旁白讲完动作、未发生动作和作者意图；马雯雯只充当摄像机；通用比喻和内心判断可任意换人|
|问题层级|旁白／POV／人物声音／比喻／读者接收|
|修改等级|L4 内局部复验|
|主归因模块|MOD-KB-EXPRESSION|
|次要影响模块|MOD-SKILL-PUBLIC；MOD-SKILL-DRAFT-QUALITY；MOD-SKILL-DRAFT-CHECK|
|是否需要作者介入|yes；生成后作者审美校准，不触发 L5|
|修改内容|新增 EXPRESSION-P0-011；同步 Public Skill 门禁；将抽象预防规则回流 Draft Skill|
|复验对象|F05—F06 原失败表达|
|复验版本|V1.3|
|复验结果|pass；作者确认|
|是否回写 CURRENT／INDEX|yes／yes|

### 10.2 两组原片段复验

|片段|最终版本|事实与边界|作者审美|修改深度|作者确认|
|---|---|---|---|---|---|
|F04|`11-S3盘问片段表达重构测试.md` V1.1 正文|pass|pass|pass|yes|
|F05—F06|`12-S4工作人员回拉表达重构测试.md` V1.3 正文|pass|pass|pass|yes|

### 10.3 模块同步核对

|模块|本轮结果|状态|
|---|---|---|
|MOD-KB-EXPRESSION|新增 `EXPRESSION-P0-011@1.0`，含识别信号、步骤、边界、换人测试和场景关联检查|synced|
|MOD-SKILL-PUBLIC|增加 011 路由、说明式旁白门禁、POV 参与门禁和换人测试|synced|
|MOD-SKILL-DRAFT-QUALITY|加入首次生成预防规则|synced|
|MOD-SKILL-DRAFT-CHECK|加入说明式旁白、POV 参与、换人和场景关联检查|synced|
|Draft 预防映射|建立 `EXPRESSION-P0-011@1.0` 版本同步和 `SYNC-DRAFT-DEAI-001` 失配协议|current|
|正式 Draft 模板／本地镜像|增加映射版本、同步状态和风险字段|synced|
|表达库 CHANGELOG／README|增加条目记录与 Public→Draft 同步协议|synced|
|设计 INDEX|增加 Draft 预防映射入口|synced|
|CURRENT|阶段和下一步同步|synced|

### 10.4 T6 结论

- F04 与 F05—F06 均已使用相同冻结事实回原片段复验；
- 两组冒烟测试三类门禁全部通过并获作者确认；
- 失败问题均有唯一主归因模块；
- 新方法、执行门禁、Draft 预防、版本同步、CHANGELOG、INDEX 与 CURRENT 均已闭环；
- T6 状态：`passed`；
- 下一步：进入 T7，生成新的整章 `14-System Public V1.1-第3章.md` 与完整测试记录；不得覆盖失败 V1。

## 十一、T7 整章生成与装配复核

### 11.1 产物

- `14-System Public V1.1-第3章.md`
- `15-Draft-to-Public测试记录-第3章.md`

### 11.2 装配结果

|范围|处理|结果|
|---|---|---|
|F01—F03|按 L2—L4 重写开场、父女冲突和风险信息入口|pass|
|F04|装配作者确认的 V1.1 正文|pass；逐字符一致|
|F05—F06|装配作者确认的 V1.3 正文|pass；逐字符一致|
|F07—F09|压缩配角、用行动兑现现实方案、重构章末认知运动|pass|
|全章接口|统一轻喜基调、人物声音、POV、节奏与片段衔接|pass|

### 11.3 三类门禁

|门禁|结果|
|---|---|
|事实与边界|pass|
|作者审美|pass|
|修改深度|pass|

T7 未发现需要回写正式库的新问题，也未触发 ASK-A—ASK-H。System Public V1.1 状态为 `system_public_frozen`；下一步进入 T8 作者 V2 与知识回灌。
