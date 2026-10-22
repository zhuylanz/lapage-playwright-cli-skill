<p align="center">
  <a href="https://lapage.vn"><img src="assets/lapage-digital-mark.png" width="96" alt="LaPage Digital"></a>
</p>

# LaPage Playwright CLI Skill

**A LaPage Digital open-source agent skill for reliable browser automation with Playwright CLI.**

[![CI](https://github.com/zhuylanz/lapage-playwright-cli-skill/actions/workflows/ci.yml/badge.svg)](https://github.com/zhuylanz/lapage-playwright-cli-skill/actions/workflows/ci.yml)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-F47A32.svg)](LICENSE)

## Why This Skill Exists

[Playwright CLI](https://github.com/microsoft/playwright-cli) gives coding agents a
token-efficient way to drive a real browser: open pages, read accessibility
snapshots, click by element ref, fill forms, record traces, and generate tests.

This distribution packages the upstream skill with the conventions LaPage
Digital uses in production agent work:

- **Self-updating guidance.** On first use in a session the agent checks this
  repository for a newer version and asks before updating.
- **Profile discipline.** In-memory profiles for anonymous and parallel work; one
  shared persistent profile for logged-in services, so sign-ins survive across
  agent runs without leaking between workers.
- **Credential hygiene.** Clear rules against storing tokens, cookies, or login
  details in prompts, notes, screenshots, or committed files.

## Install With An Agent

Share this repository URL with your coding agent and ask it to install the skill:

```text
Install the lapage-playwright-cli skill from https://github.com/zhuylanz/lapage-playwright-cli-skill
```

The repository root is the skill directory, so it can be cloned directly into a
supported skills location:

```bash
git clone https://github.com/zhuylanz/lapage-playwright-cli-skill ~/.agents/skills/lapage-playwright-cli
```

Installing from a git clone lets the update check offer a one-line
`git pull --ff-only` upgrade.

## Requirements

- Node.js 20+
- Playwright CLI, globally or through `npx`:

```bash
npm install -g @playwright/cli@latest
```

## Quick Start

```bash
playwright-cli open https://playwright.dev
playwright-cli snapshot
playwright-cli click e15
playwright-cli screenshot --filename=page.png
playwright-cli close
```

For logged-in work, use the persistent LaPage agent profile in headed mode:

```bash
playwright-cli open https://example.com --headed --profile="$HOME/.agents/workspace/agent-chrome-profile"
```

See [SKILL.md](SKILL.md) for the full command reference and
[references/](references/) for tests, mocking, tracing, video, and storage state.

## Update Check

```bash
node scripts/check-update.mjs          # one-line summary
node scripts/check-update.mjs --json   # structured result
node scripts/check-update.mjs --force  # bypass the 24h cache
```

The check reads `version` from the published `package.json` on `main`, caches
the result in `~/.cache/lapage-skills/`, and never blocks the workflow when
GitHub is unreachable. Set `LAPAGE_SKILL_UPDATE_CHECK=0` to disable it.

## Other LaPage Skills

| Skill | What it does |
| --- | --- |
| [lapage-strapi-cms-skill](https://github.com/zhuylanz/lapage-strapi-cms-skill) | Operate LaPage Strapi CMS content from a dependency-free CLI |
| [lapage-codex-imagen](https://github.com/zhuylanz/lapage-codex-imagen) | Restore Codex image generation behind model routers |
| [lapage-codex-websearch](https://github.com/zhuylanz/lapage-codex-websearch) | Restore Codex web search behind model routers |

## Development

```bash
npm run check
npm test
```

## Credits

Maintained by [LaPage Digital](https://lapage.vn). Based on the Playwright CLI
agent skill by Microsoft Corporation; see [NOTICE](NOTICE).

## License

[Apache License 2.0](LICENSE)
