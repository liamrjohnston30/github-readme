# GitHub README & Repo Creator Skill

Use this skill to create world-class GitHub repositories — production-ready READMEs, clean file structures, security-hardened configs, CI/CD workflows, and everything a professional open-source project needs. Someone should be able to clone the output and immediately understand, install, and use the project.

---

## CLI Setup

All GitHub operations go through the `gh` CLI.

```bash
# Auth check
gh auth status

# Create a new repo
gh repo create owner/repo-name --public --description "One-liner description" --clone

# Create from existing local dir
cd ~/Projects/myproject
gh repo create myproject --public --source=. --remote=origin --push

# Create a release
gh release create v1.0.0 --title "v1.0.0 — Initial Release" --notes "First stable release."

# Open a PR
gh pr create --title "feat: add X" --body "## What\n\nAdds X.\n\n## Why\n\nBecause Y."

# View repo in browser
gh repo view --web
```

---

## README Structure — The Gold Standard

Every README must have these sections IN THIS ORDER:

```
1. Hero banner (optional but professional)
2. Badges
3. One-liner description
4. Key features (3–5 bullet points)
5. Installation
6. Quick start / Usage
7. Configuration reference
8. Examples
9. Contributing
10. License
```

---

## Full README Template

```markdown
<!-- HERO BANNER — use a wide image or ASCII art -->
<div align="center">
  <img src="docs/banner.png" alt="Project Name" width="600" />
  <h1>project-name</h1>
  <p><strong>One sentence. What it does and why it matters.</strong></p>

  <!-- BADGES -->
  [![npm version](https://img.shields.io/npm/v/package-name.svg)](https://www.npmjs.com/package/package-name)
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
  [![CI](https://github.com/owner/repo/actions/workflows/ci.yml/badge.svg)](https://github.com/owner/repo/actions)
  [![Coverage](https://img.shields.io/codecov/c/github/owner/repo)](https://codecov.io/gh/owner/repo)
  [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
</div>

---

## What is this?

2–3 sentences. What problem does it solve? Who is it for? What makes it different?

## Features

- ✅ **Feature one** — brief explanation
- ✅ **Feature two** — brief explanation  
- ✅ **Feature three** — brief explanation
- ✅ **Feature four** — brief explanation

## Installation

### npm / bun / yarn

\`\`\`bash
npm install package-name
# or
bun add package-name
# or
yarn add package-name
\`\`\`

### Homebrew (macOS/Linux)

\`\`\`bash
brew tap owner/repo
brew install package-name
\`\`\`

### curl (global install)

\`\`\`bash
curl -fsSL https://install.example.com | bash
\`\`\`

### From source

\`\`\`bash
git clone https://github.com/owner/repo.git
cd repo
bun install
bun run build
\`\`\`

## Quick Start

\`\`\`typescript
import { thing } from 'package-name';

// Minimal working example — copy and run
const result = await thing({
  input: 'hello',
  option: true,
});

console.log(result); // { output: 'world' }
\`\`\`

## Configuration

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `input` | `string` | required | The input value |
| `option` | `boolean` | `false` | Enable feature X |
| `timeout` | `number` | `5000` | Timeout in ms |
| `verbose` | `boolean` | `false` | Log debug info |

### Environment Variables

Copy `.env.example` to `.env` and fill in:

\`\`\`bash
cp .env.example .env
\`\`\`

\`\`\`env
# Required
API_KEY=your_api_key_here

# Optional
LOG_LEVEL=info
TIMEOUT=5000
\`\`\`

## Examples

### Example 1: Basic usage

\`\`\`typescript
// description of what this example shows
\`\`\`

### Example 2: Advanced usage

\`\`\`typescript
// description of what this example shows
\`\`\`

See the [`examples/`](examples/) directory for more.

## API Reference

### `functionName(options)`

Description of what it does.

**Parameters:**

- `options.input` — `string` — Description
- `options.option` — `boolean` (optional) — Description

**Returns:** `Promise<Result>` — Description

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for full guidelines.

Quick version:
1. Fork the repo
2. Create your branch: `git checkout -b feat/my-feature`
3. Make changes, add tests
4. Run `bun test` — all tests must pass
5. Submit a PR with a clear description

## Changelog

See [CHANGELOG.md](CHANGELOG.md).

## License

[MIT](LICENSE) © [Your Name](https://github.com/owner)
```

