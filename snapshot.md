# 备份

<!-- toc -->

## GET /volume_snapshots

**查询磁盘备份**

*获取指定资源的所有备份。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String | No | 备份ID,多个以逗号隔开|
| resource_id | String | No | 按资源 ID 进行过滤 |
| snapshot_type | String | No | 按备份类型过滤，IS_INCREMENTAL 表示获取增量备份，IS_FULL 表示获取全量备份 |
| status | String | No | 备份状态: pending, available, suspended, deleted, ceased ,多个以逗号隔开|
| search_word | String | No | 搜索关键词 |
| tags | String[] | No | 暂时不支持 |
| verbose | Int | No | verbose level, 1表示返回备份的详细信息 暂时只支持1 |
| offset | Int | No | 结果集偏移量，默认为0 |
| limit | Int | No | 结果集长度，默认为20 |
| root_id | String | No | 全量备份ID,由于查询当前下面的增量备份 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"snapshot_id": "*String*",<br>&nbsp;&nbsp;"snapshot_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"snapshot_type": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"snapshot_time": "*String*",<br>&nbsp;&nbsp;"is_taken": "*Int*",<br>&nbsp;&nbsp;"is_head": "*Int*",<br>&nbsp;&nbsp;"head_chain": "*Int*",<br>&nbsp;&nbsp;"root_id": "*String*",<br>&nbsp;&nbsp;"parent_id": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"total_size": "*Int*",<br>&nbsp;&nbsp;"total_count": "*Int*",<br>&nbsp;&nbsp;"lastest_snapshot_time": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/volume_snapshots"
```

#### 响应内容:

```js
"snapshots": [
      {
         "snapshot_id": "ss-BTZOND4",
         "snapshot_name": "son",
         "description": "",
         "snapshot_type": "IS_FULL",
         "status": "available",
         "transition_status": "",
         "create_time": "2016-07-15T16:20:05Z",
         "status_time": "2016-07-15T16:20:05Z",
         "snapshot_time": "2016-07-15T16:20:05Z",
         "is_taken": 1,
         "is_head": 0,
         "head_chain": 0,
         "root_id": "ss-5fvm6a0u",
         "parent_id": "ss-ihles3sb",
         "size": 1,
         "total_size": 0,
         "total_count": 0,
         "lastest_snapshot_time": "2016-07-15T16:20:05Z"
      },
      {
         "snapshot_id": "ss-X0J5V8Q",
         "snapshot_name": "son",
         "description": "",
         "snapshot_type": 0,
         "status": "available",
         "transition_status": "",
         "create_time": "2016-07-15T16:20:05Z",
         "status_time": "2016-07-15T16:20:05Z",
         "snapshot_time": "2016-07-15T16:20:05Z",
         "is_taken": 1,
         "is_head": 0,
         "head_chain": 0,
         "root_id": "ss-5fvm6a0u",
         "parent_id": "ss-km1u2qxt",
         "size": 1,
         "total_size": 0,
         "total_count": 0,
         "lastest_snapshot_time": "2016-07-15T16:20:05Z"
      }
   ],
   "total_count": 2
}
```


## POST /volume_snapshots

**创建磁盘备份**

*为指定的资源创建备份*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resources | String[] | Yes | 资源ID |
| snapshot_name | String | Yes | 备份点名称 |
| is_full | Int | No | 是否创建全量备份,1为是 0为由系统决定 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots" --data '
{
    "resources":["vol-SACNVJNS","vol-ascdvf"],
    "snapshot_name":"demos",
    "is_full":"IS_FULL"
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "CreateSnapshots",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## DELETE /volume_snapshots/:snapshot_id

**删除磁盘备份**

*删除备份。请注意，当删除一条备份链中某个增量备份点之后，该增量备份点后的所有备份点都会被自动删除， 并且该操作是不可逆的。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String[] | Yes | 备份ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/volume_snapshots/:snapshot_id"
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "DeleteSnapshots",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## POST /volume_snapshots/apply

**回滚到指定备份点**

*回滚到指定备份点。请注意，为了保证回滚的安全性，当回滚的资源为运行的主机，或者为绑定在运行主机上的硬盘时，该操作会导致主机重启。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String[] | Yes | 备份ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/apply" --data '
{
    "snapshots":["s-sdDCVGBE","s-sdDCVGBE"]
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "ApplySnapshots",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## POST /volume_snapshots/capture_instance

**将指定备份导出为映像**

*将指定备份导出为映像。请注意，此备份点必须为主机的备份点才能导出为映像。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | 备份ID |
| image_name | String | Yes | 镜像名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/capture_instance/:snapshot_id" --data '
{
    "image_name":"demo"
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "CaptureInstanceFromSnapshot",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```


## POST /volume_snapshots/create_volume/:snapshot_id

**将指定备份导出为硬盘**

*将指定备份导出为硬盘。请注意，此备份点必须为硬盘的备份点才能导出为硬盘，而且通过备份创建的硬盘类型和备份的来源硬盘类型是一致的。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | 备份ID |
| volume_name | String | Yes | 磁盘名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/create_volume/:snapshot_id" --data '
{
   
    "volume_name":"demo"
}'
```

#### 响应内容:

```js
{
    "job_id": "6fcb4e9a-5398-4ddb-89c2-d0917bbdc4af",
    "id_prefix": "",
    "action": "CreateVolumeFromSnapshot",
    "request_id": "e3332d54-4567-4295-8275-3dc9f50a6960",
    "status": "pending",
    "create_time": "2016-07-26T07:38:28Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
}
```
## PUT /volume_snapshots/:snapshot_id

**修改备份属性**

*详细描述*

### 请求
QueryString说明:snapshot_id 备份ID
#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot_name | String | No | 备份名称 |
| description | String | No | 备份描述 |

### 服务端响应


#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/volume_snapshots/ss-qweqwrf" --data '
{
    "snapshot_name":"name",
    "description":"description"
}'
```

#### 响应内容:
无

