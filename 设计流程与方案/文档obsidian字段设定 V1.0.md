# 小说写作系统架构需求文档 V1.1

## 一、版本定位

本版本为小说写作系统架构需求文档 V1.1。

V1.1 在 V1.0 的系统架构基础上，进一步明确 Obsidian 的落地规范，重点固化以下内容：

```text
1. Obsidian 一级文件夹结构
2. 文件命名规则
3. YAML 字段规范
4. 双链关系使用规则
5. 文件夹、YAML、Database、正文之间的职责边界
```

V1.1 不改变 V1.0 的四大核心系统定位：

```text
叙事系统 = 正文生产线
设定系统 = 世界规则库
事件数据库 = 世界时间轴事实库
Skill系统 = LLM创作控制系统
```

V1.1 的核心修正是：

```text
YAML 不承载复杂内容，只做简洁索引。
复杂设定、关系说明、事件过程、写作规则，统一放在 Markdown 正文中。
文件夹服务作者理解。
YAML 和 Database 服务 Skill、脚本、LLM 精确定位。
双链服务语义关系说明。
```

---

# 二、系统总结构

## 2.1 一级文件夹结构

Obsidian 根目录只设置五个一级文件夹：

```text
Novel_System/
├── 00_总控台/
├── 01_叙事系统/
├── 02_设定系统/
├── 03_事件数据库/
└── 04_Skill系统/
```

不得在根目录额外增加模板库、归档库、废稿库、素材库等一级文件夹。

如需模板、归档、废稿、数据库视图，应分别放入对应系统内部。

例如：

```text
00_总控台/02_模板库/
01_叙事系统/99_叙事归档/
02_设定系统/99_设定归档/
03_事件数据库/99_事件归档/
04_Skill系统/99_Skill归档/
```

---

## 2.2 文件夹职责

文件夹只服务作者理解和人工浏览。

文件夹不承担最终分类职责。

文件最终分类应由以下内容确定：

```text
文件 ID
YAML 字段
Database 视图
type 字段
system 字段
```

也就是说：

```text
人看文件夹。
Skill 看 YAML。
脚本看 Database。
LLM 同时看 YAML、正文和双链。
```

---

## 2.3 文件唯一性原则

同一个对象只能有一个正式文件。

例如：

```text
CHR-0001_马木.md
```

只能作为马木的唯一正式人物卡。

不得再建立：

```text
马木_主角设定.md
马木_现实线.md
马木_P0设定.md
```

如果马木在不同阶段有变化，应在同一个人物卡正文中增加阶段内容，或通过人物经历线、事件卡、章节文件关联说明。

---

# 三、YAML 总规范

## 3.1 YAML 的定位

YAML 是 Obsidian 文件的简洁索引层。

YAML 的作用是帮助 Skill、Database、脚本和 LLM 快速判断：

```text
这是什么文件？
属于哪个系统？
当前状态是什么？
标题是什么？
与哪些核心对象有关？
是否有别名？
适用于哪个单元、章节或任务？
```

YAML 不负责保存复杂内容。

以下内容不得放入 YAML：

```text
人物性格详细说明
人物说话方式详细说明
事件完整过程
能力机制详细解释
章节节奏设计
正文写作规则
信息释放细节
复杂因果链
人物关系解释
```

这些内容应放在 Markdown 正文中。

---

## 3.2 YAML 长度标准

普通文件 YAML 建议控制在 7—10 行。

复杂文件原则上不超过 12 行。

YAML 字段必须简洁，字段名必须稳定。

---

## 3.3 通用 YAML 字段

所有关键文件默认使用以下字段：

```yaml
id:
type:
system:
status:
title:
rel:
tags:
```

其中：

|字段|含义|必填|
|---|---|---|
|`id`|文件唯一 ID|必填|
|`type`|文件类型|必填|
|`system`|所属系统|必填|
|`status`|文件状态|必填|
|`title`|文件标题|必填|
|`rel`|核心关联对象 ID|可选|
|`tags`|标签|可选|

