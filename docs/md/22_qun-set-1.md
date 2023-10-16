# ✅事件

 

##### ✅机器人加入群聊

l **基本概况**

| 基本     |                    |
| -------- | ------------------ |
| 事件类型 | GROUP_ADD_ROBOT    |
| 触发场景 | 机器人被添加到群聊 |
| 权限要求 | 暂无               |
| 推送方式 | Websocket          |

l **事件字段**

| **属性**         | **类型** | **说明**                         |
| ---------------- | -------- | -------------------------------- |
| timestamp        | int      | 加入的时间戳                     |
| group_openid     | string   | 加入群的群openid                 |
| op_member_openid | string   | 操作添加机器人进群的群成员openid |

l **事件示例**

![img](file:///C:/Users/Administrator/AppData/Local/Temp/msohtmlclip1/01/clip_image001.gif)

 

##### ✅机器人退出群聊

l **基本概况**

| 基本     |                  |
| -------- | ---------------- |
| 事件类型 | GROUP_DEL_ROBOT  |
| 触发场景 | 机器人被移出群聊 |
| 权限要求 | 暂无             |
| 推送方式 | Websocket        |

l **事件字段**

| **属性**         | **类型** | **说明**                         |
| ---------------- | -------- | -------------------------------- |
| timestamp        | int      | 移除的时间戳                     |
| group_openid     | string   | 移除群的群openid                 |
| op_member_openid | string   | 操作移除机器人退群的群成员openid |

l **事件示例**

![img](file:///C:/Users/Administrator/AppData/Local/Temp/msohtmlclip1/01/clip_image002.gif)

 

##### ✅群聊拒绝机器人主动消息

l **基本概况**

| 基本     |                                        |
| -------- | -------------------------------------- |
| 事件类型 | GROUP_MSG_REJECT                       |
| 触发场景 | 群管理员主动在机器人资料页操作关闭通知 |
| 权限要求 | 暂无                                   |
| 推送方式 | Websocket                              |

l **事件字段**

| **属性**         | **类型** | **说明**           |
| ---------------- | -------- | ------------------ |
| timestamp        | int      | 操作的时间戳       |
| group_openid     | string   | 操作群的群openid   |
| op_member_openid | string   | 操作群成员的openid |

l **事件示例**

![img](file:///C:/Users/Administrator/AppData/Local/Temp/msohtmlclip1/01/clip_image003.gif)

 

##### ✅群聊接受机器人主动消息

l **基本概况**

| 基本     |                                        |
| -------- | -------------------------------------- |
| 事件类型 | GROUP_MSG_RECEIVE                      |
| 触发场景 | 群管理员主动在机器人资料页操作开启通知 |
| 权限要求 | 暂无                                   |
| 推送方式 | Websocket                              |

l **事件字段**

| **属性**         | **类型** | **说明**           |
| ---------------- | -------- | ------------------ |
| timestamp        | int      | 操作的时间戳       |
| group_openid     | string   | 操作群的群openid   |
| op_member_openid | string   | 操作群成员的openid |

l **事件示例**

![img](file:///C:/Users/Administrator/AppData/Local/Temp/msohtmlclip1/01/clip_image004.gif)

 