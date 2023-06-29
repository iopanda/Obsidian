---
aliases: 私有IP, Private IP
created_at: 2023-05-06 22:57
tags: aws, vpc, network
---

# 概念

AWS VPC内部构建资源时分配的内部私有IP地址。

# 作用

规范网络IP的分配，尽量避免与 [[AWS IP Ranges]] 或其它服务之间的IP冲突。

# IPv4 VPC CIDR 块

当创建 VPC 时，必须为这个 VPC 指定 IPv4 CIDR 块。允许的块大小介于 `/16` 网络掩码 (65,536 个 IP 地址) 和 `/28` 网络掩码 (16 个 IP 地址) 之间。在创建 VPC 后，可以将额外的 IPv4 CIDR 块与 VPC 关联。有关更多信息，请参阅[将 IPv4 CIDR 块添加到 VPC](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/modify-vpcs.html#add-ipv4-cidr)。

在创建 VPC 时，建议按规范指定来自私有 IPv4 地址范围的 CIDR 块（如 [RFC 1918](http://www.faqs.org/rfcs/rfc1918.html) 中所指定）。
| RFC 1918 范围 | 示例 CIDR 块 |
| ---- | ---- |
| 10.0.0.0 - 10.255.255.255（10/8 前缀） | 10.0.0.0/16 |
| 172.16.0.0 - 172.31.255.255（172.16/12 前缀） | 172.31.0.0/16 |
| 192.168.0.0 - 192.168.255.255（192.168/16 前缀）| 192.168.0.0/20 |


# 参考文献

-   [VPC CIDR 块](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/vpc-cidr-blocks.html)