---
aliases: AWS IP 地址范围, AWS IP Ranges 
created_at: 2023-05-06 23:09
tags: aws, vpc, network
---

# 概念

AWS 以 JSON 格式发布其当前的 IP 地址范围。利用这些信息，您可以识别来自 AWS 的流量。您还可以允许或拒绝发往或来自特定类型 AWS 资源的流量。

要查看当前范围，请下载 `.json` 文件。要维护历史记录，请将连续版本的 `.json` 文件保存在系统上。要确定自上次保存文件以来是否发生更改，请检查当前文件中的发布时间，并将其与上次保存文件中的发布时间进行比较。

通过自带 IP 地址（BYOIP）引入到 AWS 的 IP 地址范围不包含在 `.json` 文件内。

或者，某些服务使用 AWS 托管式前缀列表发布其地址范围。有关更多信息，请参阅[可用的 AWS 托管前缀列表](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/working-with-aws-managed-prefix-lists.html#available-aws-managed-prefix-lists)。

# 作用

方便用户识别AWS服务的流量。

# 参考文献
-   [AWS IP 地址范围](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/aws-ip-ranges.html)