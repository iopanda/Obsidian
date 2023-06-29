---
aliases: CIDR
created_at: 2023-05-06 22:46
tags: aws, vpc, cidr, network
---

# 概念

**无类别域间路由**（英语：Classless Inter-Domain Routing，简称**CIDR**[/ˈsaɪdər, ˈsɪ-/](https://zh.wikipedia.org/wiki/Help:%E8%8B%B1%E8%AA%9E%E5%9C%8B%E9%9A%9B%E9%9F%B3%E6%A8%99 "Help:英语国际音标")）是一个用于给用户分配[IP地址](https://zh.wikipedia.org/wiki/IP%E5%9C%B0%E5%9D%80 "IP地址")以及在[互联网](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91 "互联网")上有效地路由IP[数据包](https://zh.wikipedia.org/wiki/%E6%95%B0%E6%8D%AE%E5%8C%85 "数据包")的对IP地址进行归类的方法。

# 出现原因

在[域名系统](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F "域名系统")出现之后的第一个十年里，基于[分类网络](https://zh.wikipedia.org/wiki/%E5%88%86%E7%B1%BB%E7%BD%91%E7%BB%9C "分类网络")进行地址分配和路由IP数据包的设计就已明显显得[可扩充性](https://zh.wikipedia.org/wiki/%E5%8F%AF%E6%89%A9%E6%94%BE%E6%80%A7 "可扩放性")不足（参见RFC 1517）。为了解决这个问题，[互联网工程工作小组](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91%E5%B7%A5%E7%A8%8B%E5%B7%A5%E4%BD%9C%E5%B0%8F%E7%BB%84 "互联网工程工作小组")在1993年发布了一新系列的标准——[RFC 1518](https://tools.ietf.org/html/rfc1518)和RFC 1519——以定义新的分配IP地址块和路由[IPv4](https://zh.wikipedia.org/wiki/IPv4 "IPv4")数据包的方法。

# 工作原理

无类别域间路由是基于**可变长子网掩码（VLSM）**来进行任意长度的前缀的分配的。在RFC 950（1985）中有关于可变长子网掩码的说明。CIDR包括：

-   指定任意长度的前缀的可变长子网掩码技术。遵从CIDR规则的地址有一个后缀说明前缀的位数，例如：192.168.0.0/16。这使得对日益缺乏的IPv4地址的使用更加有效。
-   将多个连续的前缀聚合成**[超网](https://zh.wikipedia.org/w/index.php?title=%E8%B6%85%E7%BD%91&action=edit&redlink=1 "超网（页面不存在）")**，以及，在互联网中，只要有可能，就显示为一个聚合的网络，因此在总体上可以减少路由表的表项数目。聚合使得互联网的路由表不用分为多级，并通过VLSM逆转“划分子网”的过程。
-   根据机构的实际需要和短期预期需要而不是分类网络中所限定的过大或过小的地址块来管理IP地址的分配的过程。

因为在[IPv6](https://zh.wikipedia.org/wiki/IPv6 "IPv6")中也使用了IPv4的用后缀指示前缀长度的CIDR，所以IPv4中的_分类_在IPv6中已不再使用。


# 参考文献
- [维基百科：无类别域间路由](https://zh.wikipedia.org/wiki/%E6%97%A0%E7%B1%BB%E5%88%AB%E5%9F%9F%E9%97%B4%E8%B7%AF%E7%94%B1#CIDR%E5%9D%97%E7%9A%84%E5%88%86%E9%85%8D)