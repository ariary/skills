# Agent Skills for business banking and financial tools on Qonto

[![Agent Skills](https://img.shields.io/badge/format-Agent%20Skills-black)](https://agentskills.io)
[![License: MIT](https://img.shields.io/badge/license-MIT-blue)](LICENSE)

> [!NOTE]
> This repository uses the [Qonto MCP server](https://docs.qonto.com/mcp/overview).
> [Connect it first](https://docs.qonto.com/mcp/install/quickstart), then install
> the skills. You sign in as yourself, and the agent inherits exactly the
> [permissions](https://docs.qonto.com/mcp/authentication) your Qonto account
> already has.
> [New to MCP?](https://modelcontextprotocol.io/docs/getting-started/intro)

AI agent skills for founders, finance teams, accountants and the developers who
automate their work, built on top of the
[Qonto MCP server](https://docs.qonto.com/mcp/overview). Transactions and
statements, client invoices, quotes and credit notes, cards and their limits,
spend requests and reconciliation, written to help your AI agents get your work
done faster.

Runs on Claude, ChatGPT, Codex, Cursor, GitHub Copilot, Gemini CLI, and any
other agent supporting the open [Agent Skills](https://agentskills.io) format.

```bash
npx skills add qonto/skills
```

> [!IMPORTANT]
> The Qonto MCP server does not move money. An agent can raise a transfer
> request and hand you a link to approve it in the Qonto app. Approving stays
> with you. Full list of what the server can and cannot do:
> [MCP capabilities](https://docs.qonto.com/mcp/capabilities).

## Available skills

<!-- Keep this table in sync with skills/. It is how people find them. -->

| Skill | Area | What it does |
| --- | --- | --- |
| _Coming soon_ | | |

## Install

### Any terminal agent

Claude Code, Codex, Cursor, GitHub Copilot, Gemini CLI, Windsurf, OpenCode and
dozens more. The installer writes each skill into whichever agent directories it
finds on your machine.

```bash
npx skills add qonto/skills
```

If you want to install one skill only, for every agent, available in every
project:

```bash
npx skills add qonto/skills --skill <skill-name> --agent '*' --global
```

Installs are project-local unless you pass `--global`. Run `npx skills update`
to pull the latest.

### Claude Desktop and claude.ai

Paid plans only (Pro, Max, Team, Enterprise).

1. Open **Customize** in the left sidebar. In Cowork, open the **Cowork** tab first.
2. Go to **Plugins**, and under **Personal plugins** click **+**, then **Add marketplace**, then **Add from a repository**.
3. Paste `qonto/skills`, hit **Sync**, then **Install**.

The skills then appear under `/` and the `+` button, in chat and in Cowork.

### Claude Code

```
/plugin marketplace add qonto/skills
/plugin install qonto-skills@qonto
```

### Codex

```
codex plugin marketplace add qonto/skills
```

## Every skill is reviewed before it ships

These skills can issue cards, change card limits, send invoices to your clients
and raise spend requests, so we treat a skill as a dependency rather than as
documentation. Nothing lands on `main` without review by the Qonto team. We
check the instructions against the live API, verify that any bundled script does
what it claims, and reject anything reaching for data or credentials a task
doesn't need.

A skill is instructions, not credentials. None of them carry your API keys.
Everything runs through the [Qonto MCP server](https://docs.qonto.com/mcp/overview),
where you sign in as yourself and inherit exactly the permissions your Qonto
account already has. A skill cannot see or do anything you couldn't see or do in
the app, and your existing approval rules stay in force.

The repository is public, so read the skill before you install it. We would.

> [!TIP]
> Built something worth sharing? [Open a pull request](https://github.com/qonto/skills/compare)
> and fill in the template. Three things to know first.
>
> **Everything you submit becomes public and permanent.** A pull request is
> visible to anyone, and it stays in the git history even after an edit or a
> force push. Do not put anything in it that you would not publish on your own
> website. That covers credentials and API keys, real IBANs, account numbers and
> card numbers, customer and employee names, internal URLs and hostnames, and
> any business data you would rather keep to yourself. Use fabricated examples.
>
> **The Qonto team reviews every skill** before it is merged, and may request
> changes or decline it.
>
> **By opening a pull request you agree that your contribution may be published
> under the [MIT License](LICENSE)**, which lets anyone use, modify and
> redistribute it. Only submit work you are entitled to license this way.

<details>
<summary><b>Write a skill</b></summary>

Drop a folder under `skills/` with a `SKILL.md` in it:

```
skills/
└── my-skill/
    ├── SKILL.md          # required
    ├── references/       # optional, loaded on demand
    ├── scripts/          # optional
    └── assets/           # optional
```

```markdown
---
name: my-skill
description: What this does. Use when the user asks to [specific trigger].
---

# My Skill

The steps an agent should follow.
```

Four things trip people up. The directory name has to match the frontmatter
`name` exactly, and that name is lowercase letters, numbers and hyphens only.
The `description` is the only text an agent sees before deciding whether to load
your skill, so it needs to say both what the skill does and when to use it.
Keep `SKILL.md` under about 500 lines and push detail into `references/`.
Files sitting loose in `skills/` are ignored, so every skill needs its own
directory.

Run `claude plugin validate .` before opening a PR.

</details>

<details>
<summary><b>Repository layout</b></summary>

```
skills/                            the skills, one copy shared by everything
.claude-plugin/plugin.json         plugin identity for Claude
.claude-plugin/marketplace.json    catalog for Claude, also read by Codex
.agents/plugins/marketplace.json   catalog for Codex and ChatGPT Work
.codex-plugin/plugin.json          plugin identity for Codex
```

Adding a skill means adding a folder. The manifests don't change.

</details>

## Links

<details>
<summary><b>Qonto</b></summary>

- [MCP server](https://docs.qonto.com/mcp/overview), what these skills run on
- [MCP capabilities](https://docs.qonto.com/mcp/capabilities), everything the server can and cannot do
- [Connect the MCP server](https://docs.qonto.com/mcp/install/quickstart), for Claude, ChatGPT, Cursor, VS Code and others
- [Authentication](https://docs.qonto.com/mcp/authentication), who can connect and which permissions apply
- [Security](https://docs.qonto.com/mcp/security)
- [API documentation](https://docs.qonto.com)
- [Developer portal](https://developers.qonto.com)
- [Legal and privacy](https://legal.qonto.com/en)

</details>

<details>
<summary><b>New to MCP?</b></summary>

- [What is MCP](https://modelcontextprotocol.io/docs/getting-started/intro), the plain-English introduction
- [Connectors in Claude](https://support.claude.com/en/articles/11175166-about-custom-connectors-remote-mcp-servers), how to connect an MCP server to Claude
- [MCP in ChatGPT and Codex](https://learn.chatgpt.com/docs/extend/mcp)

</details>

<details>
<summary><b>Agent Skills</b></summary>

- [agentskills.io](https://agentskills.io), the open format these skills follow
- [Specification](https://agentskills.io/specification), frontmatter fields and progressive disclosure
- [anthropics/skills](https://github.com/anthropics/skills), reference skills worth reading before writing your own

</details>

<details>
<summary><b>Claude</b></summary>

- [Skills in Claude Code](https://code.claude.com/docs/en/skills)
- [Use skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude), the Desktop and web side
- [Plugins overview](https://claude.com/docs/plugins/overview)
- [Plugins reference](https://code.claude.com/docs/en/plugins-reference), manifest schema and component paths
- [Plugin marketplaces](https://code.claude.com/docs/en/plugin-marketplaces), how this repository is distributed
- [Connectors and MCP](https://claude.com/docs/connectors/overview)

</details>

<details>
<summary><b>ChatGPT and Codex</b></summary>

- [Codex plugins](https://developers.openai.com/codex/plugins)
- [Build plugins](https://developers.openai.com/codex/plugins/build), manifests and local marketplaces
- [Package your plugin](https://developers.openai.com/plugins/build/plugins)
- [Submit plugins](https://developers.openai.com/plugins/deploy/submission)

</details>

<details>
<summary><b>Other agents</b></summary>

- [Cursor](https://cursor.com/docs/context/skills)
- [GitHub Copilot](https://docs.github.com/en/copilot/concepts/agents/about-agent-skills)
- [Gemini CLI](https://geminicli.com/docs/cli/skills/)

</details>

MIT licensed. See [LICENSE](LICENSE).
