# Prose Control

Use these controls to make the execution pack useful for controlled key-fragment drafting and final whole-chapter assembly without writing the prose.

## Whole-Chapter Flow

- Preserve the chapter as one reading unit.
- Use scene transitions to carry state, pressure, information, and emotion forward.
- Do not let each scene feel like an isolated prompt response.

## Scene Weighting

- Assign more space to scenes that carry conflict, reversal, emotional turn, or information release.
- Compress logistical, bridge, and setup scenes.
- Do not force every scene to have equal length.
- For each core scene, identify one protected pressure point: action, object, money/procedure, face, relationship, or information boundary.
- Do not allow later prose compression to skip a protected pressure point with a vague transition.

## Information Control

- Track protagonist knowledge separately from reader knowledge.
- Track important support-character knowledge separately when their fear, shame, anger, or control drives the scene.
- Hidden information may appear as trace, pressure, consequence, absence, or misread signal.
- Do not let prose generation explain hidden mechanics just because the outline knows them.

## Dialogue Control

- Give dialogue ratio and function for each scene.
- Do not write full dialogue lines.
- Mark what speakers cannot say because of cognition, motive, status, or secrecy.
- For key scenes, provide at least one dialogue break point: interruption, answer-not-matching-question, after-the-fact repair, silence, topic dodge, or two people each pursuing their own urgent purpose.

## Character Intent Coverage Routing

- Mark relationship pressure that can change speech or behavior.
- Mark character cognition boundaries: knows, does not know, misbelieves, suspects, and cannot judge.
- Mark key behavior risks where a character may need a reason not to take a simpler action.
- Mark key dialogue risks where a line direction could create different character meanings.
- Mark decisions the model must not make for characters.
- Record whether existing `type: character_intent_result` coverage is present, partial, missing, or requires `ASK_USER`.
- Route uncovered key fragments back to `control-character-intent`.
- Do not build full character intent tracks in the execution pack.

## Anti-AI Control

- Prevent outline-expansion prose by specifying concrete action, object, pressure, or relationship movement for each major scene.
- Flag where prose is likely to become exposition, clean Q&A, over-polished metaphor, authorial diagnosis, or isolated joke.
- Require information to emerge through conflict, pursuit, pressure, object trace, misread signal, or consequence.

## Comedy/Drama Control

- Separate `幽默感` from `笑点`: humor can be a background tone, but core jokes need setup, escalation, landing, and echo.
- Mark the emotional material that humor cannot dilute.
- Do not schedule jokes mechanically by word count.
- Treat joke landing as a prose-generation slot, not a finished punchline from non-system material.
- Do not import jokes, dialogue, or recognizable expressions from external prose drafts, comparison reports, or other non-system material into the pack.
- Give each scene one dominant joke, misread, or comic pressure. Other clever material should be marked compressible.
- Strong characters must not win every exchange. Put force into action, interruption, refusal, partial failure, or another character's pressure when the line density gets too high.
- Important support characters need a small emotional arc; do not flatten them into helpers, explainers, or atmosphere.

## Ending Hook Control

- Name exactly one main chapter hook.
- Let comic or emotional afterbeats remain only when they echo the main hook or sit clearly below it.
- If several endings compete, choose the one that best pushes the next chapter and mark the others as compressible.

## Transition Control

- For each transition, preserve at least one continuity handle:
  - action consequence
  - emotional residue
  - object/material clue
  - unanswered question
  - pressure from another character
  - time/location jump with retained state

## High-Risk Scene Routing

Mark a scene as high-risk when it contains:

- climax or reversal
- dense information reveal
- complex deception or dialogue
- important emotional break
- strict cognition boundary
- high chance of becoming exposition
- high chance of losing a pressure point during compression
- dialogue where two characters have different urgent purposes and could become clean Q&A
- a support character whose emotional turn carries the scene

Do not expand high-risk scenes here. Recommend `generate-scene-execution-brief` for that scene if local refinement is needed.

## System-Source Boundary

The execution pack is generated from the chapter creative control plan, chapter narrative expression contract, chapter detail outline, scene performance contract, character intent result when available, narrative system, setting system, event database, and approved common rule files. It must not use external prose drafts, comparison reports, finished sample text, or non-system writing material as generation material.
