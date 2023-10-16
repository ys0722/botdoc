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
| id	| string	| 平台方消息 ID，可以用于被动消息发送 |  
| author	| object	| 发送者 |  
| conent	| string	| 消息内容 |  
| timestamp	| string	| 消息生产时间 |  
| group_id	| string	| 群聊的 openid |  

	事件示例

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