---

## Badge Patterns (shields.io)

```markdown
<!-- npm -->
[![npm](https://img.shields.io/npm/v/PACKAGE)](https://npmjs.com/package/PACKAGE)
[![npm downloads](https://img.shields.io/npm/dm/PACKAGE)](https://npmjs.com/package/PACKAGE)

<!-- GitHub -->
[![GitHub stars](https://img.shields.io/github/stars/OWNER/REPO)](https://github.com/OWNER/REPO)
[![GitHub issues](https://img.shields.io/github/issues/OWNER/REPO)](https://github.com/OWNER/REPO/issues)
[![Last commit](https://img.shields.io/github/last-commit/OWNER/REPO)](https://github.com/OWNER/REPO/commits)

<!-- CI/Quality -->
[![CI](https://github.com/OWNER/REPO/actions/workflows/ci.yml/badge.svg)](https://github.com/OWNER/REPO/actions)
[![codecov](https://codecov.io/gh/OWNER/REPO/branch/main/graph/badge.svg)](https://codecov.io/gh/OWNER/REPO)
[![code style](https://img.shields.io/badge/code_style-prettier-ff69b4.svg)](https://prettier.io)

<!-- License -->
[![MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)

<!-- Social -->
[![Twitter](https://img.shields.io/twitter/follow/handle?style=social)](https://twitter.com/handle)
[![Discord](https://img.shields.io/discord/SERVER_ID?logo=discord)](https://discord.gg/INVITE)
```

---

## File Structure Convention

Every repo must follow this structure:

```
repo-name/
├── .github/
│   ├── workflows/
│   │   ├── ci.yml          # Run tests on every PR
│   │   └── release.yml     # Publish on tag push
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── pull_request_template.md
├── src/                    # All source code
│   ├── index.ts            # Main entry point / public API
│   └── lib/                # Internal modules
├── docs/                   # Documentation, diagrams, banner
├── examples/               # Runnable example files
├── tests/                  # Test files (mirror src/ structure)
├── scripts/                # Build/deploy/utility scripts
├── .env.example            # Template for environment variables (NEVER .env)
├── .gitignore
├── .prettierrc
├── biome.json              # Or eslint config
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── package.json
├── README.md
└── tsconfig.json
```

---

## Security Checklist

Before EVERY commit and definitely before making a repo public:

```bash
# Scan for secrets accidentally committed
gh secret scan  # or use: trufflehog git file://./
grep -r "sk-" . --include="*.ts" --include="*.js" --exclude-dir=node_modules
grep -r "API_KEY\s*=" . --include="*.ts" --exclude-dir=node_modules

# Verify .env is gitignored
cat .gitignore | grep ".env"
```

**Mandatory `.gitignore` entries:**
```gitignore
# Environment
.env
.env.local
.env.*.local

# Dependencies
node_modules/
.bun/

# Build
dist/
build/
.next/
out/

# OS
.DS_Store
Thumbs.db

# Editor
.vscode/settings.json
.idea/

# Logs
*.log
logs/

# Runtime
renders/
*.mp4
*.mov
```

**Mandatory `.env.example` (committed, no real values):**
```env
# Copy this file to .env and fill in real values
# NEVER commit .env

# Required — get from dashboard.example.com
API_KEY=

# Optional
LOG_LEVEL=info
PORT=3000
```

---

## CONTRIBUTING.md Template

```markdown
# Contributing to project-name

Thanks for your interest! Here's how to contribute.

## Development Setup

\`\`\`bash
git clone https://github.com/owner/repo.git
cd repo
bun install
cp .env.example .env
# fill in .env values
bun run dev
\`\`\`

## Running Tests

\`\`\`bash
bun test           # run all tests
bun test --watch   # watch mode
bun test --coverage
\`\`\`

## Commit Convention

We use [Conventional Commits](https://conventionalcommits.org/):

\`\`\`
feat: add new feature
fix: fix a bug
docs: update documentation
refactor: code change that neither fixes a bug nor adds a feature
test: add or update tests
chore: maintenance tasks
\`\`\`

## Pull Request Process

1. Branch from `main`: `git checkout -b feat/your-feature`
2. Make changes with tests
3. Run `bun test` — must pass
4. Run `bun run lint` — must pass
5. Update CHANGELOG.md under `[Unreleased]`
6. Submit PR — fill in the template completely

## Code Style

- TypeScript strict mode
- Prettier for formatting (runs on save)
- No `any` types
- All public functions must have JSDoc comments
```

