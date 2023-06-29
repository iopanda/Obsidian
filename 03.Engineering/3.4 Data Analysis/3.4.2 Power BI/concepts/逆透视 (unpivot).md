---
aliases: 逆透视, unpivot
created_at: 2023-05-09 19:16
tags: powerbi, data analysis
---
![[Pasted image 20230509191751.png]]
# 概念

在 Power Query 中，可以将列转换为属性值对，其中列成为行。

# 作用

有时我们需要将表的属性名称作为值进行处理，如日期、类型等。但在许多数据源中，这样的属性名称往往是以列名称出现的。此时可以通过逆透视来将这些属性逆透视到列值中，便于下一步处理。

# 效果

## 逆透视前
![[Pasted image 20230509191826.png]]

## 逆透视后
![[Pasted image 20230509191831.png]]

# 区分

注意，逆透视的行为与 [[转置表 (Transpose)|转置表]] 有些许类似。但他们是对数据不同的操作。
其中，[[转置表 (Transpose)|转置表]] 是作用在整个表上的，但 逆透视 是作用于选定列上的。逆透视会在处理过程中将选中的属性名称重复地填充到列值中，因此使用逆透视之后，行数可能会增加。


# 参考文献

-   [逆透视列](https://learn.microsoft.com/zh-cn/power-query/unpivot-column)