# RDB

<!-- toc -->

## GET /rdbs

**获取一个或多个数据库集群信息**

*可根据数据库集群 ID，状态，数据库集群名称作过滤条件，来获取数据库集群列表。 如果不指定任何过滤条件，默认返回你所拥有的所有数据库集群。 如果指定不存在的路由器ID，或非法状态值，则会返回错误信息。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域  |
| rdb_ids | []String| No | 数据库集群 ID |
| tag_ids | []String | No | 标签ID，逗号分隔 |
| status | String| No | 数据库集群状态: 有效值包括 pending, active, stopped, suspended, deleted, ceased|
| rdb_name | String| No | 数据库集群名称 |
| rdb_engine | RDB_ENGINE| No | 数据库类型，支持 mysql 和 psql，注意该值是大小写敏感的；默认值为 mysql |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到租用设备总数 |
| rdb_set | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"rdb_id": "*String*",<br>&nbsp;&nbsp;"rdb_name": "*String*",<br>&nbsp;&nbsp;"rdb_engine": "*String*",<br>&nbsp;&nbsp;"engine_version": "*String*",<br>&nbsp;&nbsp;"rdb_type": "*String*",<br>&nbsp;&nbsp;"rdb_class": "*String*",<br>&nbsp;&nbsp;"storage_size": "*Int*",<br>&nbsp;&nbsp;"master_ip": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"status_time": "*String*",<br>&nbsp;&nbsp;"alarm_status": "*String*",<br>&nbsp;&nbsp;"transition_status": "*String*",<br>&nbsp;&nbsp;"auto_backup_time": "*Int*",<br>&nbsp;&nbsp;"auto_minor_ver_upgrade": "*Int*",<br>&nbsp;&nbsp;"last_snapshot_time": "*String*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"description": "*String*",<br>&nbsp;&nbsp;"vxnet": "*Object*",<br>&nbsp;&nbsp;"rdb_instances": "*Object[]*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev.api.51idc.com/v2/zone/ac2/rdbs"
```

#### 响应内容:

```js
{
    "rdb_set": [
        {
            "rdb_id": "rdb-HPGBLT4",
            "rdb_name": "testtest",
            "rdb_engine": "mysql",
            "engine_version": "mysql_5_7",
            "rdb_type": "K2G4",
            "rdb_class": "PERFORMANCE",
            "storage_size": 50,
            "master_ip": "192.168.100.6",
            "status": "active",
            "status_time": "2016-11-09T09:34:32Z",
            "alarm_status": "",
            "transition_status": "",
            "auto_backup_time": 1,
            "auto_minor_ver_upgrade": 1,
            "last_snapshot_time": "2016-11-07T17:17:41Z",
            "create_time": "2016-11-04T06:40:11Z",
            "vxnet": {
                "vxnet_name": "router1478496741342",
                "vxnet_id": "vxnet-8A99107"
            },
            "rdb_instances": [
                {
                    "user_name": "testtest",
                    "rdb_instance_role": "topslave",
                    "rdb_instance_id": "rmi-KKAFXWG",
                    "rdb_inst_type": 0,
                    "storage_engine": "innodb",
                    "rdb_id": "rdb-HPGBLT4",
                    "vxnet_id": "vxnet-8A99107",
                    "private_ip": "192.168.100.5",
                    "ip": "192.168.100.5",
                    "status": "active",
                    "status_time": "2016-11-09T02:00:51Z",
                    "transition_status": "",
                    "create_time": "2016-11-04T06:41:42Z"
                },               
                {
                    "user_name": "testtest",
                    "rdb_instance_role": "slave",
                    "rdb_instance_id": "rmi-GF4C3E8",
                    "rdb_inst_type": 0,
                    "storage_engine": "innodb",
                    "rdb_id": "rdb-HPGBLT4",
                    "vxnet_id": "vxnet-8A99107",
                    "private_ip": "192.168.100.130",
                    "ip": "192.168.100.130",
                    "status": "active",
                    "status_time": "2016-11-09T07:02:11Z",
                    "transition_status": "",
                    "create_time": "2016-11-09T07:03:00Z"
                },
                {
                    "user_name": "testtest",
                    "rdb_instance_role": "master",
                    "rdb_instance_id": "rmi-3X062TV",
                    "rdb_inst_type": 0,
                    "storage_engine": "innodb",
                    "rdb_id": "rdb-HPGBLT4",
                    "vxnet_id": "vxnet-8A99107",
                    "private_ip": "192.168.100.6",
                    "ip": "192.168.100.6",
                    "status": "active",
                    "status_time": "2016-11-09T02:00:54Z",
                    "transition_status": "",
                    "create_time": "2016-11-09T07:03:00Z"
                }
            ],
            "description": ""
        }
    ],
    "total_count": 2
}
```
## POST /rdbs

**创建一个数据库集群**

*创建一个数据库集群*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域  |
| vxnet | String | Yes |   私有网络 ID|
| rdb_engine | String | No | 数据库类型，支持 mysql 和 psql，注意该值是大小写敏感的；默认值为 mysql |
| engine_version | String | No | 对应数据的版本，mysql 支持 5.5，psql 支持 9.4；默认值为 5.5 |
| rdb_username | String | Yes | 数据库用户名 |
| rdb_password | String | Yes | 数据库用户密码 |
| rdb_type | String | Yes |  数据库型号，1 – 1核2G，2 – 2核4G，3 – 4核8G，4 – 8核16G，5 – 8核32G |
| rdb_class | String | No |  数据库性能 |
| storage_size | Int | Yes |  数据库磁盘容量(GB)，用于存放数据和日志，最小10G，最大1000G |
| rdb_name | String | No |  数据库集群名称 |
| auto_backup_time | Int | No | 自动备份时间，有效值0-23，任何大于23的整型值均表示关闭自动备份，忽略的话会随机选择一个自动备份时间 |
| description | String | No | 数据库集群描述 |
| network_type | Int | No | |
| node_count | String | No | 节点数量默认2个 mysq5.6、mysql5.7最多可有5个 |
| master_ip | String | No | 节点IP,无此参数则自动分配IP |
| topslave_ip | String | No | 节点IP,无此参数则自动分配IP |
| slave_ips | String | No | slave节点IP,无此参数则自动分配IP |
| proxy_count | String | No | mysq5.6、mysql5.7代理节点数量目前支持1个 |
| proxy_ip | String | No | 代理节点IP |
| wvip | String | No | 写节点IP |
| rvip | String | No | 读节点IP |
| auto_minor_ver_upgrade | String | No |  数据库版本自动升级 |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求
```bash
$ curl -XPOST "http://dev.api.51idc.com/v2/zone/ac2/rdbs" --data '
{
    "vxnet_id": "vxnet-6120978",
    "rdb_engine": "mysql",
    "engine_version": "mysql_5_7",
    "rdb_username": "testtest",
    "rdb_password": "TESTtest1234",
    "rdb_type": "K1G2",
    "storage_size": 10,
    "rdb_name": "testtest",
    "node_count": 4,
    "proxy_count": 1,
    "network_type": 1,
    "auto_backup_time": 1,
    "master_ip": "192.168.100.221",
    "topslave_ip": "192.168.100.222",
    "wvip": "192.168.100.223",
    "rvip": "192.168.100.224",
    "proxy_ip": "192.168.100.225",
    "slave_ips": [
        "192.168.100.226",
        "192.168.100.227"
    ],
    "auto_minor_ver_upgrade": 1,
    "description": "",
    "order":{
    "payment_type":"POSTPAY"
  }
}
```
#### 响应内容:

```js
{
    "job_id": "5de9599b-5075-4a92-bd9e-c8d19c3f2b93",
    "action": "CreateRdb",
    "request_id": "3e1db903ecd07681",
    "status": "pending",
    "created_time": "2016-11-15T07:19:48Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": [
        "rdb-LUH1UV1"
    ],
    "order_no": "C2016111512900"
}
```

## POST /rdbs/stop

**关闭指定的数据库集群**

*关闭指定的数据库集群*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_ids | []String| Yes | 数据库集群 ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/stop
{
    "rdb_ids": [
        "rdb-JLF5S7E"
    ]
}
```

