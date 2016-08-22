# 负载均衡器

<!-- toc -->


## POST /loadbalancers_servercertificate

**创建服务器证书**

*详细信息*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certificate_name | String | NO | 服务器证书名称  |
| certificate_content | String | Yes | 服务器证书内容 |
| private_key | String | Yes | 服务器证书私钥 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certificate_id| String | Yes | 服务器ID |

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_servercertificate" --data '
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


## DELETE /loadbalancers_servercertificate/:lb_sf_id

**删除服务器证书**

* 详细信息 *

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certificates | String[] | Yes | 服务器证书ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certificates | String[] | Yes | 服务器证书ID |

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_servercertificate/:lb_sf_id"
```

#### 响应内容:

```js
{
    "key": "value"
}
```


## GET /loadbalancers/servertificates

**获取服务器证书列表**

* 详细信息 *

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certificates | String[] | NO | 服务器证书ID |
| search_word | String | NO |  搜索关键词，支持服务器证书ID，服务器证书名称  |
| offset | Int | NO |  数据偏移量，默认为0  |
| limit | Int | NO |  返回数据长度，默认为10 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certficates | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"server_certificate_id": "*String*",<br>&nbsp;&nbsp;"server_certificate_name": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"description": "*String*"<br>}<br>] |
| total_count | Int | Yes |  根据过滤条件得到的服务器证书总数 |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/servertificates"
```

#### 响应内容:

```js
{
    "key": "value"
}
```


## PUT /loadbalancers_servertificate

**修改服务器证书**

* 详细信息 *

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| server_certificate | String | Yes | 服务器证书ID |
| server_certificate_name | String | NO | 服务器证书名称 |
| description | String | NO | 服务器证书描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_servertificate" --data '
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


## GET /loadbalancers/listeners

**获取监听器列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listeners | String[] | NO | 监听器ID |
| loadbalancer | String | NO | 负载均衡器ID |
| offset | Int | NO | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerListeners | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_name": "*String*",<br>&nbsp;&nbsp;"backends": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_backend_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;},<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"balance_mode": "*String*",<br>&nbsp;&nbsp;"session_sticky": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"forwardfor": "*Int*",<br>&nbsp;&nbsp;"healthy_check_method": "*String*",<br>&nbsp;&nbsp;"healthy_check_option": "*String*",<br>&nbsp;&nbsp;"listener_option": "*Int*",<br>&nbsp;&nbsp;"listener_protocol": "*String*",<br>&nbsp;&nbsp;"backend_protocol": "*String*",<br>&nbsp;&nbsp;"listener_port": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"server_certificate_id": "*String*"<br>}<br>] |
| total_count | Int | Yes |根据过滤条件的到的总数 |

#####loadbalancerlisteners
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |


### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev2.51idc.com/v2/zone/ac1/loadbalancers/listeners"
```

#### 响应内容:

```js
{
loadbalancerListeners: [
{loadbalancer_listener_id: "lbl-620BDAB",
loadbalancer_listener_name: "liangs_test_6",
backends: [
{
loadbalancer_backend_id: "lbb-060F740",
loadbalancer_backend_name: "",
loadbalancer_listener_id: "lbl-620BDAB",
loadbalancer_id: "lb-737A435",
port: 8082,
weight: 1,
resource: {
resource_name: "liangs_test",
resource_type: "managed_vxnet",
resource_id: "rtr-9A74A3C"
},
status: "down",
create_time: "2016-07-204 06:54:18",
loadbalancer_policy_id: "lbp-CCE01DB",
disabled: 0,
loadbalancer_policy_name: "liangs_test"
}
],
balance_mode: "roundrobin",
session_sticky: "",
create_time: "2016-07-204 03:57:47",
forwardfor: 5,
healthy_check_method: "tcp",
healthy_check_option: "10|5|2|5",
listener_option: 2,<br>listener_protocol: "http",
backend_protocol: "http",<br>listener_port: 8070,
loadbalancer_id: "lb-737A435",<br>server_certificate_id: ""
}
],
total_count: 1
}
```


## POST /loadbalancers_listeners

**创建监听器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | Yes | 负载均衡器ID |
| listeners | Object[] | Yes | - |

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| listener_port |int|Yes|监听端口|
| listener_protocol|string|Yes| 监听协议，目前支持 http ， tcp 和 https 三种。 当指定监听协议为 HTTPS，需指定服务证器书ID: server_certificate_id |
| server_certificate_id|string|NO| 服务器证书 ID |
| backend_protocol|string|Yes| 后端协议，需要跟监听协议一致 |
| loadbalancer_listener_name|string|NO| 监听器名称 |
| balance_mode|string|NO|监听器负载均衡方式：支持 roundrobin (轮询)， leastconn (最小连接)和 source (源地址) 三种。<br><br>默认为 roundrobin|
| session_sticky|string|NO|会话保持，即拥有同一个 cookie 的请求始终发往同一后台服务器。会话保持提供两种方式:<br><br>Insert: 由负载均衡器来插入cookie，此时 cookie 名字由负载均衡器来指定， 而使用者只需要提供 cookie 的超时时间.<br>Rewrite: 由使用者自己来指定并维护 cookie，此时使用者需要主动向 client 端插入 cookie，并提供过期时间。负载均衡器通过重写该 cookie (在 cookie name 前面加上 server 标题)，借此实现会话保持。当 request 重新转发给后端服务器时，负载均衡器会主动将 server 标题删除，来实现 cookie 到后端服务器的透明。<br>格式（只对 HTTP 协议有意义）：<br><br>Rewrite：prefix\|cookie_name，例如: prefix\|sk<br>Insert：insert\|cookie_timeout，例如：insert\|3600， cookie_timeout 可以为0，表示永远不超时<br>为空表示禁用会话保持。|
| forwardfor|int|NO|转发请求时需要附加的 HTTP Header。此值是由当前支持的3个附加头字段以“按位与”的方式得到的十进制数：<br><br>X-Forwarded-For: bit 位是1 (二进制的1)，表示是否将真实的客户端IP传递给后端。 附加选项“获取客户端IP”关闭时，后端 server 得到的 client IP 是负载均衡器本身的 IP 地址。 在开启本功能之后，后端服务器可以通过请求中的 X-Forwarded-For 字段来获取真实的用户IP。<br>QC-LBID: bit 位是2 (二进制的10)，表示 Header 中是否包含 LoadBalancer 的 ID<br>QC-LBIP: bit 位是3 (二进制的100)，表示 Header 中是否包含 LoadBalancer 的公网IP<br>例如 Header 中包含 X-Forwarded-For 和 QC-LBIP 的话，forwarfor 的值则为:<br><br>“X-Forwarded-For \| QC-LBIP”，二进制结果为101，最后转换成十进制得到5。|
| healthy_check_method|string|NO|监听器健康检查方式。检查方式有 HTTP 和 TCP 两种。格式为:<br><br>TCP: tcp 。<br>HTTP: http\|url\|host，例如 http\|/index.html 或 http\|/index.html\|vhost.example.com 。<br>默认是 tcp|
| healthy_check_option|string|NO|监听器健康检查参数配置，只有当启用了健康检查了之后才有效。格式为:<br><br>inter \| timeout \| fall \| rise ，表示<br><br>检查间隔(2-60s) \| 超时时间(5-300s) \| 不健康阈值(2-10次) \| 健康阈值(2-10次)。<br><br>默认是：10\|5\|2\|5|
| listener_option|int|NO|附加选项。此值是由当前支持的2个附加选项以“按位与”的方式得到的十进制数：<br><br>取消URL校验: bit 位是1 (二进制的1)，表示是否可以让负载均衡器接受不符合编码规范的 URL，例如包含未编码中文字符的URL等<br>获取客户端IP: bit 位是2 (二进制的10)，表示是否将客户端的IP直接传递给后端。 开启本功能后，负载均衡器对与后端是完全透明的。后端主机TCP连接得到的源地址是客户端的IP， 而不是负载均衡器的IP。注意：仅支持受管网络中的后端。使用基础网络后端时，此功能无效。<br>数据压缩: bit 位是4 (二进制的100)， 表示是否使用gzip算法压缩文本数据，以减少网络流量。<br>禁用不安全的加密方式: bit 位是8 (二进制的1000), 禁用存在安全隐患的加密方式， 可能会不兼容低版本的客户端。|
| timeout |int|no|超时时间|
### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://dev2.51idc.cn:9000/v2/zone/ac2/loadbalancers/lb-737A435/listeners/add" --data '
{<br> "listeners":[<br> {<br> "listener_port":8079,<br> "listener_protocol":"http",<br> "backend_protocol":"http",<br> "loadbalancer_listener_name":"liangs_test_4",<br> "balance_mode":"roundrobin",<br> "forwardfor":5,<br> "listener_option":2<br> }<br> ]<br>}'
```

