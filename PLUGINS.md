# Plugin Installation Guide

This repository includes 13 official Claude Code plugins. This guide explains how to install and use them.

## Quick Start

1. **Install Claude Code** (if you haven't already):
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```

2. **Navigate to your project and start Claude Code:**
   ```bash
   cd /path/to/your/project
   claude
   ```

3. **Install plugins** using one of the two methods below.

---

## Installation Methods

### Method 1: `/plugin` command (interactive)

Inside a Claude Code session, run:
```
/plugin install <plugin-name>
```

For example:
```
/plugin install commit-commands
```

### Method 2: `settings.json` (recommended for teams)

Add a `plugins` marketplace entry to your project's `.claude/settings.json`, pointing at the `marketplace.json` in this repo:

```json
{
  "pluginMarketplaces": [
    {
      "source": "/path/to/claude-code/.claude-plugin/marketplace.json"
    }
  ],
  "plugins": [
    { "name": "commit-commands" },
    { "name": "code-review" }
  ]
}
```

Replace `/path/to/claude-code` with the actual path where you cloned this repository.

For user-wide installation (all projects), edit `~/.claude/settings.json` instead.

---

## Available Plugins

### Development

| Plugin | Description | Commands / Skills |
|--------|-------------|-------------------|
| [agent-sdk-dev](./plugins/agent-sdk-dev/) | Development kit for working with the Claude Agent SDK | `/new-sdk-app` |
| [claude-opus-4-5-migration](./plugins/claude-opus-4-5-migration/) | Migrate code and prompts from Sonnet 4.x / Opus 4.1 to Opus 4.5 | Skill: `claude-opus-4-5-migration` |
| [feature-dev](./plugins/feature-dev/) | 7-phase feature development workflow with specialized agents | `/feature-dev` |
| [frontend-design](./plugins/frontend-design/) | Production-grade frontend interfaces that avoid generic AI aesthetics | Auto-invoked skill |
| [plugin-dev](./plugins/plugin-dev/) | Toolkit for building new Claude Code plugins | `/plugin-dev:create-plugin` |
| [ralph-wiggum](./plugins/ralph-wiggum/) | Iterative self-referential AI loops for autonomous development | `/ralph-loop`, `/cancel-ralph` |

### Productivity

| Plugin | Description | Commands |
|--------|-------------|----------|
| [code-review](./plugins/code-review/) | Automated PR code review with 5 parallel agents and confidence scoring | `/code-review` |
| [commit-commands](./plugins/commit-commands/) | Git workflow automation | `/commit`, `/commit-push-pr`, `/clean_gone` |
| [hookify](./plugins/hookify/) | Create custom hooks from conversation patterns or explicit instructions | `/hookify`, `/hookify:list`, `/hookify:configure` |
| [pr-review-toolkit](./plugins/pr-review-toolkit/) | Comprehensive PR review (comments, tests, error handling, types, quality) | `/pr-review-toolkit:review-pr` |

### Learning

| Plugin | Description |
|--------|-------------|
| [explanatory-output-style](./plugins/explanatory-output-style/) | Adds educational insights about implementation choices (SessionStart hook) |
| [learning-output-style](./plugins/learning-output-style/) | Interactive learning mode that prompts you to contribute code at decision points |

### Security

| Plugin | Description |
|--------|-------------|
| [security-guidance](./plugins/security-guidance/) | Warns on security anti-patterns (command injection, XSS, eval, etc.) via PreToolUse hook |

---

## Plugin Structure Reference

Each plugin lives under `plugins/<name>/` and follows this layout:

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json       # Name, version, description, author
├── commands/             # Slash commands (.md files)
├── agents/               # Specialized agents (.md files)
├── skills/               # Reusable skills (SKILL.md + resources)
├── hooks/                # Event-driven automation
│   ├── hooks.json        # Hook configuration
│   └── *.py              # Hook implementations
├── .mcp.json             # MCP server config (optional)
└── README.md             # Plugin-specific documentation
```

See each plugin's `README.md` for detailed usage and configuration options.

---

## Further Reading

- [Official Plugin Documentation](https://docs.claude.com/en/docs/claude-code/plugins)
- [Claude Code Overview](https://docs.claude.com/en/docs/claude-code/overview)
- [Settings Reference](https://code.claude.com/docs/en/settings)
- [Agent SDK Documentation](https://docs.claude.com/en/api/agent-sdk/overview)
- [Example settings files](./examples/settings/)