---

## 3.4 可选 YAML 字段

只有在 Database 筛选确实需要时，才增加可选字段。

|字段|适用对象|用途|
|---|---|---|
|`alias`|所有文件|记录别名、旧称、简称|
|`unit`|叙事文件|标记 P00、P01 等单元|
|`chapter`|章节文件|标记 C01、C02 等章节|
|`time`|事件文件|标记世界时间|
|`task`|Skill 文件|标记 Skill 任务类型|
|`owner`|能力、道具、组织关系文件|标记归属对象|

---

## 3.5 字段语言规则

`system` 字段统一使用英文。

```yaml
system: control
system: narrative
system: setting
system: event
system: skill
```

`type` 字段统一使用英文。

```yaml
type: index
type: character
type: event
type: chapter_outline
type: detail_outline
type: draft
type: revision
type: skill
type: prompt
```

中文分类信息放入 `tags` 或 Markdown 正文。

---

## 3.6 rel 字段规则

`rel` 字段只放对象 ID，不放 Obsidian 双链。

正确：

```yaml
rel: [CHR-0001, EVT-0002, POW-0002]
```

不建议：

```yaml
rel:
  - "[[CHR-0001_马木]]"
  - "[[EVT-0002_陈科被高端分享局诈骗事件]]"
```

原因：

```text
ID 稳定。
文件名可能变化。
YAML 应服务检索，不承担语义解释。
```

关系性质应放入 Markdown 正文，并使用 Obsidian 双链说明。

示例：

```markdown
## 关联说明

- [[CHR-0001_马木]]：事件介入者，被反咬后承担后果。
- [[EVT-0002_陈科被高端分享局诈骗事件]]：P0 主线崩塌事件。
- [[POW-0002_任战-入席]]：事件背后的隐藏诱导机制。
```

---

## 3.7 alias 字段规则

`alias` 为可选字段。

适用于存在多个称呼、简称、旧称、误称的文件。

示例：

```yaml
alias: [六合集市APP, 集市APP, APP]
```

没有别名的文件可以不写 `alias`。

---

## 3.8 status 字段枚举

`status` 建议统一使用以下枚举：

```text
idea        想法
draft       草稿
review      待审核
active      生效中
confirmed   已确认
deprecated  已废弃
archived    已归档
```

---

# 四、文件命名总规范

## 4.1 基础命名规则

普通文件统一采用：

```text
ID_标题.md
```

示例：

```text
CHR-0001_马木.md
EVT-0002_陈科被高端分享局诈骗事件.md
POW-0002_任战-入席.md
SKL-WR-001_正文生成总规则.md
```

文件名由两部分组成：

```text
唯一 ID + 可读标题
```

ID 用于稳定识别。

标题用于作者阅读。

---

## 4.2 章节文件命名规则

章节相关文件不建议在文件名中写章节标题。

建议采用：

```text
NAR-P00-C01_章节大纲.md
OUT-P00-C01_章节细纲.md
DRAFT-P00-C01_正文.md
REV-P00-C01_修订记录.md
```

章节标题放入 YAML 的 `title` 字段和正文中。

原因：

```text
章节标题经常变化。
章节文件名应保持稳定。
双链和脚本不应因标题修改而频繁失效。
```

---

## 4.3 文件名中的编号规则

### 叙事系统编号

```text
NAR-BOOK        全书总纲
NAR-B01         分部大纲
NAR-B01-V01     分卷大纲
NAR-P00         单元大纲
NAR-P00-C01     章节大纲
OUT-P00-C01     章节细纲
DRAFT-P00-C01   正文
REV-P00-C01     修订记录
```

### 设定系统编号

```text
CHR-0001        人物
ORG-0001        组织
LOC-0001        地点
ITM-0001        道具
TEC-0001        技术
POW-0001        能力
TERM-0001       术语
WLD-APP         世界观核心条目
```

### 事件数据库编号

