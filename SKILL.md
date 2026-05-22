---
name: concept-understanding-diagnosis
description: Diagnose and improve a learner's understanding of a concept through Socratic questioning, gap analysis, durable learning records, targeted study materials, guided post-reading output, and Obsidian-friendly learning records. Use when the user asks to learn, test, detect, check, probe, evaluate, or record their understanding of a concept; when they want Solid/Unstable/Missing tracking; when they want learning materials plus output guidance; when they want Obsidian-style learning notes; or when they say not to explain directly before asking questions.
---

# Concept Understanding Diagnosis

## Purpose

Use this skill to turn a concept-learning request into an interactive learning loop with memory-friendly output. Default to diagnosing the learner's current model first, then identify what is solid, unstable, missing, or confused. Teach only the smallest useful part, recommend focused study material when needed, guide the learner to produce their own output after reading, and keep records that can be pasted into Obsidian or another learning system.

Do not trap the user in Socratic questioning. If the user says they want learning materials, a reading path, or less questioning, switch to a material-first study flow and make the output-after-reading step explicit.

## Core Workflow

1. Ask for the target concept if the user has not named one.
2. Before asking new diagnostic questions, look for an existing diagnosis record for this concept using the retrieval rules below.
3. If a record exists, summarize the saved level, `Solid`, `Unstable`, `Missing`, and `Next check`, then continue from the saved next check or highest-priority gap instead of restarting from first principles.
4. If no record exists and the user has not requested materials first, ask 3-6 diagnostic questions before explaining. Prefer questions that reveal mental models, real use, boundaries, and failure cases.
5. If the user asks for learning materials, a reading plan, or says the diagnosis style is not useful, switch to the Study Material Workflow below.
6. Wait for the user's answers when in diagnosis mode. Do not grade an empty response.
7. Diagnose the answer using the understanding levels below.
8. Name the strongest parts first, then the gaps.
9. Produce a compact learning record with `Solid`, `Unstable`, `Missing`, `Possible confusion`, and `Next`.
10. For each important `Missing` or `Unstable` item, choose one of three moves:
   - If the gap is small, fill it with a brief explanation and one realistic example.
   - If the gap needs study, recommend a minimal reading/practice set before asking more questions.
   - If the learner wants materials, provide a focused study set and schedule a post-reading output task.
11. Ask the user to restate, apply, troubleshoot, or create a small learning output after they study or after the brief explanation.
12. Create or update the durable learning record after the first diagnosis round, following the persistence rules below.
13. Update the learning record as the user improves. Move items from `Missing` to `Unstable`, and from `Unstable` to `Solid` only after the user succeeds on an application, troubleshooting task, or clear post-reading output.
14. Iterate until the user can explain and use the concept at the intended depth.

## Mode Switching

Respect the user's preferred learning mode.

- Diagnosis mode: Use questions first, then teach from the answers.
- Material-first mode: Use when the user asks for learning materials, a reading path, official docs, articles, videos, or says the questioning method is not working.
- Output-guidance mode: Use after the user reads material or asks to store learning in Obsidian. Guide them to produce a reusable note, not just a summary.

When switching modes, state the change briefly and continue. Do not defend the previous mode.

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

Do not mark something `Solid` just because the learner recognizes the term. Require a correct explanation, example, troubleshooting choice, or post-reading output.

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

## Retrieval Rules

When the user asks to learn, continue, review, test, or diagnose a concept, search for an existing diagnosis record before starting a new diagnosis.

Search order:

1. Known Obsidian vault topic package for the concept.
2. Known learning-record directories from prior context.
3. Current workspace Markdown files.
4. If the likely location is known but outside writable or readable scope, request permission or ask for the location.

Use filenames and headings such as:

- `<Concept> diagnosis.md`
- `<概念> 理解诊断.md`
- `diagnosis.md`
- headings containing `<Concept> diagnosis`, `Current level`, `Solid`, `Unstable`, `Missing`, or `Next check`

If a record is found:

1. Treat it as the current learning state, not as historical trivia.
2. Do not ask the full starter question set again unless the record is stale, empty, or clearly mismatched.
3. Resume from `Next check`, `Next practice`, or the highest-priority `Missing`/`Unstable` item.
4. State briefly that an existing record was found and name the file being continued.
5. After the user's next answer or post-reading output, update the same file rather than creating a duplicate record.

If multiple plausible records exist, choose the most specific matching concept record. If ambiguity would affect the learning path, ask the user which one to continue.

## Persistence Rules

Treat diagnosis records as durable by default when the user invokes this skill to learn, test, check, or diagnose a concept. Do not wait for a separate "record this" request.

After the first diagnosis round or first meaningful post-reading output:

