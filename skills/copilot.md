---
layout: default
title: GitHub Copilot
collection_style: skills
---

# GitHub Copilot

Public samples that explore Copilot SDK ergonomics for agent and CLI tooling.

### [GitHubCopilotSDK](https://github.com/nabs-darrel-schreyer/GitHubCopilotSDK)

**GitHub Copilot SDK - same session API in C#, TS, Python, and Go**

GitHubCopilotSDK is a multi-language learning repo that runs the same Copilot SDK session flow in C# (.NET 10), TypeScript, Python, and Go - all on SDK 1.0.14. Each CLI creates a session (model auto, approve-all permissions), sends a simple prompt, and prints the assistant reply. The Go sample highlights CLI-path discovery because that SDK does not bundle a runtime; Python's runner bootstraps a venv and avoids the Windows Store stub. Aimed at engineers comparing Copilot SDK ergonomics across languages for agent or CLI tooling.

`GitHub Copilot SDK` | `.NET` | `TypeScript` | `Python` | `Go` | `CLI`
