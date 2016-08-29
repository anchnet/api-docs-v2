# 防火墙

<!-- toc -->

## POST /security_groups

**创建防火墙**

*防火墙可用于保障主机和路由器的网络安全。*

*刚创建的防火墙不包含任何规则，即任何端口都是封闭的，需要建立规则以打开相应的端口。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| group_name | String | No | 防火墙名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_groups" --data '
{
  "group_name":"security_group_name"
}'
```

#### 响应内容:

```js
{
    "security_group_id": "sg-5PXZLGU"
} 
```
## POST /security_group_product

**创建防火墙并添加规则**

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| group_name | String | No | 防火墙名称 |
| rules | Object[] | No | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |


#### Rule 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| protocol | String | Yes | 协议，目前支持 tcp, udp, icmp, gre, esp, ah, ipip |
| priority | Int | Yes | 优先级，由高到低为 0 - 100 |
| action | String | No | 行为：accept 表示接受，drop 为拒绝 |
| val2 | String | No | 如果协议为 tcp 或 udp，此值表示起始端口。<br>如果协议为 icmp，此值表示 ICMP 类型，<br>具体类型可参见 ICMP 类型及代码 。 其他协议无需此值 |
| val1 | String | No | 如果协议为 tcp 或 udp，此值表示结束端口。<br>如果协议为 icmp，此值表示 ICMP 代码，<br>具体代码可参见 ICMP 类型及代码 。 其他协议无需此值 |
| val3 | String | No | 目标 IP，如果填写，则这条防火墙规则只对此IP（或IP段）有效。 |
| direction | Int | No | 方向，0 表示下行，1 表示上行。 |
| name | String | No | 防火墙规则名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_group_product" --data '
{
  "group_name":"secruity_group_name",
   "rules":[
            {
                "protocol": "tcp",
                "priority": 3,
                "action": "accept",
                "val2": "80",
                "val1": "80",
                "val3": "",
                "direction": 0,
                "disabled": 0,
                "name": "http1"
            }
     ]
}
```

#### 响应内容:

```js
{
    "job_id": "30ce8c26-e013-482b-8811-eaaae4d3735d",
    "action": "CreateSecurityGroupProduct",
    "request_id": "6ed9677b-563e-41bf-b5fa-584b1da33bee",
    "status": "pending",
    "create_time": "2016-08-03T01:58:03Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## GET /security_groups

**获取防火墙列表**

*可根据防火墙ID，名称作过滤条件，来获取防火墙列表。如果不指定任何过滤条件，默认返回你所拥有的所有防火墙*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | No | 防火墙ID列表 |
| search_word | String | No | 搜索关键词，支持防火墙ID，防火墙名称 |
| tags | String[] | No | - |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为20，最大100 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"is_applied": "*Int*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"is_default": "*Int*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"security_group_name": "*String*",<br>&nbsp;&nbsp;"resources": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"resource_id": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}<br>] |
| total_count | Int | Yes | 根据过滤条件得到的防火墙总数 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/security_groups"
```

#### 响应内容:

```js
{
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
            "security_group_name": "security_group_name",
            "resources": []
        }
    ],
    "total_count": 2
}
```


## DELETE /security_groups/:sg_id

**删除防火墙 支持批量**

*防火墙须在没有资源（主机或路由器）使用的情况下才能被删除。已加载规则到资源的防火墙，需先将相关资源从防火墙移出后才能被删除。*
*要删除的防火墙已加载规则到主机，则需要先调用 ApplySecurityGroup 将其他防火墙的规则应用到对应主机，之后才能被删除。*
*要删除的防火墙已加载规则到路由器，则需要先调用 ModifyRouterAttributes 并 UpdateRouters 将其他防火墙的规则应用到对应路由器，之后才能被删除。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | Yes | 防火墙ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_groups | String[] | Yes | 防火墙ID列表 |

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/security_groups/:sg_id"
```

#### 响应内容:

```js
{
    "security_groups": [
        "sg-5PXZLGU"
    ]
}
```


## POST /security_groups/apply_instances

**应用防火墙 支持多台主机**

*应用防火墙规则。当防火墙的规则发生改变后，新规则不会即刻生效 （可通过 is_applied 属性分辨），需要调用 ApplySecurityGroup 之后才生效。*

*防火墙规则可通过 AddSecurityGroupRules, DeleteSecurityGroupRules, ModifySecurityGroupRuleAttributes 修改。*

*如果请求参数中传递了 instances.n ，则表示将此防火墙的规则应用到对应的主机。如果不传此参数，则会将最新规则更新到所有已应用此防火墙的主机*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | 防火墙 ID |
| instances | String[] | No | 应用防火墙的主机ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_groups/apply_instances" --data '
{
  "security_group":"sg-YZOEB6B",
  "instances":["ins-C7WXRO0"]
}'
```

