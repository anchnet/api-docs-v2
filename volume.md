# 磁盘

<!-- toc -->
## POST /volumes

**创建磁盘**

*创建一块或多块硬盘，每块硬盘都可加载到任意一台主机中。*

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| size | Int | Yes | 硬盘容量，目前可创建最小 10G，最大 500G 的硬盘， 在此范围内的容量值必须是 10 的倍数 |
| volume_name | String | No | 磁盘名称 |
| volume_type | Int | No | 磁盘类型: <br/>性能型是 PERFORMANCE <br/>超高性能型是 HIGH_PERFORMANCE (只能与超高性能主机挂载，目前只支持北京2区)，<br/>容量型因技术升级过程中，在各区的 type 值略有不同:<br/>北京1区，亚太1区：容量型是 1<br/>北京2区，广东1区：容量型是 2 |
| count | Int | No | 创建硬盘的数量，默认是1,注解 每块硬盘的容量是相同的  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes" --data='
    {
        "size":10,
        "count":2
    }
'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "CreateVolume",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```

## GET /volumes

**获取磁盘列表**

*可根据磁盘ID，状态，磁盘名称作过滤条件，来获取磁盘列表。 如果不指定任何过滤条件，默认返回你所拥有的所有磁盘。 如果指定不存在的磁盘ID，或非法状态值，则会返回错误信息*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | String | No | 磁盘ID,多个以逗号隔开 |
| volume_type | Int | No | 磁盘类型:性能型是 PERFORMANCE 超高性能型是 HIGH_PERFORMANCE|
| status | String | No | 磁盘状态:pending, available, in-use, suspended, deleted, ceased ,多个以逗号隔开|
| search_word | String | No | 搜索关键词，支持硬盘ID，硬盘名称 |
| tags | String[] | No | 暂不支持 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100<br> |

### 服务端响应
``` js
   {
      "volumes": [
         {
            "volume_id": "vol-YZAKUZF",
            "volume_name": "test-volume",
            "description": "",
            "size": 10,
            "status": "available",
            "transition_status": "",
            "create_time": "2016-07-26T14:36:54Z",
            "status_time": "2016-07-26T14:36:57Z",
            "instance": {
               "device": "",
               "instance_id": "",
               "instance_name": ""
            }
         },
         {
            "volume_id": "vol-N7V07ED",
            "volume_name": "test-volume",
            "description": "",
            "size": 10,
            "status": "available",
            "transition_status": "",
            "create_time": "2016-07-26T14:36:54Z",
            "status_time": "2016-07-26T14:36:57Z",
            "instance": {
               "device": "",
               "instance_id": "",
               "instance_name": ""
            }
         }
      ],
      "total_count": 2
   }
```

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"volume_id": "*String*",<br>&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"instance": "*Array*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/volumes" --data'{"VolumeType":0}'
```

#### 响应内容:

```js
{
   "volumes": [
      {
         "volume_id": "vol-YZAKUZF",
         "volume_name": "test-volume",
         "description": "",
         "size": 10,
         "status": "available",
         "transition_status": "",
         "create_time": "2016-07-26T14:36:54Z",
         "status_time": "2016-07-26T14:36:57Z",
         "instance": {
            "device": "",
            "instance_id": "",
            "instance_name": ""
         }
      },
      {
         "volume_id": "vol-N7V07ED",
         "volume_name": "test-volume",
         "description": "",
         "size": 10,
         "status": "available",
         "transition_status": "",
         "create_time": "2016-07-26T14:36:54Z",
         "status_time": "2016-07-26T14:36:57Z",
         "instance": {
            "device": "",
            "instance_id": "",
            "instance_name": ""
         }
      }
   ],
   "total_count": 2
}
```


## DELETE /volumes/:vol_id

**删除磁盘**

*删除一块或多块磁盘。磁盘须在可用（ available ）状态下才能被删除， 已加载到主机的磁盘需先卸载后才能删除*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vol_id | String | Yes | 磁盘ID,多个按逗号隔开 |
| force | String | No | 是否强制删除, 默认false不强制 <br/>true为强制 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac2/volumes/vol-123edc?force=false"
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "DeleteVolumes",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## PUT /volumes/:volume_id

**修改磁盘属性**

*详细描述*

### 请求
QueryString说明: volume_id 硬盘ID
#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volume_name | String | No | 磁盘名称 |
| description | String | No | 磁盘描述 |

### 服务端响应


#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac2/volumes/vol-qsdfwf" --data '
{
    "volume_name":"name",
    "description":"description"
}'
```

#### 响应内容:
无


## POST /volumes/resize

**批量调整磁盘大小**

*给一块或多块“可用”（ available ）状态的磁盘扩大容量。*
*只允许扩大容量，不支持减小。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | String[] | Yes | 磁盘ID |
| size | Int | Yes | 磁盘大小 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/resize" --data '
{
    "size":20,
    "volumes":["vol-SDVAVDGB","vol-SDVAVDGT"]
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "ResizeVolumes",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## POST /volumes/attach

**挂载磁盘**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance_id | String | Yes | 主机ID |
| volumes | String[] | Yes | 磁盘ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/attach" --data '
{
    "instance_id": "ins-SDVFDBGFD",
    "volumes":["vol-SMOVDAD","vol-SMOVDAD"]
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "attachVolumes",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## POST /volumes/detach

**批量卸载磁盘**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance_id | String | Yes | 主机ID |
| volumes | String[] | Yes | 磁盘ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/detach" --data '
{
    "volumes":["vol-SMOVDAD","vol-SMOVDAF"]
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "detachVolumes",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
} 
```
