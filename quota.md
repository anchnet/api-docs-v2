# 操作日志

<!-- toc -->

## GET /v2/zone/{zone}/quota_left

**查询 JOB 状态**

### 服务端响应

#### 响应 Body 信息

|参数名 | 类型 | 必含 | 描述 |
| :-- | :-- | :-- | :-- |
| type | String | Yes | 配额类型 |
| quantity |  Integer | Yes | 总配额数 |
| left |  Integer | Yes | 剩余配额数 |
| name | String | Yes | 配额信息名称 |

### 示例

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac2/quota_left"
```

#### 响应内容:

```json
[
    {
        "type": "instance",
        "quantity": 15,
        "left": 12,
        "name": "VM"
    },
    {
        "type": "rdb",
        "quantity": 15,
        "left": 12,
        "name": "RDB"
    }
]
```

## GET /v2/zone/{zone}/apply_upgrade_quota

**申请增加配额**

### 请求

#### 请求 Body 信息

|参数名 | 类型 | 必含 | 描述 |
| :-- | :-- | :-- | :-- |
| zone | String | Yes | 区域 |
| reason |  String | Yes | 理由（最大1024字符） |
| detail |  Map<String, Integer> | Yes | 申请配额详情 |

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

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac2/apply_upgrade_quota"  --data '
{
  "zone":"ac1",
  "reason":"业务扩充",
  "detail":{
      "instance":150,
      "volume":10000,
      "rdb":50
  }
}
```

#### 响应内容:

```
HTTP/1.1 200 OK
Date: Thu, 08 Sep 2016 05:37:16 GMT
Content-Type: application/json
Content-Length: 2

{}
```
