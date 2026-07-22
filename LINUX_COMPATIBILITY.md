# Linux Compatibility Notes

Audit date: 2026-07-03

## Status

Compatible in principle. This repo is a skill package made of Markdown/YAML instructions, with no build or runtime code found.

## What Was Tested

- File and manifest inspection.
- No package manifest, build script, or test script was found.
- Host has GitHub CLI, but Node/npm are not installed.

## What Should Work On Linux

- Using the skill after it is installed into a supported agent.
- GitHub CLI based installation if the local `gh skill` command is available.
- `npx skills add ...` after Node/npm are installed.

## Linux Blockers

- No repo-level blocker found.
- External installer tooling is required:
  - Node/npm for `npx skills add`
  - or GitHub CLI skill support for `gh skill install`

## Suggested Ubuntu Smoke Path

```bash
node --version
npm --version
npx skills add Micsushi/unvibe-code
```

For Codex specifically:

```bash
npx skills add Micsushi/unvibe-code -g -a codex
```
