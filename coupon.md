# API 秘钥

<!-- toc -->

## GET /v2/coupon

**获取代金券列表**

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| limit | Integer | No | 每页条数 |
| offset |  Integer | No | 偏移量 |
| code | String | No | 代金券号码 |
| order_number| String| No | 订单号|
| type_id | Integer | No | 代金券类型|
| is_used| Integer | No | 是否已使用 可选值 `1` 已使用  `0` 未使用  `-1` 已过期|
| zone_scope| String | No | 区域筛选 例如 `ac1` `ac2` |
| service_scope| String | No | 服务范围 <br>instance: 创建主机 <br>bandwidth: 新建带宽 <br>ops: 运维服务 <br>cdn: 开通 CDN <br>rds: 新建RDS <br>security_scan: 开通安全扫描服务  |

### 服务端响应

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|code|string|是|代金券编号 (16位字符)|
|name|string|是|名称|
|description|sring|是|描述|
|begin_time|string|是|开始时间|
|end_time|string|否|结束时间 `NUll` 空值表示长期有效|
|created_time|string|是|创建时间|
|discount|double|是| 折扣金额|
|service_scope|map<string, bool>|是|适用业务范围 |
|zone_scope|map<string, bool>|是|适用区域范围|

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/coupon"
```

#### 响应内容:

```js
{
    "data": [
        {
            "code": "34k53h4k5h43h459",
            "name": "新用户大礼包",
            "description": "仅限新注册用户",
            "begin_time": "2016-09-11T12:01:23Z",
            "end_time": "2017-09-11T12:01:23Z",
            "created_time":"2016-09-11T12:01:23Z",
            "discount":20.1
            "status": "enabled",
            "service_scope": {
              "INSTANCE":true,
              "BANDWIDTH":false,
              "CDN"：true,
            },
            "zone_scope":{
              "ac1":true,
              "ac2":false
            }
        }
    ],
    "total_count": 1
}
```


## POST /coupon/:coupon_code/bind

**激活/绑定 代金券**


### 请求

#### URI 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| coupon_code | String | Yes | 代金券号码（16位字符） |

### 服务端响应

#### 相应状态码
|状态吗 | 描述 |
| :-- | :-- |
|200|成功|
|404|APIKey 不存在|

#### Body 内容

_empty object_
`{}`

### 示例
#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/coupon/abcedfghijklmnop/bind"
```
#### 响应内容:


```
HTTP/1.1 200 OK
Date: Thu, 08 Sep 2016 05:37:16 GMT
Content-Type: application/json
Content-Length: 2

{}
```