```text
EVT-0001        大事件
EXP-CHR-0001    人物经历线
ACT-ORG-0001    组织行动线
CAU-P00         因果链
TIME-REAL-2026  世界时间轴
```

### Skill 系统编号

```text
SKL-CALL-001    资料调用 Skill
SKL-OUT-001     大纲生成 Skill
SKL-WR-001      正文生成 Skill
SKL-REV-001     正文修订 Skill
SKL-CHK-001     一致性校验 Skill
PRM-001         Prompt 模板
```

---

# 五、00_总控台设计

## 5.1 系统定位

总控台是系统入口。

总控台不存放小说正文内容，不存放具体设定，不存放事件详情。

总控台负责：

```text
系统入口
当前进度
待处理问题
Database 视图
模板索引
归档索引
```

---

## 5.2 文件夹结构

```text
00_总控台/
├── 00_首页/
│   ├── SYS-INDEX_系统总览.md
│   ├── SYS-DASH_当前进度.md
│   └── SYS-TODO_待处理问题.md
│
├── 01_Database视图/
│   ├── DB-CHAR_人物数据库.md
│   ├── DB-EVT_事件数据库.md
│   ├── DB-NAR_叙事数据库.md
│   ├── DB-SET_设定数据库.md
│   └── DB-SKL_Skill数据库.md
│
├── 02_模板库/
│   ├── TPL-CHR_人物卡模板.md
│   ├── TPL-EVT_事件卡模板.md
│   ├── TPL-NAR-CH_章节大纲模板.md
│   ├── TPL-DRAFT_正文模板.md
│   └── TPL-SKL_Skill模板.md
│
└── 99_归档索引/
    └── SYS-ARCHIVE_归档索引.md
```

---

## 5.3 总控台 YAML 示例

```yaml
id: SYS-INDEX
type: index
system: control
status: active
title: 系统总览
tags: [总控台]
```

---

# 六、01_叙事系统设计

## 6.1 系统定位

叙事系统是正文生产线。

叙事系统负责：

```text
总纲
分部大纲
分卷大纲
单元大纲
章节大纲
章节细纲
正文
修订记录
信息释放
伏笔回收
读者体验设计
```

叙事系统使用 B / V / P / C 等叙事结构编号。

---

## 6.2 文件夹结构

```text
01_叙事系统/
├── 00_叙事总控/
│   ├── NAR-INDEX_叙事系统总览.md
│   ├── NAR-TIME_叙事结构轴.md
│   ├── NAR-INFO_信息释放表.md
│   └── NAR-FORESHADOW_伏笔回收表.md
│
├── 01_全书/
│   └── NAR-BOOK_星渊总纲.md
│
├── 02_分部/
│   └── B01_六合集市/
│       └── NAR-B01_第一部大纲.md
│
├── 03_分卷/
│   └── B01_V01_六合集市/
│       └── NAR-B01-V01_第一卷大纲.md
│
├── 04_单元/
│   └── P00_命运的馈赠/
│       └── NAR-P00_命运的馈赠单元纲.md
│
├── 05_章节/
│   └── P00_命运的馈赠/
│       ├── C01/
│       │   ├── NAR-P00-C01_章节大纲.md
│       │   ├── OUT-P00-C01_章节细纲.md
│       │   ├── DRAFT-P00-C01_正文.md
│       │   └── REV-P00-C01_修订记录.md
│       └── C02/
│           ├── NAR-P00-C02_章节大纲.md
│           ├── OUT-P00-C02_章节细纲.md
│           ├── DRAFT-P00-C02_正文.md
│           └── REV-P00-C02_修订记录.md
│
└── 99_叙事归档/
```

---

## 6.3 章节大纲 YAML

```yaml
id: NAR-P00-C01
type: chapter_outline
system: narrative
status: draft
title: 我那一事无成的堂哥
unit: P00
chapter: C01
rel: [CHR-0001, CHR-0002, EVT-0001]
tags: [P00, C01, 章节大纲]
```

