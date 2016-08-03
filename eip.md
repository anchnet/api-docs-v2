# 公网 IP

<!-- toc -->

## PUT /eips

**修改公网IP 属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| description | String | NO | 公网IP的描述 |
| eip | String | YES |  公网IP的ID |
| eip_name | String | NO |  公网IP的名字|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/eips" --data '
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


## POST /eips/change_billing_mode

**改变公网IP 计费方式**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes |  公网IP的ID  |
| billing_mode | String | Yes |  公网IP计费模式：bandwidth 按带宽计费，traffic 按流量计费，默认是 bandwidth  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/change_billing_mode" --data '
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


## POST /eips/change_bandwidth

**改变公网IP 带宽**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes |  公网IP的ID  |
| bandwidth | Int | Yes |  公网IP带宽，单位是 Mbps  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/change_bandwidth" --data '
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


## POST /eip/associate

**绑定公网IP 到主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | 公网IP的ID |
| instance | String | Yes | 要绑定的主机ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/associate" --data '
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


## POST /eips/dissociate

**从主机解绑公网IP**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | 要解绑的公网IP的ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/dissociate" --data '
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


## POST /eips

**分配公网IP**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bandwidth | Int | Yes |  公网IP带宽，单位是 Mbps  |
| billing_mode | String | No|  公网IP计费模式：bandwidth 按带宽计费，traffic 按流量计费，默认是 bandwidth  |
| eip_name | String | NO | 公网IP名称 |
| count | Int | Yes | 分配公网IP数量 |
| eip_group | String | Yes | 公网IP分组ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips" --data '
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


## DELETE /eips/:eip_id

**释放公网IP**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | 要释放的公网IP的ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/eips/:eip_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## GET /eips

**获取公网IP列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | NO |  公网IP的ID  |
| resouces | String[] |  NO  |  资源ID，可得到已分配给此资源的公网IP 包括 负载均衡器、路由器、主机  |
| status | String[] |  NO  |  公网IP状态，有效值为 pending, available, associated, suspended，released, ceased  |
| search_word | String | NO |  搜索关键词，支持公网IP的ID，名称  |
| resource_type | String | NO | 资源ID的类型 |
| offset | Int | NO |  数据偏移量，默认为0  |
| limit | Int | NO | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"eip_id": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;"eip_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_name": "*String*"<br>&nbsp;&nbsp;}<br>}<br>] |
| total_count | Int | Yes |  根据过滤条件得到的总数  |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/eips"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