#### 响应内容:

```js
{ 
"loadbalancer_listeners": ["lbl-E186848"]
}
```


## DELETE /loadbalancers_listeners/:lb_listener_id

**删除监听器**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listeners | String[] | Yes | 监听器ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://mq.51idc.cn:9000/v2/zone/ac2/loadbalancers_listeners/ lbl-0BBCD00,lbl-39919E7 "
```

#### 响应内容:

```js
{ 
"loadbalancer_listeners": [
 "lbl-0BBCD00", "lbl-39919E7" 
  ]
}
```


## PUT /loadbalancers_listener

**修改监听器属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_listener | String | Yes | 监听器ID |
| loadbalancer_listener_name | String | NO | 监听器名称 |
| server_certificate | String | NO | 服务器证书ID |
| balance_mode | String | NO |  监听器负载均衡方式：支持 roundrobin (轮询)， leastconn (最小连接)和source (源地址) 三种。  |
| session_sticky | String | NO |会话保持，即拥有同一个cookie的请求始终发往同一后台服务器。会话保持提供两种方式:Insert:由负载均衡器来插入cookie，此时cookie名字由负载均衡器来指定，而使用者只需要提供cookie的超时时间.Rewrite:由使用者自己来指定并维护cookie，此时使用者需要主动向client端插入cookie，并提供过期时间。负载均衡器通过重写该cookie(在cookiename前面加上server标题)，借此实现会话保持。当request重新转发给后端服务器时，负载均衡器会主动将server标题删除，来实现cookie到后端服务器的透明。<br>格式（只对HTTP协议有意义）：<br>Rewrite：prefix\|cookie_name，例如:<br>prefix\|sk<br>Insert：insert\|cookie_timeout，例如：insert\|3600， cookie_timeout 可以为0，表示永远不超时|
| forwardfor | Int | NO | 转发请求时需要的 HTTP Header。此值是由当前支持的3个附加头字段以“按位与”的方式得到的十进制数：<br><br>X-Forwarded-For: bit 位是1 (二进制的1)，表示是否将真实的客户端IP传递给后端。 一般情况下，后端 server 得到的 client IP 是负载均衡器本身的 IP 地址。 在开启本功能之后，后端服务器可以通过请求中的 X-Forwarded-For 字段来获取真实的用户IP。<br>QC-LBID: bit 位是2 (二进制的10)，表示 Header 中是否包含 LoadBalancer 的 ID<br>QC-LBIP: bit 位是3 (二进制的100)，表示 Header 中是否包含 LoadBalancer 的公网IP<br>例如 Header 中包含 X-Forwarded-For 和 QC-LBIP 的话，forwarfor 的值则为:<br><br>“X-Forwarded-For \| QC-LBIP”，二进制结果为101，最后转换成十进制得到5。 |
| healthy_check_method | String | NO | 监听器健康检查方式。检查方式有 HTTP 和 TCP 两种。格式为:<br><br>TCP: tcp 。<br>HTTP: http\|url\|host，例如 http\|/index.html 或 http\|/index.html\|vhost.example.com 。 |
| healthy_check_option | String | NO | 监听器健康检查参数配置，只有当启用了健康检查了之后才有效。格式为:<br><br>inter \| timeout \| fall \| rise ，表示<br><br>检查间隔(2-60s) \| 超时时间(5-300s) \| 不健康阈值(2-10次) \| 健康阈值(2-10次)。 |
| listener_option | Int | NO | 附加选项。此值是由当前支持的2个附加选项以“按位与”的方式得到的十进制数：<br><br>取消URL校验: bit 位是1 (二进制的1)，表示是否可以让负载均衡器接受不符合编码规范的 URL，例如包含未编码中文字符的URL等<br>获取客户端IP: bit 位是2 (二进制的10)，表示是否将客户端的IP直接传递给后端。 开启本功能后，负载均衡器对与后端是完全透明的。后端主机TCP连接得到的源地址是客户端的IP， 而不是负载均衡器的IP。注意：仅支持受管网络中的后端。使用基础网络后端时，此功能无效。<br>数据压缩: bit 位是4 (二进制的100)， 表示是否使用gzip算法压缩文本数据，以减少网络流量。<br>禁用不安全的加密方式: bit 位是8 (二进制的1000), 禁用存在安全隐患的加密方式， 可能会不兼容低版本的客户端。 |
| timeout | Int | NO | 超时时间 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://dev2.51idc.com/v2/zone/ac1/loadbalancers_listeners" --data '
{ 
"loadbalancer_listener":"lbl-E186848",
"loadbalancer_listener_name":"modify_test"
}'
```


