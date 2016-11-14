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
  "history": [
    {
      "endpoint": "hanjh_server_548",
      "counter": "mem.memfree",
      "dstype": "GAUGE",
      "step": 60,
      "Values": [
        {
          "timestamp": 1476783000,
          "value": 0
        },
        {
          "timestamp": 1476783300,
          "value": 0
        },
        {
          "timestamp": 1476783600,
          "value": 0
        },
        {
          "timestamp": 1476783900,
          "value": 0
        }
      ]
    },
    {
      "endpoint": "hanjh_server_548",
      "counter": "cpu.idle",
      "dstype": "GAUGE",
      "step": 60,
      "Values": [
        {
          "timestamp": 1476783000,
          "value": 0
        },
        {
          "timestamp": 1476783300,
          "value": 0
        },
        {
          "timestamp": 1476783600,
          "value": 0
        }
      ]
    }
  ],
  "total_count": 2
}
```
## GET /v2/monitor/instance

**获取资源监控数据。支持的资源包括主机、公网 IP 和路由器， 选定不同类型资源，可获取的监控项不同。**
> *主机的监控项包括: CPU 使用率，内存使用率，系统盘数据(吞吐量， IOPS 和使用率)， 主机连接私有网络的网卡流量，与主机绑定的各磁盘数据（吞吐量， IOPS 和使用率）。
>  _注解 其中内存使用率和磁盘使用率暂不支持 Windows ，以及 kernel 版本过低的 Linux_
> *公网 IP 资源可得到公网 “进/出” 的流量数据。
> *如果资源为路由器，可得到路由器在基础网络的流量数据，以及与路由器连接的私有网络的流量数据

### 请求

#### 请求body参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| start_time | Int | Yes | 监控数据开始时间戳 |
| end_time | Int | Yes | 监控数据结束时间戳 |
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
  "history": [
    {
      "endpoint": "hanjh_server_548",
      "counter": "mem.memfree",
      "dstype": "GAUGE",
      "step": 60,
      "Values": [
        {
          "timestamp": 1476783000,
          "value": 0
        },
        {
          "timestamp": 1476783300,
          "value": 0
        },
        {
          "timestamp": 1476783600,
          "value": 0
        },
        {
          "timestamp": 1476783900,
          "value": 0
        }
      ]
    },
    {
      "endpoint": "hanjh_server_548",
      "counter": "cpu.idle",
      "dstype": "GAUGE",
      "step": 60,
      "Values": [
        {
          "timestamp": 1476783000,
          "value": 0
        },
        {
          "timestamp": 1476783300,
          "value": 0
        },
        {
          "timestamp": 1476783600,
          "value": 0
        }
      ]
    }
  ],
  "total_count": 2
}
```
