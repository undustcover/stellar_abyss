---
name: reconstruct-draft-to-public
description: "Reconstruct an already approved prose Draft into a Public version by preserving confirmed plot, scene, character, POV, information, and ending constraints while rewriting sentence structure, dialogue movement, paragraph organization, narration, information entry, tone, and reader experience at L0-L4. Use when the user explicitly asks for Draft-to-Public generation, expression reconstruction, author-aesthetic revision, or a second-stage whole-chapter prose pass that must not become synonym replacement or a new plot draft."
---

# Reconstruct Draft To Public

## Purpose

Preserve `发生了什么`; reconstruct `读者怎样读到它`.

Use this skill only after the Draft's story structure is approved. Do not use it for first-pass Draft generation or for repairing upstream plot, intent, POV, or canon.

## Required References

Before working, read:

1. `references/public-workflow.md`
2. `references/quality-gates.md`
3. The formal expression method library at `System_alpha/04_Skill系统/03_正文生成/表达重构方法论库/LIB-EXPRESSION-P0_表达重构方法论库.md`

Read the author aesthetic library and humor library only for entries relevant to the audited fragments.

## Required Inputs

Require:

- one frozen Input Draft;
- confirmed frozen story boundaries;
- the current author-aesthetic library;
- the expression reconstruction method library;
- the chapter's POV and information boundary;
- chapter-ending function when the ending is in scope.

Treat failed Public versions as diagnostic evidence only. Never use their prose as the new writing base.

## Core Workflow

1. Freeze the Input Draft and isolate prohibited target text.
2. Build a frozen-layer table.
3. Register possible author-intervention nodes before prose generation.
4. Divide the Draft into functional fragments.
5. Audit each fragment by vocabulary, syntax, dialogue, paragraph, expression path, tone, and aesthetic decision.
6. Choose L0-L4. Stop if L5 or another intervention node is triggered.
7. Convert aesthetic judgments into fragment-specific reconstruction tasks.
8. Select one primary expression method and at most two auxiliary methods.
9. Reconstruct by fragment. For L4, write from a constraint card rather than from the original sentence order.
10. Assemble fragments and unify transitions, tone, rhythm, and narration distance.
11. Run all three gates in `references/quality-gates.md`.
12. Redo only failed fragments. Never silently alter a frozen layer.

## Modification Levels

- `L0`: retain.
- `L1`: correct wording or local rhythm without changing the expression mechanism.
- `L2`: rewrite sentence structure.
- `L3`: reorganize dialogue, action, narration, paragraph order, and information entry.
- `L4`: reconstruct one functional fragment from a frozen constraint card.
- `L5`: change plot, scene function, character decision, POV, information boundary, or ending function. Stop and ask the author.

## Mandatory Stop Rules

Stop immediately when:

- a frozen item is unclear;
- confirmed aesthetic rules conflict;
- L4 would change a frozen item;
- new facts, motives, abilities, or relationship history are required;
- POV or knowledge boundaries must change;
- the primary tone cannot be decided from confirmed rules;
- the ending function or continuation interface would change;
- a method's migration boundary is unconfirmed;
- Skill architecture cannot be decided from existing responsibilities.

Report the node, affected fragment, confirmed invariants, unresolved choice, and no more than three options.

## Output Rules

- Preserve the failed version; create a new version.
- Keep prose separate from audit and process notes.
- Record fragment levels, methods, gates, and intervention status in the test record.
- Never claim success when L2-L4 text still maps sentence-by-sentence to the Draft.
- Do not update formal aesthetic or method libraries from an uncalibrated author revision.
