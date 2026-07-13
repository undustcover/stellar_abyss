---
id: TPL-NAR-VOLUME
type: template
system: narrative
level: volume
status: placeholder
title: 卷级叙事表达契约模板
created: 2026-06-23
---

# 卷级叙事表达契约模板

## 当前状态

占位，未完成。

卷级叙事共创属于下一阶段迭代工作，当前阶段不进行开发。

## 后续开发目标

卷级叙事表达契约用于约定整卷层面的主题、中心思想、读者最终情绪、叙事姿态和艺术加工边界。

当前 P0C3 校准阶段只保留本文件作为上级契约占位，章节级契约可在 YAML 或继承声明中标注：

```yaml
related_volume_contract: TPL-NAR-VOLUME_卷级叙事表达契约.md（占位，未完成，下一阶段迭代）
```

## 禁止事项

1. 当前阶段不得用本占位模板强行生成卷级契约。
2. 当前阶段不得把章节级差异规则上升为卷级通用规则。
3. 当前阶段不得让后续 skill 因卷级契约缺失而阻断 P0C3 测试。
