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
unvibe src/auth/session.ts
test my understanding of this file
teach me this code without info dumping
```

## What It Does

- Starts with the right scope: codebase, PR, current changes, file, function, flow, test, or bug.
- Asks how comfortable you are first, then picks the mode: comfortable means it tests you, not comfortable means it explains, in the middle means a mix, and not sure means it probes and adapts as it learns what you know.
- Checks whether technical terms are familiar before relying on them, and defines the ones you do not know.
- Keeps explanations short and tied to the bigger picture.
- Asks relationship questions so you connect components, files, methods, and logic.
- Uses confidence checks and observed answers to decide where to drill deeper.
- Ends with a compact readiness verdict and next reading targets.

## Core Rule

No essays. No broad summaries that replace reading. Unvibe Code teaches in layers:

```text
scope map -> component -> file -> method -> logic -> relationship check -> next
```

If a topic is large, it gives a compact map and waits for `next`.

## Repository Layout

```text
SKILL.md
agents/openai.yaml
README.md
LICENSE
```

`SKILL.md` is the runtime skill. The other files make the repository easier to install, inspect, and reuse.