#### 响应内容:

```js
{
    "job_id": "4262469b-ca1f-45dd-92c0-f13c00b84d1d",
    "id_prefix": "",
    "action": "ApplySecurityGroups",
    "request_id": "e3ec627b-58c1-40b1-8893-3dd4d089aaf1",
    "status": "pending",
    "create_time": "2016-07-26T02:29:26Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
} 
```


## POST /security_groups/remove_instances

**移除防火墙 支持多台主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | 防火墙 ID |
| instances | String[] | Yes | 应用防火墙的主机ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_groups/remove_instances" --data '
{
  "security_group":"sg-YZOEB6B",
  "instances":["ins-C7WXRO0"]
}'
```

#### 响应内容:

```js
{
    "job_id": "b4374b75-ef11-425b-9f62-30671b6a1765",
    "id_prefix": "",
    "action": "RemoveSecurityGroups",
    "request_id": "97270e35-1ac1-4ddd-9c38-bb7d0a3dd180",
    "status": "pending",
    "create_time": "2016-07-26T02:32:37Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
} 
```


## PUT /security_groups/:sg_id

**修改防火墙属性**

*修改防火墙的名称和描述。一次只能修改一个防火墙*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group_name | String | Yes |  防火墙名称 |
| description | String | Yes | 防火墙描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/security_groups/:sg_id" --data '
{
  "security_group_name":"group_name",
  "description":"test"
}'
```

#### 响应内容:

```js
{
    "security_group_id": "sg-YZOEB6B"
} 
```


## POST /create_default_security_groups

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
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/create_default_security_groups" --data ''
```

#### 响应内容:

```js
{
    "job_id": "98ce759a-d332-4528-8e9d-839c3c23fea3",
    "id_prefix": "",
    "action": "CreateDefaultSecurityGroup",
    "request_id": "365c7ae1-2d5a-4173-9fb4-31bb4f9225d5",
    "status": "pending",
    "create_time": "2016-07-26T03:00:22Z",
    "begin_time": "",
    "finished_time": "",
    "info": "",
    "extra": ""
} 
```


## POST /security_groups_snapshots

**创建防火墙备份**

*根据当前的防火墙规则创建一个备份,用于随时回滚之前的防火墙规则。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | 防火墙ID |
| name | String | Yes | 备份名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_groups_snapshots" --data '
{
  "security_group":"sg-YZOEB6B",
  "name":"bak_test"
}'
```

#### 响应内容:

```js
{
    "security_group": "sg-YZOEB6B",
    "snapshot_id": "sgs-PRY5PEH"
} 
```


## GET /security_groups_snapshots

**获取防火墙备份**

*获取防火墙的备份信息。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | No | 防火墙ID |
| snapshots | String[] | No | 防火墙备份ID |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100 |

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
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/security_groups_snapshots"
```

#### 响应内容:

```js
{
    "snapshots": [
        {
            "description": "",
            "rules": [],
            "root_user_id": "",
            "create_time": "2016-07-26T03:52:57Z",
            "snapshot_id": "sgs-PRY5PEH",
            "owner": "",
            "group_id": "sg-YZOEB6B",
            "name": "bak_test"
        },
        {
            "description": "",
            "rules": [],
            "root_user_id": "",
            "create_time": "2016-07-26T03:54:00Z",
            "snapshot_id": "sgs-J62J3PA",
            "owner": "",
            "group_id": "sg-YZOEB6B",
            "name": "bak_test2"
        }
    ],
    "total_count": 2
} 
```


## DELETE /security_groups_snapshots/:snap_id

**删除防火墙备份**

*删除防火墙备份。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| snapshots | String[] | Yes | 防火墙规则ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/security_groups_snapshots/:snap_id"
```

#### 响应内容:

```js
{
    "snapshots": [
        "sgs-J62J3PA"
    ]
}
```


## POST security_groups_snapshots/rollback

**回滚防火墙备份**

*使用防火墙备份回滚。*
*注 回滚规则后，记得调用 ApplySecurityGroup 使其生效。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | 防火墙ID |
| group_snapshot | String | Yes | 防火墙备份ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_groups_snapshots/rollback" --data '
{
  "security_group":"sg-YZOEB6B",
  "group_snapshot":"sgs-PRY5PEH"
}'
```

#### 响应内容:

```js
{
    "security_group": "sg-YZOEB6B",
    "group_snapshot": "sgs-PRY5PEH"
}
```


## GET /security_group_rules

**获取防火墙规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | No | 防火墙ID |
| security_group_rules | String[] | No | 防火墙规则ID |
| direction | Int | No | 方向，0 表示下行，1 表示上行。默认为 0。 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100 |

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
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/security_group_rules"
```

