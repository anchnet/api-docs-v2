# 消息

<!-- toc -->

## GET /messsages

**获取消息列表**

*获取一个或多个消息*

*可根据消息ID，type,title作为过滤条件，获取消息列表。如果不指定任何过滤条件，默认返回你所拥有的所有消息。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| message_ids | String[] | No | 消息ID |
| type | String| No | 消息类别 |
| status | Int| No | 状态 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到的密钥总数 |
| messsages | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"id": "*String*",<br>&nbsp;&nbsp;"title": "*String*",<br>&nbsp;&nbsp;"type": "*String*",<br>&nbsp;&nbsp;"context": "*String*",<br>&nbsp;&nbsp;"remark": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"send_at": "*String*"<br>}<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/messsages"
```

#### 响应内容:

```js
{
    "total_count": 1,
    "messsages": [
        {
           "id": "ins-D6MK7EV",
            "title": "rsa",
            "context": "sss",
            "remark": "kp",
            "status": 0,
            "send_at": "2016-07-21T09:48:08Z"
        }
    ]
} 
```

## DELETE /messsages/:message_ids

**删除消息 支持批量**

*删除一个或多个你拥有的消息对。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| messages | String[] | Yes | 消息ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/messsages/:message_ids"
```

#### 响应内容:

```js
{
    "message_ids": []
}
```

## PUT /messages/read

**标记为已读**

*标记为已读*

*一次只能修改多个消息对*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| messages | String[] | Yes | 消息ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/messages/read" --data '
{
  "messages":["msg_123443"],
}'
```

#### 响应内容:

```js
{
  "message_ids":["msg_123443"]
}
```

## GET /notice_types

**获取消息类型信息**

*获取一个或多个消息类型信息*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| name | string | No | 消息类型名 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到的密钥总数 |
| notice_types | NoticeType[] | Yes | [<br>{<br>&nbsp;&nbsp;"id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"remark": "*String*",<br>&nbsp;&nbsp;"create_at": "*String*"<br>&nbsp;&nbsp;"receivers": "*object[]*",<br>&nbsp;&nbsp;"notice_ways": "*String[]*"<br>&nbsp;&nbsp;"childs": "*NoticeType[]*",<br>}<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev2.51idc.cn:9000/v2/zone/ac2/notice_types
```

#### 响应内容:

```js
{   "notice_types":[
        {
            "id":"id",
            "name":"业务通知",
            "remark" :"remark",  
            "create_at":"",
            "notice_ways":[],
            "receivers": [],
            "childs":[
                {
                    "id":"id",
                    "name":"产品创建的信息通知",
                    "remark" :"remark",  
                    "create_at":"",
                    "notice_ways":["sms","mail"],
                    "receivers": [],
                    "childs":[]
              },
            {
                "id":"id",
                "name":"产品欠费、即将停机的信息通知",
                "remark" :"remark",  
                "create_at":"",
                "notice_ways":["mail"],
                "receivers": [],
                "childs":[]
              }
        ]
    },
    {
        "id":"id",
        "name":"运维事件",
        "remark" :"remark",  
        "create_at":"",
        "notice_ways":[],
        "receivers": [],
        "childs":[]
    }
  ],
    "total_count": 7
}
```


## PUT /notice_receivers

**修改联系人**

*修改联系人*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| notice_type_id | String | Yes | 消息类别ID |
| contact_ids | Int[] | No | 联系人ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/notice_receivers" --data '
{
    "notice_type_id":["not_123443"],
    "contact_ids":["attn_123443"]
}'
```

#### 响应内容:

```js
{
  "notice_type_id":["not_123443"]
}
```


<!--## PUT /notice_way

**修改消息接收接收方式**

*修改消息接收接收方式*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| notice_type_ids | String[] | Yes | 消息ID列表 |
| notice_ways | String[] | No | 收接收方式 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/notice_way" --data '
{
  "notice_type_ids":["msg_123443"],
  "notice_ways":["mail"]
}'
```

#### 响应内容:

```js
{
  "notice_type_ids":["msg_123443"]
}
```
-->

## POST /add_notice_way

**添加消息接收接收方式**

*添加消息接收接收方式*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| notice_type_ids | String[] | Yes | 消息ID列表 |
| notice_ways | String[] | No | 收接收方式 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/add_notice_way" --data '
{
  "notice_type_ids":["msg_123443"],
  "notice_ways":["mail"]
}'
```

#### 响应内容:

```js
{
  "notice_type_ids":["msg_123443"]
}
```

## POST /delete_notice_way

**删除消息接收接收方式**

*删除消息接收接收方式*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| notice_type_ids | String[] | Yes | 消息ID列表 |
| notice_ways | String[] | No | 收接收方式 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/delete_notice_way" --data '
{
  "notice_type_ids":["msg_123443"],
  "notice_ways":["mail"]
}'
```

#### 响应内容:

```js
{
  "notice_type_ids":["msg_123443"]
}
```