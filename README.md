# hugin-cowork

A Cowork plugin that helps **product designers and engineers ship design-to-production React apps** — translating Figma mockups into accessible, production-ready components with best-practice enforcement for React 19, TypeScript, Tailwind CSS v4, and shadcn/ui.

**22 skills**, **13 agents**, **6 MCP servers**, and **8 lifecycle hooks** covering the full stack: React 19, TypeScript, Express, Prisma, Tailwind CSS v4, shadcn/ui, Figma integration, accessibility, and testing.

Ported from [hugin-v0](https://github.com/michelve/hugin-v0) (the Claude Code CLI plugin).

## Skills (22)

| Skill                          | Description                                                              |
| ------------------------------ | ------------------------------------------------------------------------ |
| **accessibility**              | WCAG 2.1 AA — keyboard nav, ARIA, focus management, color contrast       |
| **adr-writer**                 | Write Architecture Decision Records in MADR 4.0.0 format                 |
| **automatic-code-review**      | Hook-driven semantic code review after file modifications                |
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
| **task-check**                 | Verify task completion against acceptance criteria                       |
| **web-design-guidelines**      | UI accessibility and design review                                       |
| **writing-tests**              | Test naming, assertions, edge case coverage (BugMagnet-based)            |

## Agents (13)

| Agent                          | Model  | Description                                                     |
| ------------------------------ | ------ | --------------------------------------------------------------- |
| **principal-engineer**         | opus   | First-principles engineering analysis and architectural reviews |
| **auto-error-resolver**        | sonnet | Systematically resolve TypeScript/build errors                  |
| **code-architecture-reviewer** | opus   | Review code for best practices and architectural consistency    |
| **code-refactor-master**       | sonnet | Refactor for better organization and cleaner architecture       |
| **documentation-architect**    | sonnet | Create and update comprehensive documentation                   |
| **plan-reviewer**              | opus   | Review development plans before implementation                  |
| **refactor-planner**           | sonnet | Analyze code structure and create refactoring plans             |
| **web-research-specialist**    | haiku  | Research solutions and best practices online                    |
| **automatic-code-reviewer**    | haiku  | Semantic code review using project-specific rules               |
| **task-check**                 | haiku  | Verify task completion before finishing work                    |
| **analyzer**                   | sonnet | Analyze blind comparison results for skill evaluation           |
| **comparator**                 | sonnet | Blind comparison of two outputs for skill evaluation            |
| **grader**                     | sonnet | Evaluate expectations against execution transcripts             |

## MCP Servers (6)

Configured in `.mcp.json` at the plugin root. Cowork auto-configures these servers when the plugin is installed. Directory servers (HTTP/SSE) appear in the Connectors UI; stdio servers run locally via `npx`.

| Server                  | Type  | Endpoint                             | Used by                                                |
| ----------------------- | ----- | ------------------------------------ | ------------------------------------------------------ |
| **figma**               | HTTP  | `https://mcp.figma.com/mcp`          | figma, figma-implement-design, code-connect-components |
| **miro-mcp**            | SSE   | `https://mcp.miro.com/sse`           | miro-mcp skill                                         |
| **context7**            | stdio | `@upstash/context7-mcp`              | Library documentation lookup                           |
| **playwright**          | stdio | `@playwright/mcp`                    | playwright-skill                                       |
| **sequential-thinking** | stdio | `@anthropic/sequential-thinking-mcp` | Complex reasoning tasks                                |
| **shadcn**              | stdio | `shadcn@latest mcp`                  | shadcn skill                                           |

## Hooks (8)

Lifecycle hooks in `hooks/hooks.json` provide setup checks, code quality guardrails, and automatic code review.

| Event                | Hook                     | Description                                               |
| -------------------- | ------------------------ | --------------------------------------------------------- |
| **SessionStart**     | session-start.sh         | Injects plugin context (agents, skills, MCP) into session |
| **PreToolUse**       | setup-env-check.py       | Verify environment variables and MCP servers              |
| **PreToolUse**       | commitlint-enforcer.py   | Enforce conventional commit messages (on Bash)            |
| **PreToolUse**       | anti-pattern-guard.py    | Guard against code anti-patterns (on Write/Edit)          |
| **UserPromptSubmit** | adr-gate.py              | Check for applicable Architecture Decision Records        |
| **UserPromptSubmit** | task-context-injector.py | Inject task context into prompts                          |
| **UserPromptSubmit** | inject-adr-context.py    | Inject ADR context into prompts                           |
| **PostToolUse**      | quality-gate-reminder.py | Remind about quality checks after file edits              |
| **PostToolUse**      | automatic-code-review    | Log file changes for review (on Write/Edit)               |
| **Stop**             | automatic-code-review    | Run semantic code review on all modified files            |

## Environment Variables

Some MCP servers authenticate via Cowork's connector UI (OAuth). The following env vars are only needed for stdio servers or manual overrides.

| Variable       | Used by               | Notes                                                       |
| -------------- | --------------------- | ----------------------------------------------------------- |
| `MIRO_API_KEY` | miro-mcp skill (opt.) | Only needed if your Miro board requires auth beyond the URL |

> **Figma**: Auth is handled automatically through Cowork's connector UI when using the HTTP directory server. No API key env var needed.

## Differences from hugin-v0 (CLI)

This is a full Cowork-compatible port of hugin-v0. The following CLI-only features are not included:

| Feature                 | Status     | Notes                                          |
| ----------------------- | ---------- | ---------------------------------------------- |
| Output Styles (4)       | Not ported | Cowork has no output style system              |
| LSP Server (TypeScript) | Not ported | Cowork has no .lsp.json support                |
| Agent Rules (8 JSON)    | Not ported | CLI-specific prompt/error/tool trigger configs |
| sync-schemas            | Removed    | CLI plugin schema maintenance                  |
| skill-creator           | Removed    | Builds CLI-format plugins                      |
| skill-developer         | Removed    | Deeply tied to CLI hook architecture           |

## Author

[michelve](https://github.com/michelve)
