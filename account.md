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
| cus_type | String | Yes | 用户类型，企业对应FIRM，个人对应SELF |
| tel | String | No | 固定电话 |
| mobile | String | Yes | 手机 |
| verification_code | Int | Yes | 验证码 |

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
    "cus_type":"FIRM",
    "tel":"021-9621312",
    "mobile":"13312345864"
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
| cus_type | String | No | 用户类型,FIRM对应企业用户，SELF对应个人用户 |
| tel | String | No | 固定电话 |
| address | String | No | 地址 |
| postcode | String | No | 邮编 |
| fax | String | No | 传真 |
| mobile | String | No | 手机 |
| cred_type | String | No | 证件类型，身份证对应IDENTITY，<br>军官证对应MILITARY，<br>驾照对应DRIVER |
| credentials | String | No | 证件编号 |
| permit_number | String | No | 营业执照编号 |
| permit_addr | String | No | 营业执照图片地址 |
| organizationcode | String | No | 组织机构代码证编号 |
| organizationCode_addr | String | No | 组织机构代码证图片地址 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer"
```

#### 响应内容:

```js
{
    "cus_name": "51idc",
    "cus_type": "FIRM",
    "tel": "021-4648",
    "address": "呼兰西路",
    "postcode": "242200",
    "fax": "445646",
    "mobile": "134123456",
    "cred_type": "DRIVER",
    "credentials": "146548796454515614546",
    "permit_number": "123",
    "permit_addr": "http://wwww.51idc.com",
    "organizationcode": "456",
    "organizationCode_addr": "http://www.51idc.com",
    "authorization": "121"
}
```
## PUT /customer

**修改用户基本信息**

*修改用户的基本信息*


### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| post_field | String | No | 可选字段，"phone"修改客户手机，"auth"修改服务授权码 |
| tel | String | No | 固定电话 |
| address | String | No | 地址 |
| postcode | String | No | 邮编 |
| fax | String | No | 传真 |
| authorization | String | No | 授权码 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer" --data '
{
    "tel":"021-45612",
    "address":"宝山",
    "postcode":"201900",
    "fax":"021-45612"
}'
```

#### 响应内容:

```js
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
    "available": {
        "cus_name":"51idc"
    }
} 
```
## GET /customer/contacts

**获取用户联系人信息**

*获取用户联系人的基本信息*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| contacts | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"contact_id": "*String*",<br>&nbsp;&nbsp;"name": "*String*",<br>&nbsp;&nbsp;"sex": "*String*",<br>&nbsp;&nbsp;"tel": "*String*",<br>&nbsp;&nbsp;"mobile": "*String*",<br>&nbsp;&nbsp;"email": "*String*",<br>&nbsp;&nbsp;"con_type": "*String* STYPE or JTYPE",<br>&nbsp;&nbsp;"cred_type": "*String*",<br>&nbsp;&nbsp;"credentials": "*String*",<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer/contacts"
```

#### 响应内容:

```js
   {
   "contacts": [
      {
         "contact_id": "con_YZAKUZF",
         "name": "小张",
         "sex": "M",
         "tel": "021-25228622",
         "mobile": "13751247782",
         "email": "test@163.com",
         "con_type": "JTYPE",
         "cred_type": "IDENTITY",
         "credentials": "330104598502150915"
      },
      {
         "contact_id": "con_USBENSE",
         "name": "小李",
         "sex": "M",
         "tel": "",
         "mobile": "15721460942",
         "email": "test2@heheda.net",
         "con_type": "STYPE",
         "cred_type": "IDENTITY",
         "credentials": "728923198511293151"
      }
   ],
   "total_count": 2
}
 
```
## post /customer/contacts

**增加联系人**

*增加用户联系人*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| name | String | No | 姓名 |
| sex | String | No | 性别 |
| tel | String | No | 固定电话 |
| mobile | String | No | 手机 |
| email | String | No | 类型 |
| con_type | String | No | 联系人类型 |
| cred_type | String | No | 证件类型 |
| credentials | String | No | 证件号 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| contact_id | String | Yes | ID |
| name | String | No | 姓名 |
| sex | String | No | 性别 |
| tel | String | No | 固定电话 |
| mobile | String | No | 手机 |
| email | String | No | 类型 |
| con_type | String | No | 联系人类型 |
| cred_type | String | No | 证件类型 |
| credentials | String | No | 证件号 |

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/customer/contacts" --data '
{
     "name": "小李",
     "sex": "M",
     "tel": "",
     "mobile": "15721460942",
     "email": "test2@heheda.net",
     "con_type": "STYPE",
     "cred_type": "IDENTITY",
     "credentials": "728923198511293151"
}'
```

