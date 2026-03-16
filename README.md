# hugin-cowork

A Cowork plugin that helps **product designers and engineers ship design-to-production React apps** — translating Figma mockups into accessible, production-ready components with best-practice enforcement for React 19, TypeScript, Tailwind CSS v4, and shadcn/ui.

**20 skills** covering the full stack: React 19, TypeScript, Express, Prisma, Tailwind CSS v4, shadcn/ui, Figma integration, accessibility, and testing.

Ported from [hugin-v0](https://github.com/michelve/hugin-v0) (the Claude Code CLI plugin) with CLI-only features (hooks, agents, output styles) removed for Cowork compatibility.

## Skills (20)

| Skill                          | Description                                                              |
| ------------------------------ | ------------------------------------------------------------------------ |
| **accessibility**              | WCAG 2.1 AA — keyboard nav, ARIA, focus management, color contrast       |
| **adr-writer**                 | Write Architecture Decision Records in MADR 4.0.0 format                 |
| **code-connect-components**    | Connect Figma components to code via Code Connect                        |
| **component-visualizer**       | Generate interactive HTML dependency graphs for React components         |
| **create-design-system-rules** | Generate project-specific design system Figma-to-code rules              |
| **create-tasks**               | Break PRDs into well-formed, INVEST-compliant tasks                      |
| **figma**                      | Fetch design context, screenshots, variables from Figma MCP              |
| **figma-implement-design**     | Translate Figma nodes into production-ready code                         |
| **miro-mcp**                   | Create diagrams, tables, docs on Miro boards via MCP                     |
| **nodejs**                     | Node.js backend patterns — async/await, middleware, layered architecture |
| **playwright-skill**           | Browser automation, e2e testing, UI validation                           |
| **prisma**                     | Prisma Client queries, schema, migrations, transactions                  |
| **react**                      | React 19 hooks, Suspense, lazy loading, TypeScript patterns              |
| **react-best-practices**       | Vercel Engineering performance optimization guidelines                   |
| **route-tester**               | HTTP API route testing, auth strategies, integration tests               |
| **setup**                      | Verify environment, API keys, and tool availability                      |
| **shadcn**                     | shadcn/ui component management — add, search, fix, compose               |
| **tailwindcss**                | Tailwind CSS v4 utility-first styling, responsive, dark mode             |
| **web-design-guidelines**      | UI accessibility and design review                                       |
| **writing-tests**              | Test naming, assertions, edge case coverage (BugMagnet-based)            |

## Environment Variables

Some skills require API keys. Set them in your shell before launching Cowork.

| Variable         | Used by                                | Get it from                                                        |
| ---------------- | -------------------------------------- | ------------------------------------------------------------------ |
| `FIGMA_API_KEY`  | figma, figma-implement-design skills   | [Figma → Settings → Personal access tokens](https://www.figma.com/developers/api#access-tokens) |
| `MIRO_API_KEY`   | miro-mcp skill (optional)              | Only needed if your Miro board requires auth beyond the web URL    |

## Differences from hugin-v0 (CLI)

This is a Cowork-compatible subset of hugin-v0. The following CLI-only features are not included:

| Feature                  | Status      | Notes                                                  |
| ------------------------ | ----------- | ------------------------------------------------------ |
| Hooks (8 event hooks)    | Not ported  | Cowork has no hook system                              |
| Agents (13 personas)     | Not ported  | Cowork has no agent persona system                     |
| Output Styles (4)        | Not ported  | Cowork has no output style system                      |
| LSP Server (TypeScript)  | Not ported  | Cowork has no .lsp.json support                        |
| MCP Servers (7)          | Not ported  | Cowork has no .mcp.json support                        |
| automatic-code-review    | Removed     | Depends on PostToolUse/Stop hooks                      |
| task-check               | Removed     | Depends on hook-driven agent spawning                  |
| sync-schemas             | Removed     | CLI plugin schema maintenance                          |
| skill-creator            | Removed     | Builds CLI-format plugins                              |
| skill-developer          | Removed     | Deeply tied to CLI hook architecture                   |

## Author

[michelve](https://github.com/michelve)
