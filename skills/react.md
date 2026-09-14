---
layout: default
title: React
collection_style: skills
---

# React

Public samples that show front-end work with React and the modern TypeScript toolchain.

### [NabsUiShell.Showcase](https://github.com/nabs-darrel-schreyer/NabsUiShell.Showcase)

**Corporate React shell + schema-driven DynamicForm**

NabsUiShell.Showcase is a standalone React app demonstrating [@net-advantage/nabs-ui-shell](https://www.npmjs.com/package/@net-advantage/nabs-ui-shell) 0.84.0 with an elegant corporate Shell, Branding, and path-aware Navigation. The headline feature is a multi-section vendor onboarding DynamicForm (organisation, contact, commercial terms, compliance, address) driven by nested JSON Schema - enums, currency, booleans, and long text - showing how teams adopt the shell as a single import surface for real business UI.

`React` | `TypeScript` | `Vite` | `npm` | `@net-advantage/nabs-ui-shell` | `DynamicForm` | `Nabs UI`

### [AgentCohortHostingPlatformDemo](https://github.com/nabs-darrel-schreyer/AgentCohortHostingPlatformDemo)

**Orleans multi-silo agent-cohort hosting on Aspire**

AgentCohortHostingPlatformDemo is an Aspire + Microsoft Orleans sample of an Agent Cohort hosting platform: artefact state lives in grains, not the HTTP layer. It runs a 3-replica silo with Azure Table clustering and Azure Blob grain persistence (Azurite locally), an Orleans client API over grain contracts, and a React UI to load artefacts, append prompts, and deactivate grains. Persistent state, grain lifecycle hooks, custom DTO serialization, and the Orleans Dashboard are wired in - aimed at engineers building distributed AI/agent platforms on .NET.

`Microsoft Orleans` | `.NET Aspire` | `ASP.NET Core` | `Azure Storage` | `React` | `Vite` | `TypeScript` | `Docker` | `Azurite`

### [Containerisation](https://github.com/nabs-darrel-schreyer/Containerisation)

**Aspire publish that folds SPA + API into one container**

Containerisation is a .NET Aspire sample that keeps a React/Vite frontend and ASP.NET Core API as separate resources in development, then publishes them as a single container. The AppHost uses `PublishWithContainerFiles` to build the SPA into the server's `wwwroot`, so one image serves both UI and `/api`. A `publish.ps1` script prepares the Aspire Docker environment, saves the image as a tar, and runs it locally - useful for teams who want one deployable unit without a separate static host.

`.NET Aspire` | `ASP.NET Core` | `React` | `Vite` | `TypeScript` | `Docker` | `pnpm`
