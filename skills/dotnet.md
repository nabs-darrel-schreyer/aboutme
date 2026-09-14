---
layout: default
title: .NET
collection_style: skills
---

# .NET

Public samples that show how I work in the .NET ecosystem.

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
