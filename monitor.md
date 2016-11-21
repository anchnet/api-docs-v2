# monitor

<!-- toc -->

## GET /v2/monitor_status/:endpoint

**endpoint监控状态查询**
> 查询endpoint有没有被监控

### 请求

#### 请求body参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| message | String | Yes | 监控说明 |
| ok | Bool | Yes | true表示已经监控， false表示未添加监控 |

#### 请求实例

#### CURL
```shell
curl -XGET "http://api.51idc.com/v2/monitor_status/server_9845" 
```

#### 响应示例

```json
{
    "message" : "",
    "ok"      : true
}
```
## POST /v2/monitor/idc

**物理设备监控数据获取**

### 请求

#### 请求body参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| start_time | Int | Yes | 监控数据开始时间戳 |
| end_time | Int | Yes | 监控数据结束时间戳 |
| cf | String | Yes | - AVERAGE 平均值  - MAX 最大值  - MIN 最小值|
| endpoint | String | Yes | 监控对象 |
| counter | String | Yes | 监控项 [<br>{<br>&nbsp;&nbsp;"cpu.busy": "CPU使用率",<br>&nbsp;&nbsp;"load": "1分钟, 5分钟，15分钟负载",<br>&nbsp;&nbsp;"mem.memused.percent": "内存使用率",<br>&nbsp;&nbsp;"net.if.in.bytes": "进方向流量",<br>&nbsp;&nbsp;"net.if.out.bytes": "出方向流量",<br>&nbsp;&nbsp;"disk.io.write_bytes": "IO写速率",<br>&nbsp;&nbsp;"disk.io.read_bytes": "IO读速率",<br>&nbsp;&nbsp;"tcp.closed": "tcp.closed",<br>&nbsp;&nbsp;"tcp.timewait": "tcp.timewait",<br>&nbsp;&nbsp;"tcp.synrecv": "tcp.synrecv",<br>&nbsp;&nbsp;"tcp.slabinfo.timewait": "tcp.slabinfo.timewait",<br>&nbsp;&nbsp;"tcp.orphaned": "tcp.orphaned",<br>&nbsp;&nbsp;"tcp.estab": "tcp.estab",<br>}<br>]|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| endpoint | String | Yes | 监控对象 |
| counter | String | Yes | 监控项 |
| step | String | Yes | 数据间隔时间 |
| timestamp | Int | Yes | 监控数据时间 |
| value | Int | Yes | 监控数据，-1无效 |

#### 请求实例

#### CURL
```shell
curl -XPOST "http://api.51idc.com/v2/monitor/idc" --data '
{
    "start_time": 1476782710,
    "end_time": 1476786250,
    "cf": "AVERAGE",
    "endpoint_counters": [
        {
            "endpoint": "hanjh_server_548",
            "counter": "mem.memfree"
        }, 
        { 
            "endpoint": "hanjh_server_548",
            "counter": "cpu.idle"
        }
    ]
}
'  
```

#### 响应示例

```json
{
  "meter_set": [
    {
      "endpoint": "hanjh_server_548",
      "counter": "mem.memfree",
      "step": 60,
      "data_set": {
        "timestamp": [
          1476783000,
          1476783300,
          1476783600
        ],
        "data_in": [
          0,
          0,
          0
        ]
      }
    },
    {
      "endpoint": "hanjh_server_548",
      "counter": "cpu.idle",
      "step": 60,
      "data_set": {
        "timestamp": [
          1476783000,
          1476783300,
          1476783600
        ],
        "data_in": [
          0,
          0,
          0
        ]
      }
    }
  ],
  "total_count": 2
}
```
## GET /v2/zone/{zone}/monitor/instance/:resource_id

**通过此 API 可获得负载均衡器的外网流量监控，以及每个监听器和后端服务的延迟时间，请求数和响应数。**
> * 主机的监控项包括: CPU 使用率，内存使用率，系统盘数据(吞吐量， IOPS 和使用率)， 主机连接私有网络的网卡流量，与主机绑定的各磁盘数据（吞吐量， IOPS 和使用率）。  
>  _注解 其中内存使用率和磁盘使用率暂不支持 Windows ，以及 kernel 版本过低的 Linux_
> * 公网 IP 资源可得到公网 “进/出” 的流量数据。
> * 如果资源为路由器，可得到路由器在基础网络的流量数据，以及与路由器连接的私有网络的流量数据

### 请求

