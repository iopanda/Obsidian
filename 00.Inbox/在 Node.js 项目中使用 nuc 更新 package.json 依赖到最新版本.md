---
author: iopanda
created_at: 2023-07-28 14:01
tags: nodejs, npm
---

# 概要
---
有时项目中依赖的版本会与当前node的版本不兼容，此时需要更新项目中的依赖版本。由于手动修改会十分繁琐，因此需要一个自动更新版本的工具来帮助我们快速将依赖对其到最新状态。


# 内容
---
在 npm 中使用 ncu 就可以实现以上功能，具体用法如下：

### 1. 安装

```shell
npm install -g npm-check-updated
```

### 2. 使用

在项目目录中运行以下命令：

```shell
# 检查 package.json 中依赖的最新版本
ncu

# 更新依赖到最新版本
ncu -u
```


# 引用
---

- [nodejs更新package.json中的dependencies依赖到最新版本](https://blog.51cto.com/u_15760883/5610423)
