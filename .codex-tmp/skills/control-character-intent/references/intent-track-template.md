# Character Intent Result Template Reference

Primary formal template:

```text
System_alpha/00_总控台/02_模板库/TPL-CHARACTER-INTENT-RESULT_人物意图结果模板.md
```

This reference is not the full output template. Use it only as the subtemplate for the formal template section:

```text
## 关键片段意图轨道
```

The full `人物意图结果` output must preserve the formal template's YAML, headings, tables, boundary statements, `执行包轻引用接口`, `章节运行态更新建议`, quality check, archive rules, and `待确认问题`.

## Fragment Track Scope

Build complete tracks only for P0/P1 key fragments that affect character language intent, behavior intent, cognition boundary, relationship pressure, information release, misread escalation, scene entrance/exit, or action consequence.

Do not create full tracks for every ordinary scene by default. For low-risk fragments, record coverage as `not_applicable` or a concise baseline reference in `关键片段覆盖索引`.

## Subtemplate

```yaml
intent_checkpoint:
  chapter_id:
  scene_id:
  fragment_id:
  fragment_scope:
  resume_point:
  risk_level: P0
  action: CONTINUE
  source_creative_control_plan:
  source_narrative_expression_contract:
  source_detail_outline:
  source_scene_performance_contract:
  source_execution_pack:
  source_character_cards:

character_intent_tracks:
  人物名:
    behavior_goal:
    behavior_motive:
    immediate_action:
    why_not_simpler_action:
    language_goal:
    language_strategy:
    emotional_pressure:
    knowledge:
      knows:
        -
      does_not_know:
        -
      assumes:
        -
      suspects:
        -
    forbidden:
      -
    expected_effect_on_other:
    expected_consequence:
```

## Field Rules

`behavior_goal`: what the character wants to accomplish now.

`behavior_motive`: why this goal matters to the character, not to the outline.

`immediate_action`: the action the next prose fragment is likely to stage.

`why_not_simpler_action`: why the character does not directly ask, leave, refuse, explain, call, report, or solve the problem in the simplest way.

`language_goal`: what the character wants the line to do.

`language_strategy`: how the character chooses to say it: test, hide, confirm, evade, pressure, soften, joke, deny, overstate, or redirect.

`emotional_pressure`: how fear, shame, anger, pride, urgency, embarrassment, caution, or performative calm changes the line/action.

`knowledge`: what the character knows, does not know, assumes, and suspects at this exact point.

`forbidden`: what the character must not say, know, infer, or do.

`expected_effect_on_other`: what the character wants or expects the other person to understand or do.

`expected_consequence`: how the line or action changes the situation.

## Scene Performance Reference Rule

Use the scene performance contract only to translate prose-facing rules into character-facing constraints:

- turn wording rules into language strategy;
- turn dialogue-naturalization rules into speaking-mode constraints;
- turn narration or psychology limits into "the character must not explain the setting";
- turn anti-AI requirements into natural behavior and speech checks.

Do not evaluate whole-chapter style or rewrite the scene performance contract.

## CONTINUE Requirement

Return `CONTINUE` only if all required fields can be filled from current inputs without inventing author intent.

If a required field cannot be filled:

- use `ASK_USER` for blocking P0 divergence;
- use `pending_divergences` or `待确认问题` for non-blocking gaps outside the current fragment;
- do not delete formal template fields.