#### 请求query参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource | String | Yes | 监控资源ID |
| start_time | String | Yes | 监控数据的起始 UTC 时间，格式为 2011-07-11T11:07:00Z 或 2011-07-11T11:07:00.520Z |
| end_time | String | Yes | 监控数据的结束 UTC 时间，格式为 2011-07-11T11:07:00Z 或 2011-07-11T11:07:00.520Z |
| step | String | Yes | 数据间隔时间，有效值为：5m, 15m, 2h, 1d。(m 表示分钟，h 表示小时，d 表示天)，建议5m在请求6小时监控数据时使用，15m在请求一天数据时使用，2h在请求两周数据时使用，1d在请求一个月和6个月数据时使用 |
| metersN | String | Yes | 监控项，不同类型的资源支持的监控项不同：<br> <ul><li>若资源是主机，meters 可以是<br> <ul><li>“cpu”：主机 cpu 使用率</li><li>“memory”：主机内存使用率</li><li>“disk-os”, “disk-iops-os”, “disk-us-os”：主机系统盘吞吐量，IOPS，空间使用率</li><li>“disk-硬盘ID”, “disk-iops-硬盘ID”, “disk-us-硬盘ID”：与主机绑定的硬盘的吞吐量，IOPS，空间使用率</li><li>“if-网卡地址”：主机网卡流量</li></ul><li>资源是公网IP，meters 有 “traffic”和“flow”</li><li>资源是路由器，meters 可以有 “vxnet-0” 和 “与路由器相连的私有网络ID”：带宽监控，也可以是“cpu”和“memory”：负载监控</li></ul>|
| obj | String | Yes | 操作对象，填“instance”|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource_id | String | Yes | 监控资源ID, 可选主机ID或者公网IP |
| meter_set | Array | Yes | 监控数据集，可参见下面 *监控数据集说明* |
| total_count | Int | Yes | 监控项数目 |

监控数据集说明
*   主机的 cpu，memory 监控值表示 “使用的千分比”，若要计算百分比请 先将值除以10 。比如 API 返回的 cpu 监控数据值是 56，表示资源使用百分比为5.6% 。
*   磁盘监控数据:
    *   磁盘吞吐量的监控数据单位是 B/s, 每组数据都包括两个值 [读, 写]。
    *   磁盘 IOPS 的监控数据单位就是 IOPS, 每组数据也包括两个值 [读, 写]。
    *   磁盘使用率的监控数据是类似这种格式 /|18|3319|15816 ，以 | 分隔表示 “mount 的路径”, “使用百分比”, “已使用空间（MB）”, “剩余可用空间（MB）”
*   网络流量的监控数据单位是 Bps (如果要换做 bps，记得每个值都乘以8)，每组数据都包括两个值 [进, 出]。
#### 请求实例

#### CURL
```shell
curl -XGET "http://api.51idc.com/v2/zone/ac2/monitor/ins/ins-3JJFO59?step=5m&start_time=2016-11-14T21:55:02.597Z&end_time=2016-11-15T03:55:02.597Z&metersN=cpu,disk-os,disk-iops-os,disk-us-os,if-52:54:a0:bd:b2:af,memory&obj=instance"
```

#### 响应示例

```json
{
  "resource_id": "i-dpvgz922",
  "meter_set": [
    {
      "meter_id": "if-52:54:a0:bd:b2:af",
      "vxnet_id": "",
      "sequence": 0,
      "data_set": {
        "timestamp": [
          1479160800,
          1479161100,
          1479161400
        ],
        "data_in": [
          34,
          34,
          34
        ],
        "data_out": [
          12,
          13,
          12
        ]
      }
    },
    {
      "meter_id": "disk-os",
      "data_set": {
        "timestamp": [
          1479160800,
          1479161100,
          1479161400
        ],
        "data_in": [
          0,
          0,
          0
        ],
        "data_out": [
          4420,
          3043,
          4905
        ]
      }
    },
    {
      "meter_id": "disk-iops-os",
      "data_set": {
        "timestamp": [
          1479160800,
          1479161100,
          1479161400
        ],
        "data_in": [
          0,
          0,
          0
        ],
        "data_out": [
          0,
          0,
          0
        ]
      }
    },
    {
      "meter_id": "disk-us-os",
      "data_set": {
        "timestamp": [
          1479160800,
          1479161100,
          1479161400
        ],
        "data_string": [
          "/|6|1055|18079",
          "/|6|1055|18079",
          "/|6|1055|18079"
        ]
      }
    },
    {
      "meter_id": "memory",
      "data_set": {
        "timestamp": [
          1479160800,
          1479161100,
          1479161400
        ],
        "data_in": [
          60,
          60,
          60
        ]
      }
    },
    {
      "meter_id": "cpu",
      "data_set": {
        "timestamp": [
          1479160800,
          1479161100,
          1479161400
        ],
        "data_in": [
          2,
          2,
          2
        ]
      }
    }
  ],
  "total_count": 6
}
```

## GET /v2/zone/{zone}/monitor/loadbalancer/:resource_id

**获取资源监控数据。支持的资源包括主机、公网 IP 和路由器， 选定不同类型资源，可获取的监控项不同。**
> * 因为负载均衡器可以绑定多个公网IP，所以每项监控数据都会按 IP 分组。
> * 监听器和后端服务在不同协议下，监控数据含义不同，具体可见下面”监控数据集说明”

