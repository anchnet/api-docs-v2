# SSH 秘钥

## GET /keypairs

**获取秘钥列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| key_pairs | String[] | Yes | - |
| instance_id | String | Yes | - |
| encrypt_method | String | Yes | - |
| search_word | String | Yes | - |
| tags | String[] | Yes | - |
| verbose | Int | Yes | - |
| offset | Int | Yes | - |
| limit | Int | No | 默认值: 10<br> |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | - |
| keypairs | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"encrypt_method": "*String*",<br>&nbsp;&nbsp;"keypair_name": "*String*",<br>&nbsp;&nbsp;"instance_ids": "*String[]*",<br>&nbsp;&nbsp;"create_time": "*String*",<br>&nbsp;&nbsp;"keypair_id": "*String*",<br>&nbsp;&nbsp;"pub_key": "*String*",<br>&nbsp;&nbsp;"description": "*String*"<br>}<br>] |

### 示例

#### 发送请求

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/keypairs"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /keypairs

**创建秘钥**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypair_name | String | Yes | - |
| mode | String | Yes | - |
| encrypt_method | String | Yes | - |
| public_key | String | Yes | - |
| description | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/api-docs-v2/content/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## DELETE /keypairs/:kp_id

**删除秘钥 支持批量**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/api-docs-v2/content/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id"
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /keypairs/attach

**秘钥加载到主机**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | - |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/api-docs-v2/content/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/attach" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## POST /keypairs/detach

**秘钥从主机卸载**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypairs | String[] | Yes | - |
| instances | String[] | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/api-docs-v2/content/job.html)*

### 示例

#### 发送请求

```sh
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/detach" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```


## PUT /keypairs/:kp_id

**修改秘钥属性**

*详细描述*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| keypair | String | Yes | - |
| keypair_name | String | Yes | - |
| description | String | Yes | - |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```sh
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id" --data '
{
    "key": "value"
}'
```

#### 响应内容:

```js
{
    "key": "value"
} 
```

