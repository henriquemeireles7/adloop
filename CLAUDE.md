# CLAUDE.md — adloop

## What is this project?

adloop is a CLI-first Meta ads management system. See PLAN.md for full spec, AGENTS.md for architecture overview.

## Commands

```bash
npm run build          # Compile TypeScript
npm run dev            # Watch mode
npm test               # Run vitest
npm run lint           # ESLint
npm run db:generate    # Generate Drizzle migrations
npm run db:migrate     # Apply migrations
```

## Code style

- TypeScript strict mode. No `any` unless absolutely necessary.
- Use Zod schemas for all external data validation (API responses, config files, user input).
- Use Drizzle ORM for all database access. No raw SQL except for FTS5 queries.
- Every engine function that takes an action must log to the action log with: `why`, `rule_id`, `evidence_refs`, `confidence`.
- CLI commands go in `src/cli/`, business logic in `src/engines/`. Keep them separate.
- Output format: every command must support `--robot` (compact JSON) and `--json` (pretty) flags.

## Testing

- Use Vitest. Tests go next to source files as `*.test.ts` or in `__tests__/` directories.
- Engine tests should use in-memory SQLite.
- Mock external APIs (Facebook SDK, Claude API) in tests.

## Important constraints

- Claude/LLM never makes ad decisions. The playbook makes decisions. Claude is only used for creative text generation and natural language translation.
- The action log is append-only. Never delete or modify past entries.
- `.adloop/` directory is gitignored — it contains user data and secrets.
- Never commit API keys or secrets.
