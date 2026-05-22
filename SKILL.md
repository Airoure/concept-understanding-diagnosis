---
name: concept-understanding-diagnosis
description: Diagnose and improve a learner's understanding of a concept through Socratic questioning, gap analysis, durable learning records, targeted study materials, and follow-up checks. Use when the user asks to learn, test, detect, check, probe, evaluate, or record their understanding of a concept; when they want Solid/Unstable/Missing tracking; when they want Obsidian-style learning notes; or when they say not to explain directly before asking questions.
---

# Concept Understanding Diagnosis

## Purpose

Use this skill to turn a concept-learning request into an interactive diagnosis loop with memory-friendly output. Do not start with a full lecture. First elicit the learner's current model, then identify what is solid, unstable, missing, or confused. Teach only the smallest useful part, recommend focused study material when needed, and keep a record that can be pasted into Obsidian or another learning system.

## Core Workflow

1. Ask for the target concept if the user has not named one.
2. Ask 3-6 diagnostic questions before explaining. Prefer questions that reveal mental models, real use, boundaries, and failure cases.
3. Wait for the user's answers. Do not grade an empty response.
4. Diagnose the answer using the understanding levels below.
5. Name the strongest parts first, then the gaps.
6. Produce a compact learning record with `Solid`, `Unstable`, `Missing`, `Possible confusion`, and `Next`.
7. For each important `Missing` or `Unstable` item, choose one of two moves:
   - If the gap is small, fill it with a brief explanation and one realistic example.
   - If the gap needs study, recommend a minimal reading/practice set before asking more questions.
8. Ask the user to restate, apply, or troubleshoot a small example after they study or after the brief explanation.
9. Update the learning record as the user improves. Move items from `Missing` to `Unstable`, and from `Unstable` to `Solid` only after the user succeeds on an application or troubleshooting task.
10. Iterate until the user can explain and use the concept at the intended depth.

## Diagnostic Question Types

Mix these based on the concept:

- Problem: What problem does this concept solve?
- Boundary: What is it not responsible for?
- Components: What are its core parts?
- Process: What happens step by step?
- Example: Where have you seen or used it?
- Contrast: How is it different from a similar concept?
- Failure: What errors or symptoms appear when it goes wrong?
- Application: How would you use it in a real project?

For technical concepts, include at least one concrete scenario question. For example, for HTTP ask about a request/response, status code, caching, authentication, or debugging a failed API call.

## Understanding Levels

Classify the user's current level with this scale:

- Heard the term: recognizes the name but cannot explain the purpose.
- Knows the purpose: can say what it is for but not how it works.
- Explains the flow: can describe main components and process.
- Solves problems: can debug, design, or choose correctly in real cases.
- Transfers knowledge: can connect it to adjacent concepts and explain tradeoffs.

Do not use the level as a harsh label. Use it to choose the next teaching move.

## Mastery Buckets

Track the user's knowledge in these buckets:

- Solid: The learner can explain it correctly or apply it in a concrete case.
- Unstable: The learner has the right direction but mixes boundaries, misses conditions, or cannot yet use it reliably.
- Missing: The learner did not mention it, gave no usable model, or needs external study before practice.
- Possible confusion: The learner's answer suggests a likely mistaken contrast, such as 401 vs 403, HTTP vs TCP, cookie vs token, or GET vs POST.

Do not mark something `Solid` just because the learner recognizes the term. Require a correct explanation, example, or troubleshooting choice.

## Diagnosis Format

Keep diagnosis concrete and compact:

```text
Current level: ...

Solid:
- ...

Unstable:
- ...

Missing:
- ...

Possible confusion:
- ...

Next fill order:
1. ...
2. ...
3. ...
```

Use the user's language. If the user writes in Chinese, respond in Chinese.

## Learning Record Format

When the user wants tracking, Obsidian integration, or ongoing study, also produce a paste-ready learning record:

```markdown
# <Concept> diagnosis

## Current level
...

## Solid
- ...

## Unstable
- ...

## Missing
- ...

## Possible confusion
- ...

## Next study
- ...

## Next check
- ...
```

Prefer one record per concept or sub-concept. For broad topics, create a topic map and split notes by responsibility instead of making one encyclopedic note.

Suggested Obsidian structure:

```text
<Topic>/
- overview.md
- diagnosis.md
- question-map.md
- atomic-notes/
- practice-records/
- resources/
```

Use this structure only when the user asks for note-taking, recording, Obsidian, or durable learning artifacts.

## Study Material Recommendations

Recommend materials only after diagnosing a gap. Keep them minimal and targeted:

- Prefer official docs, specs, vendor docs, or canonical tutorials for key definitions and boundaries.
- Assign exact sections or concepts to read, not an entire large document.
- Pair every material with a concrete task: summarize, compare, inspect, run, debug, or answer a scenario.
- For engineering topics, include one practical verification step, such as checking a browser Network panel, running a command, reading logs, or inspecting a real config.
- Separate "must study now" from "advanced later".

Use this format:

```text
Study:
- Must: ...
- Practice: ...
- Optional later: ...

Come back able to answer:
1. ...
2. ...
```

## Teaching Rules

- Teach from the user's answers, not from a generic syllabus.
- Prefer one clear model plus one realistic example over broad encyclopedic coverage.
- Separate "must know now" from "advanced later".
- Use contrasts to dissolve confusion, such as HTTP vs TCP, cookie vs token, class vs object, process vs thread.
- When a concept has layers, expose only the next useful layer.
- Prefer scenario questions over definition recitation when checking progress.
- When the user wants records, update the record before continuing to new subtopics.
- End each teaching pass with a small verification task.

## Reusable Starter Prompts

When the user says "check my understanding of X", start with:

```text
Let's not explain first. I will use a few questions to find the edge of your current understanding:

1. What problem does X mainly solve?
2. What trouble appears if you do not use X?
3. What are X's core parts or key steps?
4. Where have you seen or used it in a real scenario?
5. What part are you least certain about?
```

When the concept is technical, add:

```text
6. If X breaks, what symptoms would appear, and where would you check first?
```

## Final Output

After one or more rounds, produce a compact understanding map:

```text
Concept: ...

Already solid:
- ...

Need to fill:
- ...

Easy to confuse:
- ...

Next practice:
- ...

Related concepts:
- ...
```

If the user is using Obsidian or another note system, end with a durable next-action block:

```text
Record update:
- Move to Solid: ...
- Keep Unstable: ...
- Add Missing: ...

Next study:
- ...

Next practice:
- ...
```
