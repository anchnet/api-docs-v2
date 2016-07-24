# POST /instances

**新建主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| image_id | String | Yes | - |
| instance_type | Int | Yes | - |
| cpu | Int | Yes | - |
| memory | Int | Yes | - |
| count | Int | No | 默认值: 1<br> |
| instance_name | String | Yes | - |
| login_mode | String | Yes | - |
| login_keypair | String | Yes | - |
| login_passwd | String | Yes | - |
| vxnets | String[] | Yes | - |
| security_group | String | Yes | - |
| volumes | String[] | Yes | - |
| need_newsid | Int | Yes | - |
| need_userdata | Int | Yes | - |
| userdata_type | String | Yes | - |
| userdata_value | String | Yes | - |
| instance_class | String | Yes | - |
| userdata_path | String | No | 默认值: /etc/qingcloud/userdata<br> |
| userdata_file | String | No | 默认值: /etc/rc.local<br> |
| eips | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /instances

**查询主机**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| image_id | String[] | Yes | - |
| instance_type | Int[] | Yes | - |
| instance_class | Int | No | 默认值: -1<br> |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"instance_id": "*String*",<br>&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"instance_type": "*Int*",<br>&nbsp;&nbsp;"vcpus_current": "*Int*",<br>&nbsp;&nbsp;"memory_current": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"image": "*String*",<br>&nbsp;&nbsp;"vxnets": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"nic_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"private_ip": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"eip": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"volumes": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_type": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"size": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"keypair_ids": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"keypair_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"keypair_name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/instances" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /instances

**修改主机属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| instance_name | String | Yes | - |
| description | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/instances" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /instances_product

