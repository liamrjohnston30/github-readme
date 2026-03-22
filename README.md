# github-readme

<div align="center">
  <h3>Create world-class GitHub READMEs and production-ready repo structures — in one shot.</h3>
  <p>A skill for AI agents covering everything: README templates, badges, security, CI/CD, issue templates, changelogs, and the full <code>gh</code> CLI workflow.</p>

  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
  [![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-brightgreen)](https://clawhub.com)
</div>

---

## What is this?

A skill file for AI coding agents that produces professional GitHub repositories from scratch. Hand it to any AI agent and it will generate a complete, production-ready repo structure with:

- A polished README that people actually read
- Proper security (no leaked secrets, ever)
- CI/CD workflows out of the box
- Issue and PR templates
- Conventional commits and changelog format
- Everything needed to open-source a project correctly

## What's inside

| File | Purpose |
|------|---------|
| `SKILL.md` | Complete skill — all templates, patterns, checklists, and CLI commands |

## Installation

### For OpenClaw agents

```bash
git clone https://github.com/liamrjohnston30/github-readme.git \
  ~/.openclaw/skills/github-readme
```

### For Cursor / Claude Code / Codex

```bash
git clone https://github.com/liamrjohnston30/github-readme.git
```

Reference in your agent's context:
```
Read github-readme/SKILL.md before creating any GitHub repository or README.
```

## Prerequisites

```bash
# Install gh CLI
brew install gh

# Authenticate
gh auth login
```

## Quick start

### Create a new repo from scratch

```bash
gh repo create owner/my-project --public --description "What it does" --clone
cd my-project
```

Ask your agent to read `SKILL.md` then:
> "Create a complete production-ready README, CONTRIBUTING.md, CHANGELOG.md, .gitignore, .env.example, and GitHub Actions CI workflow for this project."

### Add a README to an existing project

```bash
cd my-existing-project
```

Ask your agent:
> "Read github-readme/SKILL.md and write a complete README.md for this project."

## What gets generated

### README.md
- Hero banner + badges (npm version, license, CI status)
- Clear one-liner description
- Features list
- Install commands for npm/bun/brew/curl
- Quick start with working code examples
- Full configuration table
- Contributing section
- License

### Security
- `.gitignore` — blocks `.env`, `node_modules`, build artifacts, OS files
- `.env.example` — committed template with no real values
- Pre-commit secret scanning checklist

### CI/CD (`.github/workflows/`)
- `ci.yml` — runs type check, lint, tests on every PR
- `release.yml` — publishes to npm and creates GitHub release on version tag

### Issue templates
- `bug_report.md` — structured bug report with reproduction steps
- `feature_request.md` — problem/solution/alternatives format

### PR template
- What/why/how to test checklist format

### CHANGELOG.md
- Keep a Changelog format
- Semantic versioning links

### CONTRIBUTING.md
- Dev setup, test commands, commit convention, PR process

## gh CLI Quick Reference

```bash
# Create repo
gh repo create owner/name --public --description "desc" --clone

# Create release
gh release create v1.0.0 --title "v1.0.0" --generate-notes

# Create PR
gh pr create --title "feat: add X" --body "..."

# Merge PR
gh pr merge 42 --squash --delete-branch

# View CI runs
gh run list
gh run view --log
```

## Security Checklist

Run before every push and before making any repo public:

```bash
# Check for accidental secrets
grep -r "API_KEY\s*=" . --include="*.ts" --exclude-dir=node_modules
grep -r "sk-" . --include="*.ts" --exclude-dir=node_modules

# Verify .env is ignored
cat .gitignore | grep "^\.env"
```

## README Quality Checklist

- [ ] One-liner clear to someone who's never heard of this
- [ ] Install command copy-pasteable, works first try
- [ ] Quick start runs without modification
- [ ] All config options in a table
- [ ] `.env.example` committed, `.env` gitignored
- [ ] At least one badge
- [ ] License clearly stated
- [ ] No placeholder text ("TODO", "coming soon")
- [ ] All links work
- [ ] Code blocks have language tags

## Contributing

PRs welcome. Add patterns you've found that make READMEs clearer or repos easier to use.

## License

MIT © Promptible
