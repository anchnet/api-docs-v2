# 私有网络

<!-- toc -->

## POST /vxnets

**创建私有网络**

* 信息 

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnet_name | String | Yes | 网络名称 |
| vxnet_type | Int | No | 网络类型&nbsp; &nbsp; &nbsp;  受管网络:SYSTEM_MANAGER <p>   &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp;  &nbsp; &nbsp; &nbsp; &nbsp;自管网路 :SELF_MANAAGER|
| count | Int | Yes | 数量 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

Array &nbsp; &nbsp;  vxnet_id

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/vxnets" --data '
{
 "vxnet_name": "51idc", 
 "vxnet_type": "SYSTEM_MANAGER",
 "count": 1
}
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## DELETE /vxnets/:vxnet_id

**删除私有网络**

*详细描述*

### 请求

#### path 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|  :vxnet_id  | String | Yes | 多个vxnet_id以逗号分隔 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

Array  vxnet_id

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/vxnets/vxnet-DED2XXX,vxnet-FE43XXX"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /vxnet/join

**加入私有网络**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnet| String | Yes | 网络ID |
| instances | String[] | Yes | 主机ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/vxnet/join" --data '
{ 
"instances":["ins-XC2TQFW","ins-9HDBZLS"], 
"vxnet":"vxnet-78A067A"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /vxnet/leave

**离开私有网络**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnet | String | Yes | 网络ID |
| instances | String[] | Yes | 主机ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/vxnet/leave" --data '
{ 
"instances":["ins-9HDBZLS"], 
"vxnet":"vxnet-0"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /vxnets/:vxnet_id

**修改私有网络属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnet | String | Yes | 网络ID |
| vxnetName | String | Yes | 网络名称 |
| description | String | Yes | 网络描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/vxnets/:vxnet_id" --data '
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


## GET /vxnets

**查询私有网络**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnets | String[] | Yes | - |
| vxnet_type | Int | No | 默认值: -1<br> |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |
| sdnNet | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vxnets | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"systype": "*String*",<br>&nbsp;&nbsp;"vxnet_type": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"instances": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"instance_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"status": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"routers": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"router_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"router_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"dyn_ip_end": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"dyn_ip_start": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"ip_network": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"manager_ip": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"loadbalancers": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"status": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/vxnets"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