---

## 6.4 章节细纲 YAML

```yaml
id: OUT-P00-C01
type: detail_outline
system: narrative
status: draft
title: 我那一事无成的堂哥
unit: P00
chapter: C01
rel: [NAR-P00-C01, CHR-0001, EVT-0001]
tags: [P00, C01, 章节细纲]
```

---

## 6.5 正文 YAML

```yaml
id: DRAFT-P00-C01
type: draft
system: narrative
status: draft
title: 我那一事无成的堂哥
unit: P00
chapter: C01
rel: [NAR-P00-C01, OUT-P00-C01]
tags: [P00, C01, 正文]
```

---

## 6.6 修订记录 YAML

```yaml
id: REV-P00-C01
type: revision
system: narrative
status: active
title: C01修订记录
unit: P00
chapter: C01
rel: [DRAFT-P00-C01]
tags: [P00, C01, 修订]
```

---

## 6.7 叙事文件正文建议结构

章节大纲正文建议包括：

```markdown
## 本章功能

## 章节目标

## 出场人物

## 相关事件

## 信息释放

## 伏笔与回收

## 读者奖励

## 结尾钩子

## 禁止事项
```

章节细纲正文建议包括：

```markdown
## 场景列表

## 场景一

## 场景二

## 场景三

## 节奏安排

## 对话重点

## 情绪推进

## 结尾处理
```

正文文件建议包括：

```markdown
## 调用依据

- 章节大纲：[[NAR-P00-C01_章节大纲]]
- 章节细纲：[[OUT-P00-C01_章节细纲]]

## 正文

正文内容写在这里。
```

---

# 七、02_设定系统设计

## 7.1 系统定位

设定系统是世界规则库。

设定系统负责：

```text
人物
组织
地点
世界观
能力
道具
技术
种族
文明
术语
信息暴露限制
禁用设定
```

设定系统不负责章节节奏，不负责正文安排。

---

## 7.2 文件夹结构

```text
02_设定系统/
├── 00_设定总控/
│   ├── SET-INDEX_设定系统总览.md
│   ├── SET-RULE_设定优先级.md
│   ├── SET-EXPOSE_信息暴露规则.md
│   └── SET-CONFLICT_设定冲突记录.md
│
├── 01_世界观/
│   ├── 现实层/
│   │   └── WLD-REAL_现实世界规则.md
│   ├── 宇宙层/
│   │   ├── WLD-TLEVEL_科技等级体系.md
│   │   ├── WLD-WALL_幽影之墙.md
│   │   └── WLD-APP_六合集市APP.md
│   └── 隐藏层/
│       └── WLD-HIDDEN_异常与灵能规则.md
│
├── 02_人物/
│   ├── 主角组/
│   │   └── CHR-0001_马木.md
│   ├── 现实线/
│   │   ├── CHR-0002_马雯雯.md
│   │   ├── CHR-0003_陈科.md
│   │   └── CHR-0004_周睿.md
│   ├── 异常线/
│   │   ├── CHR-0005_任战.md
│   │   └── CHR-0006_陈灏.md
│   └── 配角/
│
├── 03_组织势力/
│   ├── 现实组织/
│   │   └── ORG-0001_高端分享局.md
│   └── 宇宙势力/
│       ├── ORG-0002_失落人类帝国.md
│       └── ORG-0003_星河联盟.md
│
├── 04_地点场所/
│   ├── 现实地点/
│   │   └── LOC-0001_会所.md
│   └── 宇宙地点/
│
├── 05_道具技术/
│   ├── ITM-0001_六合集市APP.md
│   └── TEC-0001_T2点5执行层技术.md
│
├── 06_能力体系/
│   ├── POW-0001_灵能体系.md
│   ├── POW-0002_任战-入席.md
│   └── POW-0003_陈灏-机械之心.md
│
├── 07_术语表/
│   ├── TERM-0001_灵能.md
│   ├── TERM-0002_权限.md
│   └── TERM-0003_高维道具.md
│
└── 99_设定归档/
```

