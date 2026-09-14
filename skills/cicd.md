---
layout: default
title: CI/CD
collection_style: skills
---

# CI/CD

Public samples that show secure, cost-aware pipelines and infrastructure delivery.

### [azd-pipelines-azure-infra](https://github.com/nabs-darrel-schreyer/azd-pipelines-azure-infra)

**Aspire + azd GitHub Actions to ACA with OIDC and migration cleanup**

azd-pipelines-azure-infra is a .NET Aspire sample that documents end-to-end CI/CD with Azure Developer CLI and GitHub Actions onto Azure Container Apps. The workflow uses federated OIDC login (no long-lived Azure secrets), then `azd provision` and `azd deploy`, with Aspire owning ACA/SQL/App Configuration infrastructure as code. A dedicated data-migrations job applies EF migrations and App Config seed data; the pipeline then deletes that Container App so one-shot work doesn't keep costing vCPU/memory - aimed at engineers who care about secure, cost-aware Azure pipelines.

`GitHub Actions` | `Azure Developer CLI (azd)` | `.NET Aspire` | `Azure Container Apps` | `OIDC` | `Azure SQL` | `Azure App Configuration` | `EF Core` | `Blazor` | `Bicep`
