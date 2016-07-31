# 路由器

<!-- toc -->

## POST /router

**创建路由器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | Object | Yes | 路由器 |
| router_name | String | Yes | 路由器名称 |
| router_type | int | Yes | 路由器类型 |
| security_group| String | No | 防火墙ID  &nbsp;&nbsp;  不填则需用您的默认防火墙|
| nets | Object[] | Yes | 网络信息 |
| manager_ip | String | No | 路由器的管理IP |
| dyn_ip_start | String | No | DHCP服务分配开始IP |
| dyn_ip_end | String | No | DHCP服务分配终止IP |
| ip_network | String | Yes | 受管私有网络的网段，目前支持的网段为192.168.x.0/24 |
| features | Int | No | 是否开启DHCP服务  &nbsp;&nbsp; 默认开启 |
| eip | Object | Yes | 公网IP信息 |
| bandwidth | Int | Yes | 带宽 (如需新建公网IP,需填此参数)|
| eip_group | String | Yes | 公网IP分组  (如需新建公网IP,需填此参数) |
| eip_id | String | Yes | 公网IP ID (如选择已有公网IP，需此参数) |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router" --data '
```

{ "router": { "router_name": "gaotest", "router_type": 1 }, "nets": [ { "manager_ip": "192.168.100.1", "ip_network": "192.168.100.0/24", "dyn_ip_start": "192.168.100.2", "dyn_ip_end": "192.168.100.254", "features": 1 } ], "eip": { "eip": { "bandwidth": 1, "eip_group": "eipg-6666666" } }}

{ "router": { "router_name": "gaotest", "router_type": 1, "security_group":"sg-FWO2XXX" }, "nets": [ { "manager_ip": "192.168.100.1", "ip_network": "192.168.100.0/24", "dyn_ip_start": "192.168.100.2", "dyn_ip_end": "192.168.100.254", "features": 1 } ], "eip": { "eip": "eip-IFE1XXX" }}



#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /routers/power_on

**启动路由器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | 路由器ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/power_on" --data '
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


## POST /routers/power_off

**关闭路由器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | 路由器ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/power_off" --data '
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


## POST /routers/update

**更新路由器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | 路由器ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/update" --data '
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


## DELETE /routers/:router_id

**删除路由器**

*详细描述*

### 请求

#### PATH参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID 多个已逗号分隔 |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/routers/rtr-8E0BXXX"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /router/:router_id/join

**路由器加入网络**

*详细描述*

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID |

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnet | String | Yes | 网络ID |
| ip_network | String | Yes |  受管私有网络的网段，目前支持的网段为192.168.x.0/24  |
| features | Int | No | 是否需要开启DHCP服务  &nbsp;&nbsp; 默认开启 |
| manager_ip | String | No |  路由器的管理IP  |
| dyn_ip_start | String | No |  DHCP服务分配开始IP  |
| dyn_ip_end | String | No |  DHCP服务分配终止IP  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/rtr-E7D5XXX/join" --data '
{ "vxnet":"vxnet-18ADXXX", "ip_network":"192.168.103.4/24"}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /router/:router_id/leave

**路由器离开网络**

*详细描述*

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID |

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnets | String[] | Yes | 网络ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/rtr-E7D5XXX/leave" --data '
{ "vxnets":["vxnet-18ADEFC","vxnet-485535E"]}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /router/:router_id

**修改路由器属性**

*详细描述*

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID |

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_name | String | Yes | 路由器名称 |
| description | String | Yes | 路由器描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/router/rtr-E7D5XXX" --data '
{
    " router_name ": "51idc"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /router/:router_id/statics

**添加路由器规则**

*详细描述*
### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID |

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | String | Yes | - |
| vxnet | String | Yes | - |
| router_statics | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"static_type": "*Int*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"val4": "*String*",<br>&nbsp;&nbsp;"val5": "*String*",<br>&nbsp;&nbsp;"val6": "*String*",<br>&nbsp;&nbsp;"static_name": "*String*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/statics" --data '
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


## PUT /router_static/:router_static_id

**修改路由器规则属性**

*详细描述*

### 请求

#### 请求 Body 参数

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

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/router_static/:router_static_id" --data '
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


## DELETE router_statics/:router_static_id

**删除路由器规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_statics | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1router_statics/:router_static_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /router_static/:router_static_id/entries

**添加路由器规则条目**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static | String | Yes | - |
| static_entries | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router_static/:router_static_id/entries" --data '
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


## DELETE /router_static_entries/:router_static_entry_id

**删除路由器规则条目**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static_entries | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/router_static_entries/:router_static_entry_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /router_static_entry/:router_static_entry_id

**修改路由器规则条目**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_static_entry | String | Yes | - |
| router_static_entry_name | String | Yes | - |
| val1 | String | Yes | - |
| val2 | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/router_static_entry/:router_static_entry_id" --data '
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


## POST /router/:router_id/bind_eip

**关联公网ip**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | - |
| rotuer | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/bind_eip" --data '
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


## POST /router/:router_id/bind_security_group

**关联防火墙**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| router | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/bind_security_group" --data '
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


## GET /routers

**查询路由器列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerList | String[] | Yes | - |
| vxnet | String | Yes | - |
| statusList | String[] | Yes | - |
| searchWord | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;"router_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"router_type": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"eip": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_name": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"vxnets": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"eip_id": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/routers"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## GET /router_statics

**查询路由器规则列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerStaticList | String[] | Yes | - |
| router | String | Yes | - |
| staticType | Int | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| RouterStatics | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"router_static_id": "*String*",<br>&nbsp;&nbsp;"router_static_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"static_type": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"val4": "*String*",<br>&nbsp;&nbsp;"val5": "*String*",<br>&nbsp;&nbsp;"val6": "*String*",<br>&nbsp;&nbsp;"router_id": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/router_statics"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## GET /router_static_entries

**查询路由器规则条目列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerStaticEntryList | String[] | Yes | - |
| routerStatic | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerStaticEntries | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;"router_static_id": "*String*",<br>&nbsp;&nbsp;"router_static_entry_id": "*String*",<br>&nbsp;&nbsp;"router_static_entry_name": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/router_static_entries"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## GET /router_vxnets

**查询路由器网络列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router | String | Yes | - |
| verbose | Int | Yes | - |
| vxnet | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routerVxnets | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;"manager_ip": "*String*",<br>&nbsp;&nbsp;"ip_network": "*String*",<br>&nbsp;&nbsp;"dyn_ip_end": "*String*",<br>&nbsp;&nbsp;"dyn_ip_start": "*String*",<br>&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;"features": "*Int*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/router_vxnets"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```