---

## 7.3 人物卡 YAML

```yaml
id: CHR-0001
type: character
system: setting
status: active
title: 马木
rel: [EVT-0001, EVT-0002]
tags: [主角, 现实线, P00]
```

---

## 7.4 人物卡正文建议结构

```markdown
## 核心定位

## 基础信息

## 人物性格

## 说话方式

## 行为逻辑

## 已知信息范围

## 不可提前知道的信息

## 关联人物

## 关联事件

## 写作禁忌
```

---

## 7.5 能力卡 YAML

```yaml
id: POW-0002
type: power
system: setting
status: active
title: 任战-入席
alias: [留座, 入席]
owner: CHR-0005
rel: [CHR-0005, EVT-0002]
tags: [能力, 异常线, P00]
```

---

## 7.6 能力卡正文建议结构

```markdown
## 核心机制

## 使用条件

## 使用限制

## 外在表现

## 普通人感知

## 灵能者感知

## 当前阶段信息暴露

## 关联事件

## 写作禁忌
```

---

## 7.7 世界观卡 YAML

```yaml
id: WLD-APP
type: worldbuilding
system: setting
status: active
title: 六合集市APP
alias: [集市APP, APP]
rel: [ITM-0001, WLD-WALL]
tags: [世界观, 核心设定]
```

---

## 7.8 术语卡 YAML

```yaml
id: TERM-0001
type: term
system: setting
status: active
title: 灵能
alias: []
rel: [POW-0001, WLD-HIDDEN]
tags: [术语, 能力体系]
```

---

# 八、03_事件数据库设计

## 8.1 系统定位

事件数据库是世界时间轴事实库。

事件数据库负责记录小说世界真实发生的大事件、人物经历、组织行动、历史阶段和因果关系。

事件数据库使用世界内时间。

事件数据库不使用 P / C 等叙事编号定义事件本身。

---

## 8.2 文件夹结构

```text
03_事件数据库/
├── 00_事件总控/
│   ├── EVT-INDEX_事件数据库总览.md
│   ├── EVT-TIME_世界时间轴总表.md
│   ├── EVT-CAUSE_因果链总表.md
│   └── EVT-STATE_状态变更总表.md
│
├── 01_现实时间轴/
│   ├── 十几年前/
│   │   └── EVT-0001_马木当年合伙人捐款跑路事件.md
│   └── 2026年/
│       ├── 2026-05/
│       │   └── EVT-0002_陈科被高端分享局诈骗事件.md
│       └── 2026-06/
│           └── EVT-0003_张凡与小满分离事件.md
│
├── 02_隐藏世界时间轴/
│   ├── 六合集市开放前/
│   └── 灵能觉醒前/
│
├── 03_宇宙历史时间轴/
│   ├── 失落人类帝国时期/
│   └── 星河联盟时期/
│
├── 04_人物经历线/
│   ├── EXP-CHR-0001_马木经历线.md
│   ├── EXP-CHR-0003_陈科经历线.md
│   └── EXP-CHR-0008_张凡经历线.md
│
├── 05_组织行动线/
│   └── ACT-ORG-0001_高端分享局行动线.md
│
└── 99_事件归档/
```

---

## 8.3 事件卡 YAML

```yaml
id: EVT-0002
type: event
system: event
status: confirmed
title: 陈科被高端分享局诈骗事件
time: 2026-05~2026-06
rel: [CHR-0001, CHR-0003, CHR-0005, ORG-0001, POW-0002]
tags: [现实线, 诈骗线, P00]
```

---

## 8.4 事件卡正文建议结构

```markdown
## 事件摘要

## 世界时间

## 起因

## 过程

## 结果

## 影响

## 关联人物

## 关联组织

## 关联设定

## 逻辑限制

## 被哪些叙事内容使用
```

---

## 8.5 人物经历线 YAML

