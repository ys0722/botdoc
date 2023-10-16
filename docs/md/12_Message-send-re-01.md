

### ✅单聊

单独发动消息给用户。

###### 	请求

| 基本 |  |
| ---- | ---- |
| HTTP URL | /v2/users/{openid}/messages |
| HTTP Method |	POST |
| 接口频率限制 |

	路径参数

| 属性	| 类型	| 必填	| 说明 |
| --- | --- | --- | --- |
| openid | string |	是 | QQ 用户的 openid，可在各类事件中获得。|

	请求参数

| 属性 | 类型 |	必填 |	说明 |
| --- | --- | --- | ---|
| content |	string |	否 |	文本内容 |
| msg_type | int |	是 |	消息类型：0 是文本，1 图文混排 ，2 是 md ，3 ark，4 embed 备注：当发送 md，ark，embed 的时候 centent 字段需要填入随意内容，否则发送失败（后续版本解决该问题）。 |
| markdown |	object |	否 |	格式参考“消息类型=>markdown=>数据结构与协议” |
| keyboard	| object |	否 |	格式参考“消息交互=>消息按钮=>数据结构与协“ |
| ark |	object |	否 |	格式参考“消息类型=>ark=>数据结构与协议” |
| image |  | 否 |	【暂不支持】 |
| message_reference |	object |	否 |	【暂未支持】消息引用 |
| event_id| 	string |	否 |	【暂未支持】前置收到的事件ID，用于发送被动消息 |
| msg_id |	string |	否 |	前置收到的消息ID，用于发送被动消息 |

	返回参数

| 属性 |	类型 |	说明 |
| --- | --- | --- |
| id |	string |	消息唯一ID |
| timestamp	| int	| 发送时间 |

	错误码

| 错误码 | 错误码取值 |	解决方案 |
| --- | --- | --- |
| 0 |	ok	|  |

### ✅群聊

发动消息到群。

	请求

| 基本 |  |
| ---- | ---- |
| HTTP URL	| /v2/groups/{group_openid}/messages |
| HTTP Method	| POST |
| 接口频率限制	|   |

	路径参数

| 属性 | 类型 |	必填 |	说明 |
| --- | --- | --- | ---|
| group_openid |	string	| 是 |	群聊的 openid |

	请求参数

| 属性 | 类型 |	必填 |	说明 |
| --- | --- | --- | ---|
| content	| string	| 是	| 文本内容 |  
| msg_type	| int	| 是	| 消息类型： 0 是文本，1 图文混排 ，2 是 md，3 ark，4 embed，5 at @人或@all，备注：当发送 md，ark 的时候centent需要填入随意内容，否则发送失败（后续版本解决该问题）。 |   
| markdown	| object	| 否	| 格式参考“消息类型=>markdown=>数据结构与协议” |  
| keyboard	| object	| 否	| 格式参考“消息交互=>消息按钮=>数据结构与协“ |  
| ark	| object	| 否	| 格式参考“消息类型=>ark=>数据结构与协议” |  
| image	|  | 否	| 【暂不支持】 |  
| message_reference	| object	| 否	| 【暂未支持】消息引用 |  
| event_id	| string	| 否	| 【暂未支持】前置收到的事件ID，用于发送被动消息 |  
| msg_id	| string	| 否	| 前置收到的消息ID，用于发送被动消息 |  
| timestamp	| int	| 是	| unix 秒级时间戳 |  

	返回参数

| 属性	| 类型	| 说明 |  
| ---- | ---- | --- |  
| id	| string	| 消息唯一ID |  
| timestamp	| int	| 发送时间 |  

	错误码

| 错误码	| 错误码取值	| 解决方案 |  
| --- | --- | --- |  
| 0	| ok |  	

### ✅文字子频道

发动消息到文字子频道。

	请求

| 基本 |  |  
| --- | --- |  
| HTTP URL	| /v2/channels/{channel_id}/messages |  
| HTTP Method	| POST |  
基本
| 接口频率限制	|   |

	详细文档

[发送消息 \|  QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/openapi/message/post_messages.html)

### ✅频道私信

发动消息到频道私信，请求参数与文字子频道发送消息参数一致

	请求

| 基本 |  |  
| --- | --- |  
| HTTP URL	| /v2/dms/{guild_id}/messages |  
| HTTP Method	| POST |  
| 接口频率限制 |  |  	

	详细文档

[发送私信 \|  QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/openapi/dms/post_dms_messages.html)