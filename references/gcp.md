# GCP Reference

Use these common mappings when GCP is selected.

| Need | GCP service | Problem solved | Notes |
|---|---|---|---|
| Static web app | Firebase Hosting or Cloud Storage + Cloud CDN | Static hosting and CDN | Firebase is easiest; Cloud CDN offers more control. |
| Dynamic web app | Cloud Run or App Engine | Managed app runtime | Cloud Run is an excellent default for containers. |
| API/functions | Cloud Run, Cloud Functions, API Gateway | API runtime and routing | Prefer Cloud Run for containerized backends. |
| Containers | Artifact Registry + Cloud Run | Build and run Docker images | Simple scaling-to-zero path. |
| Relational DB | Cloud SQL | Managed PostgreSQL/MySQL | Include backups and connection strategy. |
| Document DB | Firestore | Serverless document database | Good for app data with document access patterns. |
| Files/uploads | Cloud Storage | Object storage | Use signed URLs where possible. |
| Secrets | Secret Manager | Secret storage | Use service accounts with least privilege. |
| Identity | Identity Platform or external IdP | User auth | Firebase Auth is often simplest for startups. |
| Queue | Pub/Sub or Cloud Tasks | Async messaging/tasks | Cloud Tasks for HTTP jobs; Pub/Sub for events. |
| Scheduler | Cloud Scheduler | Cron jobs | Often invokes Cloud Run or Pub/Sub. |
| Logs/metrics | Cloud Logging + Cloud Monitoring | Observability | Add uptime checks and alert policies. |
| IaC | Terraform or Deployment Manager | Repeatable infrastructure | Terraform is preferred; Deployment Manager is legacy. |
