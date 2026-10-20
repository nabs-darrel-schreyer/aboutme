---
layout: default
title: SQL and databases
collection_style: skills
---

# SQL and databases

Public work on relational and NoSQL data access: query plans, ORM mappings, and persistence design.

### [efcore-sargable-config](https://github.com/nabs-darrel-schreyer/efcore-sargable-config)

**EF Core + SQL Server - a Copilot agent skill for non-sargable queries, backed by plan-asserting tests**

efcore-sargable-config is a GitHub Copilot agent skill for finding why an indexed EF Core / SQL Server lookup scans. Stable rules ESC001-ESC012 cover `varchar`/`nvarchar` and MaxLength mapping mismatches, blanket `ConfigureConventions` defaults, and non-sargable predicates such as functions or arithmetic on a column, implicit conversions, leading wildcards, OR across columns and ISNULL/COALESCE; every finding uses a fixed format, is labelled confirmed, candidate, other-cause or intentional exception, and a scan is only claimed when an actual execution plan shows it. A .NET 10 / EF Core test harness backs the guidance: seeded bad, good and clean C# cases for each rule with a scoring manifest, xUnit unit tests for effective mappings, generated SQL and a model-vs-schema guardrail, and Testcontainers integration tests that run every case against SQL Server 2022 and assert the actual plans (CONVERT_IMPLICIT, Seek vs Scan, logical reads, collation). The skill itself stays guidance: it does not change mappings automatically or connect to your database.

`GitHub Copilot` | `Agent skills` | `EF Core` | `SQL Server` | `.NET` | `xUnit` | `Testcontainers` | `Query plans`

### [StatementVault](https://github.com/nabs-darrel-schreyer/StatementVault)

**Bank statement vault API - S3 + DynamoDB with CDK.NET (Aspire/LocalStack locally)**

StatementVault is an API-only .NET 10 vertical-slice sample for a bank statement archive: PDF/statement bytes in S3, metadata in DynamoDB, with upload/list/get/download (including presigned URL) endpoints. Locally, Aspire runs the API against LocalStack. Cloud deploy is CDK.NET primary (`src/StatementVault.Infra`) provisioning S3, DynamoDB, EC2 and an instance profile without baking credentials into code; Terraform under `infra/` is kept as a side-by-side comparison footprint. The layout follows nabs-templates-vertical-slice-react patterns but stays deliberately thin - teaching AWS persistence and slice style rather than shipping a full bank product.

`.NET` | `ASP.NET Core` | `Aspire` | `CDK.NET` | `AWS S3` | `DynamoDB` | `LocalStack` | `Terraform` | `Vertical Slice` | `xUnit`
