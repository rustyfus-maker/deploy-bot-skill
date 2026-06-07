---
name: deploy-bot
description: Use this skill whenever a user wants to deploy an app, asks how to host code on AWS, Azure, GCP, Vercel, Railway, PaaS platforms, or multiple clouds, needs infrastructure-as-code or platform deployment settings, wants a deployment diagram, or is unsure which cloud services match their codebase. This skill inspects the project, interviews the user briefly, recommends a cloud/PaaS architecture, and produces a deployment package with diagrams, service tables, and implementation steps.
---

# Deploy-Bot

Deploy-Bot turns an unknown codebase into a practical cloud or PaaS deployment plan. It is for users who say things like “I have this app and no idea how to deploy it,” “put this on AWS/Azure/GCP,” “deploy this to Vercel/Railway,” “make a deployment package,” or “what cloud services do I need?”

## Outcomes

Produce a deployment package that includes:

1. **Codebase assessment** — what the app appears to be, key components, runtime assumptions, and deployment blockers.
2. **Short interview** — only the questions needed to remove important ambiguity.
3. **Provider decision** — AWS, Azure, GCP, Vercel, Railway, PaaS split, or multi-cloud/hybrid, with rationale.
4. **Deployment diagram** — Mermaid diagram by default, plus notes for turning it into an image.
5. **Service recommendation table** — service, problem solved, why it fits, alternatives, and risk/cost notes.
6. **Infrastructure package plan** — Terraform by default unless the user prefers CDK, Bicep, Pulumi, Kubernetes, or platform-native config.
7. **CI/CD plan** — GitHub Actions by default unless another system is present.
8. **Security and operations checklist** — secrets, identity, network boundaries, logging, monitoring, backups, scaling, and rollback.

## Workflow

### 1. Inspect the codebase first

Look for these signals before asking questions:

- Package and lock files: `package.json`, `requirements.txt`, `pyproject.toml`, `go.mod`, `pom.xml`, `*.csproj`, `Cargo.toml`.
- App frameworks: Next.js, React, Vite, Express, FastAPI, Django, Flask, Spring, .NET, Rails, Laravel, Go services.
- Runtime/deployment files: `Dockerfile`, `docker-compose.yml`, `Procfile`, `vercel.json`, `railway.json`, `nixpacks.toml`, `serverless.yml`, `kubernetes/`, `helm/`, `terraform/`, `infra/`.
- Data dependencies: migrations, ORM configs, database env vars, seed files, queue/cache clients.
- External services: auth, email, storage, payments, webhooks, AI APIs.
- Ports and processes: dev scripts, start scripts, worker scripts, cron/scheduled jobs.
- Build output: static site, SSR app, API server, background worker, mobile backend, monorepo.

Summarize findings in plain language. State uncertainty explicitly.

### 2. Ask a short interview

Ask no more than 8 questions at once. Prefer multiple-choice questions when possible.

Core questions:

1. Which target do you prefer: Vercel, Railway, Vercel + Railway, AWS, Azure, GCP, cheapest viable, easiest managed path, or multi-cloud?
2. Is this for demo, staging, production, or enterprise production?
3. Expected traffic now and in 12 months?
4. Does the app need a database, file uploads, background jobs, queues, cron, or real-time websockets?
5. What secrets and third-party APIs are required?
6. Any compliance, region, private network, or data retention constraints?
7. Preferred deployment style: PaaS/Git-connected, serverless, containers, Kubernetes, VM, or “choose for me”?
8. Should the package include Terraform, platform config (`vercel.json`/Railway settings), provider-native IaC, GitHub Actions, Docker, or all of these?

If the user cannot answer, choose safe defaults and label them as assumptions.

### 3. Choose architecture patterns

Use the simplest reliable architecture that matches the code and user constraints.

Default preferences:

- Static/frontend app: Vercel or CDN + object/static hosting.
- SSR or full-stack JavaScript: Vercel for frontend/SSR when suitable, otherwise managed app hosting, container runtime, or serverless container.
- API/backend: Railway for simple Git-connected backends/databases when suitable, otherwise managed container or serverless function depending on runtime shape.
- Database: managed relational database for relational schemas; document/key-value only when app shape supports it.
- Secrets: managed secret store, never plaintext env files in repositories.
- CI/CD: Platform Git integration for Vercel/Railway, or GitHub Actions with environment protection and least-privilege cloud credentials when extra checks/IaC are needed.
- Observability: platform/provider-native logs/metrics/alerts first.

Read provider references as needed:

- `references/aws.md`
- `references/azure.md`
- `references/gcp.md`
- `references/paas.md` for Vercel, Railway, and Vercel + Railway deployments

### 4. Produce the deployment package

Create or propose this structure:

```text
deploy-package/
├── README_DEPLOY.md
├── architecture/
│   ├── deployment-diagram.mmd
│   └── service-matrix.md
├── infra/
│   ├── terraform/              # default IaC path for cloud providers
│   └── platform/               # Vercel/Railway settings when PaaS is selected
├── cicd/
│   └── github-actions.yml      # optional when platform Git deploys are enough
├── ops/
│   ├── security-checklist.md
│   ├── runbook.md
│   └── cost-notes.md
└── assumptions.md
```

If writing files directly, do not overwrite existing infrastructure without asking.

## Required report format

Use this structure in your final answer or in `README_DEPLOY.md`:

```markdown
# Deployment Plan for [App Name]

## Executive Summary
- Recommended provider:
- Recommended pattern:
- Estimated complexity:
- Key assumptions:

## What I Found in the Codebase

## Questions Asked and Answers

## Recommended Architecture

## Deployment Diagram

```mermaid
flowchart LR
  User[Users] --> CDN[CDN / Edge]
  CDN --> App[Application Runtime]
  App --> DB[(Managed Database)]
  App --> Secrets[Secret Manager]
  App --> Logs[Logs and Metrics]
```

## Cloud Service Matrix
| Need | Recommended Service | Problem It Solves | Why This Fits | Alternatives | Notes/Risks |
|---|---|---|---|---|---|

## Deployment Package Contents

## Step-by-Step Deployment

## Security Checklist

## Operations Runbook

## Cost and Scaling Notes

## Open Decisions
```

## Safety and quality rules

- Do not claim the package is production-ready unless security, backups, rollback, monitoring, and access control are addressed.
- Do not hard-code secrets.
- Prefer least-privilege identity and short-lived cloud credentials.
- Surface cost-impacting decisions such as NAT gateways, always-on databases, Kubernetes clusters, and cross-region traffic.
- If the codebase is incomplete, give a partial plan and list what is missing.
- If a cloud choice is unsafe or overcomplicated, explain the tradeoff and suggest a simpler path.
