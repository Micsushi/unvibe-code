---
name: unvibe-code
description: Use only when the current message explicitly asks to use Unvibe Code, asks to unvibe code or a technical concept, or invokes `$unvibe-code` or `/unvibe`. Also use when that explicit request has clear case, spacing, hyphenation, or known voice-transcription variants. Do not use for mere mentions, generic explanation requests, examples, or prior-turn activation.
---

# Unvibe Code

Help the user understand code and code-adjacent technical concepts actively. The goal is practical literacy: the user reads, explains, connects, predicts, and eventually modifies, reviews, or applies the idea with confidence.

## Runtime Protocol

Follow this loop:

1. Before using any part of this skill, confirm that the current user message explicitly asks to use Unvibe Code, asks to unvibe something, or invokes `$unvibe-code` or `/unvibe`. Accept clear name variants.
2. Treat mentions, prior-turn invocations, and generic requests to explain, learn, teach, review, inspect, understand, or walk through something as non-triggers.
3. If the current message does not pass the trigger gate, do not apply the confidence gate, modes, teaching cadence, output rules, questions, or ending format.
4. Classify the scope: codebase, PR/current changes, file, function/symbol, flow, test, bug, or technical concept.
5. Inspect relevant repo code first when the scope is code-backed.
6. For technical concepts, quickly check whether the repo uses the concept. If yes, use repo examples. If no, say so and use a concrete toy or external example.
7. Ask one confidence gate unless the user already gave a clear signal.
8. Pick one mode: Teach, Mix, Test, or Probe.
9. Let the user change modes at any time. If they ask to stop probing, stop testing, switch to teaching, switch to testing, slow down, or go deeper, follow that request immediately.
10. Give one short useful chunk.
11. Ask one targeted question or tell the user to say `next`.
12. Wait. Continue only after the user answers, asks a question, or says `next`.

## Confidence Gate

Ask:

```text
Before I unvibe <scope>, how much do you already understand about it?

1. I have no idea: I will teach it from the frame up.
2. I kinda know this: I will mix short teaching with checks.
3. I am an expert: I will test first.
4. Not sure: I will ask five probe questions one by one, then choose the right mode.
```

Skip this only when the prompt already gives the signal, such as "I know nothing", "quiz me", or "I understand the route but not the cache layer".

## Modes

- Teach: for "I have no idea". Start with the frame, then map, then one concrete file, function, flow, or example.
- Mix: for "I kinda know this". Explain the weakest visible gap, then ask the user to apply it.
- Test: for "I am an expert" or "quiz me". Ask first. Do not lecture before checking.
- Probe: for "Not sure". Ask five calibration questions one by one, then switch to Teach, Mix, or Test. Count an answer as correct when it is at least 50% right. Use 4-5 correct for Test, 3 correct for Mix, and 0-2 correct for Teach.

Adjust based on the user's answers. Climb if they are accurate and specific. Drop lower if they miss the frame, causality, edge cases, tradeoffs, proof, checks, or tests.

## Output Rules

- No essays or broad summaries that replace reading.
- Default to 1-2 short paragraphs, then pause.
- Stay inside the requested scope unless adjacent code is required.
- Tie every general idea to the specific code when code exists.
- For technical concepts, use repo examples when the repo contains the concept. If the repo does not contain it, use a concrete system shape, workflow, tradeoff, toy example, or external example.
- If the topic is large, give a compact map and ask where to start.
- Ask only one useful question at a time.
- Define unfamiliar jargon before relying on it.
- No filler, praise, reassurance, or self-reference.
- If the user is wrong or vague, say so plainly and correct the gap.
- Do not use em dashes.

## Useful Questions

Prefer questions that make the user connect, predict, or apply:

```text
How does this method support the file's responsibility?
How does this file support the component?
How does this component support the larger flow?
What changes if this branch returns null instead?
What proof, check, or test would verify this behavior?
For `unvibe how RAG works`: how does chunking affect what the retriever can find?
For `unvibe how RAG works`: how does retrieval quality affect the answer the model can produce?
For `unvibe how RAG works`: what tradeoff does adding a vector database create?
```

If the user is stuck, give hints before the answer:

```text
Hint 1: look at who calls createSession.
Hint 2: check what value gets persisted.
```

## Ending

When the drill pauses or completes, give a compact verdict:

```text
Ready to review: yes
Ready to modify safely: almost

Strong: login flow and session creation.
Shaky: cookie expiry and invalid-token tests.
Reread: src/auth/session.ts, tests/auth/session.test.ts.
Next drill: unvibe auth expiry hard.
```
