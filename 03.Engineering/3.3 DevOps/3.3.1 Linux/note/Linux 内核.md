---
aliases: Linux 内核
created_at: 2023-07-07 16:50
tags: linux, kernel, os
---

# 概念

Linux® 内核是 [Linux 操作系统（OS）](https://www.redhat.com/zh/topics/linux/what-is-linux)的主要组件，也是计算机硬件与其进程之间的核心接口。它负责两者之间的通信，还要尽可能高效地管理资源。

之所以称为内核，是因为在操作系统中就像果实硬壳中的种子一样，控制着硬件（无论是电话、笔记本电脑、服务器，还是任何其他类型的计算机）的所有主要功能。


# Linux 内核的作用是什么？

内容有以下四项作用：

1. **内存管理：** 追踪记录有多少内存存储了什么以及存储在哪里
2. **进程管理：** 确定哪些进程可以使用中央处理器（CPU）、何时使用以及持续多长时间
3. **设备驱动程序：** 充当硬件与进程之间的调解程序/解释程序
4. **系统调用和安全防护：** 从流程接受服务请求

在正确实施的情况下，内核对于用户是不可见的，它在自己的小世界（称为内核空间）中工作，并从中分配内存和跟踪所有内容的存储位置。用户所看到的内容（例如 Web 浏览器和[文件](https://www.redhat.com/zh/topics/data-storage/file-block-object-storage)）则被称为用户空间。这些应用通过系统调用接口（SCI）与内核进行交互。

可以这样理解_：_内核就像是一个为高管（硬件）服务的忙碌的个人助理。助理的工作就是将员工和公众（用户）的消息和请求（进程）转交给高管，记住存放的内容和位置（内存），并确定在任何特定的时间谁可以拜访高管、会面时间有多长。


# 内核在操作系统中的位置

为了更具象地理解内核，不妨将 [Linux](https://www.redhat.com/zh/topics/linux) 计算机想象成有三层结构：

1. **硬件：** 物理机（这是系统的底层结构或基础）是由内存（RAM）、处理器（或 CPU）以及输入/输出（I/O）设备（例如[存储](https://www.redhat.com/zh/topics/data-storage)、[网络](https://www.redhat.com/zh/topics/hyperconverged-infrastructure/what-is-software-defined-networking)和图形）组成的。其中，CPU 负责执行计算和内存的读写操作。
2. **Linux 内核：** 操作系统的核心。（没错，内核正处于核心的位置）它是驻留在内存中的软件，用于告诉 CPU 要执行哪些操作。
3. **用户进程：** 这些是内核所[管理](https://www.redhat.com/zh/topics/management)的运行程序。用户进程共同构成了用户空间。用户进程有时也简称为 _进程_ 。内核还允许这些进程和服务器彼此进行通信（称为进程间通信或 IPC）。

系统执行的代码通过以下两种模式之一在 CPU 上运行：内核模式或用户模式。在内核模式下运行的代码可以不受限制地访问硬件，而用户模式则会限制 SCI 对 CPU 和内存的访问。内存也存在类似的分隔情况（内核空间和用户空间）。这两个小细节构成了一些复杂操作的基础，例如[安全防护](https://www.redhat.com/zh/topics/security)、[构建容器](https://www.redhat.com/zh/topics/containers)和[虚拟机](https://www.redhat.com/zh/topics/virtualization/what-is-a-virtual-machine)的权限分隔。

这也意味着：如果进程在用户模式下失败，则损失有限，无伤大雅，可以由内核进行修复。另一方面，由于内核进程要访问内存和处理器，因此内核进程的崩溃可能会引起整个系统的崩溃。由于用户进程之间会有适当的保护措施和权限要求，因此一个进程的崩溃通常不会引起太多问题。  
此外，由于 Linux 内核可以在[实时修补](https://www.redhat.com/zh/topics/linux/what-is-linux-kernel-live-patching)期间持续工作，因此在应用补丁进行安全修复时不会出现停机。


# 参考文献

- [Redhat: 什么是 Linux 内核](https://www.redhat.com/zh/topics/linux/what-is-the-linux-kernel)