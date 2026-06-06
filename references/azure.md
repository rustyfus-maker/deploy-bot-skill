# Azure Reference

Use these common mappings when Azure is selected.

| Need | Azure service | Problem solved | Notes |
|---|---|---|---|
| Static web app | Azure Static Web Apps | Static hosting, CDN, optional APIs | Very good for frontend repos. |
| Dynamic web app | Azure App Service or Container Apps | Managed app runtime | App Service is familiar; Container Apps works well for Docker. |
| API/functions | Azure Functions or Container Apps | Serverless or containerized APIs | Match runtime duration and dependency needs. |
| Containers | Azure Container Registry + Container Apps | Build and run Docker images | Simpler than AKS for most apps. |
| Relational DB | Azure Database for PostgreSQL/MySQL or Azure SQL | Managed relational data | Include firewall/private endpoint guidance. |
| Document DB | Cosmos DB | Globally distributed NoSQL | Powerful but can be costly if misconfigured. |
| Files/uploads | Blob Storage | Object storage | Use SAS tokens carefully. |
| Secrets | Key Vault | Secret and certificate storage | Use managed identities. |
| Identity | Microsoft Entra ID / Entra External ID | Workforce/customer identity | Best for Microsoft ecosystems. |
| Queue | Storage Queues or Service Bus | Async messaging | Service Bus for enterprise semantics. |
| Events | Event Grid | Event routing | Good for cloud-native events. |
| Logs/metrics | Azure Monitor + Application Insights | Observability | Add dashboards and alerts. |
| IaC | Bicep or Terraform | Repeatable infrastructure | Bicep is Azure-native; Terraform is portable. |