#### 响应内容:

```js
{
     "contact_id": "con_USBENSE",
     "name": "小李",
     "sex": "M",
     "tel": "",
     "mobile": "15721460942",
     "email": "test2@heheda.net",
     "con_type": "STYPE",
     "cred_type": "IDENTITY",
     "credentials": "728923198511293151"
}
```
 
## PUT /customer/contacts

**修改联系人信息**

*修改用户联系人信息*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| contact_id | String | Yes | ID |
| name | String | No | 姓名 |
| sex | String | No | 性别 |
| tel | String | No | 固定电话 |
| mobile | String | No | 手机 |
| email | String | No | 类型 |
| con_type | String | No | 联系人类型 |
| cred_type | String | No | 证件类型 |
| credentials | String | No | 证件号 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| contact_id | String | Yes | ID |
| name | String | No | 姓名 |
| sex | String | No | 性别 |
| tel | String | No | 固定电话 |
| mobile | String | No | 手机 |
| email | String | No | 类型 |
| con_type | String | No | 联系人类型 |
| cred_type | String | No | 证件类型 |
| credentials | String | No | 证件号 |

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer/contacts --data '
{
    "contact_id": "con_USBENSE",
    "name":"name",
    "sex":"F",
    "tel":"",
    "mobile":"",
    "email":"",
    "con_type":"",
    "cred_type":"",
    "credentials":""
}'
```

#### 响应内容:

```js
{
    "contact_id": "con_USBENSE",
    "name":"name",
    "sex":"F",
    "tel":"",
    "mobile":"",
    "email":"",
    "con_type":"",
    "cred_type":"",
    "credentials":""
} 
```

## DELETE /customer/contacts/:contact_ids

**删除联系人 支持批量**

*删除一个或多个用户的联系人*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| contact_ids | String[] | Yes | 联系人ID列表,逗号分割 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/customer/contacts/con_USEWFAB,con_OIHYDNV"
```

#### 响应内容:

```js
{
    "contact_ids": [
        "con_USEWFAB",
        "con_OIHYDNV"
    ]
}
```
## GET /customer/accountmanager

**获取客户经理信息**

*获取用户的客户经理基本信息*

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
| name | String | No | 客户经理名 |
| mobile | String | No | 手机 |
| email | String | No | 邮箱 |
| qq | String | No | QQ |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer/accountmanager"
```

#### 响应内容:

```js
{
    "name": "51idc",
    "mobile": "134123456"
    "email": "242200@test.com",
    "qq": "445646"
}
```
## GET /customer/accounts

**获取登录帐号**

*获取用户的所有登录帐号*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| login_id | String | No | 模糊查询字段 |
| status | String | No | 状态过滤，ACTIVITY 或 DISABLED 或 空 |
| offset | Int | No | 数据偏移量，默认为0 |
| limit | Int | No | 返回数据长度，默认为10，最大100 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| accounts | Object[] | Yes | [<br>{<br>&nbsp;&nbsp;"login_id": "*String*",<br>&nbsp;&nbsp;"account_type": "*String*",<br>&nbsp;&nbsp;"contact_name": "*String*",<br>&nbsp;&nbsp;"last_logintime": "*TimeStamp*",<br>&nbsp;&nbsp;"last_loginip": "*String*",<br>&nbsp;&nbsp;"status": "*String*"DISABLED or ACTIVITY<br>}<br>] |
| total_count | Int | Yes | - |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer/accounts"
```

#### 响应内容:

```js
{
   "accounts": [
      {
         "login_id": "test@51idc.com",
         "account_type": "admin",
         "contact_name": "小李",
         "last_logintime": "2013-08-30T05:13:32Z",
         "last_loginip": "1.1.1.1",
         "status": "ACTIVITY"
      },
      {
         "login_id": "test@51idc.com",
         "account_type": "sub",
         "contact_name": "小李",
         "last_logintime": "2013-08-30T05:13:32Z",
         "last_loginip": "1.1.1.1",
         "status": "ACTIVITY"
      }
   ],
   "total_count": 2
}
 
```
## post /customer/accounts