```yaml
id: EXP-CHR-0001
type: experience
system: event
status: active
title: 马木经历线
owner: CHR-0001
rel: [CHR-0001, EVT-0001, EVT-0002]
tags: [人物经历, 马木]
```

---

## 8.6 人物经历线正文建议结构

```markdown
## 人物

[[CHR-0001_马木]]

## 经历总览

## 经历节点

### 十几年前

### 2026年5月

### 2026年6月

## 状态变化

## 影响后续
```

---

## 8.7 组织行动线 YAML

```yaml
id: ACT-ORG-0001
type: organization_action
system: event
status: active
title: 高端分享局行动线
owner: ORG-0001
rel: [ORG-0001, EVT-0002, CHR-0005]
tags: [组织行动, 现实线]
```

---

# 九、04_Skill系统设计

## 9.1 系统定位

Skill 系统是面向 LLM 的创作控制系统。

Skill 系统不存放具体小说内容。

Skill 系统负责：

```text
资料调用规则
生成流程规则
正文写作规则
正文修订规则
一致性校验规则
Prompt 模板
```

---

## 9.2 文件夹结构

```text
04_Skill系统/
├── 00_Skill总控/
│   ├── SKL-INDEX_Skill系统总览.md
│   ├── SKL-FLOW_写作流程总控.md
│   ├── SKL-CALL_资料调用总规则.md
│   └── SKL-CHECK_一致性校验总规则.md
│
├── 01_资料调用/
│   ├── SKL-CALL-001_总纲资料调用.md
│   ├── SKL-CALL-002_单元纲资料调用.md
│   ├── SKL-CALL-003_章节大纲资料调用.md
│   ├── SKL-CALL-004_章节细纲资料调用.md
│   └── SKL-CALL-005_正文资料调用.md
│
├── 02_大纲生成/
│   ├── SKL-OUT-001_总纲生成.md
│   ├── SKL-OUT-002_单元纲生成.md
│   └── SKL-OUT-003_章节大纲生成.md
│
├── 03_正文生成/
│   ├── SKL-WR-001_正文生成总规则.md
│   ├── SKL-WR-002_对话规则.md
│   ├── SKL-WR-003_场景推进规则.md
│   ├── SKL-WR-004_人物表现规则.md
│   └── SKL-WR-005_网文节奏规则.md
│
├── 04_正文修订/
│   ├── SKL-REV-001_正文修订总规则.md
│   ├── SKL-REV-002_AI腔清理.md
│   └── SKL-REV-003_对话口语化修订.md
│
├── 05_一致性校验/
│   ├── SKL-CHK-001_人物一致性校验.md
│   ├── SKL-CHK-002_事件一致性校验.md
│   ├── SKL-CHK-003_设定冲突校验.md
│   └── SKL-CHK-004_信息释放校验.md
│
├── 06_Prompt模板/
│   ├── PRM-001_生成章节大纲.md
│   ├── PRM-002_生成章节细纲.md
│   ├── PRM-003_生成正文.md
│   └── PRM-004_修订正文.md
│
└── 99_Skill归档/
```

---

## 9.3 Skill YAML

```yaml
id: SKL-WR-001
type: skill
system: skill
status: active
title: 正文生成总规则
task: write_draft
rel: [SKL-CALL-005, SKL-CHK-001, SKL-CHK-004]
tags: [正文生成, 写作规则]
```

---

## 9.4 Skill 正文建议结构

```markdown
## 适用任务

## 输入资料

## 调用顺序

## 生成规则

## 禁止规则

## 输出格式

## 完成后校验

## 关联 Skill
```

---

## 9.5 Prompt YAML

```yaml
id: PRM-003
type: prompt
system: skill
status: active
title: 生成正文Prompt
task: write_draft
rel: [SKL-WR-001, SKL-CALL-005]
tags: [Prompt, 正文生成]
```

---

# 十、双链关系规范

## 10.1 双链定位

双链用于 Markdown 正文中的语义关系说明。