## PUT /loadbalancers_listeners_backend

**修改监听器后端属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backend | String | Yes | 监听器后端ID |
| port | String | NO |  后端服务端口  |
| weight | String | NO |  后端服务权重  |
| disabled | String | NO |  1表示禁用，0表示启用  |
| loadbalancer_policy | String | NO |  转发策略ID |
| name | String | NO | 后端名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends" --data '
{ 
"loadbalancer_backend":"lbb-060F740", 
"loadbalancer_backend_name":"loadbalancer_backend_modify_test" 
}'
```


## DELETE  /loadbalancers_listeners_backends/:lb_listener_backends_id

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

```bash
$ curl -XDELETE "http://dev2.51idc.cn:9000/v2/zone/ac2/loadbalancers_listeners_backends/lbb-C11BED2"
```

#### 响应内容:

```js
{ 
  "loadbalancer_backends": ["lbb-C11BED2"]
}
```


## POST /loadbalancers_listeners_backends

**增加监听器后端**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| backends | Object[] | Yes | - |
| loadbalancer_listener | String | Yes | 监听器ID |

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource |string|Yes|后端资源ID|
| vxnet|string|Yes|后端资源类型 resource_id ，managed_vxnet，vxnet-0 |
| loadbalancer_backend_name |string|No|后端名称|
| loadbalancer_policy |string|No|绑定策略ID|
| port |int|Yes|端口号|
| weight |int|Yes|权重|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://dev2.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id/backends/add" --data '
{ 
"backends":
[ 
{ "weight":1, 
"port":8082, 
"resource_id":"192.168.201.204", 
"loadbalancer_backend_name":"liangs_test_ip",
"vxnet":"resource_id" 
} 
]
}'
```


## GET /loadbalancers/listeners/backends

**获取监听器后端列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_backends | String[] | Yes | 后端ID |
| loadbalancer_listener | String | NO | 监听器ID |
| offset | Int | NO | 数据偏移量默认为0 |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerBackends | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_backend_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_backend_name": "*String*",<br>&nbsp;&nbsp;"loadbalancer_listener_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"port": "*Int*",<br>&nbsp;&nbsp;"weight": "*Int*",<br>&nbsp;&nbsp;"resource": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"loadbalancer_policy_name": "*String*"<br>}<br>] |
| total_count | Int | Yes | 根据过滤条件获取的总条数 |


### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev2.51idc.com/v2/zone/ac1/loadbalancers/listeners/backends"
```

#### 响应内容:

```js
{<br>loadbalancerBackends: [<br>{<br>loadbalancer_backend_id: "lbb-060F740",<br>loadbalancer_backend_name: "",<br>loadbalancer_listener_id: "lbl-620BDAB",<br>loadbalancer_id: "lb-737A435",<br>port: 8082,<br>weight: 1,<br>resource: {<br>resource_name: "liangs_test",<br>resource_type: "managed_vxnet",<br>resource_id: "rtr-9A74A3C"<br>},<br>status: "down",<br>create_time: "2016-07-204 06:54:18",<br>loadbalancer_policy_id: "lbp-CCE01DB",<br>disabled: 0,<br>loadbalancer_policy_name: "liangs_test"<br>}<br>],<br>total_count: 1<br>}
```


## POST /loadbalancers_policy

**创建负载均衡器策略**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| operator | String | Yes |  转发策略规则间的逻辑关系：”and” 是『与』，”or” 是『或』，默认是 “or”  |
| loadbalancer_policy_name | String | Yes | 转发策略名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://dev2.51idc.cn/v2/zone/ac1/loadbalancers_policy" --data '
{ 
    "operator":"and",
    "loadbalancer_policy_name":"liangs_test"
}'
```

#### 响应内容:

```js
{ 
    "loadbalancer_poicy_id": "lbp-A0A1897"
} 
```


## POST /loadbalancers_policy/:lb_policy_id/apply

