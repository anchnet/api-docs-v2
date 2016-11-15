# monitor

<!-- toc -->

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
| counter | String | Yes | 监控项 [<br>{<br>&nbsp;&nbsp;"cpu.busy": "CPU使用率",<br>&nbsp;&nbsp;"load.load1": "1分钟负载",<br>&nbsp;&nbsp;"load.load5": "5分钟负载",<br>&nbsp;&nbsp;"load.load15": "15分钟负载",<br>&nbsp;&nbsp;"mem.memused.percent": "内存使用率",<br>&nbsp;&nbsp;"net.if.in.bytes": "进方向流量",<br>&nbsp;&nbsp;"net.if.out.bytes": "出方向流量",<br>&nbsp;&nbsp;"disk.io.write_bytes": "IO写速率",<br>&nbsp;&nbsp;"disk.io.read_bytes": "IO读速率",<br>&nbsp;&nbsp;"ss.closed": "tcp.closed",<br>&nbsp;&nbsp;"ss.timewait": "tcp.timewait",<br>&nbsp;&nbsp;"ss.synrecv": "tcp.synrecv",<br>&nbsp;&nbsp;"ss.slabinfo.timewait": "tcp.slabinfo.timewait",<br>&nbsp;&nbsp;"ss.orphaned": "tcp.orphaned",<br>&nbsp;&nbsp;"ss.estab": "tcp.estab",<br> }<br>]|

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
## GET /v2/zone/{zone}/monitor/ins/:resource_id

**获取资源监控数据。支持的资源包括主机、公网 IP 和路由器， 选定不同类型资源，可获取的监控项不同。**
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
| metersN | String | Yes | 监控项，不同类型的资源支持的监控项不同：<br> <ul><li>若资源是主机，meters 可以是<br> <ul><li>“cpu”：主机 cpu 使用率</li><li>“memory”：主机内存使用率</li><li>“disk-os”, “disk-iops-os”, “disk-us-os”：主机系统盘吞吐量，IOPS，空间使用率</li><li>“disk-硬盘ID”, “disk-iops-硬盘ID”, “disk-us-硬盘ID”：与主机绑定的硬盘的吞吐量，IOPS，空间使用率</li><li>“if-网卡地址”：主机网卡流量</li></ul> <br>  </li><li>资源是公网IP，meters 有 “traffic”和“flow”</li><li>资源是路由器，meters 可以有 “vxnet-0” 和 “与路由器相连的私有网络ID”：带宽监控，也可以是“cpu”和“memory”：负载监控</li></ul>|
| obj | String | Yes | 操作对象，填“instance”|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource_id | String | Yes | 监控资源ID |
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
curl -XGET "http://api.51idc.com/v2/zone/ac2/monitor/ins/ins-3JJFO59?step=5m&start_time=2016-11-11T23:41:03.699Z&end_time=2016-11-12T05:41:03.699Z&metersN=cpu,disk-os,disk-iops-os,disk-us-os,if-52:54:3a:5e:c1:1e,memory&obj=instance"
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