YAML 中不放双链，只放 ID。

双链承担以下任务：

```text
解释人物与事件的关系
解释事件与设定的关系
解释章节与事件的关系
解释 Skill 与任务的关系
解释伏笔与回收的关系
```

---

## 10.2 双链使用原则

双链只标记强关系，不标记普通词。

应该双链：

```markdown
[[CHR-0001_马木]] 介入 [[EVT-0002_陈科被高端分享局诈骗事件]]，但没有真正阻止陈科入局。
```

不建议：

```markdown
[[马木]] 今天去了 [[会所]]，看到 [[人群]]，产生了 [[疑惑]]。
```

双链过多会降低信息密度，也会污染图谱。

---

## 10.3 YAML 与双链的配合方式

YAML 负责告诉系统“有关联”。

正文双链负责告诉 LLM“是什么关系”。

示例：

```yaml
rel: [CHR-0001, CHR-0003, EVT-0002]
```

正文：

```markdown
## 关联说明

- [[CHR-0001_马木]]：事件介入者，最终被反咬。
- [[CHR-0003_陈科]]：被骗者，也是反咬马木的关键人物。
- [[EVT-0002_陈科被高端分享局诈骗事件]]：本章背后的核心事件。
```

---

# 十一、Database 设计原则

## 11.1 Database 的作用

Database 用于跨文件检索、筛选、汇总和 Skill 定位。

Database 不替代 Markdown 正文。

Database 主要根据 YAML 字段筛选：

```text
id
type
system
status
title
unit
chapter
time
task
owner
rel
tags
```

---

## 11.2 建议建立的 Database 视图

总控台中建议建立：

```text
DB-CHAR_人物数据库.md
DB-EVT_事件数据库.md
DB-NAR_叙事数据库.md
DB-SET_设定数据库.md
DB-SKL_Skill数据库.md
```

各数据库视图的筛选依据如下：

### 人物数据库

```text
system = setting
type = character
```

### 事件数据库

```text
system = event
type = event
```

### 叙事数据库

```text
system = narrative
```

可进一步按：

```text
type = chapter_outline
type = detail_outline
type = draft
type = revision
```

### 设定数据库

```text
system = setting
```

可进一步按：

```text
type = worldbuilding
type = power
type = organization
type = location
type = term
```

### Skill 数据库

```text
system = skill
```

可进一步按：

```text
type = skill
type = prompt
task = write_draft
task = check_consistency
```

---

# 十二、模板规范

## 12.1 人物卡模板

```yaml
id: CHR-0000
type: character
system: setting
status: draft
title:
rel: []
tags: []
```

正文：

```markdown
## 核心定位

## 基础信息

## 人物性格

## 说话方式

## 行为逻辑

## 已知信息范围

## 不可提前知道的信息

## 关联人物

## 关联事件

## 写作禁忌
```

---

## 12.2 事件卡模板

```yaml
id: EVT-0000
type: event
system: event
status: draft
title:
time:
rel: []
tags: []
```

正文：

```markdown
## 事件摘要

## 世界时间

## 起因

## 过程

## 结果

## 影响

## 关联人物

## 关联组织

## 关联设定

## 逻辑限制

## 被哪些叙事内容使用
```

---

## 12.3 章节大纲模板

```yaml
id: NAR-P00-C00
type: chapter_outline
system: narrative
status: draft
title:
unit: P00
chapter: C00
rel: []
tags: []
```

正文：

```markdown
## 本章功能

## 章节目标

## 出场人物

## 相关事件

## 信息释放

## 伏笔与回收

## 读者奖励

## 结尾钩子

## 禁止事项
```

---

## 12.4 章节细纲模板

```yaml
id: OUT-P00-C00
type: detail_outline
system: narrative
status: draft
title:
unit: P00
chapter: C00
rel: []
tags: []
```

正文：

```markdown
## 场景列表

## 场景一

## 场景二

## 场景三

## 节奏安排

## 对话重点

## 情绪推进

## 结尾处理
```

