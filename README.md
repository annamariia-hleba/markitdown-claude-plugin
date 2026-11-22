# MarkItDown plugin for Claude Code

A Claude Code plugin that adds [Microsoft MarkItDown](https://github.com/microsoft/markitdown) as an MCP server, so Claude can convert PDF, Word, PowerPoint, Excel, HTML, images, audio, YouTube links and more into Markdown.

## Requirements

[uv](https://docs.astral.sh/uv/getting-started/installation/) must be installed (`uvx` on PATH). The plugin runs `markitdown-mcp` via `uvx`, so you don't need to `pip install` anything.

```bash
# macOS / Linux
curl -LsSf https://astral.sh/uv/install.sh | sh
# Windows (PowerShell)
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

## Install

Inside Claude Code:

```
/plugin marketplace add annamariia-hleba/markitdown-claude-plugin
/plugin install markitdown@markitdown-tools
```

Or from the terminal:

```bash
claude plugin marketplace add annamariia-hleba/markitdown-claude-plugin
claude plugin install markitdown@markitdown-tools
```

Restart Claude Code, then check with `/mcp` — you should see `markitdown` connected.

## Use

Just ask, e.g. *"Summarize ~/Downloads/report.pdf"* or *"Extract the tables from budget.xlsx"*. Claude calls the `convert_to_markdown` tool with a `file://`, `https://` or `data:` URI.

## Enable for a whole project

Add to the project's `.claude/settings.json` so everyone who opens the repo is offered the plugin:

```json
{
  "extraKnownMarketplaces": {
    "markitdown-tools": {
      "source": { "source": "github", "repo": "annamariia-hleba/markitdown-claude-plugin" }
    }
  },
  "enabledPlugins": { "markitdown@markitdown-tools": true }
}
```

## Update

```
/plugin marketplace update markitdown-tools
```

## Structure

```
.claude-plugin/marketplace.json      # marketplace catalog
plugins/markitdown/
  .claude-plugin/plugin.json         # plugin manifest
  .mcp.json                          # MCP server (uvx markitdown-mcp)
  skills/markitdown/SKILL.md         # tells Claude when/how to use it
```

MarkItDown is © Microsoft, MIT License. This repository only contains configuration.
