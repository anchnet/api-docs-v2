# 标签

<!-- toc -->

## GET /tags

**获取标签列表**

*获取一个或多个标签*

*可根据标签ID，名称作为过滤条件，获取标签列表。如果不指定任何过滤条件，默认返回你所拥有的所有标签。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_ids | String[] | No | 标签ID |
| search_word | String| No | 查询条件 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_count | Int | Yes | 根据过滤条件得到的密钥总数 |
| tags | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"color": "*String*",<br>&nbsp;&nbsp;"describe": "*String*",<br>&nbsp;&nbsp;"resource_count": "*int*"<br>}<br>] |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/tags"
```

#### 响应内容:

```js
{
    "total_count": 1,
    "tags": [
        {
           "id": "ins-D6MK7EV",
            "name": "rsa",
            "color": "sss",
            "describe": "kp",
            "resource_count": 0,
            "create_at": "2016-07-21T09:48:08Z"
        }
    ]
} 
```


## POST /tags

**创建标签**

*创建标签，每对标签都可加载到任意资源。*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| name | String | Yes | 标签名称 |
| color | String | No | 颜色 |
| describe | String | No | 描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/tags" --data '
{
    "name":"tag",
    "color":"",
    "describe":"",
}'
```

#### 响应内容:

```js
{
    "tag_id": "kp-XDOOZDK"
}
```

## DELETE /tags/:tag_ids

**删除标签 支持批量**

*删除一个或多个你拥有的标签。*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_ids | String[] | Yes | 标签ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/tags/:tag_ids"
```

#### 响应内容:

```js
{
    "tag_ids": []
}
```


## PUT /tags/:tag_id

**修改标签**

*修改标签*

*一次只能修改一个标签*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_id | String | Yes | 标签ID列表 |
| name | String | NO | 标签名称 |
| color | String | No | 颜色 |
| describe | String | No | 描述 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/tags/:tag_id" --data '
{
    "tag_id":"tag_1313677",
    "name":"name",
    "color":"color",
    "describe":""
}'
```

#### 响应内容:

```js
{
  "tag_id":"tag_1313677"
}
```

## POST /tags/attach

**加载标签**

*将任意数量的标签加载到资源*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tag_ids | String[] | Yes | 密钥ID列表 |
| resources | Object[] | Yes | 资源列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/tags/attach" --data '
{
  "tag_ids":["tag-1313677"],
  "resources":[
               
                {
                    "resource_id":"ins-D6MK7EV",
                    "resource_type":"instance"
                },
                {
                    "resource_id":"lb-921B97F",
                    "resource_type":"loadbalancer"
                }
              ]
}'
```

#### 响应内容:

```js
{
      "tagi_ids":["tag-1313677"]
} 
```


## POST /tags/detach

**卸载标签**

*将任意数量的标签对从资源卸载*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tagi_ids | String[] | Yes | 标签ID列表 |
| resources | Object[] | Yes | 资源列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/tags/detach" --data '
{
  "tag_ids":["tag-1313677"],
  "resources":[
                {
                    "resource_id":"ins-D6MK7EV"
                },
                {
                    "resource_id":"lb-921B97F"
                }
            ]
}'
```

#### 响应内容:

```js
{
  "tag_ids":["tag-1313677"]
}
```