**应用负载均衡器策略**

*详细描述*

### 请求

#### 请求  QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy| String | Yes | 转发策略ID |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/lbp-A0A1897/apply"
```



## DELETE /loadbalancers_policies/:lb_policy_id

**删除负载均衡器策略**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies| String[] | Yes | 转发策略ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies| String[] | Yes | 转发策略ID |

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://dev2.51idc.cn/v2/zone/ac1/loadbalancers_policy/lbp-A0A1897 "
```

#### 响应内容:

```js
{
    "loadbalancer_policies": [ "lbp-A0A1897" ]
}
```


## GET /loadbalancers_policies

**获取负载均衡器策略列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policies | String[] | Yes | 转发策略ID |
| offset | Int | NO | 数据偏移量默认为0 |
| limit | Int | NO | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerPolicys | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_name": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"rules": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_rule_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"val": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"disabled": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"operator": "*String*"<br>}<br>] |
| total_count | Int | Yes | 根据过滤条件得到的总条数 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policies"
```

#### 响应内容:

```js
{<br>loadbalancerPolicys: [<br>{<br>loadbalancer_policy_id: "lbp-CCE01DB",<br>loadbalancer_policy_name: "liangs_test",<br>create_time: "2016-07-204 05:57:37",<br>is_applied: 0,<br>rules: [<br>{<br>loadbalancer_policy_rule_id: "lbpr-00F4ADB",<br>loadbalancer_policy_rule_name: "rules_test_1",<br>rule_type: "url",<br>val: "test_test",<br>loadbalancer_policy_id: "lbp-CCE01DB",<br>disabled: 0<br>},<br>{<br>loadbalancer_policy_rule_id: "lbpr-B55E183",<br>loadbalancer_policy_rule_name: "rules_test_2",<br>rule_type: "url",<br>val: "test_test",<br>loadbalancer_policy_id: "lbp-CCE01DB",<br>disabled: 0<br>}<br>],<br>description: "",<br>operator: "and"<br>}<br>],<br>total_count: 1<br>}
```


## PUT /loadbalancers_policy

**修改负载均衡器策略属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy | String | Yes | 转发策略ID |
| loadbalancer_policy_name | String | NO | 转发策略名称 |
| operator | String | NO |  转发策略规则间的逻辑关系：”and” 是『与』，”or” 是『或』，默认是 “or”  |
| description | String | NO |  负载均衡器策略描述  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" --data '
{ 
    "loadbalancer_policy":"lbp-CCE01DB", 
    "operator":"or", 
    "loadbalancer_policy_name":"modify_test"
}'
```



## DELETE /loadbalancers_policy_rules/:lb_policy_rules_id

**删除策略规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rules | String[] | Yes | 转发策略规则ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules/lbpr-00F4ADB "
```

#### 响应内容:

```js
{     
    "loadbalancer_policy_rules": [ "lbpr-00F4ADB" ]
}
```


## PUT /loadbalancers_policy_rule

**修改策略规则属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rule | String | Yes | 转发策略规则ID |
| loadbalancer_policy_rule_name | String | NO | 转发策略规则名称 |
| val | String | NO |  转发策略规则匹配规则  |
| disabled | Int | NO | 1为启用，0为禁用 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rule" --data '
{ 
    "loadbalancer_policy_rule":"lbpr-B55E183", 
    "val":"4645", 
    "loadbalancer_policy_rule_name":"test"
}'
```



## POST /loadbalancers_policy_rules

**增加策略规则**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;"val": "*String*"<br>}<br>] |
| loadbalancer_policy | String | Yes | 转发策略ID |

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rule_name |String|NO|策略规则名称|
| rule_type |String|Yes|策略规则类型 and \| or|
| val |String|||
### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/rules/add" --data '
{ 
    "rules":
    [ 
     { 
       "loadbalancer_policy_rule_name":"rules_test_1", 
       "val":"test_test", 
       "rule_type":"url" 
     }, 
     { 
       "loadbalancer_policy_rule_name":"rules_test_2", 
       "val":"test_test",
       "rule_type":"url"
     } 
    ] 
}'
```

#### 响应内容:

```js
{ 
    "loadbalancer_policy_rules": [ "lbpr-2562688", "lbpr-0EBCE7D" ]
}
```


## GET /loadbalancers_policy_rules

**获取策略规则列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer_policy_rules | String[] | NO | 转发策略规则ID |
| loadbalancer_policy | String | NO | 转发策略ID |
| offset | Int | NO | 数据偏移量默认为0 |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancerPolicyRules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_policy_rule_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_rule_name": "*String*",<br>&nbsp;&nbsp;"rule_type": "*String*",<br>&nbsp;&nbsp;"val": "*String*",<br>&nbsp;&nbsp;"loadbalancer_policy_id": "*String*",<br>&nbsp;&nbsp;"disabled": "*Int*"<br>}<br>] |
| total_count | Int | Yes | 根据条件过滤得到的总数 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules"
```

