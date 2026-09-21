---
layout: default
title: AWS
collection_style: skills
---

# AWS

Public samples that show how I work on Amazon Web Services.

### [StatementVault](https://github.com/nabs-darrel-schreyer/StatementVault)

**Bank statement vault API - S3 + DynamoDB with CDK.NET (Aspire/LocalStack locally)**

StatementVault is an API-only .NET 10 vertical-slice sample for a bank statement archive: PDF/statement bytes in S3, metadata in DynamoDB, with upload/list/get/download (including presigned URL) endpoints. Locally, Aspire runs the API against LocalStack. Cloud deploy is CDK.NET primary (`src/StatementVault.Infra`) provisioning S3, DynamoDB, EC2 and an instance profile without baking credentials into code; Terraform under `infra/` is kept as a side-by-side comparison footprint. The layout follows nabs-templates-vertical-slice-react patterns but stays deliberately thin - teaching AWS persistence and slice style rather than shipping a full bank product.

`.NET` | `ASP.NET Core` | `Aspire` | `CDK.NET` | `AWS S3` | `DynamoDB` | `LocalStack` | `Terraform` | `Vertical Slice` | `xUnit`






