---
aliases: TiDB的分布式事务
created_at: 2023-08-08 16:23
tags: tidb, transaction, database
---

# 概念

TiDB支持完整的分布式事务，提供[[乐观事务]]和[[悲观事务]]两种事务模型。

## 事务隔离级别
![[Pasted image 20230808164046.png]]
[[SQL-92]] 标准定义了4中隔离级别：
- 读未提交（READ UNCOMMITTED）
- 读已提交（READ COMMITTED）
- 可重复读（REPEATABLE READ）
- 串行化（SERIALIZABLE）

TiDB语法上支持 READ COMMITTED 和 REPEATABLE READ 两种隔离级别。
```shell
mysql> SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
ERROR 8048 (HY000): The isolation level 'READ-UNCOMMITTED' is not supported. Set
↪→ tidb_skip_isolation_level_check=1 to skip this error
mysql> SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
Query OK, 0 rows affected (0.00 sec)
mysql> SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;
Query OK, 0 rows affected (0.00 sec)
mysql> SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
ERROR 8048 (HY000): The isolation level 'SERIALIZABLE' is not supported. Set
↪→ tidb_skip_isolation_level_check=1 to skip this error
```

TiDB实现了快照隔离（Snapshot Isolation，SI）级别的一致性。为与MySQL保持一致，又称其为“可重复度”。该隔离级别不同于 [[ANSI 可重复读隔离级别]] 和 [[MySQL 可重复读隔离级别]]。

## 乐观事务和悲观事务

- 乐观事务模型就是直接提交，遇到冲突就回滚。
- 悲观事务模型就是在真正提交事务前，先尝试对需要修改的资源上锁，只有在确保事物一定能够执行成功后才开始提交。

## 事务限制

- TiDB 支持的隔离级别是 RC 与 SI ，其中 SI 与 RR 隔离级别基本等价。
- TiDB 的 SI 隔离级别可以克服 [[幻读异常（Phantom Reads）]]，但 [[ANSI/ISO SQL]] 标准中的 RR 不能。
- TiDB 的 SI 不能克服 [[写偏斜异常（Write Skew）]]，需要使用“select for update”愈发来克服。
- 大事务限制：
	- 最大单行记录容量为 120MB（TiDB v5.0 及更高版本可通过 tidb-server 配置项 performance.txn-entry-size-limit 调整，低于TiDB v5.0 的版本支持的单行容量为 6MB）
	- 支持的最大单个事务容量为 10GB（TiDB v4.0 及更高版本可通过 tidb-server 配置项 performance.txn-total-size-limit 调整，低于 TiDB v4.0 的版本支持的最大单个事务容量为 100MB）
- 自动提交的 SELECT FOR UPDATE 语句不会等锁，这里与MySQL不兼容。

# 用法

开启事务：
```sql
BEGIN;
# DO YOUR WORK HERE
```
或：
```sql
START TRANSACTION;
# DO YOUR WORK HERE
```

TiDB的默认事务模式是悲观事务，当然也可以显示定义事务类型：
```sql
# 开启乐观事务
BEGIN OPTIMISTIC;

# 开启悲观事务
BEGIN PESSIMISTIC;
```

如果执行以上语句时，当前Session正处于一个事务的中间过程，则系统会先提交当前事务，再开启一个新的事务。

提交事务：
```sql
COMMIT;
```

回滚事务：
```sql
ROLLBACK;
```
# 对比



# 参考文献

