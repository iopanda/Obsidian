---
author: iopanda
created_at: 2023-05-09 21:04
tags: 在用户确认注册后配置响应的Lambda
---

# Overview
---



# Content
---

首先在“用户池属性”中添加响应的动作并与Lambda绑定：

![[Pasted image 20230509210517.png]]

此时，如果用户在确认账号之后，Lambda会收到如下事件：

```json
{
    "version": "1",
    "region": "us-east-1",
    "userPoolId": "us-east-1_UwzKGmAb9",
    "userName": "jason_username",
    "callerContext": {
        "awsSdkVersion": "aws-sdk-unknown-unknown",
        "clientId": "6o9ei11451iho8acjpn69e15i9"
    },
    "triggerSource": "PostConfirmation_ConfirmSignUp",
    "request": {
        "userAttributes": {
            "sub": "69f23de6-af9e-43cc-b208-8b269334667d",
            "cognito:email_alias": "sunxiaoyu.space@outlook.com",
            "email_verified": "true",
            "cognito:user_status": "CONFIRMED",
            "name": "jason_name",
            "email": "sunxiaoyu.space@outlook.com"
        }
    },
    "response": {}
}
```


# References
---


