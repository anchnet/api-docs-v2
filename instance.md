# 主机


<!-- toc -->

## POST /instances

**打包产品**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instance | Object | Yes | 主机配置详情<br>{<br>&nbsp;&nbsp;"image_id": "*String*",<br>&nbsp;&nbsp;"instance_type": "*Int*",<br>&nbsp;&nbsp;"cpu": "*Int*",<br>&nbsp;&nbsp;"memory": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;"login_mode": "*String*",<br>&nbsp;&nbsp;"login_keypair": "*String*",<br>&nbsp;&nbsp;"login_passwd": "*String*",<br>&nbsp;&nbsp;"vxnets": "*String[]*",<br>&nbsp;&nbsp;"security_group": "*String*",<br>&nbsp;&nbsp;"volumes": "*String[]*",<br>&nbsp;&nbsp;"need_newsid": "*Int*",<br>&nbsp;&nbsp;"need_userdata": "*Int*",<br>&nbsp;&nbsp;"userdata_type": "*String*",<br>&nbsp;&nbsp;"userdata_value": "*String*",<br>&nbsp;&nbsp;"instance_class": "*String*",<br>&nbsp;&nbsp;"userdata_path": "*String*",<br>&nbsp;&nbsp;"userdata_file": "*String*",<br>&nbsp;&nbsp;"eips": "*String[]*"<br>} |
| vxnet |[ Object ] | No | 新建私有网络 <br>[<br>{<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"type": "*String*",<br>}<br>] |
| eip | Object | No | 新建公网 IP <br>{<br>&nbsp;&nbsp;"bandwidth": "*Int*",<br>&nbsp;&nbsp;"billing_mode": "*String*",<br>&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;"count": "*Int*",<br>&nbsp;&nbsp;"eip_group": "*String*"<br>} |
| volume | [ Object ] | No | 新建磁盘<br>[<br>{<br>&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>&nbsp;&nbsp;"volume_type": "*Int*",<br>&nbsp;&nbsp;"count": "*Int*"<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## GET /instances

**查询主机**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | 主机 ID 筛选，多个用 半角逗号',' 分割 <br> 例如：instances=ins-24h3k2j,ins-k2sfh345 |
| image_id | String[] | Yes | 镜像 ID |
| instance_type | String[] | Yes | 主机类型 <br> PERFORMANCE: 性能型 <br> HIGH_PERFORMANCE: 超高性能型 |
| status | String[] | Yes | 主机状态<br>可选值：<br>pending 处理中<br>running 运行中<br>stopped 已关机<br>suspended 已暂停<br>terminated 已删除<br>ceased  已终止|
| search_word | String | Yes | 查询关键词 |
| tags | String[] | Yes | 筛选标签 |
| offset | Int | Yes | 分页跨度 |
| limit | Int | No | 分页数量，默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | Object[] | Yes | 主机列表 <br> [<br>{<br>&nbsp;&nbsp;"instance_id": "*String*",<br>&nbsp;&nbsp;"instance_name": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"instance_type": "*Int*",<br>&nbsp;&nbsp;"vcpus_current": "*Int*",<br>&nbsp;&nbsp;"memory_current": "*Int*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"image": "*String*",<br>&nbsp;&nbsp;"vxnets": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_type": "*Int*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"vxnet_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"nic_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"private_ip": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"eip": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_addr": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"eip_id": "*String*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"security_group": {<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"security_group_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;"is_default": "*Int*"<br>&nbsp;&nbsp;},<br>&nbsp;&nbsp;"volumes": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_name": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_type": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"volume_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"size": "*Int*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;],<br>&nbsp;&nbsp;"keypair_ids": [<br>&nbsp;&nbsp;&nbsp;&nbsp;{<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"keypair_id": "*String*",<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"keypair_name": "*String*"<br>&nbsp;&nbsp;&nbsp;&nbsp;}<br>&nbsp;&nbsp;]<br>}<br>] |
| total_count | Int | Yes | 总数量 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/instances"
```

#### 响应内容:

```js
{
	"instances": [
		{
			"instance_id": "ins-JWFQNPY",
			"instance_name": "test-go",
			"description": "",
			"instance_type": "PERFORMANCE",
			"vcpus_current": 1,
			"memory_current": 1024,
			"status": "running",
			"transition_status": "",
			"create_time": "2016-07-22T06:02:33Z",
			"status_time": "2016-07-29T03:15:03Z",
			"image": {
				"image_id": "centos65x64d",
				"image_name": "Ubuntu 16.04 LTS",
				"image_size": 10,
				"platform": "linux",
				"processor_type": "64bit",
				"os_family": "ubuntu",
				"provider": "system",
				"is_shared": 0
			},
			"vxnets": [
				{
					"vxnet_name": "公有网络",
					"vxnet_type": "SYSTEM_MANAGER",
					"vxnet_id": "vxnet-0",
					"nic_id": "52:54:31:27:3c:04",
					"private_ip": ""
				}
			],
			"eip": {
				"eip_name": "test-eip",
				"eip_addr": "118.184.0.102",
				"eip_id": "eip-EF217BD"
			},
			"keypair_ids": [
				{
					"keypair_id": "kp-ZRM7SM2",
					"keypair_name": "sss"
				}
			]
		}
	],
	"total_count": 125
}
```


## PUT /instances

**修改主机属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | 主机 ID列表 |
| instance_name | String | Yes | 主机名称 |
| description | String | Yes | 主机描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
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


## POST /instances/start

**启动主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | 主机实例 ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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
| instances | String[] | Yes | 主机实例 ID |
| force | Int | Yes | 是否强制关机<br>1: 强制关机<br>0: 非强制关机，默认为0 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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
| instances | String[] | Yes | 主机实例 ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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
| instances | String[] | Yes | 主机实例 ID |
| login_mode | String | Yes | 指定登录方式。当为 linux 主机时，有效值为 keypair 和 passwd; 当为 windows 主机时，只能选用 passwd 登录方式。<br>当登录方式为 keypair 时，需要指定 login_keypair 参数；<br>当登录方式为 passwd 时，需要指定 login_passwd 参数。 |
| login_keypair | String | Yes | 登录密钥ID |
| login_passwd | String | Yes | 登录密码 |
| need_newsid | Int | Yes | 1: 生成新的SID<br>0: 不生成新的SID, 默认为0；只对Windows类型主机有效 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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
| instances | String[] | Yes | 主机实例 ID |
| instance_type | String | Yes | 主机类型 <br> PERFORMANCE: 性能型 <br> HIGH_PERFORMANCE: 超高性能型 |
| cpu | Int | Yes | CPU core，有效值为: 1, 2, 4, 8, 16 |
| memory | String | Yes | 内存，有效值为: 1024, 2048, 4096, 6144, 8192, 12288, 16384, 24576, 32768 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
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


## POST /instances/reset_login_passwd

**重置系统密码**

*主机必须处于关机状态才能重置密码*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| instances | String[] | Yes | 主机实例 ID |
| login_passwd | String | Yes | 登录密码 |

### 服务端响应

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/reset_login_passwd" --data '
{
    "instances":["ins-AVVNTPJ"],
    "login_passwd":"Test123456"
}'
```

#### 响应内容:

```js
{
  "job_id": "ce9d13b7-cd22-4fef-8805-a0f04b7051f7",
  "action": "ResetLoginPasswd",
  "request_id": "1543d6bf-5434-4274-afb6-c33823dc04fb",
  "status": "pending",
  "create_time": "2016-08-17T06:16:32Z",
  "begin_time": "",
  "finished_time": "",
  "extra": "",
  "zone": "ac2",
  "resource_ids": []
}
```


## DELETE /instances/:ins_id

**销毁主机**

*详细描述*

### 请求

#### URI PATH 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| :ins_id | String | Yes | 主机实例 ID<br> *多个用英文半角逗号 ',' 分割* |


### Query String 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| volumes | String | Yes | 强制删除磁盘列表， 多个以英文半角逗号','分隔 |
| eips | String | Yes | 强制删除公网IP列表， 多个以英文半角逗号','分隔 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/instances/i-23kh43?volumes=vol-hk2h34,vol-23k4h324"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

