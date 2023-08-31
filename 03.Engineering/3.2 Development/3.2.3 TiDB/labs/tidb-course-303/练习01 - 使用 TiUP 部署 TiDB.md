---
author: iopanda
created_at: 2023-08-18 13:51
tags: tidb
---


**练习目的**

- 在这个练习中，您将会用到 TiUP 工具来部署 TiDB 数据库集群，并且连接到 TiDB 执行 SQL 语句。

**前提条件**

- 注意，您的实验环境（包括 IP、端口号、用户名、密码和目录）可能与手册不同。
- 可以连接到实验用虚拟机。

步骤

1. 下载并安装 TiUP 工具

- 打开终端
	- Linux 进入 Terminal
	- MacOS 打开 Terminal.app

- 执行以下命令，下载并安装 TiUP 工具（注意 `$` 是终端提示符，常见的也有可能是`%`）。

```shell
$ curl --proto '=https' --tlsv1.2 -sSf https://tiup-mirrors.pingcap.com/install.sh | sh

$ source .bash_profile
```

- 执行以下命令，下载并安装 tiup cluster 组件：

```
tiup cluster
```

2. 初始化集群拓扑文件

- 执行如下命令，生成集群初始化配置文件：

```
$ tiup cluster template > topology.yaml
```

- 执行 `vi topology.yaml`， 修改配置文件的内容：

```
$ vi topology.yaml
```

3. 执行部署命令

- 检查集群是否存在潜在的风险

```
$ tiup cluster check ./topology.yaml --user root -p
```

- 使用“--apply”修复潜在的问题

```
$ tiup cluster check ./topology.yaml --apply --user root -p
```

- 部署 TiDB 集群

```
$ tiup cluster deploy tidb-test v6.1.0 ./topology.yaml --user root -p
```

4. 查看 TiUP 管理的集群情况

```
$ tiup cluster list
```

5. 检查部署的 TiDB 集群情况：

```
$ tiup cluster display tidb-test
```

6. 启动集群

- 方式一：安全启动

```
$ tiup cluster start tidb-test --init
```

- 方式二：普通启动

```
$ tiup cluster start tidb-test
```

7. 验证集群运行状态

- 通过 TiUP 检查集群状态
  - 查看 TiDB Dashboard 检查 TiDB 集群状态
    - 通过 `{pd-ip}:{pd-port}/dashbaord` 登录 TiDB Dashboard，登录用户和口令为 TiDB 数据库 root 用户和口令。如果您修改过数据库的 root 密码，则以修改后的密码为准，默认密码为空。
    - 主页面显示 TiDB 集群中节点的信息
  - 查看 Grafana 监控 Overview 页面，检查 TiDB 集群状态
    - 通过`{grafana-ip}:3000` 登录 Grafana 监控，默认用户名及密码为 admin/admin。
    - 点击`Overview`监控页面检查 TiDB 端口和负载监控信息。

8. 使用 mysql 客户端连接 TiDB，并且将密码修改为“tidb”

```
$ mysql --host 172.31.0.106 --port 4000 -u root -p
```

```mysql
> set password for 'root'@'%' = 'tidb'
```
