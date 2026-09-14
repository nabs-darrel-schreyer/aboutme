---
layout: default
title: React
collection_style: skills
---

# React

Public samples that show front-end work with React and the modern TypeScript toolchain.

### [artefact-driven-sdlc](https://github.com/nabs-darrel-schreyer/artefact-driven-sdlc)

**Lean artefact-driven SDLC - agent cohorts + Next.js UI**

artefact-driven-sdlc is a standalone .NET 10 + Next.js product for artefact-driven agentic SDLC. Specialised agent cohorts mature work along a deterministic graph - refined idea to story to module-spec to UI design to wireframe to initial assessment - using a shared producer/reviewer skill model. A Spectre.Console CLI and AAC.Api drive the same Azure AI Foundry agent path; a chat-style Next.js UI lets you pick a cohort, point at a feature folder, and run single or pipeline modes. Built as a focused app slice (Aspire portal and brownfield assessment paths intentionally out of scope).

`.NET` | `Microsoft Agents AI` | `Azure AI Foundry` | `Spectre.Console` | `ASP.NET Core` | `Next.js` | `React` | `TypeScript` | `Agentic SDLC`

### [NabsUiShell.Showcase](https://github.com/nabs-darrel-schreyer/NabsUiShell.Showcase)

**Corporate React shell + schema-driven DynamicForm**

NabsUiShell.Showcase is a React/Vite app that demos the [@net-advantage/nabs-ui-shell](https://www.npmjs.com/package/@net-advantage/nabs-ui-shell) npm package (0.84.0) as a single import surface for Shell, Branding, Navigation, Cards, Panel, Button, and Tab. Path-aware navigation and tabbed DynamicForm vendor onboarding (organisation, contact, commercial, compliance, address) show real business UI. [Live demo on GitHub Pages](https://nabs-darrel-schreyer.github.io/NabsUiShell.Showcase/).

`React` | `TypeScript` | `Vite` | `npm` | `@net-advantage/nabs-ui-shell` | `DynamicForm` | `GitHub Pages`

### [AgentCohortHostingPlatformDemo](https://github.com/nabs-darrel-schreyer/AgentCohortHostingPlatformDemo)

**Orleans multi-silo agent-cohort hosting on Aspire**

AgentCohortHostingPlatformDemo is an Aspire + Microsoft Orleans sample of an Agent Cohort hosting platform: artefact state lives in grains, not the HTTP layer. It runs a 3-replica silo with Azure Table clustering and Azure Blob grain persistence (Azurite locally), an Orleans client API over grain contracts, and a React UI to load artefacts, append prompts, and deactivate grains. Persistent state, grain lifecycle hooks, custom DTO serialization, and the Orleans Dashboard are wired in - aimed at engineers building distributed AI/agent platforms on .NET.

`Microsoft Orleans` | `.NET Aspire` | `ASP.NET Core` | `Azure Storage` | `React` | `Vite` | `TypeScript` | `Docker` | `Azurite`

### [Containerisation](https://github.com/nabs-darrel-schreyer/Containerisation)

**Aspire publish that folds SPA + API into one container**

Containerisation is a .NET Aspire sample that keeps a React/Vite frontend and ASP.NET Core API as separate resources in development, then publishes them as a single container. The AppHost uses `PublishWithContainerFiles` to build the SPA into the server's `wwwroot`, so one image serves both UI and `/api`. A `publish.ps1` script prepares the Aspire Docker environment, saves the image as a tar, and runs it locally - useful for teams who want one deployable unit without a separate static host.

`.NET Aspire` | `ASP.NET Core` | `React` | `Vite` | `TypeScript` | `Docker` | `pnpm`
