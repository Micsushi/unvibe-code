# Unvibe Code

Skill to help you "unvibe" the insane amount of code output LLM spits out so you actually understand the code. Helped me to be less lazy by interactively teaching me the codebase, hopefully it can help you too.

## Install

Install to the agent detected in your current terminal:

```bash
npx skills add Micsushi/unvibe-code
```

Install globally for supported agents:

```bash
npx skills add Micsushi/unvibe-code -g
```

Install for a specific harness:

```bash
# Codex
npx skills add Micsushi/unvibe-code -g -a codex

# Claude Code
npx skills add Micsushi/unvibe-code -g -a claude-code

# Cursor
npx skills add Micsushi/unvibe-code -g -a cursor

# GitHub Copilot
npx skills add Micsushi/unvibe-code -g -a github-copilot

# Gemini CLI
npx skills add Micsushi/unvibe-code -g -a gemini-cli
```

Install to every supported harness:

```bash
npx skills add Micsushi/unvibe-code --all
```

GitHub CLI users can also install with:

```bash
gh skill install Micsushi/unvibe-code unvibe-code
```

## Use

Try prompts like:

```text
unvibe codebase
unvibe current changes
unvibe this PR
unvibe auth, I do not know how it works
unvibe RAG
unvibe src/auth/session.ts
```

Only a current message that explicitly asks to `unvibe` something, or invokes
`$unvibe-code` or `/unvibe`, activates the skill. Mentioning Unvibe while
discussing its behavior does not activate it. Generic requests such as
"explain this code," "teach me this repository," or "how does this work?" do
not activate it, and activation never carries forward from an earlier turn.

## What It Does

- Starts with the right scope: codebase, PR, current changes, file, function, flow, test, bug, or technical concept.
- Runs only when you explicitly ask to `unvibe` something.
- Asks how well you know the topic first: no idea, kinda know it, expert, or not sure.
- Routes by confidence: no idea teaches, kinda know it mixes teaching and checks, expert tests first, and not sure runs a five-question probe before choosing a mode.
- Uses Feynman explanations, worked examples, retrieval practice, misconception checks, concept maps, and tiny application tasks when teaching is needed.
- For technical concepts without matching repo code, says so and uses a concrete toy example or system map.
- Checks whether technical terms are familiar before relying on them, and defines the ones you do not know.
- Keeps explanations short and tied to the bigger picture.
- Asks relationship questions so you connect components, files, methods, and logic.
- Uses confidence checks and observed answers to decide where to drill deeper.
- Ends with a compact readiness verdict and next reading targets.

## Core Rule

No essays. No broad summaries that replace reading. For code-backed scopes, Unvibe Code teaches in layers:

```text
scope map -> component -> file -> method -> logic -> relationship check -> next
```

For pure technical concepts, it teaches in layers:

```text
concept map -> workflow -> core mechanism -> toy example -> tradeoff -> application check -> next
```

If a topic is large, it gives a compact map and waits for `next`.

## Repository Layout

```text
SKILL.md
agents/openai.yaml
README.md
LINUX_COMPATIBILITY.md
MACOS_COMPATIBILITY.md
ui-design.md
LICENSE
```

`SKILL.md` contains the runtime instructions. `agents/openai.yaml` supplies the
OpenAI interface metadata and invocation policy. The compatibility notes cover
platform prerequisites, and `ui-design.md` documents the conversational
interface.
