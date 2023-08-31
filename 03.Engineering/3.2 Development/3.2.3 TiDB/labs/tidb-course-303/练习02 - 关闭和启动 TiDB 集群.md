---
aliases: 练习02 - 关闭和启动 TiDB 集群
created_at: 2023-08-18 14:34
tags: tidb
---

**练习目的**

- 在这个练习中，您将会练习到关闭和启动 TiDB 数据库集群并查看系统文件。

**前提条件**

- 注意，您的实验环境（包括 IP、端口号、用户名、密码和目录）可能与手册不同。
- 可以连接到实验用虚拟机。

# 步骤

1. TiDB Cluster 的启动

```
tiup cluster start tidb-test
```

2. TiDB Cluster 的停止

```
tiup cluster stop tidb-test
```

3. 查看文件位置

```
tiup cluster edit-config tidb-test
```

- TiDB 节点的文件：

配置文件与日志

```
cd /tidb-deploy/tidb-4000/
```

数据文件

```
cd /tidb-data/
```

- TiKV 节点的文件

配置文件与日志

```
cd /tidb-deploy/
cd tikv-20160/
```

数据文件

```
cd /tidb-data/
cd tikv-20160/
```

- PD 节点的文件

