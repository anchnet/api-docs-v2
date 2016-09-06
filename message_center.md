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


<!--## POST /keypairs

**创建秘钥**

*创建SSH密钥对，每对密钥都可加载到任意多台主机中。*
*支持以下两种加密算法：*
*1024-位DSS*
*2048-位RSA(默认)*
*创建密钥对成功后，请及时从API返回结果中保存私钥，因为我们不会保存用户的私钥数据。公钥数据可以随时通过DescribeKeyPairs得到。*
*另外用户也可以通过已有公钥来创建SSH密钥。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypair_name | String | No | 密钥对名称 |
| mode | String | No | 密钥创建方式，有效值为system和user，默认为system.<br>当密钥创建方式system时，表示 SSH密钥将由系统为你创建，此时你需要下载并保存系统创建的私钥；<br>当密钥创建方式user时，表示SSH密钥将通过您提供的公钥(public_key)参数进行创建. |
| encrypt_method | String | No | 加密算法，有效值为ssh-rsa和ssh-dss，默认为ssh-rsa。只有当mode=sytem的时候才需要提供。|
| public_key | String | No | SSH公钥内容,只有当mode = user的时候才需要提供 |
| description | String | No | 密钥描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs" --data '
{
    "keypair_name": "kp-test",     
    "description": "test"
}'
```

#### 响应内容:

```js
{
    "private_key": "private_key",
    "keypair_id": "kp-XDOOZDK"
}
```

-->
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


<!--## POST /keypairs/attach

**秘钥加载到主机**

*将任意数量的密钥加载到主机，主机状态须为“运行中”(running)或“已关机”(stopped)。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | 密钥ID列表 |
| instances | String[] | Yes | 主机ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/attach" --data '
{
  "keypairs":["kp-XDOOZDK"],
  "instances":[
                "ins-D6MK7EV",
                "ins-TVXB1GX",
                "ins-16T0WNM",
                "ins-QTEYKVS",
                "ins-11PVAQR",
                "ins-C7WXRO0",
                "ins-JWFQNPY"
              ]
}'
```

#### 响应内容:

```js
{
    "job_id": "55ac3200-a742-438e-8353-7e3558763260",
    "id_prefix": "",
    "action": "AttachKeyPairs",
    "request_id": "004ee0e7-89d2-47f4-8957-557de68589dd",
    "status": "pending",
    "create_time": "2016-07-26T06:12:44Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
} 
```


## POST /keypairs/detach

**秘钥从主机卸载**

*将任意数量的密钥对从主机中卸载，主机状态须为“运行中”(running)或“已关机”(stopped)。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | 密钥ID列表 |
| instances | String[] | Yes | 主机ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/detach" --data '
{
  "keypairs":["kp-XDOOZDK"],
  "instances":[
                "ins-D6MK7EV",
                "ins-TVXB1GX",
                "ins-16T0WNM",
                "ins-QTEYKVS",
                "ins-11PVAQR",
                "ins-C7WXRO0",
                "ins-JWFQNPY"
              ]
}'
```

#### 响应内容:

```js
{
    "job_id": "af4e593c-0a61-47ad-bf06-2ab753876565",
    "id_prefix": "",
    "action": "DetachKeyPairs",
    "request_id": "8f664714-dd6c-4b4e-a4b8-c7ebd06f7d9d",
    "status": "pending",
    "create_time": "2016-07-26T06:15:58Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```
-->

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
| id | string | Yes | 根据过滤条件得到的密钥总数 |
| notice_types | NoticeType[] | Yes | [<br>{<br>&nbsp;&nbsp;"id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"remark": "*String*",<br>&nbsp;&nbsp;"create_at": "*String*"<br>&nbsp;&nbsp;"receivers": "*object[]*",<br>&nbsp;&nbsp;"name": "*String[]*"}<br>] |

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
            "name":"name",
            "remark" :"remark",  
            "create_at":"",
            "notice_ways":[],
            "receivers": [
                {
                "id":"id",
                "name":"name",
                "mail" :"mail",
                "mobile":"mobile",
                "type":"type"
                }
            ]
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


## PUT /notice_way

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