---

## CHANGELOG.md Template

Follow [Keep a Changelog](https://keepachangelog.com/) format:

```markdown
# Changelog

All notable changes to this project will be documented here.

Format: [Semantic Versioning](https://semver.org/)

## [Unreleased]

### Added
- 

### Changed
- 

### Fixed
- 

## [1.0.0] - 2026-03-22

### Added
- Initial release
- Feature X
- Feature Y

[Unreleased]: https://github.com/owner/repo/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/owner/repo/releases/tag/v1.0.0
```

---

## GitHub Actions — CI Workflow

`.github/workflows/ci.yml`:

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - uses: oven-sh/setup-bun@v2
        with:
          bun-version: latest

      - name: Install dependencies
        run: bun install --frozen-lockfile

      - name: Type check
        run: bun run typecheck

      - name: Lint
        run: bun run lint

      - name: Test
        run: bun test --coverage

      - name: Upload coverage
        uses: codecov/codecov-action@v4
        with:
          token: ${{ secrets.CODECOV_TOKEN }}
```

---

## GitHub Actions — Release Workflow

`.github/workflows/release.yml`:

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

jobs:
  release:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      
      - uses: oven-sh/setup-bun@v2

      - name: Install & Build
        run: |
          bun install --frozen-lockfile
          bun run build

      - name: Publish to npm
        run: bun publish
        env:
          NPM_TOKEN: ${{ secrets.NPM_TOKEN }}

      - name: Create GitHub Release
        run: gh release create ${{ github.ref_name }} --generate-notes
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

---

## Issue Templates

`.github/ISSUE_TEMPLATE/bug_report.md`:

```markdown
---
name: Bug Report
about: Something isn't working
labels: bug
---

## Describe the bug
A clear description of what the bug is.

## To Reproduce
Steps to reproduce:
1. 
2. 
3. 

## Expected behavior
What you expected to happen.

## Actual behavior
What actually happened.

## Environment
- OS: 
- Node/Bun version: 
- Package version: 

## Additional context
Paste any error messages or logs here.
```

`.github/ISSUE_TEMPLATE/feature_request.md`:

```markdown
---
name: Feature Request
about: Suggest an idea
labels: enhancement
---

## Problem
What problem does this solve? Who needs it?

## Proposed solution
What would you like to happen?

## Alternatives considered
Any alternative solutions you've thought of?
```

`.github/pull_request_template.md`:

```markdown
## What does this PR do?

Brief description.

## Why?

Context / motivation.

## How to test

Steps to verify this works:
1. 
2. 

## Checklist

- [ ] Tests added/updated
- [ ] CHANGELOG.md updated
- [ ] Docs updated if needed
- [ ] No secrets committed
```

---

## gh CLI Quick Reference

```bash
# REPOS
gh repo create owner/name --public --description "desc" --clone
gh repo view --web
gh repo clone owner/name
gh repo fork owner/name --clone

# ISSUES
gh issue create --title "Bug: X" --body "..." --label bug
gh issue list --label bug
gh issue close 42

# PRs
gh pr create --title "feat: X" --body "..." --base main
gh pr list --state open
gh pr merge 42 --squash --delete-branch
gh pr checkout 42

# RELEASES
gh release create v1.0.0 --title "v1.0.0" --notes "Release notes"
gh release list

# ACTIONS
gh run list
gh run view 12345678 --log
gh run rerun 12345678

# SECRETS
gh secret set API_KEY
gh secret list
```

---

## README Quality Checklist

Before publishing any README:

- [ ] One-liner is clear to someone who's never heard of this project
- [ ] Install command is copy-pasteable and works on first try
- [ ] Quick start example runs without modification
- [ ] All config options documented in a table
- [ ] `.env.example` exists and is committed
- [ ] `.env` is in `.gitignore`
- [ ] At least one badge (version, CI, or license)
- [ ] License clearly stated
- [ ] No placeholder text left (no "TODO", "coming soon", "description here")
- [ ] All links work
- [ ] Code blocks have language tags for syntax highlighting