#### 响应内容:

```js
{
    "job_id": "6102d908-4fc7-491f-85bb-5484ec5f009b",
    "action": "StopRdbs",
    "request_id": "4cb3021c0b41bda3",
    "status": "pending",
    "created_time": "2016-11-10T08:50:54Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## POST /rdbs/start

**启动指定的数据库集群**

*启动指定的数据库集群*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_ids | []String| Yes | 数据库集群 ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/start
{
    "rdb_ids": [
        "rdb-JLF5S7E"
    ]
}
```

#### 响应内容:

```js
{
    "job_id": "ad3f090b-d1ff-466b-aa66-35ee654b6050",
    "action": "StopRdbs",
    "request_id": "3307f72665049061",
    "status": "pending",
    "created_time": "2016-11-10T08:58:27Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## POST /rdbs/resize

**扩容指定的数据库集群**

*扩容指定的数据库集群*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_ids | []String| Yes | 数据库集群 ID |
| rdb_type | String| No | 数据库型号，1-2核4G，2-4核8G，3-8核16G，4-8核32G |
| storage_size | Int| No |数据库磁盘容量(GB)，用于存放数据和日志，最小50G，最大1000G，扩容时该值不能比原始容量小 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/resize
{
    "zone": "ac2",
    "rdb_ids": [
        "rdb-JLF5S7E"
    ],
    "rdb_type": "K2G4",
    "storage_size": 50
}
```

