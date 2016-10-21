# IDC

<!-- toc -->

## GET /idc/dev

**获取设备列表**

*可根据标签ID，名称作为过滤条件，获取租用设备列表。如果不指定任何过滤条件，默认返回你所拥有的所有设备。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag | String | No | 标签ID |
| search_word | String| No | 查询条件 |
| status | String| No | 状态 |
| type | String| No | 类型 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到租用设备总数 |
| dev | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"model": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"networkip": "*String*"<br>&nbsp;&nbsp;"dev_ip": "*Object[]*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/idc/dev"
```

#### 响应内容:

```js
{
    "total_count": 1,
    "dev": [
        {
           "id": "ins-D6MK7EV",
            "name": "rsa",
            "model": "model",
            "status": "status",
            "networkip": "networkip",
            "dev_ip": {
                "addr":"addr",
                "carrier_code":"carrier_code"
            }
        }
    ]
} 
```


## GET /idc/dev_dettails

**获取设备详情**

*设备详情*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| dev_id | String | No | 设备ID |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| dev | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"dev_id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"model": "*String*",<br>&nbsp;&nbsp;"status": "*String*",<br>&nbsp;&nbsp;"networkip": "*String*"<br>&nbsp;&nbsp;"os": "*String*"<br>&nbsp;&nbsp;"up_time": "*String*"<br>&nbsp;&nbsp;"payment_cycle": "*Int*"<br>&nbsp;&nbsp;"payment_amount": "*double*"<br>&nbsp;&nbsp;"leases": "*Int*",<br>&nbsp;&nbsp;"tags": "*String*",<br>&nbsp;&nbsp;"dev_ip": "*Object[]*",<br> }<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/idc/dev_dettails"
```

#### 响应内容:

```js
{
    "id": "ins-D6MK7EV",
    "name": "rsa",
    "model": "model",
    "status": "status",
    "networkip": "networkip",
    "os": "os",
    "up_time": "up_time",
    "payment_cycle": 3,
    "payment_amount": 4,
    "leases": 5,
    "tags": "tags",
    "dev_ip": {
        "addr": "addr",
        "port": "port",
        "bandwidth": 5,
        "private_line_id": "private_line_id"
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
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/idc/racks"
```

#### 响应内容:

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
                "id":"id",
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
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/idc/ips"
```

#### 响应内容:

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
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/idc/private_lines"
```

#### 响应内容:

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
                "id":"id",
                "name":"name"
            }
        }
    ]
} 
```s

## Post /idc/private_line

**创建专线**

*创建专线。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| type | String | No | 类型|
| band_width | Int| No | 带宽 |
| access_address_a | String| No | 数据中心 |
| access_address_b | Int | No | 接入点B |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/idc/private_line"
```

#### 响应内容:

```js
{} 
```s