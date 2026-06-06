# Deploy-Bot Skill

Deploy-Bot is an installable AI skill for turning an unknown codebase into a practical AWS, Azure, GCP, or hybrid cloud deployment package.

## What it does

- Inspects the user's codebase and detects app/runtime/dependency signals.
- Runs a short deployment interview to gather missing requirements.
- Recommends AWS, Azure, GCP, or hybrid architecture.
- Produces a deployment diagram, cloud service matrix, infrastructure plan, CI/CD guidance, security checklist, runbook, and cost/scaling notes.

## Skill structure

```text
SKILL.md
references/
  aws.md
  azure.md
  gcp.md
templates/
  interview.md
  service-matrix.md
```

## Install/use

Download this repository as a ZIP or clone it into your skills directory.

```bash
git clone https://github.com/rustyfus-maker/deploy-bot-skill.git
```

Then point your agent/skill loader at the cloned folder.
