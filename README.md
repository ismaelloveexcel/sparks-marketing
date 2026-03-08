# Sparks Marketing

Public landing site and content pipeline for **Spark** — built with [Next.js](https://nextjs.org/) (App Router).

[![CI](https://github.com/ismaelloveexcel/sparks-marketing/actions/workflows/ci.yml/badge.svg)](https://github.com/ismaelloveexcel/sparks-marketing/actions/workflows/ci.yml)

---

## What this repo is

This is the **public-facing marketing site** for Spark, including:

- Landing pages and marketing copy
- SEO metadata and Open Graph assets
- A structured **content pipeline** for the editorial calendar, video scripts, and social captions
- Press-kit downloads served from `public/presskit/`

> ⚠️ This is a public repository. Do **not** commit secrets, API keys, or any internal/private information.

---

## Quickstart

```bash
# 1. Install dependencies
npm install

# 2. Run the development server (http://localhost:3000)
npm run dev

# 3. Production build (must pass before merging any PR)
npm run build

# 4. Start the production server
npm run start
```

---

## Folder structure

```
sparks-marketing/
├── app/                  # Next.js App Router — pages & layouts
├── components/           # Shared UI components
├── public/
│   └── presskit/         # Press-kit assets (logos, brand guidelines, screenshots)
├── content/
│   ├── calendar/         # Editorial calendar drafts (markdown / CSV)
│   ├── scripts/          # Video & reel scripts
│   └── captions/         # Social media captions
├── styles/               # Global CSS (if separate from app/globals.css)
├── AGENTS.md             # Agent guide — conventions, commands, quality gates
└── .github/
    ├── workflows/ci.yml  # Continuous integration
    ├── PULL_REQUEST_TEMPLATE.md
    └── ISSUE_TEMPLATE/agent-task.md
```

### `content/` conventions

| Folder | What goes here |
|---|---|
| `content/calendar/` | Dated editorial-calendar entries (`YYYY-MM-DD-<slug>.md`) |
| `content/scripts/` | Video and reel scripts (`YYYY-MM-DD-<slug>.md`) |
| `content/captions/` | Social captions ready to publish (`YYYY-MM-DD-<slug>.txt`) |
| `public/presskit/` | Static press-kit files served at `/presskit/<filename>` |

---

## Deployment

Deployment is managed via **[Vercel](https://vercel.com)** (recommended).

- Connect the repository to a Vercel project.
- Set any required environment variables in the Vercel dashboard — **never commit them here**.
- Every push to `main` triggers a production deployment; every PR gets a preview deployment automatically.

---

## Cross-repo boundaries

| Repo | Purpose |
|---|---|
| **`ismaelloveexcel/sparks-marketing`** | ← you are here — public site & content pipeline |
| `ismaelloveexcel-sparks-mobile` | Mobile app (iOS / Android) |
| `ismaelloveexcel-sparks-agents` | Agents API / backend services |

Changes that span repos (e.g., a new API endpoint consumed by the landing page) require coordinated PRs — reference each PR in the other.

---

## Contributing

1. Branch from `main`.
2. Make your changes; run `npm run build` to verify.
3. Open a PR using the provided template.
4. CI must be green before merging.

See [AGENTS.md](./AGENTS.md) for full architecture conventions and quality gates.