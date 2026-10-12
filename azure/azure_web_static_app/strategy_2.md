# GitHub Organization to Azure

## Table of Contents

- [(1) Recommended Setup](#1-recommended-setup)
- [(2) Organization Authorization](#2-organization-authorization)
- [(3) Security Model](#3-security-model)
- [(4) Does This Still Count as "Always Azure"?](#4-does-this-still-count-as-always-azure)

---

Yes—this is the recommended approach when your organization already uses GitHub.

- GitHub manages source control and deployment triggers, while Azure provides hosting, DNS, TLS, and monitoring.
- Azure Static Web Apps can connect directly to a GitHub Organization repository. During setup, select the organization, repository, and production branch. Azure then creates a GitHub Actions workflow that deploys changes to the Static Web App.

[Azure Static Web Apps quickstart](https://learn.microsoft.com/en-us/azure/static-web-apps/get-started-portal?pivots=github&tabs=vanilla-javascript)

```mermaid
---
title: "~ GitHub Organization to Azure Static Web Apps ~"
config:
  theme: dark
---

flowchart TD
    Dev[Developers] --> Repo[GitHub Organization repository]
    Repo --> PR[Pull request]
    PR --> Checks[GitHub Actions: build and validation]
    Checks --> Preview[Azure Static Web Apps preview]
    Preview --> Approval[Review and approval]
    Approval --> Main[Merge into main]
    Main --> Deploy[GitHub Actions deployment]
    Deploy --> Azure[Azure Static Web Apps production]
    Visitor[Internet visitor] --> DNS[Azure DNS]
    DNS --> Azure
```

---

## (1) Recommended Setup

| # | Area | Recommendation |
| --: | --- | --- |
| 1 | Repository | `github.com/<organization>/zen-garden` |
| 2 | Production branch | Protect `main`; require pull requests and passing workflow checks. |
| 3 | Production deployment | Deploy only after changes are merged into `main`. |
| 4 | Pull requests | Use Static Web Apps preview environments for visual review before merging. |
| 5 | Azure resources | Use a dedicated resource group for Static Web Apps, Azure DNS, and optional Application Insights. |
| 6 | Access control | Use GitHub teams for repository access and Azure RBAC for Azure resources. |
| 7 | Secrets | Store the generated Static Web Apps deployment token in GitHub Actions secrets; never commit it to source control. |
| 8 | Infrastructure | Define Azure resources in Bicep and deploy them through a separate infrastructure workflow. |

---

## (2) Organization Authorization

A GitHub Organization owner may need to approve the **Azure Static Web Apps** GitHub OAuth application before organization repositories appear in the Azure portal. This is expected when the organization restricts third-party application access.

[Microsoft guidance](https://learn.microsoft.com/en-us/azure/static-web-apps/get-started-portal?pivots=github&tabs=vanilla-javascript)

```mermaid
---
title: "~ Governance and Access Boundaries ~"
config:
  theme: dark
---

flowchart TD
    OrgOwner[GitHub Organization owner] --> AppApproval[Approve Azure Static Web Apps integration]
    OrgOwner --> Teams[GitHub teams and repository permissions]
    AzureAdmin[Azure subscription owner] --> RBAC[Azure RBAC]
    Teams --> Repo[Repository and pull requests]
    RBAC --> SWA[Static Web Apps resource]
    Repo --> Workflow[GitHub Actions workflow]
    Workflow --> SWA
```

---

## (3) Security Model

Use separate deployment identities for application delivery and infrastructure changes.

| # | Workload | Authentication | Rationale |
| --: | --- | --- | --- |
| 1 | Static-site deployment | Generated `AZURE_STATIC_WEB_APPS_API_TOKEN` GitHub secret | Standard Static Web Apps deployment mechanism. Rotate the token in Azure if exposure is suspected. |
| 2 | Infrastructure changes, including Bicep and Azure DNS | GitHub Actions OIDC federation with Microsoft Entra ID | Avoids long-lived Azure credentials in GitHub. Restrict federation to the specific organization, repository, and branch or environment. |

- [Deployment token guidance](https://learn.microsoft.com/en-us/azure/static-web-apps/deployment-token-management)
- [OIDC with Azure](https://docs.github.com/en/actions/how-tos/secure-your-work/security-harden-deployments/oidc-in-azure)

---

## (4) Does This Still Count as "Always Azure"?

Yes—if "always Azure" means that the public application and its cloud resources run on Azure.

| # | Model | Source Control and CI/CD | Public Hosting | Best Fit |
| --: | --- | --- | --- | --- |
| 1 | GitHub Organization + Azure | GitHub + GitHub Actions | Azure Static Web Apps | Recommended when the organization already uses GitHub. |
| 2 | Azure DevOps + Azure | Azure Repos + Azure Pipelines | Azure Static Web Apps | Use when source control and pipelines must remain in Azure DevOps. |

Azure Static Web Apps supports both GitHub and Azure DevOps integrations. [Hosting plan comparison](https://learn.microsoft.com/azure/static-web-apps/plans)

For this project, use the GitHub Organization repository, protect `main`, deploy through GitHub Actions to Azure Static Web Apps, and manage the public domain with Azure DNS.
