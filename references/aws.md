# AWS Reference

Use these common mappings when AWS is selected.

| Need | AWS service | Problem solved | Notes |
|---|---|---|---|
| Static web app | S3 + CloudFront or Amplify Hosting | Global static hosting and CDN | Amplify is easiest; S3/CloudFront gives more control. |
| SSR/full-stack web | Amplify Hosting, App Runner, ECS Fargate, Lambda | Runs dynamic app code | App Runner is a simple container path; ECS is more flexible. |
| API | API Gateway + Lambda, App Runner, ECS Fargate | HTTPS API runtime | Prefer containers for long-running APIs or websocket complexity. |
| Containers | ECR + App Runner/ECS Fargate | Build and run Docker images | ECS needs more setup but scales well. |
| Relational DB | RDS/Aurora | Managed PostgreSQL/MySQL | Include backups, private subnet choice, and migration plan. |
| Key-value/document | DynamoDB | Serverless NoSQL | Good for simple keyed access patterns. |
| Files/uploads | S3 | Durable object storage | Use presigned URLs where possible. |
| Secrets | Secrets Manager or SSM Parameter Store | Secure secret storage | Secrets Manager for rotation; SSM for lower-cost config. |
| Identity | Cognito or external IdP | User auth | Often external auth is simpler. |
| Queue | SQS | Async jobs | Pair with Lambda/ECS workers. |
| Events | EventBridge | Scheduled/event routing | Good for cron and integration events. |
| Logs/metrics | CloudWatch | Observability | Add alarms for errors, latency, and spend. |
| IaC | Terraform or CDK | Repeatable infrastructure | Terraform is most portable. |