**增加新账户**

*增加新登录账户*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| login_id | String | Yes | 登录账户 |
| passwd | String | Yes | 密码 |
| account_type | String | Yes | 账户类型, admin对应主帐号,sub对应子帐号 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| login_id | string | Yes | 账户 |

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/customer/accounts" --data '
{
    "login_id":"",
    "passwd":"123abc",
    "account_type":"admin"
}'
```

#### 响应内容:

```js
{
    "login_id": ""
} 
```
## DELETE /customer/accounts/:account_ids

**删除登录账户 支持批量**

*删除一个或多个用户的登录账户*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| account_ids | Int[] | Yes | 账户ID列表 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

### 示例

#### 发送请求

```bash
$ curl -XDELETE "http://api.51idc.com/v2/zone/ac1/customer/accounts/:account_ids"
```

#### 响应内容:

```js
{
    "account_ids": []
}
```
## PUT /customer/accounts/:account_id/disabled

**禁用账户**

*修改用户登录账户状态*

### 请求

#### 请求 Body 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| reason | String | Yes | 理由 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| account_id | String | Yes | 登录Id |
| status | String | Yes | 状态 |

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer/accounts/test@51idc.com/disabled --data '
{
    "account_id": "test@51idc.com"
}'

```

#### 响应内容:

```js
{
    "account_id": "test@51idc.com",
    "status": "DISABLED"
} 
```
## PUT /customer/accounts/:account_id/undisabled

**解禁账户**

*修改用户登录账户状态*

### 请求

#### 请求 Body 参数
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| reason | String | Yes | 理由 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| account_id | String | Yes | 登录Id |
| status | String | Yes | 状态 |

**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer/accounts/test@51idc.com/undisabled --data '
{
    "account_id": "test@51idc.com"
}'
```

#### 响应内容:

```js
{
    "account_id": "test@51idc.com"
    "status": "ACTIVITY"
} 
```


## GET /customer/profession

**获取业务信息**

*获取用户的业务信息*

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
| industry_application | String | No | 行业应用 |
| main_business | String | No | 主营业务 |
| website | String | No | 用户网址 |

### 示例

#### 发送请求

```bash
$ curl -XGET "http://api.51idc.com/v2/zone/ac1/customer/profession"
```

#### 响应内容:

```js
{
    "industry_application": "",
    "main_business": "",
    "website": ""
}
```

## PUT /customer/profession

**修改业务信息**

*修改用户业务信息*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| industry_application | String | No | 行业应用 |
| main_business | String | No | 主营业务 |
| website | String | No | 用户网址 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer/profession --data '
{
    "industry_application":"",
    "main_business":"",
    "website":""
}'
```
## PUT /customer/account/passwd

**修改密码**

*修改登录密码*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| login_id | String | Yes | 帐号 |
| old_passwd | String | Yes | 原密码 |
| new_passwd | String | Yes | 新密码 |
| verify_type | String | Yes | 验证方式，phone对应手机，wechat对应微信 |
| cell_number | String | Yes | 手机号或微信号 |
| verify_code | String | Yes | 验证码 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer/account/passwd --data '
{
    "login_id":"",
    "old_passwd":"",
    "new_passwd":"",
    "verify_type":"",
    "cell_number":"",
    "verify_code":""
}'
```
## PUT /customer/account/phone

**绑定手机**

*绑定账户手机*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| mobile | String | Yes | 手机号 |
| verification_code | Int | Yes | 验证码 |
| action_type | Int | Yes | 动作，0表示绑定，1表示解除绑定 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息
**NONE**
### 示例

#### 发送请求

```bash
$ curl -XPUT "http://api.51idc.com/v2/zone/ac1/customer/account/passwd --data '
{
    "mobile":"",
    "verification_code":,
    "action_type":0
}'
```
## post /verification_code

**获取验证码**

*给手机发送验证码*

### 请求

#### 请求 Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| addition | String | Yes | 附加字段 |
| smsype | String | Yes | 验证类型，certify |
| mobile | String | Yes | 手机 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac1/join" --data '
{
    "addition":"123abc",
    "smstype":"certify",
    "mobile":"13312345864"
}'
```