---

## 12.5 正文模板

```yaml
id: DRAFT-P00-C00
type: draft
system: narrative
status: draft
title:
unit: P00
chapter: C00
rel: []
tags: []
```

正文：

```markdown
## 调用依据

## 正文
```

---

## 12.6 Skill 模板

```yaml
id: SKL-XXX-000
type: skill
system: skill
status: draft
title:
task:
rel: []
tags: []
```

正文：

```markdown
## 适用任务

## 输入资料

## 调用顺序

## 生成规则

## 禁止规则

## 输出格式

## 完成后校验

## 关联 Skill
```

---

# 十三、系统运行流程

## 13.1 基础流程

```text
1. 作者在设定系统维护人物、世界观、能力、组织、道具等规则。
2. 作者在事件数据库维护世界时间轴、大事件、人物经历、组织行动和因果链。
3. 作者在叙事系统维护总纲、分部、分卷、单元、章节、细纲、正文和修订记录。
4. Skill 系统根据任务类型读取 YAML、Database、双链和正文内容。
5. LLM 在 Skill 规则约束下生成或修订叙事系统内容。
6. 正文完成后，作者或 Skill 回写必要的修订记录、伏笔记录、信息释放记录和状态变更。
7. 一致性校验 Skill 检查人物、事件、设定、信息释放和正文风格是否冲突。
```

---

## 13.2 章节正文生成调用顺序

生成正文时，建议调用顺序为：

```text
1. 读取正文生成 Skill
2. 读取正文资料调用 Skill
3. 读取章节大纲
4. 读取章节细纲
5. 读取出场人物卡
6. 读取相关事件卡
7. 读取信息释放规则
8. 读取写作风格规则
9. 生成正文
10. 执行人物一致性校验
11. 执行事件一致性校验
12. 执行信息释放校验
13. 执行正文风格修订
```

---

# 十四、V1.1 固化结论

V1.1 固化以下规则：

```text
1. 根目录只保留五个一级文件夹：
   总控台、叙事系统、设定系统、事件数据库、Skill系统。

2. 文件夹可以多层嵌套，但只服务作者理解。

3. 文件唯一性由 ID 保证。

4. 文件归类由 YAML 和 Database 保证。

5. YAML 只做简洁索引，不承载复杂正文内容。

6. YAML 字段统一使用英文字段值：
   system 使用英文。
   type 使用英文。

7. rel 字段只放 ID，不放 Obsidian 双链。

8. Obsidian 双链只写在 Markdown 正文中，用于解释语义关系。

9. 章节正文文件名不带章节标题，标题放 YAML 和正文中。

10. alias 作为可选字段保留，用于别名、简称、旧称、误称检索。

11. 复杂设定、人物关系、事件过程、写作规则全部写入 Markdown 正文。

12. Skill 系统不存小说内容，只存调用、生成、修订、校验规则。
```

---

# 十五、后续阶段方向

V1.2 建议继续设计：

```text
1. Obsidian Database 视图字段规则
2. Dataview 查询模板
3. 人物卡正文标准模板
4. 事件卡正文标准模板
5. 章节大纲正文标准模板
6. 正文生成 Skill 详细流程
7. 一致性校验 Skill 详细流程
8. CLI 或脚本如何读取 YAML 与正文
9. 如何自动生成投喂给 LLM 的上下文摘要
10. 如何避免重复文件和设定冲突
```

---

# 结论

小说写作系统 V1.1 的核心是：

```text
五个一级文件夹建立系统边界。
ID 保证文件唯一。
YAML 保证精确定位。
Database 保证筛选归类。
Markdown 正文承载复杂内容。
双链说明语义关系。
Skill 负责调用、生成、修订和校验。
```

本版本正式将 Obsidian 落地方式从“信息完整型 YAML”修正为“简洁索引型 YAML”，更适合长期维护、Database 管理、脚本调用和 LLM 精确检索。