# Cloud Service Matrix

| Need | Recommended Service | Problem It Solves | Why This Fits | Alternatives | Notes/Risks |
|---|---|---|---|---|---|
| Web hosting | TBD, e.g. Vercel / CDN hosting | Serves the user-facing app | TBD | AWS/Azure/GCP static hosting | Check SSR/static output needs. |
| Runtime/API | TBD, e.g. Railway / managed container / functions | Runs backend code | TBD | Cloud Run, App Runner, Container Apps | Check websockets, workers, and timeouts. |
| Database | TBD | Stores application data | TBD | TBD | TBD |
| Object storage | TBD | Stores uploads/static assets | TBD | TBD | TBD |
| Secrets | TBD | Protects credentials | TBD | TBD | Never commit secrets. |
| CI/CD | TBD, e.g. Vercel/Railway Git deploys or GitHub Actions | Automates build/deploy | TBD | Provider pipelines | Use least-privilege credentials. |
| Observability | TBD | Logs, metrics, alerts | TBD | TBD | Define alerts before production. |