### 请求

#### 请求query参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource | String | Yes | 监控资源ID |
| start_time | String | Yes | 监控数据的起始 UTC 时间，格式为 2011-07-11T11:07:00Z 或 2011-07-11T11:07:00.520Z |
| end_time | String | Yes | 监控数据的结束 UTC 时间，格式为 2011-07-11T11:07:00Z 或 2011-07-11T11:07:00.520Z |
| step | String | Yes | 数据间隔时间，有效值为：1m, 15m, 2h, 1d。(m 表示分钟，h 表示小时，d 表示天)，建议1m在请求6小时监控数据时使用，15m在请求一天数据时使用，2h在请求两周数据时使用，1d在请求一个月和6个月数据时使用 |
| metersN | String | Yes | 监控项，不同类型的资源支持的监控项不同：<br> <ul><li>如果资源是负载均衡器，meters 为 traffic时表示带宽监控，meters 为cpu和memory时表示节点的cpu和内存监控<li>如果资源是监听器，meters 目前只有 request</li><li>如果资源是后端服务，meters可以是request和healthy</li></ul>|
| obj | String | Yes | 操作对象，可选“lb”：负载均衡器，“lbl”：监听器，“lbb”：后端|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource_id | String | Yes | 监控资源ID, 可选主机ID或者公网IP |
| meter_set | Array | Yes | 监控数据集，可参见下面 *监控数据集说明* |
| total_count | Int | Yes | 监控项数目 |

监控数据集说明
*   负载均衡器的流量监控数据单位是 Bps (如果要换做 bps，记得每个值都乘以8)，每组数据都包括两个值 [进, 出]。
*   监听器在不同协议下的监控数据不同
    1. HTTP 协议时数据含义为：
        “请求数 | LB 4xx | LB 5xx | 总 backend 1xx | 总 backend 2xx | 总 backend 3xx | 总 backend 4xx | 总 backend 5xx | 最大延迟 | 最小延迟 | 平均延迟 | 最大并发连接数 | 平均并发连接数 | 并发连接数上限”  
        *警告 需要注意的是，请求数及响应数对应的数据值都是指在该段时间(即 step 指定的时间间隔)内的 累计数 。*
        1xx, 2xx, 3xx, 4xx, 5xx 表示响应的 HTTP status code.
    2. TCP 协议时数据含义为：
        “该段时间内连接个数 | 最大并发连接数 | 平均并发连接数 | 并发连接数上限”
*   后端服务在不同协议下的监控数据也不同
    1. HTTP 协议时数据含义为：
        “backend 1xx | backend 2xx | backend 3xx | backend 4xx | backend 5xx | 最大延迟 | 最小延迟 | 平均延迟”  
        *警告 响应数也是指在该段时间(即 step 指定的时间间隔)内的 累计数 。*
    2. TCP 协议时数据含义为：
        “该段时间内连接个数”

#### 请求实例

#### CURL
```shell
curl -XGET "http://api.51idc.com/v2/zone/ac2/monitor/loadbalancer/lbl-FE142D9?step=1m&start_time=2016-11-15T01:46:15.221Z&end_time=2016-11-15T07:46:15.221Z&metersN=request,healthy&obj=lbl"
```

#### 响应示例  当监听器的监听协议是 HTTP 时的监控数据

```json
{
  "resource_id": "lbl-FE142D9",
  "meter_set": [
    {
      "meter_id": "healthy",
      "data_set": []
    },
    {
      "meter_id": "request",
      "data_set": [
        {
          "timestamp": [
            1479195720,
            1479195780,
            1479195840,
            1479195900,
            1479195960
          ],
          "data_string": [
            "0|0|0|0|0|0|0|0|0|0|0|0|0|20000",
            "0|0|0|0|0|0|0|0|0|0|0|0|0|20000",
            "0|0|0|0|0|0|0|0|0|0|0|0|0|20000",
            "0|0|0|0|0|0|0|0|0|0|0|0|0|20000",
            "0|0|0|0|0|0|0|0|0|0|0|0|0|20000"
          ],
          "eip_id": "eip-ji6stb2l"
        }
      ]
    }
  ],
  "total_count": 2
}
```

## GET /v2/zone/{zone}/monitor/rdb/:resource_id

**获取指定数据库实例的监控信息。**

### 请求

