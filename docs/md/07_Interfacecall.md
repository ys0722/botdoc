# 接口调用

在每次调用 https 的 openapi 开放接口请求的时候，需要在 header 内引入 access_token 进行调用权限验证。

| 地址 |
| ----- |
| https://api.sgroup.qq.com |

##### 请求头

| 名称 | 类型 | 必填 | 描述|
| --------------------- | ---- | ---------- | -------- |
| Authorization	| string | 是 | 格式值："QQBot ACCESS_TOKEN" |
| X-Union-Appid	| string | 是 | 格式值："BOT_APPID", 机器人 appid |


##### 事例

 