#### 响应内容:

```js
{
    "rules": [
        {
            "protocol": "icmp",
            "security_group_id": "sg-9UY7WTG",
            "priority": 1,
            "action": "accept",
            "security_group_rule_id": "sgr-WWT8F8A",
            "val2": "0",
            "val1": "8",
            "val3": "",
            "direction": 0,
            "disabled": 0,
            "name": "ping"
        }
    ],
    "total_count": 1
}
```


## POST /security_group_rules

**添加防火墙规则**

*给防火墙添加规则。每条规则包括的属性为：*
*protocol：协议*
*priority：优先级，由高到低为 0 - 100*
*security_group_rule_name：规则名称*
*action：操作，分为 accept 接受 和 drop 拒绝*
*direction：方向，0 表示下行，1 表示上行。*
*val1：如果协议为 tcp 或 udp，此值表示起始端口。如果协议为 icmp，此值表示 ICMP 类型。具体类型可参见 ICMP 类型及代码*
*val2：如果协议为 tcp 或 udp，此值表示结束端口。如果协议为 icmp，此值表示 ICMP 代码。具体代码可参见 ICMP 类型及代码*
*val3：源IP*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | 防火墙ID |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |


#### Rule 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group_id | String | Yes |   防火墙规则ID |
| protocol | String | Yes | 协议，目前支持 tcp, udp, icmp, gre, esp, ah, ipip |
| priority | Int | Yes | 优先级，由高到低为 0 - 100 |
| action | String | No | 行为：accept 表示接受，drop 为拒绝 |
| val2 | String | No | 如果协议为 tcp 或 udp，此值表示起始端口。<br>如果协议为 icmp，此值表示 ICMP 类型，<br>具体类型可参见 ICMP 类型及代码 。 其他协议无需此值 |
| val1 | String | No | 如果协议为 tcp 或 udp，此值表示结束端口。<br>如果协议为 icmp，此值表示 ICMP 代码，<br>具体代码可参见 ICMP 类型及代码 。 其他协议无需此值。 |
| val3 | String | No | 目标 IP，如果填写，则这条防火墙规则只对此IP（或IP段）有效。 |
| direction | Int | No | 方向，0 表示下行，1 表示上行。 |
| name | String | No | 防火墙规则名称 |
### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/security_group_rules" --data '
{
  "security_group":"sg-YZOEB6B",
  "rules":[ 
            {
                "protocol": "tcp",
                "priority": 3,
                "action": "accept",
                "val2": "80",
                "val1": "80",
                "val3": "",
                "direction": 0,
                "disabled": 0,
                "name": "http123"
            }
  ]
}'
```

#### 响应内容:

```js
{
    "security_group_rules": [
        "sgr-ZL4HY0B"
    ]
} 
```


## DELETE /security_group_rules/:rules_id

**删除防火墙规则**

*删除防火墙规则。*

*注 删除规则后，记得调用 ApplySecurityGroup 使其生效。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | String[] | Yes | 防火墙规则ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/security_group_rules/:rules_id"
```

#### 响应内容:

```js
{
    "rules": [
        "sgr-J9PJQ6W"
    ]
}
```


## PUT /security_group_rules/:rules_id

