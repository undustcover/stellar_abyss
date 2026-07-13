# Interrupt Protocol

## When to ASK_USER

Return `ASK_USER` when any P0 item is unclear.

Language intent P0:

- unclear why a character speaks;
- one line can serve two different goals;
- unclear whether the character tests, explains, hides, counters, evades, or redirects;
- unclear what the character wants the other person to know or misunderstand;
- unclear whether the character would say something directly;
- two line directions create different character meanings;
- the line moves plot but may betray the character.

Behavior intent P0:

- unclear current character goal;
- two equally plausible actions exist;
- action serves plot but not the character;
- action changes plot direction, relationship, or character attitude;
- unclear whether the character acts actively or reacts passively;
- no reason explains why the character avoids the simpler action.

P1 items trigger `ASK_USER` only if they change language or behavior intent:

- cognition boundary;
- information gap;
- misread mechanism;
- POV;
- reader information;
- scene initiative;
- foreshadowing;
- comedy mechanism.

Do not ask for P2 issues alone:

- wording;
- minor gesture;
- decorative setting;
- paragraph rhythm;
- general writing difficulty.

## ASK_USER Format

```markdown
## 人物意图中断：需要确认一个关键分歧

### 已确认

- ...

### 当前分歧

A方向：...

B方向：...

### 我的判断

建议采用...

原因：...

### 最小验证片段

...

请确认 A、B，或直接改写人物意图轨道。
```

## Hard Stop

After `ASK_USER`, stop the response. Do not write prose, do not continue the outline, and do not answer the question on behalf of the author.