#### 响应内容:

```js
{<br>loadbalancerPolicyRules: [<br>{<br>loadbalancer_policy_rule_id: "lbpr-B55E183",<br>loadbalancer_policy_rule_name: "test",<br>rule_type: "url",<br>val: "4645",<br>loadbalancer_policy_id: "lbp-CCE01DB",<br>disabled: 0<br>}<br>],<br>total_count: 1<br>}
```


## POST /loadbalancers/eips/dissociate

**从负载均衡器中解绑公网IP**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | 公网IP的ID |
| loadbalancer | String | Yes | 负载均衡器ID
 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## POST /loadbalancers/eips/associate

**绑定公网IP到负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eips | String[] | Yes | 公网IP的ID |
| loadbalancer | String | Yes | 负载均衡器ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## POST /loadbalancers/resize

**调整负载均衡器容量**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | 负载均衡器ID |
| loadbalancer_type | String | Yes | 负载均衡器类型（MAX_COUNT_5000，MAX_COUNT_20000，MAX_COUNT_40000，MAX_COUNT_100000） |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## POST /loadbalancers/apply

**应用负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes | 负载均衡器ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## POST /loadbalancers/stop

**关闭负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes |  负载均衡器ID  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## POST /loadbalancers/start

**启动负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | String[] | Yes |  负载均衡器ID  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## PUT /loadbalancer

**修改负载均衡器属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | Yes |  负载均衡器ID  |
| loadbalancer_name | String | NO |  负载均衡器名称 |
| security_group | String | NO |  更改的负载均衡器加载的防火墙ID，为空则保持不变  |
| description | String | NO |  负载均衡器描述 |
| private_ip | String | NO | 私网IP |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
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
| delete_eips | String[] | no | 要删除的公网IP ID |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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
| loadbalancers | String[] | NO | 负载均衡器ID |
| status | String[] | NO |  负载均衡器状态: pending，active，stopped，suspended，deleted，ceased  |
| search_word | String | NO |  搜索关键词，支持负载均衡器ID，负载均衡器名称 |
| offset | Int | NO |  数据偏移量，默认为0 |
| limit | Int | NO | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancers | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"loadbalancer_id": "*String*",<br>&nbsp;&nbsp;"loadbalancer_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"eips": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"loadbalancer_type": "*Int*",<br>&nbsp;&nbsp;"vxnet": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"private_ip": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*String*"<br>&nbsp;&nbsp;}<br>}<br>] |
| total_count | Int | Yes | 根据过滤条件的到的总数 |

### 示例

#### 发送请求

```bash
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
| loadbalancer | Object | YES | - |
| eip | Object | No |-|

#####loadbalancer

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|eips|String[]|No| 公网IP的ID |
|vxnet|String|Yes| 要加入的私网ID |
|private_ip|String|NO| 要使用的私网IP |
|loadbalancer_name|String|Yes|负载均衡器名称|
|loadbalancer_type|String|Yes|负载均衡器类型 MAX_COUNT_5000，MAX_COUNT_20000，MAX_COUNT_40000，MAX_COUNT_100000 |
|security_group|String|Yes|防火墙ID|

#####eip
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|bandwidth|Int|Yes|公网IP带宽|
|billing_mode|String|No| 公网IP计费模式：bandwidth 按带宽计费，traffic 按流量计费，默认是 bandwidth |
|eip_name|String|No|公网IP名称|
|count|Int|Yes|公网IP数量|
|eip_group|String|Yes|公网IP分组Id|
### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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

## POST /loadbalancer/bind_security_group

**应用防火墙到负载均衡器**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| loadbalancer | String | YES | 负载均衡器ID |
| security_group | String | YES | 防火墙ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/bind_security_group" --data '
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