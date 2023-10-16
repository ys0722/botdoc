# API 调用｜鉴权

QQ BOT 服务端开放的 openapi 接口，均使用 https 方式进行调用，通过  access token 机制实现对 openapi 接口调用的鉴权。

### 获取接口凭证

#####	请求  

| 基本| - |
| --------------------- | ---- |  
| HTTP URL | https://bots.qq.com/app/getAppAccessToken |
| HTTP Method | POST |  

### 接口频率限制	

##### 请求参数

| 属性 | 类型 | 必填 | 说明 |
| --------------------- | ---- | ---------- | -------- |
| appId | string | 是 | 在开放平台管理端上获得。 |
| clientSecret | string	| 是 | 在开放平台管理端上获得。 |

##### 返回参数

| 属性 | 类型 | 说明 |
| --------------------- | ---- | ---------- |
| access_token | string	| 获取到的凭证。 |
| expires_in | number | 凭证有效时间，单位：秒。目前是7200秒之内的值。 |

##### 错误码

| 错误码 | 错误码取值 | 解决方案 |
| --------------------- | ---- | ---------- |
| 0	| ok |  |

##### 调用示例  

```
curl --location 'https://bots.qq.com/app/getAppAccessToken' \
--header 'Content-Type: application/json' \
--data '{
    "appId": "APPID",
    "clientSecret": "CLIENTSECRET"
}'

```



##### 返回示例  

```
{
    "access_token": "ACCESS_TOKEN",
    "expires_in": "7200"
}

```



##### 其他说明  

目前 access_token 生命周期默认 7200 秒，每次请求不会刷新新的 access_token，开发者需要在过期后自行刷新 access_token，保证调用链路权限正常。

在上一个 access_token 接近过期时间 60 秒内，获取 access_token 时，会获得一个新的 access_token，老的 access_token 在这个60秒内仍然有效。

