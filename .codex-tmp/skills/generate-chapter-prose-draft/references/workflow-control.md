# Prose Generation Workflow Control

This file defines the prose generation control system.

## Anti-AI Mapping Preflight

Before any operation, read `public-derived-anti-ai-prevention.md` and compare its mapped `method ID@version` with the formal expression method library.

- `current`: continue with Draft prevention rules;
- `stale`: report `SYNC-DRAFT-DEAI-001` and synchronize before prose when maintenance is authorized;
- `stale` without maintenance authority: stop and ask the author; never continue silently.

Only abstract rules may cross from Public to Draft. Do not read or reuse Public finished prose, chapter bridges, fixed metaphors, dialogue, or paragraph order.

## Operations

Use exactly one operation at a time.

### START_CHAPTER

Prepare chapter drafting from:

- chapter creative control plan;
- chapter narrative expression contract;
- chapter detail outline;
- scene performance contract;
- chapter execution pack;
- chapter runtime state if available;
- intent-control interface fields.

Do not write key prose until the first key fragment has `CONTINUE` or `RESUME` from `control-character-intent`.

### WRITE_FRAGMENT

Write the current key prose fragment only after `control-character-intent` returns `CONTINUE`.

Input must include:

- fragment id or scope;
- approved character intent tracks;
- inherited runtime-state rules;
- relevant creative control, narrative contract, detail outline, scene performance contract, and pack sections.

Output:

- clean prose fragment;
- concise generation notes;
- fragment status for runtime state.

### RESUME_FRAGMENT

Continue from an interruption only after `control-character-intent` returns `RESUME`.

Before prose, preserve:

- normalized author decision;
- affected scope;
- resume point;
- runtime-state update.

Do not repeat prior prose.

### ASSEMBLE_V1

Assemble generated fragments into a complete chapter V1.

Run whole-chapter checks:

- character language intent remains stable;
- behavior causality remains intact;
- scene transitions are smooth;
- information release stays within bounds;
- prose performance follows the scene performance contract;
- upstream artifacts remain coordinated under the creative control plan;
- one main ending hook is preserved.

### REVISE_FRAGMENT

Revise only the failed fragment or necessary adjacent passage.

If failure is caused by unclear language or behavior intent, return to `control-character-intent` before rewriting.

## Control Actions

`CONTINUE`: write the approved fragment.

`ASK_USER`: stop prose generation and let `control-character-intent` ask the author.

`RESUME`: continue from the named resume point using normalized intent rules.

## Hard Rules

- Do not write prose after unresolved `ASK_USER`.
- Do not make P0 character language or behavior decisions inside this skill.
- Do not put intent tracks, tables, or process labels inside `## 正文`.
- Do not restart a chapter when only one fragment is blocked.
- Preserve whole-chapter flow during final assembly.
- Do not generate or assemble prose while the Public-derived anti-AI prevention mapping is stale.
