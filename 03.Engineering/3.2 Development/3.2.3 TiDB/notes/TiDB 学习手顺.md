---
author: iopanda
created_at: 2023-08-04 18:24
tags: TiDB 学习手顺
---

# 概要
---

# 内容
---

## 简介

### 五大核心特性

- 一键水平扩缩容
- 金融级高可用
- 实时HTAP
- 云原生分布式数据库
- 兼容MySQL协议及生态

### 四大核心应用场景

- 对数据一致性及高可靠、系统高可用、可扩展性、容灾要求较高的金融行业属性的场景
- 对存储容量、可扩展性、并发要求较高的海量数据及高并发的OLTP场景
- 实时HTAP场景
- 数据汇聚、二次加工处理的场景



![[Pasted image 20230816131652.png]]

![[Pasted image 20230816133327.png]]


WAL, sync_log=true, write_buffer_size
write_stall：rocksDB限速
compaction

![[Pasted image 20230816154241.png]]



# 引用
---


