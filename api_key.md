# API 秘钥

<!-- toc -->

## GET /api_keys

**获取秘钥列表**

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| search_word | String | Yes | 名称/Tag |
| offset | Int | Yes | 偏移量 |
| limit | Int | No | 默认值: 10 |

### 服务端响应

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|ins_id|string|是|ID|
|name|string|是|秘钥名称|
|description|sring|是|秘钥描述|
|access_id|string|是|access_id|
|secret_key|string|是|secret_key|
|enabled|int|是|启用状态 **1** 启用 **0** 禁用|

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/api_keys"
```

#### 响应内容:

```js
{
    "data":[
        {
            "ins_id":"api-sk34h3k4",
            "name":"测试 KEY",
            "description":"测试描述",
            "access_id":"4h3k2h4k32hk4h3",
            "secret_key":"k23k4hk3j2h4kj",
            "enabled":1,
            "created_at":"2016-02-23T19:23:11Z"
        }
    ],
    "total_count":1
}
```


## POST /api_keys
**创建APIKey**







