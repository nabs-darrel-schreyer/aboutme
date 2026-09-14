---
layout: default
title: Azure
collection_style: skills
---

# Azure

Public samples that use Azure services for persistence, clustering, and cloud-native hosting.

### [artefact-driven-sdlc](https://github.com/nabs-darrel-schreyer/artefact-driven-sdlc)

**Lean artefact-driven SDLC - agent cohorts + Next.js UI**

artefact-driven-sdlc is a standalone .NET 10 + Next.js product for artefact-driven agentic SDLC. Specialised agent cohorts mature work along a deterministic graph - refined idea to story to module-spec to UI design to wireframe to initial assessment - using a shared producer/reviewer skill model. A Spectre.Console CLI and AAC.Api drive the same Azure AI Foundry agent path; a chat-style Next.js UI lets you pick a cohort, point at a feature folder, and run single or pipeline modes. Built as a focused app slice (Aspire portal and brownfield assessment paths intentionally out of scope).

`.NET` | `Microsoft Agents AI` | `Azure AI Foundry` | `Spectre.Console` | `ASP.NET Core` | `Next.js` | `React` | `TypeScript` | `Agentic SDLC`

### [azd-pipelines-azure-infra](https://github.com/nabs-darrel-schreyer/azd-pipelines-azure-infra)

**Aspire + azd GitHub Actions to ACA with OIDC and migration cleanup**

azd-pipelines-azure-infra is a .NET Aspire sample that documents end-to-end CI/CD with Azure Developer CLI and GitHub Actions onto Azure Container Apps. The workflow uses federated OIDC login (no long-lived Azure secrets), then `azd provision` and `azd deploy`, with Aspire owning ACA/SQL/App Configuration infrastructure as code. A dedicated data-migrations job applies EF migrations and App Config seed data; the pipeline then deletes that Container App so one-shot work doesn't keep costing vCPU/memory - aimed at engineers who care about secure, cost-aware Azure pipelines.

`GitHub Actions` | `Azure Developer CLI (azd)` | `.NET Aspire` | `Azure Container Apps` | `OIDC` | `Azure SQL` | `Azure App Configuration` | `EF Core` | `Blazor` | `Bicep`

### [AgentCohortHostingPlatformDemo](https://github.com/nabs-darrel-schreyer/AgentCohortHostingPlatformDemo)

**Orleans multi-silo agent-cohort hosting on Aspire**

AgentCohortHostingPlatformDemo is an Aspire + Microsoft Orleans sample of an Agent Cohort hosting platform: artefact state lives in grains, not the HTTP layer. It runs a 3-replica silo with Azure Table clustering and Azure Blob grain persistence (Azurite locally), an Orleans client API over grain contracts, and a React UI to load artefacts, append prompts, and deactivate grains. Persistent state, grain lifecycle hooks, custom DTO serialization, and the Orleans Dashboard are wired in - aimed at engineers building distributed AI/agent platforms on .NET.

`Microsoft Orleans` | `.NET Aspire` | `ASP.NET Core` | `Azure Storage` | `React` | `Vite` | `TypeScript` | `Docker` | `Azurite`
