---
id: TPL-REFERENCE-STYLE-EVIDENCE-001
type: template
status: active
version: "0.1"
created: 2026-07-17
---

# 参考文风蒸馏证据卡

```yaml
evidence_id:
source_id:
location:
scene_id:
analysis_layers: []
evidence_role: induction | holdout | counterexample
observable_text_change_or_pattern:
verb_and_object:
omitted_or_retained_modifiers:
syntax_and_omission:
positive_behavior:
physical_spatial_relational_consequence:
explanation_stopping_point:
character_ownership:
rhythm_function:
context_dependency:
candidate_deep_mechanism:
transferable_part:
non_transferable_surface:
counterevidence:
failure_risk:
confidence: low | medium | high
status: observed
```

## 填写约束

1. `location` 必须能回到具体行号或稳定段落。
2. 先写可观察现象，再写机制，不得把需求文档中的候选假设当证据。
3. 每张卡至少填写一个反证或边界。
4. 不复制长段原文；短摘记只用于定位。
5. 卡片状态只能是 `observed`，作者校准前不得升级。
6. 同一表面句式出现在多处，不等于同一深层机制；必须说明它在场景中的功能。
