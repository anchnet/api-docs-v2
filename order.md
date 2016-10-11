# 订单

<!-- toc -->
## GET /resource_type

**获取资源类型列表**

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/event_type"

```

#### 响应内容:

```js

{

 "key": "value"

}

```


## GET /order_type

**获取订单类型列表**

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/event_type"

```

#### 响应内容:

```js

{

 "key": "value"

}

```


## GET /order_state

**获取订单状态列表**

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/event_type"

```

#### 响应内容:

```js

{

 "key": "value"

}

```




## GET /orders

**获取订单列表**

*详细描述*

### 请求

#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| end_time | String | NO | 订单结束时间
| start_time | String | NO | 订单开始时间 |
| order_type | String | NO | 订单类型  |
| search_word | String | NO | 搜索关键词，支持订单编号，名称 |
| resource_type | String | NO | 资源的类型 |
| offset | Int | NO | 数据偏移量，默认为0 |
| limit | Int | NO | 默认值: 10|
| account_type | String | NO | 账户类型 admin (主账号) sub（子账号） |
| order_state | String | NO | 订单状态 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| orders | Objects | Yes | 订单列表 |
| total_count | Int | Yes | 根据过滤条件得到的总数 |

### Order

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_name | String | Yes | 订单名称 |
| order_number | Int | Yes | 订单编号 |
| resource_type | String | Yes | 资源的类型 |
| account_type| String | Yes | 账户类型 admin(主账号) sub（子账号） |
| pay_way | String | Yes | 计费方式 HOUR(小时) MONTH(月) QUARTER(季度) HALF_YEAR(半年) YEAR(年) |
| product_name | String | Yes | 产品名称 |
| order_state | String | Yes | 订单状态 |
| create_time | String | Yes | 创建时间 |
| price | double | Yes | 价格 |
| is_self | boolean | Yes | 是否是账号本身(yes,no) |
| seq | int | Yes | 当前期次 |
| seq_count | int | Yes | 总期次 |



### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/zone/ac1/orders"

```

#### 响应内容:

```js

{

 "key": "value"

}

```



## GET /order_details/:order_number

**获取订单详情**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_number| String | Yes | 订单编号 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_summary | Object | Yes | 订单摘要 |
| order_pay_info | Object | Yes | 订单付款信息 |
| order_details | Object[] | Yes | 订单详情 |
| change_config | Object[] | No | 订单配置变更信息 |

### order_summary
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_state | String | Yes | 订单状态 |
| order_no | String | Yes | 订单编号 |
| delivery_time | String | Yes | 订单开通日期  |
| expiration_time | String | Yes | 订单截止日期 |
| cus_manager_name | String | Yes | 客户经理 |
| cus_name | String | Yes | 用户名 |
| create_time | String | Yes | 创建时间 |

### order_pay_info
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_sum | double | Yes | 订单总额 |
| pay_cycle | int | Yes | 付款周期 demand(周期付款) once (一次付款) |
| pay_time | String | Yes | 付款时间 |
| comment | String | Yes | 备注 |
| first_pay_sum | double | No | 首次付款金额 |
| once_pay_sum | double | No | 一次付款金额 |
| pay_way | String | Yes | 付款方式 |
| remain_count | int | No | 剩余次数 |

### order_details
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| name | String | Yes | 产品名称 |
| type | String | Yes | 产品类型 |
| zone | String | Yes | 地区 |
| count | int | Yes | 数量 |
| pay_way | String | No | 购买方式 HOUR(小时) MONTH(月) QUARTER(季度) HALF_YEAR(半年) YEAR(年)|
| duration | int | No | 购买时长 |
| price | String | Yes | 产品价格 |
| product_details | Object[] | Yes | 产品详情 |

### product_details
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| detail_name | String | Yes | 产品名称 |
| detail_type | String | Yes | 产品类型 |

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/zone/ac1/orders"

```

#### 响应内容:

```js