**修改防火墙属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| protocol | String | Yes | 协议，目前支持 tcp, udp, icmp, gre, esp, ah, ipip |
| priority | Int | Yes | 优先级，由高到低为 0 - 100 |
| action | String | Yes | 行为：accept 表示接受，drop 为拒绝s |
| val2 | String | Yes | 如果协议为 tcp 或 udp，此值表示起始端口。<br>如果协议为 icmp，此值表示 ICMP 类型，<br>具体类型可参见 ICMP 类型及代码 。 其他协议无需此值 |
| val1 | String | Yes | 如果协议为 tcp 或 udp，此值表示结束端口。<br>如果协议为 icmp，此值表示 ICMP 代码，<br>具体代码可参见 ICMP 类型及代码 。 其他协议无需此值。 |
| val3 | String | Yes | 目标 IP，如果填写，则这条防火墙规则只对此IP（或IP段）有效。 |
| direction | Int | Yes | 方向，0 表示下行，1 表示上行。 |
| name | String | Yes | 防火墙规则名称 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/security_group_rules/:rules_id" --data '
   {
            "protocol": "tcp",     
            "priority": 3,
            "action": "accept",
            "val2": "80",
            "val1": "80",
            "val3": "",
            "direction": 1,
            "disabled": 0,
            "name": "httpt"
}'
```

#### 响应内容:

```js
{
    "rule_id": "sgr-278lsi9z"
}
```


## GET /security_rules

**获取防火墙规则**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | No | 防火墙ID |
| security_group_rules | String[] | No | 防火墙规则ID |
| direction | Int | No | 方向，0 表示下行，1 表示上行。默认为 0。 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"tcp": "*object*",<br>&nbsp;&nbsp;"udp": "*object*",<br>&nbsp;&nbsp;"icmp": "*object*",<br>&nbsp;&nbsp;"address": "*object*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |
| total_count | Int | Yes | - |


#### tcp , udp 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| start_port | String | no | 起始端口 |
| end_port | String | No | 结束端口|
*protocol 为tcp,udp时出现该参数, 其他协议无需此值*

#### icmp 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| icmp_type | String | no |  ICMP类型 |
| icmp_code | String | No |  ICMP代码|
*protocol 为icmp时出现该参数  其他协议无需此值*

#### address 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| saddr | String | no |  源IP,用于下行规则|
| daddr | String | no |  目的IP,用于上行规则|
*目标 IP，如果填写，则这条防火墙规则只对此IP（或IP段）有效*
### 服务端响应

### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev2.51idc.cn:9000/v2/zone/ac2/security_rules"
```

#### 响应内容:

```js
{
    "rules": [
         {
            "name": "ping",
            "security_group_id": "sg-F2L8YCV",
            "security_group_rule_id": "sgr-NY60OKL",
            "priority": 1,
            "action": "accept",
            "direction": "DOWN",
            "protocol": "icmp",
            "disabled": 0,
            "icmp": {
                "icmp_type": "8",
                "icmp_code": "0"
            }
        },
        {
            "name": "mstsc",
            "security_group_id": "sg-F2L8YCV",
            "security_group_rule_id": "sgr-NSH8ZSO",
            "priority": 3,
            "action": "accept",
            "direction": "DOWN",
            "protocol": "tcp",
            "disabled": 0,
            "tcp": {
                "start_port": "3389",
                "end_port": "3389"
            }
        }
    ],
    "total_count": 2
}
```


## POST /security_rules

**添加防火墙规则**

*给防火墙添加规则。每条规则包括的属性为：*
*protocol：协议*
*priority：优先级，由高到低为 0 - 100*
*security_group_rule_name：规则名称*
*action：操作，分为 accept 接受 和 drop 拒绝*
*direction：方向，0 表示下行，1 表示上行。*
*tcp：如果协议为 tcp ，此值表示起始端口。*
*udp：如果协议为 udp，此值表示结束端口。*
*icmp:如果协议为 icmp，此值表示 ICMP 代码 具体代码可参见 ICMP 类型及代码*
*val3：源IP*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group | String | Yes | 防火墙ID |
| rules | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"security_group_rule_id": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |


