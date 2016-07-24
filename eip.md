# 公网 IP

## PUT /eips

**修改公网IP 属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| description | String | Yes | - |
| eip | String | Yes | - |
| eip_name | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
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
| eips | String[] | Yes | - |
| billing_mode | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
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
| eips | String[] | Yes | - |
| bandwidth | Int | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
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


## POST /eips/associate

**绑定公网IP 到主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | - |
| instance | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
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
| eips | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
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
| bandwidth | Int | Yes | - |
| billing_mode | String | Yes | - |
| eip_name | String | Yes | - |
| count | Int | Yes | - |
| eip_group | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
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
| eips | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
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
| eips | String[] | Yes | - |
| resouce_ids | String | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| resource_type | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"eip_id": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;"eip_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_group_name": "*String*"<br>&nbsp;&nbsp;}<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/eips"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

