# AGENTS.md — adloop

## Product Position

adloop is an internal tool first, built for Henry to operate Facebook ads workflows for infobusiness clients.
If it proves itself in real use, it becomes market-ready and can later serve both as:
- a standalone product, especially for the Brazilian market
- the paid-ads module inside Infoclaw

## First Jobs To Be Done

1. Campaign setup and management via agent-driven workflows
2. Reporting and operational visibility
3. Then choose between creative generation and budget management

This product is Meta/Facebook Ads only, focused on info-business specific paid acquisition.

## Non-Negotiable Engineering Rules

- Safety-first over speed theatrics.
- Schema-first always.
- Test-first always.
- Production-ready patterns from day one.
- Monitoring-first because this system can move money.
- Code quality target: 10/10.
- Minimum coverage target: 85%, focused on behavior.

AI is already fast. Do not optimize for recklessness.

## Standard Stack

- Package manager: Bun
- Language: TypeScript
- API-first design
- UI: monitoring/admin UI with polished startup-SaaS quality
- Database: Supabase Postgres + Drizzle where useful, or justify any local-state deviation explicitly
- Auth: Supabase Auth if/when multi-user surfaces exist
- Deployments: Vercel for UI surfaces; service/runtime architecture may differ if required
- Monitoring: Sentry + explicit action logs
- Browser verification: Playwright where UI exists

## Core Product Rules

- Meta API integration is required in MVP
- Logs are first-class product features
- Every operational action should be inspectable: campaign created, paused, resumed, budget raised, bug encountered, tracking error, etc.
- Prefer API-first internals with a monitoring UI on top

## Workflow Phases

Every substantial task should map to one of:
1. PLAN
2. CODE
3. REVIEW
4. DEPLOY

Tasks, prompts, and docs should be tagged by phase.

## Agent Workflow

- Mira is the orchestrator.
- Substantial coding should be delegated to background Claude Code runs.
- Different prompts/instructions may be used for PLAN, CODE, REVIEW, and DEPLOY phases.
- Do not mix unsafe action-taking with vague reasoning.

## Design Priorities

- Deterministic operational logs
- Reliable Meta API execution
- Clear approvals/visibility for money-affecting actions
- Monitoring UI that explains exactly what happened and why
- Reusability later inside Infoclaw

## Documentation Rules

When durable value is created, update repo files, not just chat.
At minimum update the relevant combination of:
- task docs
- architecture notes
- API contracts
- decisions
- setup docs
- action logging/monitoring docs

## What to Avoid

- Black-box ad decisions with no auditability
- Thin wrappers with weak logs
- Shipping money-moving behavior without observability
- Treating adloop as generic adtech instead of info-business-specific operations software
