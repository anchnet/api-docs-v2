# 主机


<!-- toc -->

## POST /instances

**新建主机**

*详细描述*

### 请求

#### 请求 Body 参数

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

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances" --data '
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


## GET /instances

**查询主机**

*详细描述*

### 请求

#### QueryString 参数

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

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"instance_id": "*String*",<br>&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"instance_type": "*Int*",<br>&nbsp;&nbsp;"vcpus_current": "*Int*",<br>&nbsp;&nbsp;"memory_current": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"image": "*String*",<br>&nbsp;&nbsp;"vxnets": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"nic_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"private_ip": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"eip": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"volumes": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_type": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"size": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"keypair_ids": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"keypair_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"keypair_name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/instances"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /instances

**修改主机属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| instance_name | String | Yes | - |
| description | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/instances" --data '
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


## POST /instances_product

**打包产品**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance | Object | Yes | [<br>{<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"image_id": "*String*",<br>&nbsp;&nbsp;"instance_type": "*Int*",<br>&nbsp;&nbsp;"cpu": "*Int*",<br>&nbsp;&nbsp;"memory": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;"login_mode": "*String*",<br>&nbsp;&nbsp;"login_keypair": "*String*",<br>&nbsp;&nbsp;"login_passwd": "*String*",<br>&nbsp;&nbsp;"vxnets": "*String[]*",<br>&nbsp;&nbsp;"security_group": "*String*",<br>&nbsp;&nbsp;"volumes": "*String[]*",<br>&nbsp;&nbsp;"need_newsid": "*Int*",<br>&nbsp;&nbsp;"need_userdata": "*Int*",<br>&nbsp;&nbsp;"userdata_type": "*String*",<br>&nbsp;&nbsp;"userdata_value": "*String*",<br>&nbsp;&nbsp;"instance_class": "*String*",<br>&nbsp;&nbsp;"userdata_path": "*String*",<br>&nbsp;&nbsp;"userdata_file": "*String*",<br>&nbsp;&nbsp;"eips": "*String[]*"<br>}<br>] |
| vxnet | Object | Yes | {<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"type": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*"<br>} |
| eip | Object | Yes | [<br>{<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"eip_group": "*String*"<br>}<br>] |
| volume | Object | Yes | [<br>{<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"volume_type": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances_product" --data '
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


## POST /instances/start

**启动主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/start" --data '
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


## POST /instances/stop

**关闭主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| force | Int | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/stop" --data '
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


## POST /instances/restart

**重启主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/restart" --data '
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


## POST /instances/reset

**重置主机至初始状态**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| login_mode | String | Yes | - |
| login_keypair | String | Yes | - |
| login_passwd | String | Yes | - |
| need_newsid | Int | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/reset" --data '
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


## POST /instances/resize

**修改主机配置**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |
| instance_type | Int | Yes | - |
| cpu | Int | Yes | - |
| memory | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/resize" --data '
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


## DELETE /instances/:ins_id

**销毁主机**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/instances/:ins_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```