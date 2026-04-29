# Cursor — project MCP servers

This folder configures project-scoped MCP servers used by Cursor (Desktop, Cloud Agents, CLI). Cursor reads `mcp.json` automatically when the workspace opens.

## What's wired

### `figma-developer-mcp` — Framelink MCP for Figma

The canonical community Figma MCP server ([`GLips/Figma-Context-MCP`](https://github.com/glips/figma-context-mcp), npm: [`figma-developer-mcp`](https://www.npmjs.com/package/figma-developer-mcp)). Translates Figma file/node data into compact, agent-friendly context — much smaller than raw API dumps, optimised for design-to-code prompts in Cursor.

Available tools after the MCP boots:

- `get_figma_data` — fetches a node's structure (frames, text, fills, strokes, layout) from `figma.com/design/<fileKey>?node-id=<nodeId>`.
- `download_figma_images` — exports raster (PNG/JPG) and vector (SVG) assets for a list of node IDs at a chosen scale.

## Authentication

The config reads the API token from the env var `FIGMA_API_KEY`. **Add it as a Cursor secret, not in this file.**

### For Cloud Agents

[cursor.com/dashboard](https://cursor.com/dashboard) → **Cloud Agents → Secrets** → New secret:

| Name | Value |
|---|---|
| `FIGMA_API_KEY` | (paste your token) |

Scope: user-level if it's your personal token; team / repo-level if shared. Secrets persist across runs and are injected into every new Cloud Agent VM as env vars.

### For Cursor Desktop / CLI

Set it in your shell profile (`~/.zshrc` / `~/.bashrc`):

```bash
export FIGMA_API_KEY="figd_..."
```

…or set it in a per-workspace `.env` and source it before launching Cursor.

### How to get the token

[figma.com/settings](https://www.figma.com/settings) → **Personal access tokens** → **Generate new token**. Required scopes:

- **File content** — read access (for `get_figma_data`)
- **Dev resources** — read access (for design tokens / variables, optional but recommended)

The token is a single string that starts with `figd_`. Treat it like a password.

## Quick test

Once `FIGMA_API_KEY` is set and the workspace is reloaded, ask the agent:

> "Use the figma MCP to read node `9:3558` from `figma.com/design/i9IzNaxwPCHiScbuxbhAqv/...`"

The agent should call `get_figma_data` and return the node tree. If it 401s, the token is wrong or missing scopes; if it 404s, the file isn't shared with the token's owner.

## Notes for this repo

- The `figma-developer-mcp` package is pinned to whatever `npx -y` resolves at run time (latest semver). To pin a specific version, edit the `args` in `mcp.json`:
  ```json
  "args": ["-y", "figma-developer-mcp@0.11.0", "--stdio"]
  ```
- The package is pre-fetched into the npm cache during the agent's first run — first call in a fresh VM may take ~5 s while npx cold-starts; subsequent calls are instant.
- The OD-style `f2c-mcp-*` Figma tools (Figma → code) are a different MCP and are configured via Cursor's global MCP marketplace, not this file. The two can coexist.
