# Sparks Marketing — Agent Guide

## Purpose

This repository hosts the **public marketing site and content pipeline for Spark**.

- Public landing pages built with **Next.js App Router**
- Content pipeline folders for the social/editorial calendar, video scripts, and captions
- Press kit assets under `public/presskit/`

## Non-Goals

- No private or internal product strategy documents
- No secrets, API keys, backend credentials, or environment-specific config values
- No backend services or databases (see the agents API repo for that)

## Commands

```bash
# Install dependencies
npm install

# Start the development server
npm run dev

# Production build (must pass before merging)
npm run build

# Start the production server
npm run start

# Lint (if the script exists)
npm run lint

# TypeScript type-check (if the script exists)
npm run typecheck
```

> If `lint` or `typecheck` scripts are absent from `package.json`, skip those steps — CI handles this gracefully.

## Architecture Conventions

| Concern | Location |
|---|---|
| App Router pages & layouts | `app/` |
| Shared UI components | `components/` |
| Global styles | `app/globals.css` or `styles/` |
| Static assets (images, fonts) | `public/` |
| Press kit downloads | `public/presskit/` |
| Editorial calendar drafts | `content/calendar/` |
| Video / reel scripts | `content/scripts/` |
| Social media captions | `content/captions/` |

### Next.js App Router conventions

- Pages are defined in `app/**/page.tsx` (or `.jsx`).
- Layouts wrap shared chrome in `app/**/layout.tsx`.
- Server Components are the default; opt into Client Components only when interactivity requires it (`"use client"`).
- Images should use `next/image` for automatic optimisation.
- Links should use `next/link`.

### Content pipeline conventions

- Files in `content/` are markdown, plain text, or CSV — **no credentials**.
- Filenames should follow `YYYY-MM-DD-<slug>.<ext>` where a date is relevant.

## Quality Gates

Before a PR can be merged:

1. `npm run build` exits with code 0 (zero type errors, no missing imports).
2. No secrets or credentials are committed (CI and secret-scanning check this).
3. GitHub Actions CI is green.
4. PR description is filled in (see `.github/PULL_REQUEST_TEMPLATE.md`).

## Cross-Repo Boundaries

| Repo | Purpose | Link |
|---|---|---|
| `ismaelloveexcel/sparks-marketing` | **This repo** — public site & content pipeline | — |
| `ismaelloveexcel-sparks-mobile` | Mobile app (iOS/Android) | — |
| `ismaelloveexcel-sparks-agents` | Agents API / backend services | — |

> Changes that span repos require coordinated PRs. Reference the related PR in each PR description.
