# Trading Alerts Platform

AWS platform infrastructure for the Trading Alerts application. This repository owns the EKS cluster, its network, and the ECR repositories used by the application. It does not own application source or app-specific Kubernetes manifests. Application code and kubernetes manifests are stored in the separat `market-alerts-application` repository.

## Ownership and delivery boundaries

- The application repository tests and builds the API, worker, and fetcher images.
- This repository provisions AWS infrastructure and publishes the ECR repository URLs as Terraform outputs.
- Application deployment remains app-owned initially. A later GitOps controller can reconcile pinned image versions from environment desired state; Terraform should manage the cluster and bootstrap that controller, not each application release.
