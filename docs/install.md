# ai-workflow plugin installation

`ai-workflow` is a skills-only plugin. Its nine canonical Skills live in `skills/`; shared resources stay in `references/` and `templates/`. The plugin adds no MCP server and does not configure ADO. Each worker must configure its own authorized ADO MCP. This public distribution repository can be cloned without private source access.

## Codex

The root `plugin.json` uses the portable Agent Plugins format and discovers `skills/` at the plugin root. Codex CLI supports repo marketplaces through `.agents/plugins/marketplace.json`; this repository includes a local entry whose `source.path` is `.`. From a Codex CLI version supporting plugin marketplaces, run `codex plugin marketplace add <public-clone-path>`, inspect `codex plugin list --marketplace ai-workflow --available`, then install `ai-workflow@ai-workflow`. Clone https://github.com/vuthethienlong/ai-workflow-plugin to a local directory. Check for an existing `ai-workflow` marketplace/plugin name first; do not overwrite one. The marketplace add changes user-level Codex configuration; remove only the marketplace you added if cleanup is requested.

For project discovery, the committed `.agents/plugins/marketplace.json` points at this package. It does not alter `AGENTS.md` or existing repository instructions. If you copy Skills manually, copy the complete repository so `../../references/` and `../../templates/` links resolve.

## Claude Code

Claude Code reads `.claude-plugin/plugin.json` and the canonical root `skills/` directory. For a one-session local validation/use:

```powershell
claude --plugin-dir <path-to-local-ai-workflow-plugin>
```

For persistent user-scope or project-scope installation, add the public repository as a Claude Code marketplace, inspect available plugin names, then install `ai-workflow` with the desired scope (`user` or `project`). Use the public GitHub repository with the provider's supported install method. Review any existing marketplace/plugin name before adding or installing; do not overwrite settings or `CLAUDE.md`. Claude Code stores plugin selection in its settings; use the CLI rather than replacing existing settings manually.

## Runtime checks

Packaging validation checks manifest shape, skill discovery and relative resource links. A strict `claude plugin validate` or Codex `plugin list` result does not prove a plugin was enabled in an agent session. Verify provider runtime discovery separately in a clean test session; report any unavailable host/runtime rather than claiming success. Codex and Claude Code MCP configuration remains per worker and outside this plugin.
