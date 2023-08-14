---
aliases: TiKV
created_at: 2023-08-08 17:34
tags: tidb, database
---

# 概念

TiKV 是一个分布式事务型的键值数据库，提供了满足 ACID 约束的分布式事务接口，并且通过 [[Raft 协议]] 保证了多副本数据一致性及高可用。TiKV 作为 TiDB 的存储层，为用户写入 TiDB 的数据提供了持久化及读写服务，同时还存储了 TiDB 的统计信息数据。

## 整体架构

TiKV 参考 Spanner 设计了 multi-raft-group 的副本机制。将数据按照 key 的范围划分成**大致相等**的切片（Region），每个Region会有多个副本（通常是3个），其中一个副本是Leader，提供读写服务。KiTV 通过 PD 对这些 Region 以及副本进行调度，以保证数据和读写负载都**均匀地**分散在各个 TiKV 上，这样的设计保证了整个集群资源的充分利用，并且可以随着机器数量的增加水平扩展。

![TiKV 架构](https://download.pingcap.com/images/docs-cn/tikv-arch.png)

## Region 与 [[RocksDB]]

## Region 与 [[Raft 协议]]

## 分布式事务

## 计算加速


# 用法



# 对比



# 参考文献

