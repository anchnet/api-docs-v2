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
| counter | String | Yes | 监控项 |

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
        },
        {
          "timestamp": 1476784200,
          "value": 0
        },
        {
          "timestamp": 1476784500,
          "value": 0
        },
        {
          "timestamp": 1476784800,
          "value": 0
        },
        {
          "timestamp": 1476785100,
          "value": 0
        },
        {
          "timestamp": 1476785400,
          "value": 0
        },
        {
          "timestamp": 1476785700,
          "value": 0
        },
        {
          "timestamp": 1476786000,
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
        },
        {
          "timestamp": 1476783900,
          "value": 0
        },
        {
          "timestamp": 1476784200,
          "value": 0
        },
        {
          "timestamp": 1476784500,
          "value": 0
        },
        {
          "timestamp": 1476784800,
          "value": 0
        },
        {
          "timestamp": 1476785100,
          "value": 0
        },
        {
          "timestamp": 1476785400,
          "value": 0
        },
        {
          "timestamp": 1476785700,
          "value": 0
        },
        {
          "timestamp": 1476786000,
          "value": 0
        }
      ]
    }
  ],
  "total_count": 2
}
```
