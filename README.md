# tyr — SaaS Infrastructure for Coding Agents

The `tyr` CLI gives your coding agent full control of [tyga.run](https://tyga.run) — the platform that runs your SaaS. 48 modules, 4,600+ endpoints, zero dependencies.

Your agent manages users, billing, scheduling, support, CRM, compliance, and more — all from the terminal.

## Early Access

tyga.run is in **closed beta**. [Join the waitlist](https://tyga.run/waitlist) to get your API key.

Already have access? Install and go:

## Install

```bash
npm install -g tygarun
```

## Quick Start

```bash
# Create your SaaS
tyr signup my-project --local

# Check status
tyr status

# Manage users
tyr users
tyr user create "alice@company.com" --role admin

# Subscription plans
tyr plans
tyr plan create "Pro" --price 29.99 --interval monthly

# Support tickets
tyr ticket create "Dashboard loading slow" -p high

# CRM
tyr lead create "John Smith" --email john@co.com

# Compliance (ISO 27001)
tyr compliance dashboard
tyr compliance policies create --framework iso27001

# Call ANY of 4,600+ endpoints
tyr api GET /scheduling/bookings
tyr api POST /ecommerce/catalog --data '{"name":"Widget","price":9.99}'

# Full reference
tyr --help
```

## 48 SDK Modules

Every module is a first-class CLI command:

| Category | Modules |
|----------|---------|
| **Identity** | `users`, `keys`, `orgs`, `members`, `workspaces` |
| **Billing** | `plans`, `invoices`, `subscriptions`, `payments`, `coupons` |
| **Scheduling** | `bookings`, `availability`, `event-types`, `meetings` |
| **CRM** | `leads`, `opportunities`, `pipelines`, `campaigns` |
| **Support** | `tickets`, `kb`, `agents` |
| **Ecommerce** | `products`, `orders`, `carts`, `collections` |
| **Compliance** | `dashboard`, `audit-trail`, `access-review`, `dpa`, `sub-processors`, `policies` |
| **Content** | `pages`, `blogs`, `forms`, `newsletters`, `courses` |
| **AI** | `ai chat`, `ai agents`, `ai image` |
| **Analytics** | `analytics events`, `analytics metrics`, `analytics dashboard` |
| **Communication** | `channels`, `posts`, `notifications`, `email` |
| **Infrastructure** | `domains`, `webhooks`, `hosting`, `maps`, `files` |

Plus `tyr api` — a raw escape hatch to call any endpoint directly.

## Agent Integration

Works with every agent platform:

```bash
tyr init    # auto-detects your agent, shows config snippet
```

| Agent | Config File | Supported |
|-------|-------------|-----------|
| Claude Code | `CLAUDE.md` + `.mcp.json` | MCP native tools |
| Cursor | `.cursorrules` | CLI commands |
| Cline | `.clinerules` | CLI commands |
| Windsurf | `.windsurfrules` | CLI commands |
| Aider | `AGENTS.md` | CLI commands |
| Codex | `AGENTS.md` | CLI commands |

## MCP Server (Claude Code)

Native tool integration — Claude Code discovers `tyr` tools automatically:

```json
{
  "mcpServers": {
    "tygarun": {
      "type": "stdio",
      "command": "tyr",
      "args": ["mcp-serve"]
    }
  }
}
```

14 built-in tools including `tygarun_api` — the escape hatch that gives your agent access to all 4,600+ endpoints as a native tool.

## Per-Project Config

```bash
tyr login --local --key YOUR_KEY    # saves to .tyr/config.json (project)
tyr login --key YOUR_KEY            # saves to ~/.tyr/config.json (global)
tyr config                          # show active config
```

Config priority: `--key` flag > `TYR_API_KEY` env > `.tyr/config.json` (local) > `~/.tyr/config.json` (global)

## Usage Tracking

Every CLI call includes `X-Tyr-Module` and `X-Tyr-Command` headers for per-module usage metering. Track what your agents use, rate-limit by plan tier, bill per call.

## Zero Dependencies

Built with Node.js built-in modules only. No `axios`, no `commander`, no `chalk`. One `npm install`, works everywhere.

## Documentation

- [tyga.run](https://tyga.run) — Platform
- [Documentation](https://tyga.run) — Platform docs
- [llms.txt](https://tyga.run/llms.txt) — Machine-readable API reference

## License

Proprietary — Tyga.Cloud Ltd. See [LICENSE](./LICENSE).
