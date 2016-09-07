# 用户信息

<!-- toc -->

## post /join

**注册**

*注册成为云平台用户*

*可以选择注册成为个人用户和企业用户*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| cus_name | String | Yes | 用户名 |
| short_name | String| No | 昵称 |
| passwd | String | Yes | 密码 |
| cus_type | String | Yes | 用户类型，企业对应firm，个人对应self |
| tel | String | No | 固定电话 |
| mobile | String | Yes | 手机 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| cus_name | string | Yes | 用户名 |

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/join" --data '
{
    "cus_name":"51idc",
    "short_name":"idc",
    "passwd":"123abc",
    "cus_type":"firm",
    "tel":"021-9621312",
    "mobile":"13312345864",
}'
```

#### 响应内容:

```js
{
    "cus_name": "51idc"
} 
```


## GET /customer

**获取用户信息**

*获取用户的基本信息*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| cus_name | String | No | 用户名 |
| cus_type | String | No | 用户类型 |
| tel | String | No | 固定电话 |
| address | String | No | 地址 |
| postcode | String | No | 邮编 |
| fax | String | No | 传真 |
| mobile | String | No | 手机 |
| cred_type | String | No | 证件类型，身份证对应Identity，<br>军官证对应Military，<br>驾照对应Driver |
| credentials | String | No | 证件编号 |
| permit_number | String | No | 营业执照编号 |
| permit_addr | String | No | 营业执照图片地址 |
| organizationcode | String | No | 组织机构代码证编号 |
| organizationCode_adrr | String | No | 组织机构代码证图片地址 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer"
```

#### 响应内容:

```js
{
    "cus_name": "51idc",
    "cus_type": "firm",
    "tel": "021-4648",
    "address": "呼兰西路",
    "postcode": "242200",
    "fax": "445646",
    "mobile": "134123456",
    "cred_type": "Driver",
    "credentials": "146548796454515614546",
    "permit_number": "123",
    "permit_addr": "http://wwww.51idc.com",
    "organizationcode": "456",
    "organizationCode_adrr": "http://www.51idc.com"
}
```

## GET /customer/available:customer_name

**查询用户名是否可用**

*用户名唯一，注册时需要查询是否可用*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| cus_name | String | Yes | 用户名 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| available | String | Yes | 用户名 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer/available?cus_name=51idc"
```

#### 响应内容:

```js
{
    "available": "51idc"
} 
```

## PUT /customer

**修改用户信息**

*修改用户的基本信息*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| tel | String | No | 固定电话 |
| address | String | No | 联系地址 |
| postcode | String | No | 邮编 |
| fax | String | No | 传真 |
| mobile | String | No | 手机 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/tags/:tag_id" --data '
{
    "tag_id":"tag_1313677",
    "name":"name",
    "color":"color",
    "describe":""
}'
```

#### 响应内容:

```js
```
