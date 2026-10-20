---
layout: default
title: GitHub Copilot
collection_style: skills
---

# GitHub Copilot

Public samples and documented tools that use GitHub Copilot in agent, CLI, and editor tooling.

### [GitHubCopilotSDK](https://github.com/nabs-darrel-schreyer/GitHubCopilotSDK)

**GitHub Copilot SDK - same session API in C#, TS, Python, and Go**

GitHubCopilotSDK is a multi-language learning repo that runs the same Copilot SDK session flow in C# (.NET 10), TypeScript, Python, and Go - all on SDK 1.0.14. Each CLI creates a session (model auto, approve-all permissions), sends a simple prompt, and prints the assistant reply. The Go sample highlights CLI-path discovery because that SDK does not bundle a runtime; Python's runner bootstraps a venv and avoids the Windows Store stub. Aimed at engineers comparing Copilot SDK ergonomics across languages for agent or CLI tooling.

`GitHub Copilot SDK` | `.NET` | `TypeScript` | `Python` | `Go` | `CLI`

### [NABS Retros](https://net-advantage.github.io/nabs-launchpad-vs-extension/index.html)

**NABS Retros - a VS Code extension that keeps agile retrospectives in the repository**

A VS Code extension I designed and built in TypeScript that runs agile retrospectives inside the team's own Git repository. It adds a Retros view, a Home page and a webview Retro Dashboard that steps each retro through six stages mapped to the retrospective maturity curve (Prepare and Gather are fully guided so far), with retros, feedback and objectives stored as plain Markdown that is committed and reviewed like the rest of the code. Objectives carry acceptance criteria with automatic measures from Git and GitHub data; GitHub Copilot is optional and only suggests summaries and assessments, including through the `@retro` chat participant, while people record the verdict. Action items become GitHub issues that the next retro checks, and finished retros can be archived to a GitHub Discussion. Distributed as a VSIX rather than through the Marketplace. The source is private; the public user guide (checked against v0.11.0) shows how it works.

`VS Code extension` | `TypeScript` | `GitHub Copilot` | `Chat participant` | `GitHub Issues` | `GitHub Discussions` | `Markdown`

### [efcore-sargable-config](https://github.com/nabs-darrel-schreyer/efcore-sargable-config)

**EF Core SQL Server string mappings - a Copilot agent skill for non-sargable predicates**

efcore-sargable-config is a GitHub Copilot agent skill for finding and fixing EF Core SQL Server string mappings that can make predicates non-sargable, such as an `nvarchar` parameter compared with an indexed `varchar` column. Its schema-first workflow checks the effective mapping (Fluent API, attributes, value converters, `ConfigureConventions`) against the real column type, length, collation and index, labels each finding confirmed, candidate or intentional exception, and only claims a column-side `CONVERT_IMPLICIT` or Index Scan when an actual execution plan shows it. Fixes target the narrowest owning mapping, such as `IsUnicode(false)` with a verified `HasMaxLength`, and real Unicode columns are never silently changed. Manual evals and trigger prompts check answer quality and skill selection separately. It is guidance only: it does not install an analyser, change mappings automatically or connect to SQL Server.

`GitHub Copilot` | `Agent skills` | `EF Core` | `SQL Server` | `.NET` | `Query plans` | `Evals`
