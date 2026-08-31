# design-inspiration-mcp — third-party fork, actively modified

Upstream: https://github.com/YonasValentin/design-inspiration-mcp-server (author: Yonas
Valentin, MIT). Forked to alvin-alex/design-inspiration-mcp-server and cloned here
2026-08-29. Unlike this workspace's other third-party clones (`doctor-plus`, `octogent`,
`llm-council`, held at upstream for reference), this one is developed: SDK bumped, new
design sources added, then registered as a local MCP server for the Agentic planning
workspace.

## What it is

A stdio MCP server, single file `src/index.ts`. Four tools: `design_search_images`,
`design_search_references`, `design_search_styles`, `design_extract_tokens`. Search tools
call Serper (`SERPER_API_KEY`, not vendored — reads the env var itself); token extraction
shells out to the `dembrandt` npm CLI.

Full history and the adoption rationale live in
`~/Documents/Agentic/archive-plans/[DONE] - design-inspiration-mcp-fork-2026-08-29.md` — read that
before changing scope here.

## Stack

- Node >=18, plain `tsc` build: `npm install && npm run build` → `dist/index.js`.
- `npm run clean` removes `dist/`.
- No lint/test scripts upstream shipped none.

## Where context lives

`Active/` for in-progress notes on this fork, `Archive/` once done. Durable reference (if
any accumulates) goes in a docs folder created when there's something to put in it.

## Project-specific rules

- `SERPER_API_KEY` is a credential: goes in an env file the server reads itself, never in
  argv or the MCP registration command, never echoed.
- Don't reset this tree to upstream — the SDK bump and added sources are intentional local
  changes, not drift to undo.

## Quality gates

`npm run build` (tsc, no `any` used to silence errors) is the only gate. No test suite
shipped upstream.
