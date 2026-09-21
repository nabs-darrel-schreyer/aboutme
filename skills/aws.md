---
layout: default
title: AWS
collection_style: skills
---

# AWS

Public samples that show how I work on Amazon Web Services.

### [StatementVault](https://github.com/nabs-darrel-schreyer/StatementVault)

**Bank statement vault API - S3 + DynamoDB on Aspire/LocalStack and Terraform**

StatementVault is an API-only .NET 10 vertical-slice sample for a bank statement archive: PDF/statement bytes in S3, metadata in DynamoDB, with upload/list/get/download (including presigned URL) endpoints. Locally, Aspire runs the API against LocalStack; Terraform provisions the cloud path (S3, DynamoDB, EC2 + instance profile) without baking credentials into code. The layout follows nabs-templates-vertical-slice-react patterns but stays deliberately thin-teaching AWS persistence and slice style rather than shipping a full bank product.

`.NET` | `ASP.NET Core` | `Aspire` | `AWS S3` | `DynamoDB` | `LocalStack` | `Terraform` | `Vertical Slice` | `xUnit`




