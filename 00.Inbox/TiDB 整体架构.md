---
aliases: TiDB 整体架构
created_at: 2023-08-08 18:01
tags: tidb, database
---

# 概念

在内核设计上，TiDB 将整体拆分成了多个模块，各个模块之间互相通信，组成完整的 TiDB 系统：
![architecture](https://download.pingcap.com/images/docs-cn/tidb-architecture-v6.png)
- TiDB Server：SQL层，对外暴露 MySQL 协议的连接 endpoint，负责接受客户端的连接，执行SQL解析和优化，最终生成分布式执行计划。
- PD（Placement Driver） Server：整个 TiDB 集群的元信息管理模块，负责存储每个 TiKV 节点实时的数据分布情况和集群的整体拓扑结构，提供 TiDB Dashboard 管控洁面，并为分布式事务分配事务 ID。PD 本身由至少3个接待你构成，拥有高可用的能力。建议部署奇数个PD节点。
- 存储节点：
	- TiKV Server
	- TiFlash

# 用法



# 对比



# 参考文献

