---
author: iopanda
created_at: 2023-05-06 22:16
tags: VPC
---

# Overview
---
- 什么是 [[Virtual Private Cloud (VPC)]] ？
![[Virtual Private Cloud (VPC)#^vpc-concpet]]

# Content
---

## 1. [[CIDR]]

CIDR是一组连续的IP地址构成的块。例如：192.168.0.0/26 表示IP地址从192.168.0.0 ～ 192.168.0.63。
在AWS中，CIDR经常出现在 [[安全组]]、[[路由表]]、[[Virtual Private Cloud (VPC)|VPC]]、[[子网]] 等配置中。

## 2. [[私有IP]]

私有IP是AWS网络内部使用的IP地址，与 [[公有IP]] 相比，其仅限于AWS网络内部资源的相互访问

## 3. [[公有IP]]

用于与Internet通信的IP地址

## 4. VPC 和 CIDR

在创建VPC时必须为其定义一个[[CIDR]]块，所有创建在该VPC中的资源均共享此CIDR块地址空间
VPC是私有的网络，所以只有 [[私有IP]] 的CIDR区间可被分配

## 5. [[子网]]

子网存在与 [[Virtual Private Cloud (VPC)|VPC]] 内部，通过分割VPC的CIDR空间来划分相互独立且隔离的逻辑空间
子网内部的实例将从子网的CIDR空间中分配IP地址
子网的前4个和最后一个IP是AWS的保留地址，不可将其分配给实例

## 6. [[路由表]]

用于控制网络流量的流向；
可以被绑定到特定的 [[子网]]；
始终遵循“最具体”的路由规则（192.168.0.1/24 强于 0.0.0.0/0）

## 7. [[Internet网关（IGW）]]

用于将VPC连接到Internet，高可用，可横向扩展
充当具有公共 IPv4 或公共 IPv6 实例的 [[NAT]]

## 8. [[公有子网]]

路由表中拥有从 0.0.0.0/0 到 [[Internet网关（IGW）|IGW]] 路由的子网
实例必须拥有 [[公有IP]] 才能与Internet通信

## 9. [[私有子网]]

路由表中不包含到 [[Internet网关（IGW）|IGW]] 的路由
私有如果需要访问Internet资源，需要配合 [[NAT 实例]] 或 [[NAT 网关]] 来实现网络地址转换

## 10. [[NAT 实例]]

NAT 实例 是一个部署在 [[公有子网|公有子网]] 中的 [[EC2 实例]]
可以为 [[私有子网|私有子网]] 中的路由表配置一条从 0.0.0.0/0 到 [[NAT 实例]] 的路由，来实现 [[私有子网|私有子网]] 中的实例资源访问Internet的目的
没有弹性，带宽受限，价格便宜
必须自己管理 [[故障转移]]
必须为该EC2实例禁用 **源/目的 检查**

## 11. [[NAT 网关]]

AWS管理的NAT解决方案，带宽可自动扩展
对单个 [[AZ]] 内的故障具有弹性
必须在多个 AZ 中部署多个 NAT 网关以实现 [[HA]]
拥有弹性IP，外部服务以 NAT 网关 的IP为源

## 12. [[Network ACL (NACL)]]

在 [[子网|子网]] 级别定义的无状态防火墙，适用于其中的所有实例
支持允许和拒绝规则
无状态 = 规则必须明确允许返回流量
有助于快速且廉价地 [[阻止特定 IP 地址]]

## 13. [[安全组 (Security Groups, SG)]]

应用于实例级别，只支持允许规则，不支持拒绝规则
有状态 = 自动允许返回流量，无论规则如何
可以引用同地域的其他安全组（[[对等VPC]]、[[跨账号]]）

## 14. [[VPC Flows Logs]]

记录通过您的 [[Virtual Private Cloud (VPC)|VPC]] 的互联网流量
可以在 [[Virtual Private Cloud (VPC)|VPC]] 级别、[[子网|子网]] 级别或 [[ENI]] 级别定义
有助于捕获“拒绝的互联网流量”
可以发送到 [[CloudWatch Logs]] 和 [[Amazon S3]]

## 15. [[堡垒机 (Bastion Hosts)]]

通过公共 EC2 实例（堡垒主机）SSH 进入私有 EC2 实例
您必须自己管理这些实例（故障转移、恢复）
[[SSM Session Manager]] 是一种更安全的远程控制方式，无需 SSH

## 16. IPv6 简述

所有 IPv6 地址都是公开的，总共 3.4×10^38 个地址（相对于 43 亿个 IPv4）
示例 CIDR：2600:1f18:80c:a900::/56
地址是“随机”的，无法在线扫描（因为太多）

## 17. VPC 对 IPv6 的支持

为 VPC 创建 IPv6 CIDR 并使用 [[Internet网关（IGW）|IGW]]（支持 IPv6）
• 公共子网：
	• 创建支持 IPv6 的实例
	• 创建路由表条目到 ::/0（IPv6“全部”）到 [[Internet网关（IGW）|IGW]]
• 私有子网（实例无法通过IPv6 访问但可以访问IPv6）：
	• 在公共子网中创建 [[仅出口互联网网关 (Egress-Only IGW)]]
	• 将私有子网的路由表条目从 ::/0 添加到 [[仅出口互联网网关 (Egress-Only IGW)]]


# References
---
- [AWS VPC 用户指南](https://docs.aws.amazon.com/zh_cn/vpc/latest/userguide/index.html)



