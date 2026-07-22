# macOS Compatibility Notes

Audit date: 2026-07-03

## Status

Compatible in principle. This repo is a skill package made of Markdown/YAML instructions with no build or runtime code found.

This was audited from Ubuntu, so no native macOS install was executed.

## What Was Checked

- File and manifest inspection.
- No package manifest, build script, or test script was found.

## What Should Work On macOS

- Skill usage after installation into a supported agent.
- `npx skills add ...` after Node/npm install.
- `gh skill install ...` if the local GitHub CLI has skill support.

## macOS Blockers

- No repo-level blocker found.
- External installer tooling is required:
  - Node/npm for `npx skills add`
  - or GitHub CLI skill support

## Suggested macOS Smoke Path

```bash
node --version
npm --version
npx skills add Micsushi/unvibe-code
```

For Codex:

```bash
npx skills add Micsushi/unvibe-code -g -a codex
```
