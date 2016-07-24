# 负载均衡器

<!-- toc -->

## GET /loadbalancers/listeners

**获取监听器列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listeners | String[] | Yes | - |
| loadbalancer | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerListeners | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_name": "*String*",<br>&nbsp;&nbsp;"backends": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_backend_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"balance_mode": "*String*",<br>&nbsp;&nbsp;"session_sticky": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"forwardfor": "*Int*",<br>&nbsp;&nbsp;"healthy_check_method": "*String*",<br>&nbsp;&nbsp;"healthy_check_option": "*String*",<br>&nbsp;&nbsp;"listener_option": "*Int*",<br>&nbsp;&nbsp;"listener_protocol": "*String*",<br>&nbsp;&nbsp;"backend_protocol": "*String*",<br>&nbsp;&nbsp;"listener_port": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"server_certificate_id": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/listeners"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /loadbalancers/:lb_id/listeners/add

**创建监听器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | Yes | - |
| listeners | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"listener_port": "*Int*",<br>&nbsp;&nbsp;"listener_protocol": "*String*",<br>&nbsp;&nbsp;"server_certificate_id": "*String*",<br>&nbsp;&nbsp;"backend_protocol": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_name": "*String*",<br>&nbsp;&nbsp;"balance_mode": "*String*",<br>&nbsp;&nbsp;"session_sticky": "*String*",<br>&nbsp;&nbsp;"forwardfor": "*Int*",<br>&nbsp;&nbsp;"healthy_check_method": "*String*",<br>&nbsp;&nbsp;"healthy_check_option": "*String*",<br>&nbsp;&nbsp;"listener_option": "*Int*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/listeners/add" --data '
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


## DELETE /loadbalancers_listeners/:lb_listener_id

**删除监听器**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listeners | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /loadbalancers_listeners

**修改监听器属性**

*详细描述*

### 请求

#### 请求 Body 参数

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

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners" --data '
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


## PUT /loadbalancers_listener_backends

**修改监听器后端属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backend | String | Yes | - |
| port | String | Yes | - |
| weight | String | Yes | - |
| disabled | String | Yes | - |
| loadbalancer_policy_id | String | Yes | - |
| name | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends" --data '
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


## DELETE /loadbalancers_listener_backends/:lb_listener_backends_id

**删除监听器后端**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backends | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends/:lb_listener_backends_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /loadbalancers_listeners/:lb_listener_id/backends/add

**增加监听器后端**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| backends | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"resource_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;"vxnet": "*String*"<br>}<br>] |
| loadbalancer_listener | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id/backends/add" --data '
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


## GET /loadbalancers/listeners/backends

**获取监听器后端列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backends | String[] | Yes | - |
| loadbalancer_listener | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerBackends | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_backend_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_policy_name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/listeners/backends"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /loadbalancers_policy

**创建负载均衡器策略**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| operator | String | Yes | - |
| loadbalancer_policy_name | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" --data '
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


## POST /loadbalancers_policy/:lb_ld_policy/apply

**应用负载均衡器策略**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/apply" --data '
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


## DELETE /loadbalancers_policy/:lb_ld_policy

**删除负载均衡器策略**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## GET /loadbalancers_policy

**获取负载均衡器策略列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies | String[] | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerPolicys | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_name": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"rules": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_rule_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"operator": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /loadbalancers_policy

**修改负载均衡器策略属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy | String | Yes | - |
| loadbalancer_policy_name | String | Yes | - |
| operator | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" --data '
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


## DELETE /loadbalancers_policy_rules/:lb_ld_policy_rules

**删除策略规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rules | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules/:lb_ld_policy_rules"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /loadbalancers_policy_rules

**修改策略规则属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rule | String | Yes | - |
| loadbalancer_policy_rule_name | String | Yes | - |
| val | String | Yes | - |
| disabled | Int | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules" --data '
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


## POST /loadbalancers_policy/:lb_ld_policy/rules/add

**增加策略规则**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;"val": "*String*"<br>}<br>] |
| loadbalancer_policy | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/rules/add" --data '
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


## GET /loadbalancers_policy/rules

**获取策略规则列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rules | String[] | Yes | - |
| loadbalancer_policy | String | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerPolicyRules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_rule_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;"val": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*"<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/rules"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /loadbalancers/:lb_id/eips/dissociate

**从负载均衡器中解绑公网IP**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| loadbalancer | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/eips/dissociate" --data '
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


## POST /loadbalancers/:lb_id/eips/associate

**绑定公网IP到负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | - |
| loadbalancer | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/eips/associate" --data '
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


## POST /loadbalancers/:lb_id/resize

**调整负载均衡器容量**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |
| loadbalancer_type | Int | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/resize" --data '
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


## POST /loadbalancers/:lb_id/apply

**应用负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/apply" --data '
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


## POST /loadbalancers/:lb_id/stop

**关闭负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/stop" --data '
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


## POST /loadbalancers/:lb_id/start

**启动负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/start" --data '
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


## PUT /loadbalancers

**修改负载均衡器属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | Yes | - |
| loadbalancer_name | String | Yes | - |
| security_group | String | Yes | - |
| description | String | Yes | - |
| private_ip | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers" --data '
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


## DELETE /loadbalancers/:lb_id

**删除负载均衡器**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## GET /loadbalancers

**获取负载均衡器列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"eips": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"loadbalancer_type": "*Int*",<br>&nbsp;&nbsp;"vxnet": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*String*"<br>&nbsp;&nbsp;}<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /loadbalancers

**创建负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | Object | No | 默认值: Object<br>[<br>{<br>&nbsp;&nbsp;"eips": "*String[]*",<br>&nbsp;&nbsp;"vxnet": "*String*",<br>&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;"loadbalancer_type": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_name": "*String*",<br>&nbsp;&nbsp;"security_group": "*String*",<br>&nbsp;&nbsp;"zone": "*String*"<br>}<br>] |
| eip | Object | No | 默认值: Object<br>[<br>{<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"zone": "*String*",<br>&nbsp;&nbsp;"eip_group": "*String*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers" --data '
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

