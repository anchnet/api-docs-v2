# 订单
## GET /orders

**获取订单列表**

*详细描述*

### 请求

#### Body 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| end_time | String | NO | 订单结束时间
| start_time | String | NO | 订单开始时间 |
| order_type | String | NO | 订单类型 ADDNEW(新增) RENEW(续约) |
| search_word | String | NO | 搜索关键词，支持订单编号，名称 |
| resource_type | String | NO | 资源的类型 CLOUD(云资源) IDC(物理架构) |
| offset | Int | NO | 数据偏移量，默认为0 |
| limit | Int | NO | 默认值: 10|
| account_type | String | NO | 账户类型 MAIN(主账号) BUSINESS（商务）TECHNOLOGY(技术) CHILD（子账号） |
| order_state | String | NO | 订单状态 PREPAID（已支付）NOTPAY（未支付）SUSPEND(已终止) EXPIREING(即将到期) |

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
| pay_way | String | Yes | PREPAY（包年包月）POSTPAY（按需） |
| product_name | String | Yes | 产品名称 |
| order_state | String | Yes | 订单状态 |
| create_time | String | Yes | 创建时间 |
| price | double | Yes | 价格 |
| price_details | Object[] | Yes | 价格详情 |

### price_details
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| details_name | String | Yes | 资源名称 |
| details_price | double | Yes | 资源单价 |

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

**获取订单列表**

*详细描述*

### 请求

#### QueryString 参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| eorder_number| String | Yes | 订单编号 |

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
| order_number | String | Yes | 订单编号 |
| delivery_time | String | Yes | 订单开通日期  |
| expiration_time | String | Yes | 订单截止日期 |
| cus_manager_name | String | Yes | 客户经理 |
| cus_name | String | Yes | 用户名 |
| create_time | String | Yes | 创建时间 |

### order_pay_info
|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_sum | double | Yes | 订单总额 |
| pay_cycle | int | Yes | 付款周期 |
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
| pay_way | String | No | 购买方式 |
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
