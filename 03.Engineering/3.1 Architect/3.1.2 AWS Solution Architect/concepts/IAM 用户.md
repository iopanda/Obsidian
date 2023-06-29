---
aliases: iam user
author: iopanda
created_at: 2023-05-06 11:32
tags: IAM User, 
---

# Overview
---
AWS Identity and Access Management（IAM）用户是您在 AWS 中创建的实体。IAM 用户表示使用 IAM 用户与 AWS 互动的人类用户或工作负载。AWS 中的用户包括名称和凭证。

具备管理员权限的 IAM 用户与 [[AWS 账户根用户]] 并不是一回事

# Content
---

## AWS 如何标识 IAM 用户

当您创建 IAM 用户时，IAM 提供以下这些方法来识别该用户：

-   该 IAM 用户的“易记名称”，这是您在创建 IAM 用户时指定的名称，如 `Richard` 或 `Anaya`。您将在 AWS Management Console中看到这些名称。
-   IAM 用户的 [[Amazon 资源名称]]（[[ARN]]）。当您需要跨所有 AWS 唯一标识 IAM 用户时，可以使用 ARN。例如，您可以使用 ARN 在 Amazon S3 存储桶的 IAM policy 中将 IAM 用户指定为 `Principal`。IAM 用户的 ARN 可能类似于以下内容：
    ``arn:aws:iam::`account-ID-without-hyphens`:user/Richard``
-   IAM 用户的唯一标识符。仅在您使用 API、Tools for Windows PowerShell 或 AWS CLI 创建 IAM 用户时返回此 ID；控制台中不会显示此 ID。



# References
---
[[AWS Certified Solutions Architect Professional v12.pdf]]
[AWS Identity and Access Management](https://docs.aws.amazon.com/iam/index.html)
