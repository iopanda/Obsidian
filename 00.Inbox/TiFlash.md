---
aliases: TiFlash
created_at: 2023-08-08 17:43
tags: tidb, database
---

# 概念

TiFlash 是 TiDB HTAP 形态的关键组件，它是 TiKV 的列存扩展。在提供了良好的隔离性的同时，也兼顾了强一致性。列存副本痛过 [[Raft Learner 协议]] 异步复制，但是在读取的时候通过 Raft 校对索引配合 MVCC 的方式获得 Snapshot Isolation 的一致性隔离级别。这个架构很好地解决了 HTAP 场景的隔离性以及列存同步的问题。

## 整体架构

![TiFlash 架构](https://download.pingcap.com/images/docs-cn/tidb-storage-architecture-1.png)

TiFlash 提供列式存储，且拥有借助 ClickHouse 高效实现的协处理器层。除此之外，它与 TiKV 非常类似，以来同样的 Multi-Raft 体系，以 Region 为单位进行数据复制和分散。

TiFlash 以低消耗不阻塞 TiKV 写入的方式，实时复制 TiKV 集群中的数据，并同时提供宇 TiKV 一样的一致性读取，且可以保证读取到最新的数据。TiFlash 中的 Region 副本与 TiKV 中完全对应，且会跟随 TiKV 中的 Leader 副本同时进行分裂与合并。

TiFlash 可以兼容 TiDB 与 TiSpark，用户可以选择使用不同的计算引擎。

TiFlash 推荐使用和 TiKV 不同的节点以做到负载隔离，但在无隔离需求的前提下，也可以同点部署。

TiFlash 暂时无法直接接受数据写入，任何数据必须先写入 TiKV 再同步到 TiFlash。TiFlash 以 learner 角色接入 TiDB 集群。

TiFlash 主要包含三个组件，除了主要的存储引擎组件，另外包含 [[tiflash proxy]] 和 [[pd buddy]] 组件。其中 tiflash proxy 主要用于处理 Multi-Raft 协议通信的相关工作，pd buddy 负责与 PD 协同工作，将 TiKV 数据按表同步到 TiFlash。

# 特性

## 异步复制

## 一致性

## 智能选择

## 计算加速


# 对比



# 参考文献

