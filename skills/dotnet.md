---
layout: default
title: .NET
collection_style: skills
---

# .NET

Public samples that show how I work in the .NET ecosystem.

### [artefact-driven-sdlc](https://github.com/nabs-darrel-schreyer/artefact-driven-sdlc)

**Lean artefact-driven SDLC - agent cohorts + Next.js UI**

artefact-driven-sdlc is a standalone .NET 10 + Next.js product for artefact-driven agentic SDLC. Specialised agent cohorts mature work along a deterministic graph - refined idea to story to module-spec to UI design to wireframe to initial assessment - using a shared producer/reviewer skill model. A Spectre.Console CLI and AAC.Api drive the same Azure AI Foundry agent path; a chat-style Next.js UI lets you pick a cohort, point at a feature folder, and run single or pipeline modes. Built as a focused app slice (Aspire portal and brownfield assessment paths intentionally out of scope).

`.NET` | `Microsoft Agents AI` | `Azure AI Foundry` | `Spectre.Console` | `ASP.NET Core` | `Next.js` | `React` | `TypeScript` | `Agentic SDLC`

### [azd-pipelines-azure-infra](https://github.com/nabs-darrel-schreyer/azd-pipelines-azure-infra)

**Aspire + azd GitHub Actions to ACA with OIDC and migration cleanup**

azd-pipelines-azure-infra is a .NET Aspire sample that documents end-to-end CI/CD with Azure Developer CLI and GitHub Actions onto Azure Container Apps. The workflow uses federated OIDC login (no long-lived Azure secrets), then `azd provision` and `azd deploy`, with Aspire owning ACA/SQL/App Configuration infrastructure as code. A dedicated data-migrations job applies EF migrations and App Config seed data; the pipeline then deletes that Container App so one-shot work doesn't keep costing vCPU/memory - aimed at engineers who care about secure, cost-aware Azure pipelines.

`GitHub Actions` | `Azure Developer CLI (azd)` | `.NET Aspire` | `Azure Container Apps` | `OIDC` | `Azure SQL` | `Azure App Configuration` | `EF Core` | `Blazor` | `Bicep`

### [LaunchpadCoreApis.WeatherSample](https://github.com/nabs-darrel-schreyer/LaunchpadCoreApis.WeatherSample)

**NuGet-first APIs with NabsEndpointBase + MapNabsEndpoints**

LaunchpadCoreApis.WeatherSample is a .NET 10 showcase for the [Nabs.Launchpad.Core.Apis](https://www.nuget.org/packages/Nabs.Launchpad.Core.Apis/10.0.273) NuGet package (10.0.273). It defines one endpoint class per route by subclassing NabsEndpointBase, declaring path/method/metadata in NabsEndpointOptions, and implementing HandleAsync. A single MapNabsEndpoints<Program>() call discovers and maps those endpoints - illustrated with GET /weatherforecast - so teams can structure APIs as discoverable classes instead of scattered minimal-route lambdas.

`.NET` | `ASP.NET Core` | `NuGet` | `OpenAPI` | `Nabs.Launchpad.Core.Apis`

### [AgentCohortHostingPlatformDemo](https://github.com/nabs-darrel-schreyer/AgentCohortHostingPlatformDemo)

**Orleans multi-silo agent-cohort hosting on Aspire**

AgentCohortHostingPlatformDemo is an Aspire + Microsoft Orleans sample of an Agent Cohort hosting platform: artefact state lives in grains, not the HTTP layer. It runs a 3-replica silo with Azure Table clustering and Azure Blob grain persistence (Azurite locally), an Orleans client API over grain contracts, and a React UI to load artefacts, append prompts, and deactivate grains. Persistent state, grain lifecycle hooks, custom DTO serialization, and the Orleans Dashboard are wired in - aimed at engineers building distributed AI/agent platforms on .NET.

`Microsoft Orleans` | `.NET Aspire` | `ASP.NET Core` | `Azure Storage` | `React` | `Vite` | `TypeScript` | `Docker` | `Azurite`

### [Containerisation](https://github.com/nabs-darrel-schreyer/Containerisation)

**Aspire publish that folds SPA + API into one container**

Containerisation is a .NET Aspire sample that keeps a React/Vite frontend and ASP.NET Core API as separate resources in development, then publishes them as a single container. The AppHost uses `PublishWithContainerFiles` to build the SPA into the server's `wwwroot`, so one image serves both UI and `/api`. A `publish.ps1` script prepares the Aspire Docker environment, saves the image as a tar, and runs it locally - useful for teams who want one deployable unit without a separate static host.

`.NET Aspire` | `ASP.NET Core` | `React` | `Vite` | `TypeScript` | `Docker` | `pnpm`

### [AfSessionExperiment](https://github.com/nabs-darrel-schreyer/AfSessionExperiment)

**Multi-agent hand-off with MAF session StateBag**

AfSessionExperiment is a Microsoft Agent Framework (MAF) console sample where Producer and Reviewer agents share work in one session. The Producer stores a test-plan artefact in session StateBag; the Reviewer gets that content injected as context before it runs, then stores its review the same way. It talks to Gemma hosted on Docker Desktop through an OpenAI-compatible endpoint - handy for engineers exploring multi-agent collaboration without stuffing everything into chat history.

`.NET` | `Microsoft Agent Framework (MAF)` | `AI agents` | `OpenAI-compatible API` | `Docker` | `Gemma`
