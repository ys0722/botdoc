# 消息交互

 

#### ✅表情表态

![文本框: 目前表情表态仅支持在频道内使用](file:///C:/Users/Administrator/AppData/Local/Temp/msohtmlclip1/01/clip_image001.gif)

##### 机器人发表表情表态

l **详细文档**

[发表表情表态 | QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/openapi/reaction/put_message_reaction.html)

##### 删除机器人发表的表情表态

l **详细文档**

[删除自己的表情表态 | QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/openapi/reaction/delete_own_message_reaction.html)

##### 获取消息表情表态的用户列表

l **详细文档**

[拉取表情表态用户列表 | QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/openapi/reaction/get_reaction_users.html)

 

##### 事件

###### 用户发表

l **基本概况**

用户对消息进行表情表态时，触发事件通知。

l **详细文档**

[表情表态事件 | QQ机器人文档](https://bot.q.qq.com/wiki/develop/api/gateway/guild_message_reactions.html)

 

#### ✅文字链

文本消息内嵌的蓝色文本，QQ Bot 提供文本消息的交互能力，当开发者使用指定的格式发送消息，用户即可在消息体上进行点击交互操作，例如@某人，跳转链接等。
 

##### AT 相关

群聊&文字子频道，支持 文本消息、图文消息、markdown消息。

at 某人，解析为 @用户 标签

嵌入文本格式：

```
<@userid>
```

at 所有人，解析为 @所有人 标签，需要机器人拥有发送 @所有人 消息的权限，仅在文字子频道可用

嵌入文本格式：

```
@everyone
```



##### 指令相关

目前仅在 markdown 支持。

格式：

```
<cmd enter=true reply=true cmd="/回车指令">
```

原生 scheme 格式：

```
[/回车指令](mqqapi://aio/inlinecmd?command={urlencode('/回车指令')}&reply=false&enter=true)
```

格式：

```
<cmd reply=true cmd="/参数指令（带引用本消息）">
<cmd reply=false cmd="/参数指令（不带引用）">
```

原生 scheme 格式：

```
[/参数指令（带引用本消息）](mqqapi://aio/inlinecmd?command="{urlencode('/参数指令（带引用本消息）')"&reply=true&enter=false) 
[/参数指令（不带引用）](mqqapi://aio/inlinecmd?command="{urlencode('/参数指令（不带引用）')"&reply=false&enter=false) 
```

 

##### 跳转子频道

仅频道可用，#子频道 解析为 #子频道 标签，点击可以跳转至子频道，仅支持当前频道内的子频道

```
<#channel_id>
```



##### 表情

仅频道可用，解析为系统表情，具体表情id参考 [Emoji 列表](https://bot.q.qq.com/wiki/develop/api/openapi/emoji/model.html#emoji-列表)，仅支持type=1的系统表情，type=2的emoji表情直接按字符串填写即可



#### ✅消息按钮

在 markdown 消息的基础上，支持消息最底部挂载按钮。

#####  

##### 发送方式

【申请使用】按钮模版，按钮模版暂时不支持使用变量填充。

```
{
    "keyboard": {
        "id": "123" // 申请模版后获得
    }
}

```

【内邀开通】自定义按钮

```
{
    "keyboard": {
        "content": {
            "rows": [
                {"buttons": [{button}, {button}, {button}, {button}, {button}]},
                {"buttons": [{button}, {button}, {button}, {button}, {button}]},
                {"buttons": [{button}, {button}, {button}, {button}, {button}]},
                {"buttons": [{button}, {button}, {button}, {button}, {button}]},
                {"buttons": [{button}, {button}, {button}, {button}, {button}]},
            ] // 自定义按钮内容，最多可以发送5行按钮，每一行最多5个按钮。
        }
    }
}

```



##### 数据结构与协议

消息发送接口 keyboard 字段值是一个 json object，rows 数组表示每一行按钮

每个 button 是一个 json object，具体字段如下：

| **属性**                          | **类型** | **必填** | **说明**                                                     |
| --------------------------------- | -------- | -------- | ------------------------------------------------------------ |
| id                                | string   | 否       | 按钮ID：在一个keyboard消息内设置唯一                         |
|                                   |          |          |                                                              |
| render_data.label                 | string   | 是       | 按钮上的文字                                                 |
| render_data.visited_label         | string   | 是       | 点击后按钮的上文字                                           |
| render_data.style                 | int      | 是       | 按钮样式：0 灰色线框，1 蓝色线框                             |
|                                   |          |          |                                                              |
| action.type                       | int      | 是       | 0 跳转按钮：http 或  小程序 客户端识别 schem, data字段为链接  1 回调按钮：回调后台接口,  data 传给后台  2 指令按钮：自动在输入框插入  @bot data |
|                                   |          |          |                                                              |
| action.permisson.type             | int      | 是       | 0 指定用户可操作  1 仅管理者可操作  2 所有人可操作  3 指定身份组可操作（仅频道可用） |
| action.permisson.specify_role_ids | array    | 否       | 有权限的身份组id的列表（仅频道可用）                         |
| action.permisson.specify_user_ids | array    | 否       | 有权限的用户id的列表                                         |
|                                   |          |          |                                                              |
| data                              | string   | 是       | 操作相关的数据                                               |
|                                   |          |          |                                                              |
| at_bot_show_channel_list          | bool     | 否       | 指令按钮可用，弹出子频道选择器，默认 false（已弃用）         |
| reply                             | bool     | 否       | 指令按钮可用，指令是否带引用回复本消息，默认 false  支持版本？ |
| enter                             | bool     | 否       | 指令按钮可用，点击按钮后直接自动发送 data，默认 false。  支持版本？ |
| anchor                            | bool     | 否       | 指令按钮可用，自动锚点到选图器，默认 false，设置 ture 后会忽略 enter 配置。  支持版本？ |
|                                   |          |          |                                                              |
| click_limit                       | int      | 否       | 可操作点击的次数，默认不限                                   |
| unsupport_tips                    | string   | 是       | 客户端不支持本action的时候，弹出的toast文案                  |

示例

```
{
  "rows": [
    {
      "buttons": [
        {
          "id": "1",
          "render_data": {
            "label": "⬅️上一页",
            "visited_label": "⬅️上一页"
          },
          "action": {
            "type": 1,
            "permission": {
              "type": 1,
              "specify_role_ids": [
                "1",
                "2",
                "3"
              ]
            },
            "click_limit": 10,
            "unsupport_tips": "兼容文本",
            "data": "data",
            "at_bot_show_channel_list": true
          }
        },
        {
          "id": "2",
          "render_data": {
            "label": "➡️下一页",
            "visited_label": "➡️下一页"
          },
          "action": {
            "type": 1,
            "permission": {
              "type": 1,
              "specify_role_ids": [
                "1",
                "2",
                "3"
              ]
            },
            "click_limit": 10,
            "unsupport_tips": "兼容文本",
            "data": "data",
            "at_bot_show_channel_list": true
          }
        }
      ]
    },
    {
      "buttons": [
        {
          "id": "3",
          "render_data": {
            "label": "📅 打卡（5）",
            "visited_label": "📅 打卡（5）"
          },
          "action": {
            "type": 1,
            "permission": {
              "type": 1,
              "specify_role_ids": [
                "1",
                "2",
                "3"
              ]
            },
            "click_limit": 10,
            "unsupport_tips": "兼容文本",
            "data": "data",
            "at_bot_show_channel_list": true
          }
        }
      ]
    }
  ]
}

```



##### 事件

###### 点击回调按钮

l **基本概况**

| 基本     |                            |
| -------- | -------------------------- |
| intents  | 1<<26                      |
| 事件类型 | INTERACTION_CREATE         |
| 触发场景 | 用户点击了消息体的回调按钮 |
| 权限要求 | 无特殊要求                 |
| 推送方式 | Websocket                  |

l **事件字段**

| **属性**                   | **类型** | **说明**                                                    |
| -------------------------- | -------- | ----------------------------------------------------------- |
| id                         | string   | 平台方事件 ID，可以用于被动消息发送                         |
| type                       | int      | 按钮事件固定是 11                                           |
| chat_type                  | int      | 消息内容                                                    |
| timestamp                  | string   | 消息生产时间                                                |
| guild_id                   | string   | 频道的 openid                                               |
| channel_id                 | string   | 文字子频道的 openid                                         |
| group_open_id              | string   | 群聊的 openid                                               |
| chat_type                  | int      | 目前只有群和单聊有该字段，1 群聊，2 单聊，  后续加入 3 频道 |
| data.resoloved.button_data | string   | 操作按钮的data字段值【在发送按钮时规划】                    |
| data.resoloved.button_id   | string   | 操作按钮的id字段值【在发送按钮时规划】                      |
| data.resoloved.user_id     | string   | 操作的用户openid                                            |
| data.resoloved.message_id  | string   | 操作的消息id                                                |
| version                    | int      | 默认1                                                       |
| application_id             | string   | 机器人的appid                                               |
|                            |          |                                                             |

l **事件示例**

```
// Websocket
{
    "op": 0,
    "s": 4,
    "t": "INTERACTION_CREATE",
    "id": "INTERACTION_CREATE:b68a29b3-2373-434d-ab7e-76638506237c",
    "d": {
        "application_id": "102041818",
        "chat_type": 2,
        "data": {
            "resolved": {
                "button_data": "回调按钮",
                "button_id": "21",
                "user_id": "E4F4AEA33253A2797FB897C50B81D7ED"
            },
            "type": 11
        },
        "id": "30540ff7-9d8f-4737-83f1-e116ce6afa8b",
        "type": 11,
        "version": 1
    }
}

```

l **其他说明**

由于 websocket 推送事件是单向的，开发者收到事件之后，需要进行一次“回应”，告知QQ后台，事件已经收到，否则客户端会一直处于loading状态，直到超时。

回应的 openapi 接口

l **请求**

| 基本         |                                |
| ------------ | ------------------------------ |
| HTTP URL     | /interactions/{interaction_id} |
| HTTP Method  | PUT                            |
| 接口频率限制 |                                |

l **路径参数**

| **属性**       | **类型** | **必填** | **说明**         |
| -------------- | -------- | -------- | ---------------- |
| interaction_id | string   | 是       | 上述事件中获得。 |

l **请求参数**

| **属性** | **类型** | **必填** | **说明**                                                     |
| -------- | -------- | -------- | ------------------------------------------------------------ |
| code     | int      | 是       | 0   成功  1   操作失败  2   操作频繁  3   重复操作  4   没有权限  5   仅管理员操作 |

l **返回参数**

| **属性** | **类型** | **说明** |
| -------- | -------- | -------- |
|          |          |          |

l **错误码**

| **错误码** | **错误码取值** | **解决方案** |
| ---------- | -------------- | ------------ |
| 0          | ok             |              |

 