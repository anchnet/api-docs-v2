# 备份

## GET /volume_snapshots

**查询磁盘备份**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String[] | Yes | - |
| resource_id | String | Yes | - |
| snapshot_type | Int | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |
| root_id | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"snapshot_id": "*String*",<br>&nbsp;&nbsp;"snapshot_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"snapshot_type": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"snapshot_time": "*String*",<br>&nbsp;&nbsp;"is_taken": "*Int*",<br>&nbsp;&nbsp;"is_head": "*Int*",<br>&nbsp;&nbsp;"head_chain": "*Int*",<br>&nbsp;&nbsp;"root_id": "*String*",<br>&nbsp;&nbsp;"parent_id": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"total_size": "*Int*",<br>&nbsp;&nbsp;"total_count": "*Int*",<br>&nbsp;&nbsp;"lastest_snapshot_time": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/volume_snapshots"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /volume_snapshots

**创建磁盘备份**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resources | String[] | Yes | - |
| snapshot_name | String | Yes | - |
| is_full | Int | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## DELETE /volume_snapshots/:snapshot_id

**删除磁盘备份**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | - |
| snapshot_name | String | Yes | - |
| description | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/volume_snapshots/:snapshot_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /volume_snapshots/apply

**回滚到指定备份点**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/apply" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /volume_snapshots/capture_instance

**将指定备份导出为映像**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | - |
| image_name | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/capture_instance" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /volume_snapshots/create_volume

**将指定备份导出为硬盘**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | - |
| volume_name | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/create_volume" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

