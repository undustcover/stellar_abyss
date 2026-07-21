---
name: revise-draft-common-rules
description: "Shared boundary and workflow rules for local failed-scene repair after a web-novel prose draft already exists. Use when Codex needs to diagnose a weak scene, decide whether it belongs to outline, execution pack, or prose drafting, and perform a local replacement without reviving whole-chapter post-processing."
---

# Failed Scene Repair Common Rules

## Purpose

Use this skill as the common contract for the fallback repair stage:

```text
草稿诊断 -> 定位失败场景 -> 分场景再导演 -> 正文局部替换
```

This is not a default whole-chapter revision chain. De-AI feel, style consistency, and dialogue humor now belong inside:

```text
generate-chapter-detail-outline
-> generate-chapter-execution-pack
-> generate-chapter-prose-draft
```

This fallback exists only when a generated draft has one or more clearly failed scenes.

## Required Reference

Before repairing, read `references/revision-boundary.md`.

Use that file as the authority when local repair appears to drift into plot repair, consistency rewriting, or execution-pack redesign.

## Revision Principle

Preserve `发生了什么`; repair `这一场怎么被读者读到`.

The local replacement may rework the telling of the same scene facts for reader effect, including narration order, time compression or expansion, dialogue density, paragraph rhythm, comic timing, sensory focus, and emotional aftertaste.

It must not add, remove, or rewrite execution-pack scene facts, character decisions, causal relations, information boundaries, or world rules.

## Inputs

Use the following inputs when available:

- The current whole-chapter prose draft.
- The chapter execution pack or equivalent whole-chapter constraints.
- The chapter outline or detail outline, only to confirm chapter function and hard facts.
- Character cards or language packs, only to confirm voice and knowledge boundaries.
- Approved style, anti-AI, humor, and prose-generation rules from `System_alpha`.
- User-specified repair target for this pass.

If a hard input is missing, repair conservatively and record the missing input in the notes.

## Workflow

1. Identify the failed scene and the failure type: reader experience, information release, scene pressure, dialogue collision, humor timing, style drift, word-budget drift, or AI-like explanation.
2. Read the execution pack before the prose draft when it is available.
3. Extract only hard facts and constraints from upstream materials.
4. Do not revise the whole chapter unless several core scenes fail for the same upstream reason.
5. Preserve all required scene facts, major decisions, causal sequence, hidden information, and ending state.
6. Redesign only the failed scene's reader experience: expectation, pressure, misread, reveal, comic landing, and exit state.
7. Replace only the failed scene or the smallest surrounding beat required for continuity.
8. When a structural problem appears, mark it as a rollback issue instead of patching plot inside the replacement.
9. Output the local replacement plus concise repair notes.

## Allowed Changes

- Reorder narration inside the same scene or between immediately adjacent scene beats when the underlying event order remains intelligible.
- Reveal a reaction before its cause, then backfill the cause, if this improves reading tension.
- Compress transitions, waiting, travel, repeated explanations, and mechanical connective tissue.
- Expand a key second, awkward pause, embodied reaction, or charged silence.
- Change dialogue volume by cutting explanatory lines, adding character-specific responses, or turning direct information into subtext.
- Adjust action, psychology, description, and dialogue ratios.
- Move emphasis from information delivery to lived pressure, embarrassment, misunderstanding, or relationship strain.
- Rebuild a joke through reaction, misread, silence, wording contrast, or timing.
- Split or merge paragraphs and local beats.

## Forbidden Changes

- Add a new scene fact not required or allowed by the execution pack.
- Delete a required scene fact, object, decision, clue, payment, document, call, encounter, or ending hook.
- Change who knows what, when they know it, or what they choose.
- Change event outcomes, causal order, relationship state, world rules, or timeline constraints.
- Solve a structural problem by inventing missing plot.
- Explain hidden truth earlier than the execution pack allows.
- Let the revision become a new outline, new execution pack, or new canon card.
- Put process notes, craft labels, or analysis inside the prose body.

## Rollback Notes

If the draft cannot be repaired cleanly because the scene itself is broken, add a short rollback note:

```markdown
## 局部替换备注

|项目|内容|
|---|---|
|失败场景||
|失败类型||
|保留的场景事实||
|局部替换范围||
|需回退处理||
|回退原因||
```

Use `需回退处理` for issues that belong to `细纲`, `执行包`, or `正文草稿`.

## Output Rule

Return the local replacement text and notes. Return a whole revised chapter only when the user explicitly asks for whole-chapter assembly.

Keep the prose body clean. Put all notes under `## 局部替换备注`.
