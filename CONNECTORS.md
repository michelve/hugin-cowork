# Connectors

## How tool references work

This plugin integrates with external design and collaboration tools via MCP servers. Cowork will prompt you to connect each service when the plugin is installed. Skills that depend on a connector will note the requirement in their description.

## Connectors for this plugin

| Category        | Server              | Service | Skills that use it                                     |
| --------------- | ------------------- | ------- | ------------------------------------------------------ |
| Design          | figma               | Figma   | figma, figma-implement-design, code-connect-components |
| Collaboration   | miro-mcp            | Miro    | miro-mcp                                               |
| Browser testing | playwright          | —       | playwright-skill                                       |
| UI components   | shadcn              | —       | shadcn                                                 |
| Documentation   | context7            | —       | All skills (library documentation lookup)              |
| Reasoning       | sequential-thinking | —       | Complex multi-step tasks                               |

## Connection types

- **figma** — HTTP connector via Cowork directory. Connect through Cowork's connector UI; authentication is handled automatically.
- **miro-mcp** — SSE connector. Connect through Cowork's connector UI; requires Miro account authorization.
- **playwright**, **shadcn**, **context7**, **sequential-thinking** — Local stdio servers. These run automatically via `npx` when a skill invokes them. No manual connection required.
