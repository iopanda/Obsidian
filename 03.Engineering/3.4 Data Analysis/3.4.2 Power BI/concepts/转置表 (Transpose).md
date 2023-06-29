---
aliases: 转置表, Transpose
created_at: 2023-05-09 19:12
tags: powerbi, data analysis
---

# 概念

Power Query 中的转置表操作会将表旋转 90 度，将行转换为列，将列转换为行。

# 效果

## 转换前
![[Pasted image 20230509191237.png]]

## 转换后
![[Pasted image 20230509191249.png]]

# 作用

在某些场景下，数据的初始状态由于各种原因（大多由于人类的阅读习惯）而被设置成最左列为属性名称，而这样的结构非常不便于计算机对其进行处理。因此使用转置表功能可以将表结构旋转90度以便于后续处理。


# 参考文献

-   [转置表](https://learn.microsoft.com/zh-cn/power-query/transpose-table)