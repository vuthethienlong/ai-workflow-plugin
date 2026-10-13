# ADO MCP boundaries

- Use only the executing Codex or Claude Code worker's previously configured Azure DevOps MCP tools for ADO reads and writes. Orca is not an ADO API client.
- Before relying on ADO, confirm the needed MCP tool and permissions are available. Never request, print, or save access tokens in package artifacts.
- If reads are unavailable, continue only with user-provided context and label duplicate/hierarchy checks unavailable. Do not invent IDs or claim verification.
- No writes during brainstorming or proposal review. Before writes, show the exact approved item types, titles, descriptions, parent links, and operation. Write only those items after explicit approval.
- Check existing items and uncertain retries before creation; verify returned IDs, URLs, and hierarchy. Report partial failures.
- ChatGPT sessions must not assume access to another worker's MCP.