#### Rule 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| security_group_id | String | Yes |   防火墙规则ID |
| protocol | String | Yes | 协议，目前支持 tcp, udp, icmp, gre, esp, ah, ipip |
| priority | Int | Yes | 优先级，由高到低为 0 - 100 |
| action | String | No | 行为：accept 表示接受，drop 为拒绝 |
| direction | Int | No | 方向，0 表示下行，1 表示上行。 |
| name | String | No | 防火墙规则名称 |
| tcp | Object | No | 如果协议为 tcp ，此值表示起始,结束端口。其他协议无需此值 |
| udp | Object | No | 如果协议为 tcp ，此值表示起始,结束端口。其他协议无需此值。 |
| icmp | Object | No | 如果协议为 icmp，此值表示 ICMP 类型,如果协议为 icmp，此值表示 ICMP 类型,其他协议无需此值 |
| addr | Object | No | 目标 IP，如果填写，则这条防火墙规则只对此IP（或IP段）有效。 |
### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://dev2.51idc.cn:9000/v2/zone/ac2/security_rules" --data '
{
    "security_group": "sg-F2L8YCV",
    "rules": [
        {
            "name": "ping",
            "priority": 1,
            "action": "accept",
            "direction": "DOWN",
            "protocol": "icmp",
            "disabled": 0,
            "icmp": {
                "icmp_type": "8",
                "icmp_code": "0"
            },
            "addr": {
                "saddr": "192.168.11.12"
            }
        },
        {
            "name": "mstsc",
            "priority": 3,
            "action": "accept",
            "direction": "DOWN",
            "protocol": "tcp",
            "disabled": 0,
            "tcp": {
                "start_port": "3389",
                "end_port": "3389"
            },
            "addr": {
                "saddr": "192.168.11.12"
            }
        }
    ]
}'
```

#### 响应内容:

```js
{
    "security_group_rules": [
        "sgr-KNWLWNT",
        "sgr-ERQCZYR"
    ]
}
```


## PUT /security_group_rules/:rules_id

**修改防火墙属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| protocol | String | Yes | 协议，目前支持 tcp, udp, icmp, gre, esp, ah, ipip |
| priority | Int | Yes | 优先级，由高到低为 0 - 100 |
| action | String | Yes | 行为：accept 表示接受，drop 为拒绝s |
| direction | Int | Yes | 方向，0 表示下行，1 表示上行。 |
| name | String | Yes | 防火墙规则名称 |
| start_port | String | Yes | 如果协议为 tcp 或 udp，此值表示起始端口。其他协议无需此值 |
| end_port | String | Yes | 如果协议为 tcp 或 udp，此值表示结束端口。其他协议无需此值。|
| icmp_type | String | Yes | 如果协议为 icmp，此值表示 ICMP 类型，具体类型可参见 ICMP 类型及代码 其他协议无需此值。|
| icmp_code | String | Yes |如果协议为 icmp，此值表示 ICMP代码 ，其他协议无需此值 |
| saddr | String | Yes | 用于上行规则，如果填写，则这条防火墙规则只对此目的IP（或IP段）有效。 |
| daddr | String | Yes | 用于下行规则，如果填写，则这条防火墙规则只对此源IP（或IP段）有效。 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://dev2.51idc.cn:9000/v2/zone/ac2/security_rules/:rules_id" --data '
{
    "name": "mstsc1",
    "priority": 2,
    "action": "accept",
    "direction": "UP",
    "protocol": "tcp",
    "disabled": 0,
    "start_port": "3389",
    "end_port": "3389",
    "daddr": "192.168.11.13"
}'
```

#### 响应内容:

```js
{"rule_id":"sgr-ERQCZYR"}



## DELETE /security_rules/:rules_id

**删除防火墙规则**

*删除防火墙规则。*

*注 删除规则后，记得调用 ApplySecurityGroup 使其生效。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rules | String[] | Yes | 防火墙规则ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://dev2.51idc.cn:9000/v2/zone/ac2/security_rules/:rules_id"
```

#### 响应内容:

```js
{
    "rules": [
        "sgr-KNWLWNT"
    ]
}
```

## POST /new/security_group_product

**创建防火墙并添加规则**

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| group_name | String | No | 防火墙名称 |
| rules | Object[] | No | [<br>{<br>&nbsp;&nbsp;"protocol": "*String*",<br>&nbsp;&nbsp;"priority": "*Int*",<br>&nbsp;&nbsp;"action": "*String*",<br>&nbsp;&nbsp;"val2": "*String*",<br>&nbsp;&nbsp;"val1": "*String*",<br>&nbsp;&nbsp;"val3": "*String*",<br>&nbsp;&nbsp;"direction": "*Int*",<br>&nbsp;&nbsp;"disabled": "*Int*",<br>&nbsp;&nbsp;"name": "*String*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://dev2.51idc.cn:9000/v2/zone/ac2/new/security_group_product" --data '
{
    "group_name":"secruity_group_name",
    "rules": [
        {
            "name": "ping",
            "priority": 1,
            "action": "accept",
            "direction": "DOWN",
            "protocol": "icmp",
            "disabled": 0,
            "icmp": {
                "icmp_type": "8",
                "icmp_code": "0"
            },
            "addr": {
                "saddr": "192.168.11.12"
            }
        },
        {
            "name": "mstsc",
            "priority": 3,
            "action": "accept",
            "direction": "DOWN",
            "protocol": "tcp",
            "disabled": 0,
            "tcp": {
                "start_port": "3389",
                "end_port": "3389"
            },
            "addr": {
                "saddr": "192.168.11.12"
            }
        }
    ]
}
```

#### 响应内容:

```js
{
    "job_id": "08b2ee3e-1be6-4c6c-802c-c3fd21143f5a",
    "action": "CreateSecurityGroupProduction",
    "request_id": "c37e2be8-c8e2-489b-be10-307a2d3fd611",
    "status": "pending",
    "create_time": "2016-08-29T10:47:46Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```