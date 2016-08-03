# SSH 秘钥

<!-- toc -->

## GET /keypairs

**获取秘钥列表**

*获取一个或多个SSH密钥*

*可根据密钥ID，密钥名称，主机ID，加密方式作为过滤条件，获取密钥列表。如果不指定任何过滤条件，默认返回你所拥有的所有密钥。*
*如果指定不支持的加密方式，则会返回错误信息。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| key_pairs | String[] | No | 密钥ID |
| instance_id | String | No | 主机ID |
| encrypt_method | String | No | 加密算法:ssh-rsa,ssh-dss |
| search_word | String | No | 搜索关键词，支持密钥ID，密钥名称 |
| tags | String[] | No | 按照标签ID过滤, 只返回已绑定某标签的资源 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到的密钥总数 |
| keypairs | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"encrypt_method": "*String*",<br>&nbsp;&nbsp;"keypair_name": "*String*",<br>&nbsp;&nbsp;"instance_ids": "*String[]*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"keypair_id": "*String*",<br>&nbsp;&nbsp;"pub_key": "*String*",<br>&nbsp;&nbsp;"description": "*String*"<br>}<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/keypairs"
```

#### 响应内容:

```js
{
    "total_count": 1,
    "keypairs": [
        {
            "encrypt_method": "rsa",
            "keypair_name": "sss",
            "instance_ids": [
                "ins-D6MK7EV",
                "ins-TVXB1GX",
                "ins-16T0WNM",
                "ins-QTEYKVS",
                "ins-11PVAQR",
                "ins-C7WXRO0",
                "ins-JWFQNPY"
            ],
            "create_time": "2016-07-21T09:48:08Z",
            "keypair_id": "kp-ZRM7SM2",
            "pub_key": "pub_key",
            "description": ""
        }
    ]
} 
```


## POST /keypairs

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


## DELETE /keypairs/:kp_id

**删除秘钥 支持批量**

*删除一个或多个你拥有的密钥对。密钥对须在未使用的情况下才能被删除;*
*已加载到主机的密钥对需先卸载后才能删除，关于卸载密钥对可参考DetachKeyPairs*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | 密钥ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id"
```

#### 响应内容:

```js
{
    "keypris": [
        "kp-CX82W3L"
    ]
}
```


## POST /keypairs/attach

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


## PUT /keypairs/:kp_id

**修改秘钥属性**

*修改密钥对的名称和描述*

*一次只能修改一个密钥对*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypair_name | String | Yes | 密钥名称 |
| description | String | Yes | 密钥描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id" --data '
{
  "keypair_name":"kp-test-test",
  "description":"test"
}'
```

#### 响应内容:

```js
```

