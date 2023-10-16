# ✅事件(8)

### ✅单聊消息

用户在单聊发送消息给机器人

	基本概况

| 基本 |  |  
| --- | --- |  
| intents	| 1<<25 |  
| 事件类型	| C2C_MESSAGE_CREATE | 
| 触发场景	| 用户在单聊发送消息给机器人 |  
| 权限要求	| 无特殊要求 |  
| 推送方式	| Websocket |  

	事件字段

| 属性	| 类型	| 说明 | 
| --- | --- | --- |  
| id	| string	| 平台方消息ID，可以用于被动消息发送 |  
| author	| object	| 发送者 |  
| conent	| string	| 消息内容 |  
| timestamp	| string	| 消息生产时间 |  
| attachments	| [] | 	|  

	事件示例

```
{
    "op": 0,
    "s": 2,
    "t": "C2C_MESSAGE_CREATE",
    "id": "C2C_MESSAGE_CREATE:051c863a-05d1-483d-8fd5-15b4e1d7ea1a",
    "d": {
        "author": {
            "id": "E4F4AEA33253A2797FB897C50B81D7ED"
        },
        "content": "123",
        "group_id": "0",
        "id": "ROBOT1.0_.b6nx.CVryAO0nR58RXuU6SC.m92gc19j02qKqdm8ek!",
        "timestamp": "2023-09-04 18:42:57.404149365 +0800 CST m=+352051.396449269"
    }
}

```

	其他说明

暂无

### ✅群聊@机器人

用户在群内@机器人发动的消息

	基本概况

| 基本 |  |  
| --- | --- |  
| intents	| 1<<25 |  
| 事件类型	| GROUP_AT_MESSAGE_CREATE |  
| 触发场景	| 用户在群聊@机器人发送消息 |  
| 权限要求	| 无特殊要求 |  
| 推送方式	| Websocket |  

	事件字段

| 属性	| 类型	| 说明 |  
| --- | --- | --- |
| id	| string	| 平台方消息 ID，可以用于被动消息发送 |  
| author	| object	| 发送者 |  
| conent	| string	| 消息内容 |  
| timestamp	| string	| 消息生产时间 |  
| group_id	| string	| 群聊的 openid |  

	事件示例

```
// Websocket
{
    "op": 0,
    "s": 3,
    "t": "GROUP_AT_MESSAGE_CREATE",
    "id": "GROUP_AT_MESSAGE_CREATE:87612938-5b4b-441f-b4aa-2c0266092fe0",
    "d": {
        "author": {
            "id": "E4F4AEA33253A2797FB897C50B81D7ED"
        },
        "content": " 123",
        "group_id": "C9F778FE6ADF9D1D1DBE395BF744A33A",
        "id": "ROBOT1.0_eBIyWnxpmSu6uLQ7u7fU0eGloKGYg4eEa737vRyKnMCgyZjKi7JLYkQ9B0VapbiY",
        "timestamp": "2023-09-04 18:50:34.560639335 +0800 CST m=+352012.788711412"
    }
}

```

	其他说明

暂无

### 🚫群聊全量消息（私域）

「暂不开放」用户在群内发送的所有聊天消息

### 🚫群聊关键词消息

「暂不开放」用户在群内发送的消息命中了某些关键词

### ✅频道私信消息

用户在频道私信给机器人发送的消息

	基本概况

| 基本 |  |  
| --- | --- |  
| 事件类型	| DIRECT_MESSAGE_CREATE |  
| 触发场景	| 用户在频道私信内发送消息给机器人 |  
| 权限要求	| 无特殊要求 |  
| 推送方式	| Websocket |  

	详细文档

[私信消息事件 \|  QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/gateway/direct_message.html#direct-message-create-intents-direct-message)

### ✅文字子频道@机器人

用户在文字子频道内@机器人发送的消息

	基本概况

| 基本 |  |  
| --- | --- |  
| 事件类型	| AT_MESSAGE_CREATE |  
| 触发场景	| 用户在频道私信内发送消息给机器人 |  
| 权限要求	| 无特殊要求 |  
| 推送方式	| Websocket |  

	详细文档

[消息事件 \|  QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/gateway/message.html)

### ✅文字子频道全量消息（私域）

用户在文字子频道内发送的所有聊天消息（私域）

	基本概况

| 基本 |  |  
| --- | --- |  
| 事件类型	| MESSAGE_CREATE |  
| 触发场景	| 用户在频道私信内发送消息给机器人 | 
| 权限要求	| 无特殊要求 |  
| 推送方式	| Websocket |  

	详细文档

[消息事件 \|  QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/gateway/message.html)，字段结构与 AT_MESSAGE_CREATE 相同。

### 🚫文字子频道关键词消息

「暂不开放」用户在文字子频道内发送的消息命中了某些关键词

