# PLAN.md — adloop MVP v1

## Phase 0 — Setup
- Bun + TypeScript baseline
- decide API-first service shape
- Supabase project for shared state / monitoring UI
- Sentry baseline
- Playwright baseline for UI surfaces
- Vercel deployment for monitoring UI

## MVP Goal
Launch the first real internal version of Adloop that proves the product direction with a narrow but valuable workflow.

## First Test Build
Build the minimum product slice we can test end-to-end:
1. Authenticated monitoring/admin UI shell
2. Action log model + views
3. Campaign action command model (create/pause/resume/change budget as logged intents)
4. Meta integration adapter interface with mocked initial implementation if credentials are not ready
5. Reporting page shell
6. Deployment to Vercel for UI surface

## v1 Core Entities
- user
- workspace
- ad_account
- campaign
- action_log
- integration_connection

## v1 User Flow
1. Henry logs in
2. Sees monitoring dashboard
3. Sees campaign/action log timeline
4. Can trigger safe logged actions through controlled UI/API
5. Can review reporting shell

## Non-goals for first build
- full autonomous budget management
- full creative engine
- multi-client SaaS
- full production Meta execution without guardrails

## Done Criteria
- local dev runs
- auth works
- basic DB schema exists
- monitoring UI works
- action log persists and renders
- deployed preview works on Vercel
