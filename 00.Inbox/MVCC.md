---
aliases: MVCC, Multi-Version Concurrency Control ,多版本并发控制
created_at: 2023-08-17 17:25
tags: tidb
---

# 概念

很多数据库都会实现多版本并发控制（MVCC），TiKV也不例外。当两个客户端同时修改一个KV时，如果没有数据的多版本控制，就需要对数据上锁。在分布式场景下，这可能会带来性能及死锁问题。TiKV的MVCC实现是通过在Key后面添加版本好来实现。简单来说，没有MVCC之前，可以把TiDK看作如下所示：

```
Key1 -> Value 
Key2 -> Value 
…… 
KeyN -> Value
```

有了MVCC之后，TiKV的Key排列是这样的：

```text
Key1_Version3 -> Value
Key1_Version2 -> Value
Key1_Version1 -> Value
…… 
Key2_Version4 -> Value 
Key2_Version3 -> Value 
Key2_Version2 -> Value 
Key2_Version1 -> Value 
…… 
KeyN_Version2 -> Value 
KeyN_Version1 -> Value 
……
```

注意，对于同一个 Key 的多个版本，版本号较大的会被放在前面，版本号小的会被放在后面（见 [Key-Value](https://docs.pingcap.com/zh/tidb/stable/tidb-storage#key-value-pairs%E9%94%AE%E5%80%BC%E5%AF%B9) 一节，Key 是有序的排列），这样当用户通过一个 Key + Version 来获取 Value 的时候，可以通过 Key 和 Version 构造出 MVCC 的 Key，也就是 Key_Version。然后可以直接通过 RocksDB 的 SeekPrefix(Key_Version) API，定位到第一个大于等于这个 Key_Version 的位置。

# 用法



# 对比



# 参考文献

- [MVCC](https://docs.pingcap.com/zh/tidb/stable/tidb-storage#mvcc)