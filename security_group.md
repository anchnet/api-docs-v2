# 防火墙

<!-- toc -->

## POST /secruity_groups

**创建防火墙**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| group_name | String | Yes | 防火墙名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups" --data '
{
  "group_name":"secruity_group_name"
}'
```

#### 响应内容:

```js
{
    "security_group_id": "sg-5PXZLGU"
} 
```


## GET /secruity_groups

**获取防火墙列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | No | 防火墙ID列表 |
| search_word | String | No | 搜索关键词，支持防火墙ID，防火墙名称 |
| tags | String[] | No | - |
| verbose | Int | No | 是否返回冗长的信息，若为1，则返回应用了此防火墙的其他资源的信息，默认为0. |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为20，最大100 |
<!--| is_default | Int | Yes | - |-->

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | Object[] | Yes | {
    "security_groups": [
        {
            "is_applied": 1,
            "description": "",
            "security_group_id": "sg-9UY7WTG",
            "is_default": 1,
            "create_time": "2016-07-18T01:57:50Z",
            "security_group_name": "default firewall",
            "resources": []
        },
        {
            "is_applied": 1,
            "description": "",
            "security_group_id": "sg-5PXZLGU",
            "is_default": 0,
            "create_time": "2016-07-25T08:22:34Z",
            "security_group_name": "secruity_group_name",
            "resources": []
        }
    ],
    "total_count": 2
} |
| total_count | Int | Yes | 根据过滤条件得到的防火墙总数 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_groups"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## DELETE /secruity_groups/:sg_id

**删除防火墙 支持批量**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_groups/:sg_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /secruity_groups/apply_instances

**应用防火墙 支持多台主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups/apply_instances" --data '
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


## POST /secruity_groups/remove_instances

**移除防火墙 支持多台主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups/remove_instances" --data '
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


## PUT /secruity_groups/:sg_id

**修改防火墙属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| security_group_name | String | Yes | - |
| description | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/secruity_groups/:sg_id" --data '
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


## POST /create_default_secruity_groups

**创建默认防火墙**

*详细描述*

### 请求

#### 请求 Body 参数

**NONE**
### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/create_default_secruity_groups" --data '
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


## POST /secruity_groups_snapshots

**创建防火墙备份**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| name | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots" --data '
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


## GET /secruity_groups_snapshots

**获取防火墙备份**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| snapshots | String[] | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"rules": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"root_user_id": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"snapshot_id": "*String*",<br>&nbsp;&nbsp;"owner": "*String*",<br>&nbsp;&nbsp;"group_id": "*String*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## DELETE /secruity_groups_snapshots/:snap_id

**删除防火墙备份**

*详细描述*

### 请求

#### QueryString 参数

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

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots/:snap_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST secruity_groups_snapshots/rollback

**回滚防火墙备份**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| group_snapshot | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1secruity_groups_snapshots/rollback" --data '
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


## GET /secruity_group_rules

**获取防火墙规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| security_group_rules | String[] | Yes | - |
| direction | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_group_rules"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /secruity_group_rules

**添加防火墙规则**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | - |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_group_rules" --data '
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


## DELETE /secruity_group_rules/:rules_id

**删除防火墙规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_group_rules/:rules_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /secruity_group_rules/:rules_id

**修改防火墙属性**

*详细描述*

### 请求

#### 请求 Body 参数

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

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/secruity_group_rules/:rules_id" --data '
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

