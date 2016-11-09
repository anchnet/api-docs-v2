# IDC

<!-- toc -->

## GET /idc/devs

**获取设备列表**

*可根据标签ID，名称作为过滤条件，获取租用设备列表。如果不指定任何过滤条件，默认返回你所拥有的所有设备。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tags | String | No | 标签ID，逗号分隔 |
| search_word | String| No | 查询条件 |
| status | String| No | 状态,healthy对应运行中，unhealthy对应已断网 |
| type | String| No | 类型：hire对应租用列表，managed对应托管列表 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到租用设备总数 |
| dev | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"memo": "*String*",<br>&nbsp;&nbsp;"model": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"networkip": "*String*",<br>&nbsp;&nbsp;"tags": "*String*",<br>&nbsp;&nbsp;"dev_ip": "*Object[]*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/idc/dev"
```

#### 响应内容:

```js
{
    "dev": [
    {
      "id": "JH-TG-11387",
      "name": "just test",
      "memo": "描述",
      "model": "Dl360GS",
      "status": "正常",
      "networkip": "",
      "tags": [
        {
          "tag_id": "tag-SNM3AXO",
          "name": "tag-test",
          "color": "7"
        },
        {
          "tag_id": "tag-ZZZ20ZZ",
          "name": "idc",
          "color": "1"
        }
      ],
      "dev_ip": [
        {
          "addr": "114.80.200.79",
          "carrier_code": "PuN_CTC"
        }
      ]
    },
    "total_count": 1
} 
```
## PUT /idc/devs/:dev_id

**修改设备信息**

*修改租用和托管设备的设备信息*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| name | String | Yes | 设备名 |
| memo | String | No | 描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求
```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/idc/devs/NJ-TG-10032" --data '
{
    "name":"设备名字",
    "memo": "描述"
}'
```
#### 响应内容:

## GET /idc/devs/:dev_id

**获取设备详情**

*设备详情*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| type | String| No | 类型：hire对应租用列表，managed对应托管列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| dev | Object | Yes | <br>{<br>&nbsp;&nbsp;"dev_id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"memo": "*String*",<br>&nbsp;&nbsp;"model": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"networkip": "*String*"<br>&nbsp;&nbsp;"os": "*String*"<br>&nbsp;&nbsp;"up_time": "*String*"<br>&nbsp;&nbsp;"payment_cycle": "*Int*"<br>&nbsp;&nbsp;"payment_amount": "*double*"<br>&nbsp;&nbsp;"leases": "*Int*",<br>&nbsp;&nbsp;"tags": "*String*",<br>&nbsp;&nbsp;"dev_ip": "*Object[]*",<br> }<br> |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/idc/devs/JH-HK-1002"
```

#### 响应内容:

```js
{
    "id": "ins-D6MK7EV",
    "name": "名字",
    "memo": "描述",
    "model": "型号",
    "status": "状态",
    "networkip": "内网IP",
    "os": "操作系统",
    "up_time": "上架时间",
    "payment_cycle": 付款周期,
    "payment_amount": 月付额,
    "leases": 租赁时长,
    "tags": "tags",
    "dev_ip": {
        "addr": "addr",
        "port": "port",
        "bandwidth": 带宽,
        "private_line_id": "专线"
    }
}
```

## GET /idc/racks

**获取机柜列表**

*可根据标签ID，名称作为过滤条件，获取机柜列表。如果不指定任何过滤条件，默认返回你所拥有的所有机柜。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_ids | String[] | No | 标签ID |
| search_word | String| No | 查询条件 |
| data_center | String| No | 数据中心 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到机柜总数 |
| racks | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"rack_id": "*String*",<br>&nbsp;&nbsp;"data_center": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"actual_unit": "*Int*",<br>&nbsp;&nbsp;"power_max": "*int*"<br>&nbsp;&nbsp;"total_slot": "*int*"<br>&nbsp;&nbsp;"devs": "*Object[]*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/idc/racks"
```

#### 响应内容:
rack_id:机柜ID
data_center:数据中心
status:
actual_unit:剩余空间
power_max:标准电量
total_slot:插座数量
dev:{
    dev_id:设备ID
    name:设备名
}
```js
{
    "total_count": 1,
    "racks": [
        {
           "rack_id": "rack_id",
            "data_center": "data_center",
            "status": "status",
            "actual_unit": 3,
            "power_max": 3,
            "total_slot": 3,
            "devs": {
                "dev_id":"id",
                "name":"name"
            }
        }
    ]
} 
```

## GET /idc/ips

**获取IP列表**

*可根据标签ID，名称作为过滤条件，获取机柜列表。如果不指定任何过滤条件，默认返回你所拥有的所有IP。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_ids | String[] | No | 标签ID |
| search_word | String| No | 查询条件 |
| data_center | String| No | 数据中心 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到机柜总数 |
| ips | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"ip_addr": "*String*",<br>&nbsp;&nbsp;"data_center": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"network": "*String*",<br>&nbsp;&nbsp;"mask": "*String*"<br>&nbsp;&nbsp;"gateway": "*String*"<br>&nbsp;&nbsp;"carrier": "*String*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/idc/ips"
```

#### 响应内容:
ip_addr:IP地址
data_center:数据中心
status:
network:网络属性
mask:掩码
gateway:网关
carrier:线路

```js
{
    "total_count": 1,
    "ips": [
        {
           "ip_addr": "ip_addr",
            "data_center": "data_center",
            "status": "status",
            "network": "network",
            "mask": "mask",
            "gateway": "gateway",
            "carrier": "carrier"
        }
    ]
} 
```

## GET /idc/private_lines

**获取专线列表**

*可根据标签ID，名称作为过滤条件，获取机柜列表。如果不指定任何过滤条件，默认返回你所拥有的所有专线。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_ids | String[] | No | 标签ID |
| search_word | String| No | 查询条件 |
| data_center | String| No | 数据中心 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到机柜总数 |
| private_lines | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"private_line_id": "*String*",<br>&nbsp;&nbsp;"access_address_a": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"type": "*String*",<br>&nbsp;&nbsp;"band_width": "*int*"<br>&nbsp;&nbsp;"access_address_b": "*int*"<br>&nbsp;&nbsp;"devs": "*Object[]*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/idc/private_lines"
```

#### 响应内容:
private_line_id:专线id
access_address_a:接入点a
status:
type:专线类型
band_width:带宽
access_address_b:接入点b
devs:绑定资源id和名字
```js
{
    "total_count": 1,
    "private_lines": [
        {
           "private_line_id": "private_line_id",
            "access_address_a": "access_address_a",
            "status": "status",
            "type":"type",
            "band_width": 3,
            "access_address_b": "access_address_b",
            "devs": {
                "dev_id":"id",
                "name":"name"
            }
        }
    ]
} 
```

## POST /idc/private_line

**创建专线**

*创建专线。*

### 请求

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| type | String | No | 类型|
| band_width | Int| No | 带宽 |
| access_address_a | String| No | 数据中心 |
| access_address_b | String | No | 接入点B |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/idc/private_line"
```

#### 响应内容:

```js
{} 
```
## GET /agent/downloadlink

**获取监控器下载地址**


### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| dev_id | String| Yes | 设备ID |
| monitor_name | String| Yes | 监控器名字 |
| os_type | String| Yes | 操作系统类型（linux, windows） |
| os_bit | Int | Yes | 操作系统位数（32, 64） |
| agent_type | Int | Yes | 监控器部署方式（0:公网，1:内网）|
| gateway | String| No | 网关地址，当部署方式为内网时必须传 |
| ip | String| No | 服务器ip，为空时可不传，有多个时传一个 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| agent_addr | String| Yes | 采集器下载地址 |
| gateway_addr | String| No | gateway下载地址, 当部署方式为外网时返回空 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/agent/downloadlink?dev_id=INS-12&monitor_name=test&os_type=linux&os_bit=32&agent_type=0&ip=165.1.12.45"
```

#### 响应内容:

```js
{
    "agent_addr": "", 
    "gateway_addr": ""
} 
```
