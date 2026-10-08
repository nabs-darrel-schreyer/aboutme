---
layout: default
title: VS Code extensions
collection_style: skills
---

# VS Code extensions

Editor tooling I have designed and built. Where the source is private, a public user guide shows how it works.

### [NABS Retros](https://net-advantage.github.io/nabs-launchpad-vs-extension/index.html)

**NABS Retros - a VS Code extension that keeps agile retrospectives in the repository**

A VS Code extension I designed and built in TypeScript that runs agile retrospectives inside the team's own Git repository. It adds a Retros view, a Home page and a webview Retro Dashboard that steps each retro through six stages mapped to the retrospective maturity curve (Prepare and Gather are fully guided so far), with retros, feedback and objectives stored as plain Markdown that is committed and reviewed like the rest of the code. Objectives carry acceptance criteria with automatic measures from Git and GitHub data; GitHub Copilot is optional and only suggests summaries and assessments, including through the `@retro` chat participant, while people record the verdict. Action items become GitHub issues that the next retro checks, and finished retros can be archived to a GitHub Discussion. Distributed as a VSIX rather than through the Marketplace. The source is private; the public user guide (checked against v0.11.0) shows how it works.

`VS Code extension` | `TypeScript` | `GitHub Copilot` | `Chat participant` | `GitHub Issues` | `GitHub Discussions` | `Markdown`