#### 响应内容:

```js
{
    "job_id": "b55d88d2-d66a-4847-b624-6a6566f7ad18",
    "action": "ResizeRdbs",
    "request_id": "4977a1daa9dc546f",
    "status": "pending",
    "created_time": "2016-11-10T09:09:10Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## POST /rdbs/leave_vxnet

**将指定的数据库集群从私有网络中脱离**

*将指定的数据库集群从私有网络中脱离*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_ids | []String| Yes | 数据库集群 ID |
| vxnet_id | String| Yes | 私有网络 ID|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/leave_vxnet
{
    "rdb_ids": [
        "rdb-JLF5S7E"
    ],
  "vxnet_id":"vxnet-8A99107"
}
```

#### 响应内容:

```js
{
    "job_id": "89959f1d-dbdc-4109-b946-9917aa254d09",
    "action": "RdbsLeaveVxnet",
    "request_id": "1fbf655096f407a6",
    "status": "pending",
    "created_time": "2016-11-10T09:34:48Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```


## POST /rdbs/join_vxnet

**将指定的数据库集群加入私有网络**

*将指定的数据库集群加入私有网络*

### 请求

####  参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_ids | []String| Yes | 数据库集群 ID |
| vxnet_id | String| Yes | 私有网络 ID|
| wvip | String | No | 写节点IP |
| rvip | String | No | 读节点IP |
| instances | Object[] | No | [<br>{<br>&nbsp;&nbsp;"rdb_instance_id": "*String*",<br>&nbsp;&nbsp;"private_ip": "*String*",<br>}<br>] |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/join_vxnet
{
    "rdb_id": "rdb-JLF5S7E",
    "vxnet_id": "vxnet-A6FF81F",
    "wvip": "192.168.100.201",
    "rvip": "192.168.100.202",
    "instances": [
        {
            "rdb_instance_id": "rmi-YQWIMTU",
            "private_ip": "192.168.100.203"
        }
    ]
}
```

#### 响应内容:

```js
{
    "job_id": "94fed941-1fda-488d-a415-806aa1694360",
    "action": "RdbsJoinVxnet",
    "request_id": "101e78564d3e9d0c",
    "status": "pending",
    "created_time": "2016-11-10T09:47:19Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## POST /rdbs/snapshot/create_rdb

**从指定备份创建出一个全新的数据库集群**

*从指定备份创建出一个全新的数据库集群*

### 请求

#### 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| snapshot_id | String| Yes | 数据库集群备份 ID |
| vxnet_id | String | Yes |   私有网络 ID|
| rdb_username | String | Yes | 数据库用户名 |
| rdb_password | String | Yes | 数据库用户密码 |
| rdb_type | String | Yes |  数据库型号，1 – 1核2G，2 – 2核4G，3 – 4核8G，4 – 8核16G，5 – 8核32G |
| rdb_class | String | No |  数据库性能 |
| rdb_name | String | No |  数据库集群名称 |
| auto_backup_time | Int | No | 自动备份时间，有效值0-23，任何大于23的整型值均表示关闭自动备份，忽略的话会随机选择一个自动备份时间 |
| instances | Object[] | No | [<br>{<br>&nbsp;&nbsp;"rdb_instance_id": "*String*",<br>&nbsp;&nbsp;"private_ip": "*String*",<br>}<br>] |
| wvip | String | No | 写节点IP |
| rvip | String | No | 读节点IP |
| description | String | No | 数据库集群描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/snapshot/create_rdb
{
    "snapshot_id": "ss-VR3GZD9",
    "vxnet_id": "vxnet-8A99107",
    "rdb_username": "testtest",
    "rdb_password": "TESTtest1234",
    "rdb_type": "K1G2",
    "rdb_class": "HIGH_PERFORMANCE",
    "rdb_name": "",
    "auto_backup_time": 0,
    "instances": [
        {
            "rdb_instance_role": "master",
            "private_ip": "192.168.100.103"
        }
    ],
    "wvip": "192.168.100.102",
    "rvip": "192.168.100.101",
    "description": ""
}
```

#### 响应内容:

```js
{
    "job_id": "d2c03b9e-6382-4e8e-b12f-685207b48c90",
    "action": "CreateRdbFromSnapshot",
    "request_id": "13195ce20c75ae44",
    "status": "pending",
    "created_time": "2016-11-10T10:46:32Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```


## POST /rdbs/snapshot/create_temp_instance

**从备份创建一个临时性数据库实例，并将之添加到指定的数据库集群**

*从备份创建一个临时性数据库实例，并将之添加到指定的数据库集群*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | 数据库集群 ID |
| snapshot_id | String| Yes | 数据库集群备份 ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/snapshot/create_temp_instance
{
    "snapshot_id": "ss-VR3GZD9",
    "rdb_id": "rdb-JYSD9NZ"
}
```

#### 响应内容:

```js
{
    "job_id": "2c5e2237-0ae2-4b54-872b-318c8baf7789",
    "action": "CreateTempRdbInstanceFromSnapshot",
    "request_id": "50d76582d72a619f",
    "status": "pending",
    "created_time": "2016-11-10T11:16:14Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## GET /rdbs/instances/:instance/logs

**获取机柜列表**

*可根据标签ID，名称作为过滤条件，获取机柜列表。如果不指定任何过滤条件，默认返回你所拥有的所有机柜。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String | Yes | 区域ID |
| rdb_instance_id | String | No | 数据库节点ID |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rdb_instance_id | String | Yes | 节点 Id |
| slow_logs | Object[] | No | [<br>{<br>&nbsp;&nbsp;"last_modify": "*String*",<br>&nbsp;&nbsp;"file": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>}<br>] |
| binary_logs | Object[] | No | [<br>{<br>&nbsp;&nbsp;"last_modify": "*String*",<br>&nbsp;&nbsp;"file": "*String*",<br>&nbsp;&nbsp;"size": "*Int*",<br>}<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev.api.51idc.com/v2/zone/ac2/rdbs/instances/rmi-YQWIMTU/logs"
```

#### 响应内容:

```js
{
    "rdb_instance_id": "rmi-YQWIMTU",
    "slow_logs": [
        {
            "last_modify": "2016-11-10 17:48:29",
            "file": "mysql-slow.log",
            "size": 740
        }
    ],
    "binary_logs": [
        {
            "last_modify": "2016-11-10 16:51:18",
            "file": "mysql-bin.000001",
            "size": 3095
        },
        {
            "last_modify": "2016-11-10 17:48:29",
            "file": "mysql-bin.000004",
            "size": 194
        }
    ]
} 
```

## POST /rdbs/instance_logs/copy2ftp

**将指定的日志文件拷贝到 FTP 目录**

*将指定的日志文件拷贝到 FTP 目录*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_instance_id | String| Yes | 节点ID |
| files | []String[ | Yes | log文件名  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/instance_logs/copy2ftp
{
    "rdb_instance_id": "rmi-YQWIMTU",
    "files": [
      "mysql-bin.000004"
    ]

}
```

#### 响应内容:

```js
{
    "job_id": "5d906081-7baa-4510-88e8-d2a27d40ce50",
    "action": "CopyRdbInstanceFilesToFTP",
    "request_id": "635cd910aab57936",
    "status": "pending",
    "created_time": "2016-11-10T11:35:29Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```


## POST /rdbs/instance_logs/purge

**清除日志文件**

*清除日志文件*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_instance_id | String| Yes | 数据库节点 ID |
| rdb_id | String| Yes | RDB ID |
| log_type | String[ | Yes | 日志类型，binary_log，slow_log，error_log  |
| before_file | String| Yes | binlog日志文件名 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/instance_logs/purge
{
    "zone": "ac2",
    "rdb_id": "rdb-JLF5S7E",
    "rdb_instance_id": "rmi-YQWIMTU",
    "log_type": "binary_log",
    "before_file": "mysql-bin.000002"
}
```

#### 响应内容:

```js
{
    "job_id": "c08cc297-bb38-48bd-a280-cf2669ae95c7",
    "action": "PurgeRdbLogs",
    "request_id": "71351e243ac8cb3",
    "status": "pending",
    "created_time": "2016-11-10T11:48:56Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## PUT /rdbs/attributes

**修改数据库名称描述备份时间等属性**

*修改数据库名称描述备份时间等属性*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | RDB ID |
| rdb_name | String[ | No | RDB name |
| description | String| No | description |
| auto_backup_time | Int| No | 备份时间 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPUT http://dev.api.51idc.com/v2/zone/ac2/rdb/attributes
{
    "zone": "ac2",
    "rdb_id": "rdb-JLF5S7E",
    "rdb_name": "test-name",
    "log_type": "binary_log",
    "description": "description"
}
```

#### 响应内容:

```js
{}
```

## POST /rdbs/update_rdb

**修改数据库读写IP及实例节点IP**

*修改数据库读写IP及实例节点IP*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | RDB ID |
| instances | Object[]| Yes | 节点IP |
| wvip | String | No | 写节点IP |
| rvip | String | No | 读节点IP |
| features | Int | No | 主从模式 0开启1关闭 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/update_rdb
{
    "zone": "ac2",
    "rdb_id": "rdb-JLF5S7E",
    "instances": [
        {
            "rdb_instance_id": "rmi-YQWIMTU",
            "private_ip": "192.168.100.115"
        },
        {
            "rdb_instance_id": "rmi-RW3Y3KC",
            "private_ip": "192.168.100.116"
        }
    ],
    "rvip": "192.168.100.118",
    "wvip": "192.168.100.117"
}
```

#### 响应内容:

```js
{
    "job_id": "9287a731-44f4-4be0-9027-307e57891f00",
    "action": "UpdateRdb",
    "request_id": "17b530be1fe27280",
    "status": "pending",
    "created_time": "2016-11-10T12:14:41Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## POST /rdbs/instances

**创建数据库实例**

*创建数据库实例*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | RDB ID |
| rdb_instance_role | String | Yes | 节点类型 |
| private_ip | String | No | 节点IP |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/instances
{
    "zone": "ac2",
    "rdb_id": "rdb-JLF5S7E",
    "rdb_instance_role": "slave",
    "private_ip": "192.168.100.120"
}
```

#### 响应内容:

```js
{
    "job_id": "fdc64481-0e82-4fee-ac57-b4a3864aa9c2",
    "action": "AddRdbInstances",
    "request_id": "7b68f3264114983a",
    "status": "pending",
    "created_time": "2016-11-10T12:21:42Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```


## POST /rdbs/instances/delete

**删除数据库实例**

*删除数据库实例*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | RDB ID |
| rdb_instance_ids | []String | Yes | 节点ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/instances/delete
{
    "zone": "ac2",
    "rdb_id": "rdb-JLF5S7E",
    "rdb_instance_ids": ["rmi-YEFEPXM"]
}
```

#### 响应内容:

```js
{
    "job_id": "c1a0eee8-f7b6-4d5f-adc9-f8ef38348ee0",
    "action": "DeleteRdbInstances",
    "request_id": "2442055195cd46cd",
    "status": "pending",
    "created_time": "2016-11-10T12:24:55Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```


## PUT /rdbs/parameters

**启动指定的数据库集群**

*启动指定的数据库集群*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | RDB ID |
| parameters | Object[] | No |  [<br>{<br>&nbsp;&nbsp;"var_value": "*String*",<br>&nbsp;&nbsp;"var_name": "*String*",<br>}<br>]  |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPUT http://dev.api.51idc.com/v2/zone/ac2/rdbs/parameters
{
    "zone": "ac2",
    "rdb_id": "rdb-HPGBLT4",
    "parameters": [
        {
            "var_value": "13",
            "var_name": "expire_logs_days"
        }
    ]
}
```

#### 响应内容:

```js
{}
```


## POST /rdbs/parameters/apply

**应用数据库配置**

*应用数据库配置*

### 请求

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_id | String| Yes | RDB ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XPOST http://dev.api.51idc.com/v2/zone/ac2/rdbs/parameters/apply
{
    "zone": "ac2",
    "rdb_id": "rdb-HPGBLT4"
}
```

#### 响应内容:

```js
{
    "job_id": "e8301404-46b5-4f1d-b52c-e76d22a1b292",
    "action": "ApplyRdbParameterGroup",
    "request_id": "7fd60c6300fd1c81",
    "status": "pending",
    "created_time": "2016-11-10T12:49:18Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```

## GET /rdbs/parameters

**获取专线列表**

*可根据标签ID，名称作为过滤条件，获取机柜列表。如果不指定任何过滤条件，默认返回你所拥有的所有专线。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| rdb_id | String| Yes | RDB ID |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到机柜总数 |
| parameters | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"is_static": "*Int*",<br>&nbsp;&nbsp;"family": "*String*",<br>&nbsp;&nbsp;"is_readonly": "*Int*",<br>&nbsp;&nbsp;"var_value": "*String*",<br>&nbsp;&nbsp;"opt_name": "*String*"<br>&nbsp;&nbsp;"var_type": "*String*"<br>&nbsp;&nbsp;"var_name": "*String*",<br>&nbsp;&nbsp;"section_name": "*String*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://dev.api.51idc.com/v2/zone/ac2/rdbs/parameters?rdb_id=rdb-JLF5S7E"
```

```js
{
    "parameters": [
        {
            "is_static": 0,
            "family": "mysql5.7",
            "is_readonly": 1,
            "var_value": "slave_net_timeout",
            "opt_name": "slave-net-timeout",
            "var_type": "int",
            "var_name": "slave_net_timeout",
            "section_name": "mysqld"
        },
        {
            "is_static": 0,
            "min_value": "1",
            "family": "mysql5.7",
            "is_readonly": 0,
            "var_value": "max_connect_errors",
            "max_value": "1.048576e+06",
            "opt_name": "",
            "var_type": "int",
            "var_name": "max_connect_errors",
            "section_name": "mysqld"
        }
    ],
    "total_count": 64
}
```



## DELETE /rdbs/rdbs/:rdb_ids

**删除一个数据库集群**

*删除一个数据库集群*

### 请求

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String| Yes | 区域 ID |
| rdb_ids | String[] | Yes |数据库集群 ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XDELETE http://dev.api.51idc.com/v2/zone/ac2/rdbs/rdb-JYSD9NZ
{}
```

#### 响应内容:

```js
{
    "job_id": "f14f9c65-e0c1-4bf8-b675-95e391c63b0f",
    "action": "DeleteRdbs",
    "request_id": "302c66226879fd60",
    "status": "pending",
    "created_time": "2016-11-11T03:31:25Z",
    "begin_time": "",
    "finished_time": "",
    "extra": "",
    "zone": "ac2",
    "resource_ids": []
}
```