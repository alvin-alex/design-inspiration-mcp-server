# design-inspiration-mcp — third-party fork, actively modified

Upstream: https://github.com/YonasValentin/design-inspiration-mcp-server (author: Yonas
Valentin, MIT). Forked to alvin-alex/design-inspiration-mcp-server and cloned here
2026-08-29. Unlike this workspace's other third-party clones (`doctor-plus`, `octogent`,
`llm-council`, held at upstream for reference), this one is developed: SDK bumped, new
design sources added, then registered as a local MCP server for the Agentic planning
workspace.

## Map

A stdio MCP server, all in `src/index.ts`. The search tools call Serper; token extraction
shells out to the `dembrandt` CLI (installed globally, not an npm dependency).

Full history and the adoption rationale live in
`~/Documents/Agentic/archive-plans/[DONE] - design-inspiration-mcp-fork-2026-08-29.md` — read that
before changing scope here.

Plans go in `Active/`, then `Archive/` once done.

## Project-specific rules

- `SERPER_API_KEY` is a credential: goes in an env file the server reads itself, never in
  argv or the MCP registration command, never echoed.
- Don't reset this tree to upstream — the SDK bump and added sources are intentional local
  changes, not drift to undo.

## Quality gates

`npm run build` (tsc, no `any` used to silence errors) is the only gate. Upstream shipped no tests.