#### 请求query参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource | String | Yes | 监控资源ID |
| start_time | String | Yes | 监控数据的起始 UTC 时间，格式为 2011-07-11T11:07:00Z 或 2011-07-11T11:07:00.520Z |
| end_time | String | Yes | 监控数据的结束 UTC 时间，格式为 2011-07-11T11:07:00Z 或 2011-07-11T11:07:00.520Z |
| step | String | Yes | 数据间隔时间，有效值为：1m, 15m, 2h, 1d。(m 表示分钟，h 表示小时，d 表示天)，建议1m在请求6小时监控数据时使用，15m在请求一天数据时使用，2h在请求两周数据时使用，1d在请求一个月和6个月数据时使用 |
| metersN | String | Yes | 监控项，数据库的监控项包括：<br> <ul><li>如果想获取主机监控，meters 可以为"cpu","memory","disk-us-volume","disk-iops-volume","disk-volume"<li>如果想监控数据库服务，meters 目前只有 status：MySQL 数据库基础状态数据，返回值是由”&#124;”分隔的多项状态值：</li><ul><li>Slow_queries: 慢查询次数</li><li>Opened_tables: 当前打开的数据库表数量</li><li>Select_scan: 全表扫描次数</li><li>Threads_connected: 当前连接线程数</li><li>Threads_running: 当前活跃连接线程数</li><li>Max_used_connections: 最大并发连接数</li><li>Innodb_buffer_pool_pages_free: InnoDB 缓冲池可用空间（单位：页）</li><li>Com_commit: 提交事务数</li><li>Com_rollback: 回滚事务数</li><li>Innodb_buffer_pool_reads: 穿透 InnoDB 缓冲池的查询数量</li><li>Innodb_buffer_pool_read_requests: 从 InnoDB 缓冲池返回的查询数量</li><li>Qcache_hits: 从查询缓存返回的查询数量</li><li>Qcache_inserts: 穿透查询缓存的查询数量</li><li>Threads_created: 已创建连接线程数</li><li>Connections: 全部连接数（包括连接失败的连接数量）</li><li>Questions: 查询数量</li><li>Seconds_Behind_Master: 从节点落后主节点的秒数</li></ul><li>“status”: PostgreSQL 数据库基础状态数据，返回值是由”&#124;”分隔的多项状态值：</li><ul><li>blks_read: 未命中中缓存的查询数量 &#124; blks_hit: 命中缓存的查询数量 &#124; connections: 当前连接数</li></ul></ul>|
| obj | String | Yes | 操作对象，填“rdbi”|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource_id | String | Yes | 监控资源ID, 可选主机ID或者公网IP |
| meter_set | Array | Yes | 监控数据集|
| total_count | Int | Yes | 监控项数目 |


#### 请求实例

#### CURL
```shell
主机监控
curl -XGET "http://dev.api.51idc.com/v2/zone/ac2/monitor/rdb/rmi-HVA1DB8?step=5m&start_time=2016-11-15T02:20:08.354Z&end_time=2016-11-15T08:20:08.354Z&metersN=cpu,memory,disk-us-volume,disk-iops-volume,disk-volume&obj=rdbi"
```

#### 响应示例  主机监控

```json
{
  "resource_id": "rmi-HVA1DB8",
  "meter_set": [
    {
      "meter_id": "disk-us-volume",
      "data_set": [
        {
          "timestamp": [
            1479198600
          ],
          "data_string": [
            "/data|2|177|9390"
          ]
        }
      ]
    },
    {
      "meter_id": "disk-iops-volume",
      "data_set": [
        {
          "timestamp": [
            1479198600
          ],
          "data_in": [
            12
          ],
          "data_out": [
            17
          ]
        }
      ]
    },
    {
      "meter_id": "memory",
      "data_set": [
        {
          "timestamp": [
            1479198600
          ],
          "data_in": [
            23
          ]
        }
      ]
    },
    {
      "meter_id": "cpu",
      "data_set": [
        {
          "timestamp": [
            1479198600
          ],
          "data_in": [
            64
          ]
        }
      ]
    },
    {
      "meter_id": "disk-volume",
      "data_set": [
        {
          "timestamp": [
            1479198600
          ],
          "data_in": [
            54776
          ],
          "data_out": [
            7710091
          ]
        }
      ]
    }
  ],
  "total_count": 5
}
```
#### CURL
```shell
主机监控
curl -XGET "http://dev.api.51idc.com/v2/zone/ac2/monitor/rdb/rmi-HVA1DB8?step=5m&start_time=2016-11-15T02:20:08.354Z&end_time=2016-11-15T08:20:08.354Z&metersN=status&obj=rdbi"
```

#### 响应示例  主机监控

```json
{
  "resource_id": "rmi-HVA1DB8",
  "meter_set": [
    {
      "meter_id": "status",
      "data_set": [
        {
          "timestamp": [
            1479198900
          ],
          "data_string": [
            "0|160|106|4|4|0|98013|477|0|0|0|0|0|5|710|1941|0"
          ],
          "role": "master",
          "rdb_instance_id": "rmi-k060ld50"
        }
      ]
    }
  ],
  "total_count": 1
}
```
