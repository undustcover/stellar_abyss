# Runtime State Rules

## Runtime State Location

Use one chapter runtime state per chapter.

Suggested name:

```text
CXX_章节运行态_意图控制.md
```

## What Runtime State Stores

- temporary chapter-local character intent;
- author-confirmed rules for the chapter;
- resolved divergences;
- pending divergences;
- resume points;
- generated fragment records;
- long-term rule candidates.

## What Runtime State Must Not Store

- full character cards;
- long-term world facts copied wholesale;
- full prose text;
- unconfirmed long-term character conclusions;
- broad writing-method essays.

## Update Blocks

When the author confirms or edits intent, output an update block:

```yaml
resolved_intents:
  - id:
    source_checkpoint:
    character:
    type: language_intent # language_intent / behavior_intent / cognition / relationship / reader_info
    decision:
    normalized_rule:
    scope: 当前片段 # 当前片段 / 当前场景 / 本章后续 / 长期规则候选
    confirmed_by_author: true
    created_at:
```

For a divergence:

```yaml
resolved_divergences:
  - id:
    risk_level:
    divergence_type:
    character:
    question:
    author_decision:
    model_recommendation:
    final_rule:
    affected_scope:
    resume_point:
```

For a blocking unresolved issue:

```yaml
pending_divergences:
  - id:
    risk_level:
    divergence_type:
    character:
    blocking_reason:
    must_ask_before:
    resume_point:
```

## Character Card Boundary

Never automatically write chapter-local intent into a character card.

If an answer may become a long-term character rule, record only:

```yaml
long_term_rule_candidates:
  - id:
    source:
    character:
    candidate_rule:
    reason:
    target_file:
    status: pending_review
```

The author must confirm any long-term update separately.

