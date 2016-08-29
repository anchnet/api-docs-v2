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
| nets | Object[] | Yes | 网络信息 |
| eip | Object | Yes | 公网IP信息 |
###  router 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| router_name | String | Yes | 路由器名称 |
| router_type | String | Yes | 路由器类型 <br> SMALL：小型 <br> SUPER：大型| 
| security_group| String | No | 防火墙ID  &nbsp;&nbsp;  不填则需用您的默认防火墙|
### nets
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| manager_ip | String | No | 路由器的管理IP |
| dyn_ip_start | String | No | DHCP服务分配开始IP |
| dyn_ip_end | String | No | DHCP服务分配终止IP |
| ip_network | String | Yes | 受管私有网络的网段，目前支持的网段为192.168.x.0/24 |
| features | int | No | 是否开启DHCP服务  &nbsp;&nbsp; 默认开启 |
### eip
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | Object | Yes | 公网IP信息 |
###  选择新建 eip 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bandwidth | Int | Yes | 带宽 |
| eip_group | String | Yes | 公网IP分组 |
### 选择已有 eip
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | 公网IP ID |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router" --data '
{
     "router":{
         "router_name":"51idc",
         "router_type":1
     },
     "nets":[
         {
             "manager_ip":"192.168.100.1",
             "ip_network":"192.168.100.0/24",
             "dyn_ip_start":"192.168.100.2",
             "dyn_ip_end":"192.168.100.254",
             "features":1
         }
     ],
     "eip":{
         "bandwidth":1,
         "eip_group":"eipg-6666666"
     }
}

{
     "router":{
         "router_name":"51idc",
         "router_type":1,
         "eip":""
     },
     "nets":[
         {
             "manager_ip":"192.168.100.1",
             "ip_network":"192.168.100.0/24",
             "dyn_ip_start":"192.168.100.2",
             "dyn_ip_end":"192.168.100.254",
             "features":1
         }
     ]
}
```
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
    "routers": ["rtr-5350XXX"]
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
     "routers": ["rtr-5350XXX"]
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
     "routers": ["rtr-5350XXX"]
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

## POST /routers/resize

**路由器扩容**

*详细描述*
### 请求

#### 请求 Body 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| routers | String[] | Yes | 路由器ID |
| router_type| String | Yes | 路由器类型 <br> SMALL：小型 <br> SUPER：大型 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
参考: *[Job 数据结构](/job.html)*

### 示例
#### 发送请求
```bash

$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/resize" --data '