1. If a known Obsidian vault or matching concept topic folder exists, create or update the diagnosis note there.
2. If no durable location is known, create a Markdown diagnosis record in the current workspace, or ask for the target location when writing to the wrong place would be risky.
3. If filesystem permission is required, request permission proactively and explain that the skill is trying to persist the learning record.
4. Continue updating the same diagnosis note after each verification task or post-reading output.
5. Keep one diagnosis note per concept or sub-concept. Do not bury the record in a broad overview note.
6. If creating a learning-output template, use a general learning/process template location, not the current concept package, unless the user explicitly asks for a concept-specific template.

Default note names:

- Chinese concept: `<概念> 理解诊断.md`
- English concept: `<Concept> diagnosis.md`

Default Obsidian placement:

- If a matching topic package exists, write the diagnosis note into that package root.
- If no package exists and the user is using Obsidian, create or propose this structure:

```text
<Topic>/
- overview.md
- diagnosis.md
- question-map.md
- atomic-notes/
- practice-records/
- resources/
```

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

## Study Material Workflow

Use this when the user asks for learning materials, says the questioning method is not useful, or needs external study before practice.

1. Start from diagnosed gaps when available. If no diagnosis exists, ask at most 1-2 quick scoping questions or make a reasonable beginner/intermediate assumption.
2. Provide a small, sequenced study set. Prefer official docs, specs, vendor docs, canonical tutorials, or high-signal examples.
3. Assign exact sections or concepts to read, not an entire large document.
4. Separate `Must`, `Practice`, and `Optional later`.
5. Pair every material with a concrete output task, not just a reading task.
6. Tell the user what to bring back after reading: notes, confusion points, examples, screenshots, API logs, or a rough explanation.
7. After the user returns, switch to Output-guidance mode and help turn the reading into Obsidian-ready artifacts.

Use this format:

```text
Study:
- Must: ...
- Practice: ...
- Optional later: ...

After reading, bring back:
1. ...
2. ...

Output we will create:
- Topic map update / atomic note / practice record / diagnosis update / resource note
```

## Post-Reading Output Workflow

Use this after the learner reads a material, pastes notes, asks to store the result in Obsidian, or asks you to guide output.

The goal is not to create a concept-specific template every time. The goal is to route learning into a reusable knowledge system.

1. Ask what they read if not provided: title, link, reading range, and target topic.
2. Ask or infer which question the material answered.
3. Guide a short output using the Universal Learning Output Template below.
4. Decide where the output should go:
   - Topic map update: if it changes the learner's overview, relationships, entry questions, or learning path.
   - Atomic note: if it explains one stable concept, distinction, mechanism, or rule.
   - Practice record: if it comes from debugging, hands-on verification, an experiment, or a worked example.
   - Resource note: if it is mainly a useful external source that has not yet been fully absorbed.
   - Diagnosis update: if it changes `Solid`, `Unstable`, `Missing`, or `Next check`.
5. Write or update durable notes when allowed. If not allowed, provide paste-ready Markdown.
6. End with one next question or next practice task.

## Universal Learning Output Template

Use this as the general post-reading output shape across all topics. Do not name it after the current concept unless the user explicitly wants a concept-specific variant.

~~~markdown
# 学习输出：<资料或问题标题>

## 资料信息
- 标题：
- 链接：
- 阅读范围：
- 阅读日期：
- 所属主题：

## 这份资料回答了什么问题？
-

## 我读完后的 3 句话理解
不要照抄，用自己的话说。

```text

```

## 核心模型
把内容压缩成一个结构、流程、对比表或因果链。

```text

```

## 它补充/纠正了我什么？
- 补充了：
- 纠正了：
- 仍然不确定：

## 放回我的知识系统
- 应该链接到哪个主题地图：
- 应该新建哪条原子笔记：
- 应该更新哪条旧笔记：
- 是否需要做一个练习记录：
- 是否需要更新理解诊断：

## 实践验证
我能用它解决什么小问题？

```text
场景：
我会怎么用：
结果/判断：
```

## 下一步问题
-
~~~

## Teaching Rules

- Teach from the user's answers or reading output, not from a generic syllabus.
- Prefer one clear model plus one realistic example over broad encyclopedic coverage.
- Separate "must know now" from "advanced later".
- Use contrasts to dissolve confusion, such as HTTP vs TCP, cookie vs token, class vs object, process vs thread.
- When a concept has layers, expose only the next useful layer.
- Prefer scenario questions over definition recitation when checking progress.
- When the user wants materials, provide materials and attach an output task instead of continuing to quiz.
- When the user wants records, update the record before continuing to new subtopics.
- End each teaching pass with a small verification task or a post-reading output task.

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

When the user asks for materials, use:

```text
I will switch to material-first study. Read only the focused parts below, then come back with rough notes. I will help turn them into an Obsidian-ready output instead of leaving them as bookmarks.
```

When the user returns after reading, use:

```text
Let's convert what you read into a reusable note. First: what question did this material answer for you, and what changed in your understanding?
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

Next study:
- ...

Next output:
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

Next output:
- Topic map update / atomic note / practice record / resource note / diagnosis update
```
