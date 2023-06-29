---
aliases: Internet 网关, Internet Gateway, IGW
created_at: 2023-05-06 23:46
tags: aws, vpc, network, gateway
---

# 概念

Internet 网关是一种横向扩展、冗余且高度可用的 VPC 组件，支持在 VPC 和 Internet 之间进行通信。它支持 IPv4 和 IPv6 流量。它不会对您的网络流量造成可用性风险或带宽限制。

# 作用

借助互联网网关，公有子网中具有公有 IPv4 地址或 IPv6 地址的资源（例如 EC2 实例）可以连接到互联网。同样，互联网上的资源也可以使用公有 IPv4 地址或 IPv6 地址发起到子网中的资源的连接。例如，您可以通过互联网网关，使用本地电脑连接到 AWS 中的 EC2 实例。

# 特点

建立互联网网关并不需要缴纳额外的费用。
如果子网的关联路由表包含指向互联网网关的路由，则该子网称为 [[公有子网]]。如果子网的关联路由表没有指向互联网网关的路由，则该子网称为 [[私有子网]]。

# 参考文献

- [Internet 网关](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/VPC_Internet_Gateway.html)