**打包产品**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance | Object | Yes | [<br>{<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"image_id": "*String*",<br>&nbsp;&nbsp;"instance_type": "*Int*",<br>&nbsp;&nbsp;"cpu": "*Int*",<br>&nbsp;&nbsp;"memory": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;"login_mode": "*String*",<br>&nbsp;&nbsp;"login_keypair": "*String*",<br>&nbsp;&nbsp;"login_passwd": "*String*",<br>&nbsp;&nbsp;"vxnets": "*String[]*",<br>&nbsp;&nbsp;"security_group": "*String*",<br>&nbsp;&nbsp;"volumes": "*String[]*",<br>&nbsp;&nbsp;"need_newsid": "*Int*",<br>&nbsp;&nbsp;"need_userdata": "*Int*",<br>&nbsp;&nbsp;"userdata_type": "*String*",<br>&nbsp;&nbsp;"userdata_value": "*String*",<br>&nbsp;&nbsp;"instance_class": "*String*",<br>&nbsp;&nbsp;"userdata_path": "*String*",<br>&nbsp;&nbsp;"userdata_file": "*String*",<br>&nbsp;&nbsp;"eips": "*String[]*"<br>}<br>] |
| vxnet | Object | Yes | {<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"type": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*"<br>} |
| eip | Object | Yes | [<br>{<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"eip_group": "*String*"<br>}<br>] |
| volume | Object | Yes | [<br>{<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"volume_type": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances_product" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /instances/start

**启动主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/start" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /instances/stop

**关闭主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| force | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/stop" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /instances/restart

**重启主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/restart" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /instances/reset

**重置主机至初始状态**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| login_mode | String | Yes | - |
| login_keypair | String | Yes | - |
| login_passwd | String | Yes | - |
| need_newsid | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/reset" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /instances/resize

**修改主机配置**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| instance_type | Int | Yes | - |
| cpu | Int | Yes | - |
| memory | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/resize" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /instances/:ins_id

**销毁主机**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/instances/:ins_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /volumes

**获取磁盘列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | String[] | Yes | - |
| volume_type | Int | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"volume_id": "*String*",<br>&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"instance": "*Array*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/volumes" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /volumes/:vol_id

**删除磁盘**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/volumes/:vol_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /volumes

**修改磁盘属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volume | String | Yes | - |
| volume_name | String | Yes | - |
| description | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/volumes" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volumes/resize

**批量调整磁盘大小**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | String[] | Yes | - |
| size | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/resize" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volumes/attach

**挂载磁盘**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance_id | String | Yes | - |
| volumes | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/attach" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volumes/detach

**卸载磁盘**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance_id | String | Yes | - |
| volumes | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/detach" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /volume_snapshots

**查询磁盘备份**

*详细描述*

## 请求

### QueryString 参数

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

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"snapshot_id": "*String*",<br>&nbsp;&nbsp;"snapshot_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"snapshot_type": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"snapshot_time": "*String*",<br>&nbsp;&nbsp;"is_taken": "*Int*",<br>&nbsp;&nbsp;"is_head": "*Int*",<br>&nbsp;&nbsp;"head_chain": "*Int*",<br>&nbsp;&nbsp;"root_id": "*String*",<br>&nbsp;&nbsp;"parent_id": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"total_size": "*Int*",<br>&nbsp;&nbsp;"total_count": "*Int*",<br>&nbsp;&nbsp;"lastest_snapshot_time": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/volume_snapshots" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volume_snapshots

**创建磁盘备份**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resources | String[] | Yes | - |
| snapshot_name | String | Yes | - |
| is_full | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /volume_snapshots/:snapshot_id

**删除磁盘备份**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | - |
| snapshot_name | String | Yes | - |
| description | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/volume_snapshots/:snapshot_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volume_snapshots/apply

**回滚到指定备份点**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/apply" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volume_snapshots/capture_instance

**将指定备份导出为映像**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | - |
| image_name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/capture_instance" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /volume_snapshots/create_volume

**将指定备份导出为硬盘**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshot | String | Yes | - |
| volume_name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/create_volume" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /loadbalancers/listeners

**获取监听器列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listeners | String[] | Yes | - |
| loadbalancer | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerListeners | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_name": "*String*",<br>&nbsp;&nbsp;"backends": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_backend_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"balance_mode": "*String*",<br>&nbsp;&nbsp;"session_sticky": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"forwardfor": "*Int*",<br>&nbsp;&nbsp;"healthy_check_method": "*String*",<br>&nbsp;&nbsp;"healthy_check_option": "*String*",<br>&nbsp;&nbsp;"listener_option": "*Int*",<br>&nbsp;&nbsp;"listener_protocol": "*String*",<br>&nbsp;&nbsp;"backend_protocol": "*String*",<br>&nbsp;&nbsp;"listener_port": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"server_certificate_id": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/listeners" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/listeners/add

**创建监听器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | Yes | - |
| listeners | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"listener_port": "*Int*",<br>&nbsp;&nbsp;"listener_protocol": "*String*",<br>&nbsp;&nbsp;"server_certificate_id": "*String*",<br>&nbsp;&nbsp;"backend_protocol": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_name": "*String*",<br>&nbsp;&nbsp;"balance_mode": "*String*",<br>&nbsp;&nbsp;"session_sticky": "*String*",<br>&nbsp;&nbsp;"forwardfor": "*Int*",<br>&nbsp;&nbsp;"healthy_check_method": "*String*",<br>&nbsp;&nbsp;"healthy_check_option": "*String*",<br>&nbsp;&nbsp;"listener_option": "*Int*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/listeners/add" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /loadbalancers_listeners/:lb_listener_id

**删除监听器**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listeners | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /loadbalancers_listeners

**修改监听器属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listener | String | Yes | - |
| loadbalancer_listener_name | String | Yes | - |
| server_certificate_id | String | Yes | - |
| balance_mode | String | Yes | - |
| session_sticky | String | Yes | - |
| forwardfor | Int | Yes | - |
| healthy_check_method | String | Yes | - |
| healthy_check_option | String | Yes | - |
| listener_option | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /loadbalancers_listener_backends

**修改监听器后端属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backend | String | Yes | - |
| port | String | Yes | - |
| weight | String | Yes | - |
| disabled | String | Yes | - |
| loadbalancer_policy_id | String | Yes | - |
| name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /loadbalancers_listener_backends/:lb_listener_backends_id

**删除监听器后端**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backends | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends/:lb_listener_backends_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers_listeners/:lb_listener_id/backends/add

**增加监听器后端**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| backends | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"resource_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;"vxnet": "*String*"<br>}<br>] |
| loadbalancer_listener | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id/backends/add" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /loadbalancers/listeners/backends

**获取监听器后端列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backends | String[] | Yes | - |
| loadbalancer_listener | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerBackends | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_backend_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_policy_name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/listeners/backends" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers_policy

**创建负载均衡器策略**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| operator | String | Yes | - |
| loadbalancer_policy_name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers_policy/:lb_ld_policy/apply

**应用负载均衡器策略**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/apply" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /loadbalancers_policy/:lb_ld_policy

**删除负载均衡器策略**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /loadbalancers_policy

**获取负载均衡器策略列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies | String[] | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerPolicys | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_name": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"rules": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_rule_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"operator": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /loadbalancers_policy

**修改负载均衡器策略属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy | String | Yes | - |
| loadbalancer_policy_name | String | Yes | - |
| operator | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /loadbalancers_policy_rules/:lb_ld_policy_rules

**删除策略规则**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rules | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules/:lb_ld_policy_rules" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /loadbalancers_policy_rules

**修改策略规则属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rule | String | Yes | - |
| loadbalancer_policy_rule_name | String | Yes | - |
| val | String | Yes | - |
| disabled | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers_policy/:lb_ld_policy/rules/add

**增加策略规则**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;"val": "*String*"<br>}<br>] |
| loadbalancer_policy | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/rules/add" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /loadbalancers_policy/rules

**获取策略规则列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rules | String[] | Yes | - |
| loadbalancer_policy | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerPolicyRules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_rule_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;"val": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/rules" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/eips/dissociate

**从负载均衡器中解绑公网IP**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| loadbalancer | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/eips/dissociate" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/eips/associate

**绑定公网IP到负载均衡器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| loadbalancer | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/eips/associate" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/resize

**调整负载均衡器容量**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |
| loadbalancer_type | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/resize" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/apply

**应用负载均衡器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/apply" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/stop

**关闭负载均衡器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/stop" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers/:lb_id/start

**启动负载均衡器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/start" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /loadbalancers

**修改负载均衡器属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | Yes | - |
| loadbalancer_name | String | Yes | - |
| security_group | String | Yes | - |
| description | String | Yes | - |
| private_ip | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /loadbalancers/:lb_id

**删除负载均衡器**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /loadbalancers

**获取负载均衡器列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"eips": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"loadbalancer_type": "*Int*",<br>&nbsp;&nbsp;"vxnet": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*String*"<br>&nbsp;&nbsp;}<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /loadbalancers

**创建负载均衡器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | Object | No | 默认值: Object<br>[<br>{<br>&nbsp;&nbsp;"eips": "*String[]*",<br>&nbsp;&nbsp;"vxnet": "*String*",<br>&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;"loadbalancer_type": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_name": "*String*",<br>&nbsp;&nbsp;"security_group": "*String*",<br>&nbsp;&nbsp;"zone": "*String*"<br>}<br>] |
| eip | Object | No | 默认值: Object<br>[<br>{<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"eip_group": "*String*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /eips

**修改公网IP 属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| description | String | Yes | - |
| eip | String | Yes | - |
| eip_name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/eips" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /eips/change_billing_mode

**改变公网IP 计费方式**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| billing_mode | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/change_billing_mode" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /eips/change_bandwidth

**改变公网IP 带宽**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| bandwidth | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/change_bandwidth" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /eips/associate

**绑定公网IP 到主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | - |
| instance | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/associate" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /eips/dissociate

**从主机解绑公网IP**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/dissociate" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /eips

**分配公网IP**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bandwidth | Int | Yes | - |
| billing_mode | String | Yes | - |
| eip_name | String | Yes | - |
| count | Int | Yes | - |
| eip_group | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /eips/:eip_id

**释放公网IP**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/eips/:eip_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /eips

**获取公网IP列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| resouce_ids | String | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| resource_type | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"eip_id": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;"eip_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_name": "*String*"<br>&nbsp;&nbsp;}<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/eips" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /secruity_groups

**创建防火墙**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| group_name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /secruity_groups

**获取防火墙列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |
| is_default | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"is_default": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"security_group_name": "*String*",<br>&nbsp;&nbsp;"resources": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_groups" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /secruity_groups/:sg_id

**删除防火墙 支持批量**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_groups/:sg_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /secruity_groups/apply_instances

**应用防火墙 支持多台主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups/apply_instances" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /secruity_groups/remove_instances

**移除防火墙 支持多台主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups/remove_instances" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /secruity_groups/:sg_id

**修改防火墙属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| security_group_name | String | Yes | - |
| description | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/secruity_groups/:sg_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /create_default_secruity_groups

**创建默认防火墙**

*详细描述*

### 请求 Body 参数

**NONE**
## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/create_default_secruity_groups" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /secruity_groups_snapshots

**创建防火墙备份**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /secruity_groups_snapshots

**获取防火墙备份**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| snapshots | String[] | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"rules": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"root_user_id": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"snapshot_id": "*String*",<br>&nbsp;&nbsp;"owner": "*String*",<br>&nbsp;&nbsp;"group_id": "*String*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /secruity_groups_snapshots/:snap_id

**删除防火墙备份**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots/:snap_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST secruity_groups_snapshots/rollback

**回滚防火墙备份**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| group_snapshot | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1secruity_groups_snapshots/rollback" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /secruity_group_rules

**获取防火墙规则**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| security_group_rules | String[] | Yes | - |
| direction | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_group_rules" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /secruity_group_rules

**添加防火墙规则**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_group_rules" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /secruity_group_rules/:rules_id

**删除防火墙规则**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_group_rules/:rules_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /secruity_group_rules/:rules_id

**修改防火墙属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group_rule_id | String | Yes | - |
| protocol | String | Yes | - |
| priority | Int | Yes | - |
| action | String | Yes | - |
| val2 | String | Yes | - |
| val1 | String | Yes | - |
| val3 | String | Yes | - |
| direction | Int | Yes | - |
| name | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/secruity_group_rules/:rules_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /keypairs

**获取秘钥列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| key_pairs | String[] | Yes | - |
| instance_id | String | Yes | - |
| encrypt_method | String | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | - |
| keypairs | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"encrypt_method": "*String*",<br>&nbsp;&nbsp;"keypair_name": "*String*",<br>&nbsp;&nbsp;"instance_ids": "*String[]*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"keypair_id": "*String*",<br>&nbsp;&nbsp;"pub_key": "*String*",<br>&nbsp;&nbsp;"description": "*String*"<br>}<br>] |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/keypairs" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /keypairs

**创建秘钥**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypair_name | String | Yes | - |
| mode | String | Yes | - |
| encrypt_method | String | Yes | - |
| public_key | String | Yes | - |
| description | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /keypairs/:kp_id

**删除秘钥 支持批量**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /keypairs/attach

**秘钥加载到主机**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | - |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/attach" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /keypairs/detach

**秘钥从主机卸载**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | - |
| instances | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/detach" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /keypairs/:kp_id

**修改秘钥属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypair | String | Yes | - |
| keypair_name | String | Yes | - |
| description | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router

**创建路由器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | Object | Yes | [<br>{<br>&nbsp;&nbsp;"router_name": "*String*",<br>&nbsp;&nbsp;"router_type": "*Int*",<br>&nbsp;&nbsp;"vpc_network": "*String*",<br>&nbsp;&nbsp;"security_group": "*String*",<br>&nbsp;&nbsp;"zone": "*String*"<br>}<br>] |
| nets | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"manager_ip": "*String*",<br>&nbsp;&nbsp;"ip_network": "*String*",<br>&nbsp;&nbsp;"dyn_ip_end": "*String*",<br>&nbsp;&nbsp;"dyn_ip_start": "*String*",<br>&nbsp;&nbsp;"features": "*Int*"<br>}<br>] |
| eip | Object | Yes | [<br>{<br>&nbsp;&nbsp;"eip": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"eip_id": "*String*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /routers/power_on

**启动路由器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/power_on" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /routers/power_off

**关闭路由器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/power_off" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /routers/update

**更新路由器**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/update" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /routers/:router_id

**删除路由器**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | - |
| eips | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/routers/:router_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router/:router_id/join

**路由器加入网络**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnet | String | Yes | - |
| router | String | Yes | - |
| ip_network | String | Yes | - |
| features | Int | Yes | - |
| manager_ip | String | Yes | - |
| dyn_ip_start | String | Yes | - |
| dyn_ip_end | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/join" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router/:router_id/leave

**路由器离开网络**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnets | String[] | Yes | - |
| router | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/leave" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /router/:router_id

**修改路由器属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | String | Yes | - |
| eip | String | Yes | - |
| security_group | String | Yes | - |
| router_name | String | Yes | - |
| description | String | Yes | - |
| dyn_ip_start | String | Yes | - |
| dyn_ip_end | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/router/:router_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router/:router_id/statics

**添加路由器规则**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | String | Yes | - |
| vxnet | String | Yes | - |
| router_statics | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"static_type": "*Int*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"val4": "*String*",<br>&nbsp;&nbsp;"val5": "*String*",<br>&nbsp;&nbsp;"val6": "*String*",<br>&nbsp;&nbsp;"static_name": "*String*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/statics" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /router_static/:router_static_id

**修改路由器规则属性**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static | String | Yes | - |
| router_static_name | String | Yes | - |
| val1 | String | Yes | - |
| val2 | String | Yes | - |
| val3 | String | Yes | - |
| val4 | String | Yes | - |
| val5 | String | Yes | - |
| val6 | String | Yes | - |
| disabled | Int | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/router_static/:router_static_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE router_statics/:router_static_id

**删除路由器规则**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_statics | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1router_statics/:router_static_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router_static/:router_static_id/entries

**添加路由器规则条目**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static | String | Yes | - |
| static_entries | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*"<br>}<br>] |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router_static/:router_static_id/entries" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# DELETE /router_static_entries/:router_static_entry_id

**删除路由器规则条目**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static_entries | String[] | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/router_static_entries/:router_static_entry_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# PUT /router_static_entry/:router_static_entry_id

**修改路由器规则条目**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static_entry | String | Yes | - |
| router_static_entry_name | String | Yes | - |
| val1 | String | Yes | - |
| val2 | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

**NONE**
## 示例

### 发送请求

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/router_static_entry/:router_static_entry_id" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router/:router_id/bind_eip

**关联公网ip**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | - |
| rotuer | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/bind_eip" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# POST /router/:router_id/bind_security_group

**关联防火墙**

*详细描述*

### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| router | String | Yes | - |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | - |
| id_prefix | String | Yes | - |
| action | String | Yes | - |
| request_id | String | Yes | - |
| status | String | Yes | - |
| create_time | String | Yes | - |
| begin_time | String | Yes | - |
| finished_time | String | Yes | - |
| info | String | Yes | - |
| extra | String | Yes | - |

## 示例

### 发送请求

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/bind_security_group" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /routers

**查询路由器列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerList | String[] | Yes | - |
| vxnet | String | Yes | - |
| statusList | String[] | Yes | - |
| searchWord | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;"router_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"router_type": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"eip": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_name": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"vxnets": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"eip_id": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/routers" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /router_statics

**查询路由器规则列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerStaticList | String[] | Yes | - |
| router | String | Yes | - |
| staticType | Int | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| RouterStatics | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"router_static_id": "*String*",<br>&nbsp;&nbsp;"router_static_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"static_type": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"val4": "*String*",<br>&nbsp;&nbsp;"val5": "*String*",<br>&nbsp;&nbsp;"val6": "*String*",<br>&nbsp;&nbsp;"router_id": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/router_statics" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /router_static_entries

**查询路由器规则条目列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerStaticEntryList | String[] | Yes | - |
| routerStatic | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerStaticEntries | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;"router_static_id": "*String*",<br>&nbsp;&nbsp;"router_static_entry_id": "*String*",<br>&nbsp;&nbsp;"router_static_entry_name": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/router_static_entries" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


# GET /router_vxnets

**查询路由器网络列表**

*详细描述*

## 请求

### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | String | Yes | - |
| verbose | Int | Yes | - |
| vxnet | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

## 服务端响应

### 响应头信息

`NULL`

### 响应 Body 信息

[Job Response](http://www.51idc.com)

OR

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerVxnets | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;"manager_ip": "*String*",<br>&nbsp;&nbsp;"ip_network": "*String*",<br>&nbsp;&nbsp;"dyn_ip_end": "*String*",<br>&nbsp;&nbsp;"dyn_ip_start": "*String*",<br>&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;"features": "*Int*"<br>}<br>] |
| total_count | Int | Yes | - |

## 示例

### 发送请求

` curl -XGET "http://api.51idc.com/v2/zone/ac1/router_vxnets" `

#### 响应内容:

```js
{
    "key": "value"
} 
```


