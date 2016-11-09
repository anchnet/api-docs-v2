# API 秘钥

<!-- toc -->

## GET /v2/apikey

**获取秘钥列表**

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| search_word | String | Yes | 搜索内容 |
| offset | Int | Yes | 偏移量 |
| limit | Int | No | 默认值: 10 |
| ins_id| String| Yes | 资源 ID 筛选, 多个以英文半角 ',' 分割 |

### 服务端响应

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|ins_id|string|是|资源 ID|
|name|string|是|秘钥名称|
|description|sring|是|秘钥描述|
|access_id|string|是|密钥 ID|
|secret_key|string|是|密钥|
|status|string|是|状态 **enabled** 启用 **disabled** 禁用|
|create_time|string|是|创建时间|

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/apikey"
```

#### 响应内容:

```js
{
    "data": [
        {
            "ins_id": "api-BN9M5EB",
            "name": "测试Test",
            "description": "desc",
            "access_id": "acfP9YgZA3TSwlzi",
            "secret_key": "X9loQpTDQN8xxVWtm4ADWpK4IjOuZWv0",
            "status": "enabled",
            "create_time": "2016-09-26T02:58:47Z"
        }
    ],
    "total_count": 1
}
```


## POST /apikey

**创建APIKey**


### 请求

#### Body JSON 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| name | String | Yes | 名称 |
| description | String | No | 描述 |


### 服务端响应

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|ins_id|string|是|资源 ID|
|name|string|是|秘钥名称|
|description|sring|是|秘钥描述|
|access_id|string|是|密钥 ID|
|secret_key|string|是|密钥|
|status|string|是|状态 **enabled** 启用 **disabled** 禁用|
|create_time|string|是|创建时间|


### 示例
#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/apikey" --data '
{
    "name":"test api",
    "description":"test desc"
}'
```
#### 响应内容:

```js
 {
  "ins_id": "api-BN9M5EB",
  "name": "测试Test",
  "description": "desc",
  "access_id": "acfP9YgZA3TSwlzi",
  "secret_key": "X9loQpTDQN8xxVWtm4ADWpK4IjOuZWv0",
  "status": "enabled",
  "create_time": "2016-09-26T02:58:47Z"
}
```


## DELETE /apikey/:ins_id
**删除APIKey**

### 请求
#### URI 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| ins_id | String | Yes | 资源 ID |

### 服务端响应

#### 相应状态码
|状态吗 | 描述 |
| :-- | :-- |
|200|成功|
|404|APIKey 不存在|

#### Body 内容

_empty object_
`{}`


#### 响应示例

```
HTTP/1.1 200 OK
Date: Thu, 08 Sep 2016 05:37:16 GMT
Content-Type: application/json
Content-Length: 2

{}
```



## PUT /apikey

**修改APIKey**

### 请求

#### Body JSON 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|ins_id|String|Yes|资源 ID|
| name | String | No | 名称 |
| description | String | No | 描述 |
| status| string|No|状态 可选值：`enabled` `disabled`|


### 服务端响应

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|ins_id|string|是|资源 ID|
|name|string|是|秘钥名称|
|description|sring|是|秘钥描述|
|access_id|string|是|密钥 ID|
|secret_key|string|是|密钥|
|status|string|是|状态 **enabled** 启用 **disabled** 禁用|
|create_time|string|是|创建时间|

### 示例
#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/apikey" --data '
[
	{
		"ins_id":"api-8K047ZT", // Required
		"name":"tttt2",
		"description":"desc2",
		"status":"enabled"
	}	
]'
```

#### 响应内容:

```js
[
  {
    "ins_id": "api-8K047ZT",
    "name": "tttt2",
    "description": "desc2",
    "access_id": "acSdwCKCrR2OOOkh",
    "secret_key": "5xLhmxQDn9VBxPpaAsHc8nBtU5sWN8HR",
    "status": "enabled",
    "create_time": "2016-09-26T02:50:24Z"
  }
]
```


## GET /v2/download/apikey/:ins_id

**下载 AccessID 和 SecretKey**

`注: 新创建 10 分钟内下载有效，超过时间后仍可下载，但 SecretKey 会被星号 * 替换`

### 请求

#### 路由参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
|ins_id|String|Yes|资源 ID|


### 示例
#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/apikey"
```

#### 响应下载头:

```js

```


