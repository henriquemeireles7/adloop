# adloop

A self-improving Meta ads management system for infoproduct businesses.

The product is not the ads — it is the loop:

```
PLAYBOOK -> EXECUTE -> LOG (with reasoning) -> MEASURE -> UPDATE PLAYBOOK
```

Every action is logged with why it was taken. The playbook evolves daily based on measured outcomes.

## What adloop does

- Finds your highest-revenue historical periods ("Golden Eras")
- Replicates them exactly as a "Recipe"
- Measures against server-side truth (CAPI + checkout, not just Facebook)
- Logs every decision with full reasoning
- Updates its own rules nightly based on evidence

## Stack

- **Runtime:** Node.js + TypeScript
- **CLI:** Commander
- **Database:** SQLite (better-sqlite3) + Drizzle ORM
- **Validation:** Zod
- **Testing:** Vitest
- **AI:** Claude API (creative generation only — decisions are deterministic)
- **Deployment:** NanoClaw (Slack bot + cron + container isolation)

## Status

**Pre-development.** Project scaffolding in place. See [PLAN.md](./PLAN.md) for the full system specification.

## Project structure

```
src/
  cli/        # Commander command definitions
  engines/    # Business logic (the unique code)
  db/         # Drizzle schema + migrations
  schemas/    # Zod validation schemas
  lib/        # SDK wrappers, output formatting
  index.ts    # CLI entrypoint
docs/         # Architecture and design docs
PLAN.md       # Full system specification
AGENTS.md     # Instructions for AI agents
```

## Getting started

> Not yet ready for development. Prerequisites will be documented as setup progresses.

1. `npm install`
2. `npm run build`
3. `adloop init` — bootstraps `.adloop/` directory with config, DB, and playbook

## Build order

See PLAN.md section 15 for the full milestone plan. Summary:

0. **Scaffold** — project init, deps, `adloop --help`
1. **Truth Foundation** — sync, measure, CAPI, safety, status
2. **Replication Engine** — golden era detection, recipe extraction, plan, execute
3. **Playbook Evolution** — nightly scoring, rule updates, memory search
4. **Creative Atoms** — hook/body/CTA decomposition, scoring, recombination
5. **Slack Integration** — NanoClaw fork, Slack bot, approval workflow
6. **Creative Generation** — Claude API text gen, asset inbox
7. **Dashboard + Hardening** — terminal/web dashboard, circuit breaker