{

 "key": "value"

}

```

## GET /bills

**获取账单列表**

*详细描述*

### 请求

#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| end_time | String | NO | 账单结束时间 |
| start_time | String | NO | 账单开始时间 |
| state | String | NO | 账单状态 |
| search_word | String | NO | 搜索关键词，支持账单编号，名称 |
| offset | Int | NO | 数据偏移量，默认为0 |
| limit | Int | NO | 默认值: 10|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bills | Objects | Yes | 账单列表 |
| total_count | Int | Yes | 根据过滤条件取得总数 |
| current_amount_count | Double | Yes | 当前页账单金额 |
| amount_count | Double | Yes | 当前状态总账单金额 |


### bills
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bill_no | String | Yes | 账单编号 |
| order_no | double | Yes | 订单编号 |
| start_time | double | Yes | 开始时间 |
| end_time | double | Yes | 结束时间 |
| seq | double | Yes | 当前期数 |
| seq_count | double | Yes | 分期总数 |
| state | double | Yes | 账单状态 |
| bill_amount | double | Yes | 账单金额 |

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/zone/ac1/bills"

```

#### 响应内容:

```js

{

 "key": "value"

}

```


## GET /bill/:bill_number

**获取账单详情**

*详细描述*

### 请求

#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bill_number | String | Yes | 账单编号 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| bill_amount | Double | Yes | 账单金额 |
| pay_statu | String | Yes | 支付状态 |
| once_amount | Double | Yes | 一次金额 |
| cycle_amount | Double | Yes | 周期金额 |
| start_time | String | Yes | 开始时间 |
| seq | Double | Int | 当前期数 |
| seq_count | Int | Yes | 总期数 |
| last_pay_time | String | Yes | 最后付款时间 |
| datacenter | String | Yes | 数据中心名称 |
| order_number | String | Yes | 订单编号 |
| order_title | String | Yes | 订单标题 |
| order_start_time | String | Yes | 订单开始时间 |
| order_end_time | String | Yes | 订单结束时间 |
| cus_name | String | Yes | 客户名称 |
| cus_manage_name | String | Yes | 客户经理名称 |
| cus_manage_email | String | Yes | 客户经理邮箱 |


### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/zone/ac1/bill/:bill_number"

```

#### 响应内容:

```js

{

 "key": "value"

}

```

## GET /records

**获取消费记录列表**

*详细描述*

### 请求

#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| end_time | String | NO | 记录结束时间 |
| start_time | String | NO | 记录开始时间 |
| offset | Int | NO | 数据偏移量，默认为0 |
| limit | Int | NO | 默认值: 10|
| datacenter | String | NO | 数据中心 |
| account_name | list | NO | 账号名称 逗号分隔 |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| consume_records | Objects | Yes | 消费记录 |
| total_count | Int | Yes | 根据过滤条件得到的总数 |

### consume_records

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_no | String | Yes | 订单编号 |
| resource_type | String | Yes | 资源的类型(cloud,或者其他) |
| account_name | String | Yes | 用户名 |
| datacenter | String | Yes | 数据中心 |
| consume_amount | Double | Yes | 消费金额 |
| consume_way | String | Yes | 消费方式 POSTPAY(按需)PREPAY(包年包月)  |
| consume_time | String | Yes | 消费时间 |
| is_self | boolean | Yes | 是否账号本身 |

### datacenter
| code | means |
| :-- | :-- |
| BA | 北艾 |
| HDYQ | 华东一区 | 
| HKST | 香港二期 |
| HL | 呼兰 | 
| JH | 金海 | 
| JQ | 金桥 | 
| KS | 昆山 | 
| LG | 长沙 | 
| LUGU | 鲁谷 | 
| NH | 南汇 |
| NJ | 怒江 |
| USA | 美国 |
| WX | 无锡 | 
| YTYQ | 亚太一区 | 

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/zone/ac1/records"

```

#### 响应内容:

```js

{

 "key": "value"

}

```

## GET /record/:order_number

**获取消费记录列表**

*详细描述*

### 请求

#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_number | String | Yes | 订单编号 |


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_no | String | Yes | 订单编号 |
| consumer_way | String | Yes | 消费方式  POSTPAY(按需)PREPAY(包年包月) |
| datacenter | String | Yes | 数据中心 |
| account_name | String | Yes | 用户名 |
| consumer_amount | Double | Yes | 消费金额 |
| details | Object | Yes | 详情 |

### details
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| id | String | Yes | 资源id |
| name | String | Yes | 资源名称 |
| type | String | Yes | 资源类型 |
| time | String | Yes | 创建时间 |
| amount | String | Yes | 消费金额 |
| start_time| String | Yes | 开始时间 |
| end_time | String | Yes | 结束时间 |

### datacenter
| code | means |
| :-- | :-- |
| BA | 北艾 |
| HDYQ | 华东一区 | 
| HKST | 香港二期 |
| HL | 呼兰 | 
| JH | 金海 | 
| JQ | 金桥 | 
| KS | 昆山 | 
| LG | 长沙 | 
| LUGU | 鲁谷 | 
| NH | 南汇 |
| NJ | 怒江 |
| USA | 美国 |
| WX | 无锡 | 
| YTYQ | 亚太一区 |

### type
| code | means |
| :-- | :-- |
| instance | 主机 |
| router | 路由器 |
| eip | 公网IP |
| volume | 磁盘 |
| image | 镜像 |
| loadbalancer | 负载均衡器 |

### 示例

#### 发送请求

```bash

$ curl -XGET "http://api.51idc.com/v2/zone/ac1/record/:order_name"

```

#### 响应内容:

```js

{

 "key": "value"

}

```

## POST /price
**获取价格**
*详细描述*
### 请求
#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| price_item | Object[] | Yes | 价格条目 |

#### price_item
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resource_kind | String | Yes | 资源种类 |
| resource_type | String | No | 资源类型 |
| size | Int | Yes | 大小 |
| amount | Int | Yes | 数量 |
| payment_type | String | Yes | 计费类型 (POSTPAY:按需，PREPAY:包月)|
| payment_months | Int | No | 周期 (包月需填) |




### 服务端响应
#### 响应头信息
`NULL`
#### 响应 Body 信息
| 类型 | 描述 |
| :-- | :-- |
| double | 价格|


### 服务端响应
#### 响应头信息
`NULL`
#### 响应 Body 信息
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| total_price |  double | Yes  | 价格|

## GET /recharge_record
**获取充值记录**
*描述*
###请求
#### Path 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| offset | Integer | No | |
| limit | Integer | No | |
| start_time | String | Yes | 起始时间  |
| end_time | String | Yes | 截止时间  |

### 服务端响应
#### 响应头信息
`NULL`
#### 响应 Body 信息


### datacenter
| code | means |
| :-- | :-- |
| BA | 北艾 |
| HDYQ | 华东一区 |
| HKST | 香港二期 |
| HL | 呼兰 |
| JH | 金海 |
| JQ | 金桥 |
| KS | 昆山 |
| LG | 长沙 |
| LUGU | 鲁谷 |
| NH | 南汇 |
| NJ | 怒江 |
| USA | 美国 |
| WX | 无锡 |
| YTYQ | 亚太一区 |

### config_kind
| code | means | unit |
| :-- | :-- | :-- |
| volume | 硬盘 | 硬盘大小 单位Gb |
| eip | 公网ip | 公网ip带宽 单位Mb |
| router | 路由器 | 最大连接数 单位个 |
| loadbalancer | 负载均衡器 | 最大连接数 单位个  |
| snapshot | 备份 | 大小 单位Gb |
| image | 镜像 | 大小 单位Gb |
| cpu | cpu | 核心数 单位个 |
| memory | 内存 | 内存大小 单位Mb |