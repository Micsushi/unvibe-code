# Linux Compatibility

Unvibe Code contains Markdown and YAML only, with no platform-specific runtime.
Installation requires one of these tools:

- Node.js and npm for `npx skills add`
- GitHub CLI with `gh skill` support

## Install Check

```bash
node --version
npm --version
npx skills add Micsushi/unvibe-code
```

Or use GitHub CLI:

```bash
gh skill install Micsushi/unvibe-code unvibe-code
```

For a global Codex install:

```bash
npx skills add Micsushi/unvibe-code -g -a codex
```
