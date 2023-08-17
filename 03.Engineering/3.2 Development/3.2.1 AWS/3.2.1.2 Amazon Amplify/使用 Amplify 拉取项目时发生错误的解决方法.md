---
author: iopanda
created_at: 2023-07-28 20:40
tags: aws, amplify
---

# 概要

在使用 [[AWS Amplify]] 拉取项目时，有时会出现在浏览器点击同意登录后，CLI 并不能成功登录的情况。
![[Pasted image 20230728204313.png]]

点击“Yes”后，CLI会报如下错误：
![[Pasted image 20230728205026.png]]

# 调查

调查后发现，发生该问题的原因是由于浏览器回调时，CLI 拉起的服务报“500 Internal Server Error“错误。具体错误如下图所示：

![[Pasted image 20230728204339.png]]

在浏览器控制台中可以看到HTTP响应的状态码：

![[Pasted image 20230728204509.png]]

此时也尝试过痛过Postman构造请求体来调起CLI暴露的服务，但也会得到同样的错误代码。
根据客户端错误提示：“🛑 Failed to receive expected authentication tokens. Error: \[Error: self signed certificate in certificate chain\]”，可知应该是在回调时遇到了自签名的证书，进而无法验证证书的有效性。

# 解决

通过 CLI 返回的响应可知，该命令是使用 Node.js 实现的。而我们知道，在 Node.js 应用程序中可以通过设置环境变量来让 Node.js 跳过证书验证过程，从而解决问题。因此，可以在命令行中执行以下命令来解决该问题：

```shell
# 让 Node.js 忽略证书验证
export NODE_TLS_REJECT_UNAUTHORIZED=0
```

执行后，再执行 Amplify 命令，即可正常运行：

![[Pasted image 20230728205918.png]]


# 引用



