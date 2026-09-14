---
layout: default
title: .NET
collection_style: skills
---

# .NET

Public samples that show how I work in the .NET ecosystem.

### [Containerisation](https://github.com/nabs-darrel-schreyer/Containerisation)

**Aspire publish that folds SPA + API into one container**

Containerisation is a .NET Aspire sample that keeps a React/Vite frontend and ASP.NET Core API as separate resources in development, then publishes them as a single container. The AppHost uses `PublishWithContainerFiles` to build the SPA into the server's `wwwroot`, so one image serves both UI and `/api`. A `publish.ps1` script prepares the Aspire Docker environment, saves the image as a tar, and runs it locally - useful for teams who want one deployable unit without a separate static host.

`.NET Aspire` | `ASP.NET Core` | `React` | `Vite` | `TypeScript` | `Docker` | `pnpm`

### [AfSessionExperiment](https://github.com/nabs-darrel-schreyer/AfSessionExperiment)

**Multi-agent hand-off with MAF session StateBag**

AfSessionExperiment is a Microsoft Agent Framework (MAF) console sample where Producer and Reviewer agents share work in one session. The Producer stores a test-plan artefact in session StateBag; the Reviewer gets that content injected as context before it runs, then stores its review the same way. It talks to Gemma hosted on Docker Desktop through an OpenAI-compatible endpoint - handy for engineers exploring multi-agent collaboration without stuffing everything into chat history.

`.NET` | `Microsoft Agent Framework (MAF)` | `AI agents` | `OpenAI-compatible API` | `Docker` | `Gemma`