{
    "routers": ["rtr-5350XXX"]
    "router_type":"SMALL"
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
| manager_ip | String | No |  路由器的管理IP  |desc
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
{ 
    "vxnet":"vxnet-18ADXXX", 
    "ip_network":"192.168.103.4/24"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

## POST /router/:router_id/nets

**添加路由子网**

*详细描述*

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID |

#### 请求 Body 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| ip_network | String | Yes | 受管私有网络的网段，目前支持的网段为192.168.x.0/24 |
| features | Int | No | 是否需要开启DHCP服务 &nbsp;&nbsp; 默认开启 |
| manager_ip | String | No | 路由器的管理IP |
| dyn_ip_start | String | No | DHCP服务分配开始IP |
| dyn_ip_end | String | No | DHCP服务分配终止IP |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash

$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/rtr-5F42XXX/nets" --data '
{     "manager_ip": "192.168.103.1",     "ip_network": "192.168.103.0/24",     "dyn_ip_start": "192.168.103.2",     "dyn_ip_end": "192.168.103.254",     "features": 1 }

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
{ 
    "vxnets":[
        "vxnet-18ADEFC",
        "vxnet-485535E"
    ]
}'
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
| static_type | string | Yes | 添加的规则类型（PORT_FORWARD，VPN，DHCP，TWO_GRE，FILTER_CONTROL，THREE_GRE，THREE_IPSEC，DNS，CONFIG） |
| port_forward_statics | Object[] | No | 转发策略规则条目 |
| vpn_statics | Object[] | No | vpn规则条目 |
| dhcp_statics | Object[] | No | dhcp规则条目 |
| twogre_statics | Object[] | No | 二层gre规则条目 |
| filter_control_statics | Object[] | No | 过滤控制规则条目 |
| threegre_statics | Object[] | No | 三层gre规则条目 |
| threeipsec_statics | Object[] | No | 三层ipsec规则条目 |
| dns_statics | Object[] | No | dns规则条目 |

####  vpn_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vpn_type | string | yes | VPN 类型，目前支持 “openvpn” 和 “pptp”，默认值为 “openvpn”。 |
| user_pwd | string | yes | OpenVPN 规则：表示 VPN 服务端口号，默认为1194。<br />PPTP VPN 规则：表示用户名和密码，格式为 user:passwor |
| connection_num | string | yes | OpenVPN 规则：表示 VPN 协议，默认为 “udp”。<br />PPTP VPN 规则：表示最大连接数，连接数范围是 1-253 |

####  dhcp_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance_id | string | yes | DHCP 主机ID |
| config | string | yes | 表示 DHCP 配置内容，格式为key1=value1;key2=value2，例如：”domain-name-servers=8.8.8.8;fixed-address=192.168.1.2”。 |

#### twogre_statics
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| remote_ip_ssh | string | yes | 表示二层隧道的远端 IP 和密钥，如：gre\|1.2.3.4\|888。 | 

####  threegre_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| remoteip_ssh_p2plocalip_p2premoteip | string | yes |  表示远端 IP 、密钥、本地点对点IP、对端点对点IP，格式如：6.6.6.6\|key\|1.2.3.4\|4.3.2.1。 |
| goalnet | string | yes | 表示目标网络，多个网络间以 “\|” 分隔。注意目标网络不能和路由器已有的私有网络重复。 |

####  filter_control_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| source_ip | string | yes | 源ip地址 |
| source_port | string | yes | 源ip端口 |
| goal_ip | string | yes | 目标ip地址 |
| goal_port | string | yes | 目标ip端口 |
| action | string | yes | 表示『行为』，包括： “accept” 和 “drop” |

####  threeipsec_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| remoteip_way_remoteid | string | yes | 表示远端IP（支持接受任意对端，可填 0.0.0.0） 、加密算法(phase2alg&ike，可为空，默认aes)、密钥和远端设备ID（支持接受任意对端设备ID，可填 %any），格式如：1.2.3.4\|\|passw0rd\|device-id |
| localnet | string | yes | 表示本地网络，多个网络间以 “\|” 分隔。|
| goalnet | string | yes | 目标网络，多个网络间以 “|” 分隔. |
| model | string | yes | 隧道模式，默认为main 支持主模式（main） 野蛮模式（aggrmode） |

####  dns_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| ip_address | string | yes | ip地址 |
| domain_name | string | yes | 域名 |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac2/router/rtr-8E0BXXX/statics" --data '
{ 
    "router_statics": [ 
        { 
            "static_type": "PORT_FORWARD", 
            "val1": "104", 
            "val2": "3.2.8.3", 
            "val3": "41", 
            "val4": "tcp" 
        },{ 
            "static_type": "PORT_FORWARD", 
            "val1": "105", 
            "val2": "3.3.6.4", 
            "val3": "56", 
            "val4": "tcp" 
        } 
    ]
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

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| : router_static_id | String | Yes | 路由器规则ID |

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| port_forward_statics | Object[] | No | 转发策略规则条目 |
| vpn_statics | Object | No | vpn规则条目 |
| dhcp_statics | Object | No | dhcp规则条目 |
| twogre_statics | Object | No | 二层gre规则条目 |
| filter_control_statics | Object | No | 过滤控制规则条目 |
| threegre_statics | Object | No | 三层gre规则条目 |
| threeipsec_statics | Object | No | 三层ipsec规则条目 |
| dns_statics | Object | No | dns规则条目 |

####  vpn_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| vpn_type | string | yes | VPN 类型，目前支持 “openvpn” 和 “pptp”，默认值为 “openvpn”。 |
| user_pwd | string | yes | OpenVPN 规则：表示 VPN 服务端口号，默认为1194。<br />PPTP VPN 规则：表示用户名和密码，格式为 user:passwor |
| connection_num | string | yes | OpenVPN 规则：表示 VPN 协议，默认为 “udp”。<br />PPTP VPN 规则：表示最大连接数，连接数范围是 1-253 |

####  dhcp_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance_id | string | yes | DHCP 主机ID |
| config | string | yes | 表示 DHCP 配置内容，格式为key1=value1;key2=value2，例如：”domain-name-servers=8.8.8.8;fixed-address=192.168.1.2”。 |

#### twogre_statics
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| remote_ip_ssh | string | yes | 表示二层隧道的远端 IP 和密钥，如：gre\|1.2.3.4\|888。 | 

####  threegre_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| remoteip_ssh_p2plocalip_p2premoteip | string | yes |  表示远端 IP 、密钥、本地点对点IP、对端点对点IP，格式如：6.6.6.6\|key\|1.2.3.4\|4.3.2.1。 |
| goalnet | string | yes | 表示目标网络，多个网络间以 “\|” 分隔。注意目标网络不能和路由器已有的私有网络重复。 |

####  filter_control_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| source_ip | string | yes | 源ip地址 |
| source_port | string | yes | 源ip端口 |
| goal_ip | string | yes | 目标ip地址 |
| goal_port | string | yes | 目标ip端口 |
| action | string | yes | 表示『行为』，包括： “accept” 和 “drop” |

####  threeipsec_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| remoteip_way_remoteid | string | yes | 表示远端IP（支持接受任意对端，可填 0.0.0.0） 、加密算法(phase2alg&ike，可为空，默认aes)、密钥和远端设备ID（支持接受任意对端设备ID，可填 %any），格式如：1.2.3.4\|\|passw0rd\|device-id |
| localnet | string | yes | 表示本地网络，多个网络间以 “|\” 分隔。|
| goalnet | string | yes | 目标网络，多个网络间以 “\|” 分隔. |
| model | string | yes | 隧道模式，默认为main 支持主模式（main） 野蛮模式（aggrmode） |

####  dns_statics 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| ip_address | string | yes | ip地址 |
| domain_name | string | yes | 域名 |

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

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| : router_static_id | String | Yes | 路由器规则ID。 多个已逗号分隔 |

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

### 请求PATH 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_static_id | String | Yes | 路由器规则ID |

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| static_entries| Object[]| Yes | 路由器规则条目信息 |
####  static_entries 
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| val1 | String| Yes |  根据规则类型的不同，代表不同含义： <br>  PPTP 账户信息：val1 表示账户名 <br>  三层 GRE 隧道：val1 表示目标网络 <br>  三层 IPsec 隧道：val1 表示本地网络 (val2 可为空) |
| val2 | String| Yes |  根据规则类型的不同，代表不同含义： <br>  PPTP 账户信息：val2 表示密码 <br>  三层 IPsec 隧道：val2 表示目标网络 (val1 可为空) |

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

#### PATH参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_static_entry_id | String[] | Yes | 路由器规则条目ID。 多个以逗号分隔 |

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
#### PATH参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :router_id | String | Yes | 路由器ID|


#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eip | String | Yes | 公网IP (如传空字符串则表示解绑公网IP) |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/rtr-139FXXX/bind_eip" --data '
{
    "eip": "eip-38hjXXX"
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
| security_group | String | Yes | 防火墙ID |
| router | String | Yes | 路由器ID |

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
| routers | String[] | Yes | 路由器ID |
| vxnet | String | Yes | - |
| status | String[] | Yes | - |
| search_word | String | Yes | - |
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
