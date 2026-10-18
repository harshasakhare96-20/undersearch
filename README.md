# AEO Service Console

A self-hosted workspace for delivering Answer Engine Optimization services to companies. It helps an operator onboard client brands, track buyer questions across AI answer experiences, compare brand and competitor visibility, analyze citations, and prepare reports.

This project is based on the open-source [GetCito](https://github.com/ai-search-guru/getcito-worlds-first-open-source-aio-aeo-or-geo-tool) AEO platform. The service offer, delivery workflow, initial workbench, and AEO branding in this repository are tailored for the AEO project. See [upstream and license notes](docs/upstream/UPSTREAM_AND_LICENSES.md).

## What is included

- A React/TypeScript dashboard with authenticated brand workspaces.
- Prompt and competitor tracking across configured answer/search providers.
- Scheduled background collection, response/citation analysis, and report generation.
- A PostgreSQL database and a REST API.
- Docker Compose setup for the web app, worker, database, migrations, and database admin UI.
- Agency service offer and operating procedure in [`docs/service`](docs/service/).
- The earlier lightweight browser-only prototype in [`docs/prototype`](docs/prototype/).

The codebase is an internal AEO service console to operate your service. The current local deployment is single-account/local mode; it is not yet a hosted multi-tenant client portal with separate client logins and subscription billing.

## Quick start with Docker

Prerequisites: Docker Desktop with Docker Compose enabled.

```bash
cp .env.example .env
```

Edit `.env` before starting:

- Set `BETTER_AUTH_SECRET` to a unique, random secret.
- Add valid provider credentials for the selected `SCRAPE_TARGETS` and `ONBOARDING_LLM_TARGET`.
- Keep `DISABLE_TELEMETRY=1` if you do not want product telemetry enabled.

Then build and start the application:

```bash
docker compose build
docker compose up -d
```

Open the app at [http://localhost:3001](http://localhost:3001). The first account registration creates the local operator account. Adminer is available at [http://localhost:8081](http://localhost:8081); PostgreSQL is exposed on `localhost:5433`.

To stop the stack:

```bash
docker compose down
```

The database persists in the `postgres_data` Docker volume. `docker compose down -v` deletes that volume and its data.

## Local development

Prerequisites: Node.js 24.x, pnpm 11.10.0, and PostgreSQL 16 or newer. Docker Compose can provide PostgreSQL if it is not already installed.

```bash
corepack enable pnpm
pnpm install
cp .env.example .env
cp apps/web/.env.example apps/web/.env
```

Set the database URL and provider credentials in both environment files as needed, then run:

```bash
pnpm dev
```

The web app runs on [http://localhost:3000](http://localhost:3000). The background worker reads `apps/web/.env` and is required for scheduled prompt checks and generated reports.

## Configure answer/search providers

The app separates collection providers from models. Configure `SCRAPE_TARGETS` using the `model:provider[:version][:online]` form, then provide the corresponding key in `.env`. For example:

```env
SCRAPE_TARGETS=chatgpt:openai-api
ONBOARDING_LLM_TARGET=chatgpt:openai-api
OPENAI_API_KEY=replace-with-your-key
```

Supported scraper/LLM providers and their environment variables are listed in [`.env.example`](.env.example) and validated in [`packages/config/src/env-registry.ts`](packages/config/src/env-registry.ts). Provider APIs and scraping vendors may charge separately; their usage and terms are your responsibility. Do not put real credentials in source control.

## AEO service workflow

1. Create a brand for the client and confirm the product, target market, competitors, and approved claims.
2. Build a stable set of real buyer questions across discovery, comparison, evaluation, and purchasing.
3. Configure the answer/search providers in scope and schedule collection.
4. Review each response and its sources; use brand/citation metrics as a directional sample, not as guaranteed engine rankings.
5. Turn accuracy, content, and citation gaps into prioritized work for the client.
6. Generate a report and compare it with analytics and qualified outcomes where client data supports the comparison.

Read the [AEO service offer](docs/service/aeo-service-offer.md) and [operator guide](docs/service/answer-visibility-workbench-guide.md) for package scope, pricing, reporting language, and the day-to-day delivery procedure.

## REA and website evidence

The repository at [`morluto/rea`](https://github.com/morluto/rea) is REA, an agent tool for evidence-backed inspection of websites, applications, and binaries. It is not an AEO application framework. The AEO product code here is based on GetCito; REA is documented as an optional development-time tool for inspecting websites you own or are authorized to assess. It is not installed as a production dependency. See [`docs/upstream/REA_WORKFLOW.md`](docs/upstream/REA_WORKFLOW.md).

## Architecture

- `apps/web` — TanStack Start dashboard and REST API.
- `apps/worker` — scheduled prompt collection, analysis, and reporting jobs.
- `packages/lib` — database, provider adapters, metrics, and business logic.
- `packages/config` — environment registry and shared configuration.
- `packages/api-spec` — OpenAPI schema.
- `packages/ui` — shared interface components.
- `docker` — multi-stage application container.

## Useful commands

```bash
pnpm dev       # run the web app and worker
pnpm build     # build the monorepo
pnpm lint      # lint with Biome
pnpm test      # run the existing unit suites
pnpm test:e2e  # run end-to-end tests (requires browser setup)
```

## Product limitations and measurement

- Answer outputs vary by platform, geography, account state, and time. An observed mention or citation rate describes the recorded prompt sample; it is not an internal provider ranking or a guarantee of future visibility.
- A successful run depends on configured provider credentials and their current API terms and availability.
- Google says its AI search experiences use existing Search systems and SEO fundamentals; no special schema or AI text file guarantees inclusion. See [Google Search Central](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide).
- ChatGPT search discovery depends on crawler access policy. Review [OpenAI's publisher guidance](https://help.openai.com/en/articles/12627856-publishers-and-developers-faq) before changing site access.

## License and upstream credits

The upstream product code is released under the MIT License. This repository retains [`LICENSE.md`](LICENSE.md), the upstream attribution, and GetCito's copyright notice. Review [upstream/license details](docs/upstream/UPSTREAM_AND_LICENSES.md) before distributing or offering hosted instances.
