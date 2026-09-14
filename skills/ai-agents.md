---
layout: default
title: AI agents
collection_style: skills
---

# AI agents

Public samples that show how I build and explore multi-agent systems.

### [artefact-driven-sdlc](https://github.com/nabs-darrel-schreyer/artefact-driven-sdlc)

**Lean artefact-driven SDLC - agent cohorts + Next.js UI**

artefact-driven-sdlc is a standalone .NET 10 + Next.js product for artefact-driven agentic SDLC. Specialised agent cohorts mature work along a deterministic graph - refined idea to story to module-spec to UI design to wireframe to initial assessment - using a shared producer/reviewer skill model. A Spectre.Console CLI and AAC.Api drive the same Azure AI Foundry agent path; a chat-style Next.js UI lets you pick a cohort, point at a feature folder, and run single or pipeline modes. Built as a focused app slice (Aspire portal and brownfield assessment paths intentionally out of scope).

`.NET` | `Microsoft Agents AI` | `Azure AI Foundry` | `Spectre.Console` | `ASP.NET Core` | `Next.js` | `React` | `TypeScript` | `Agentic SDLC`

### [AgentCohortHostingPlatformDemo](https://github.com/nabs-darrel-schreyer/AgentCohortHostingPlatformDemo)

**Orleans multi-silo agent-cohort hosting on Aspire**

AgentCohortHostingPlatformDemo is an Aspire + Microsoft Orleans sample of an Agent Cohort hosting platform: artefact state lives in grains, not the HTTP layer. It runs a 3-replica silo with Azure Table clustering and Azure Blob grain persistence (Azurite locally), an Orleans client API over grain contracts, and a React UI to load artefacts, append prompts, and deactivate grains. Persistent state, grain lifecycle hooks, custom DTO serialization, and the Orleans Dashboard are wired in - aimed at engineers building distributed AI/agent platforms on .NET.

`Microsoft Orleans` | `.NET Aspire` | `ASP.NET Core` | `Azure Storage` | `React` | `Vite` | `TypeScript` | `Docker` | `Azurite`

### [AfSessionExperiment](https://github.com/nabs-darrel-schreyer/AfSessionExperiment)

**Multi-agent hand-off with MAF session StateBag**

AfSessionExperiment is a Microsoft Agent Framework (MAF) console sample where Producer and Reviewer agents share work in one session. The Producer stores a test-plan artefact in session StateBag; the Reviewer gets that content injected as context before it runs, then stores its review the same way. It talks to Gemma hosted on Docker Desktop through an OpenAI-compatible endpoint - handy for engineers exploring multi-agent collaboration without stuffing everything into chat history.

`.NET` | `Microsoft Agent Framework (MAF)` | `AI agents` | `OpenAI-compatible API` | `Docker` | `Gemma`

## Related videos

Artefact-driven SDLC with Microsoft Agent Framework: [Part 1](https://youtu.be/jneY3Ryk_YU), [Part 2](https://youtu.be/OGiN1CrcwVA), and [Part 3](https://youtu.be/WUdDcd6v-Vc) - or watch on the [Videos]({{ '/videos/' | relative_url }}) page.
