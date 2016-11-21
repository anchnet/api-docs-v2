# 其他

<!-- toc -->

## POST /v2/zone/{zone}/lease

**资源恢复接口**

```
注意：
暂时仅支持 主机、磁盘、镜像 恢复
```

### 请求

#### 请求Form参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| resources | []String | Yes | 资源 ID  例如: `["ins-23h4j43", "vol-23k3jgg"]`|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

参考: *[Job 数据结构](/job.html)*

### 示例

#### 发送请求

```bash
$ curl -XPOST "http://api.51idc.com/v2/zone/ac2/lease" --data '
{
    "resources": ["ins-CIC3QEB"]
}'
```

#### 响应内容:

```js
{
  "job_id": "1bc0bdb3-cf10-4b6c-9e27-1e78492b9d25",
  "action": "Lease",
  "request_id": "30d327981cba6c21",
  "status": "pending",
  "created_time": "2016-10-26T09:46:21Z",
  "begin_time": "",
  "finished_time": "",
  "extra": "",
  "zone": "ac2",
  "resource_ids": []
}
```

## POST /v2/upload

**文件上传**

```
注意：
暂时仅支持图片格式；
Form 表单需要设置  enctype="multipart/form-data"；
暂不支持二进制流上传文件；
```

### 请求

#### 请求Form参数

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| attachments | String | Yes | Form 表单提交字段名称（支持批量上传）|

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| extension | String | Yes | 文件扩展名 (不含'.') |
| filename | String | Yes | 服务保存文件名 (用于提交给后端接口)|
| mime | String|Yes | 文件 Mime 类型，如：image/jpg|
| original | String | Yes | 上传时原始文件名 |
| size | Integer | Yes | 文件大小（单位字节） |
| url | String | Yes | 文件预览网络路径|

#### 请求实例

#### CURL
```shell
curl -XPOST "http://api.51idc.com/v2/upload" \
--cookie "GWSession=YfLN8pqWn1d89Ek15hnS8VbhwAWof9WDYju72ibISabf0wlTVea3uDRZV9oRvuty" \
-F "attachments=@/Users/eagle/Pictures/B172DD82-6DDE-4A9A-A23D-7C5D3C4E5381.png" \
-F "attachments=@/Users/eagle/Pictures/B172DD82-6DDE-4A9A-A23D-7C5D3C4E5382.png" \
-H "Content-Type: multipart/form-data"
```

#### form 表单
```html
<form method="post" action="http://aip.51idc.com/v2/upload" enctype="multipart/form-data">
         Please Select Image: <input type="file" name="attachments">  <!-- name must be attachments -->
         <buttom type="submit">Upload</buttom>
 </form>
```

#### 相应示例

```json
[
  {
    "extension": "jpg",
    "filename": "201610/20/2a1ef8f6-80c6-4e50-8d00-6fcacb652f73.jpg",
    "mime": "image/jpeg",
    "original": "B172DD82-6DDE-4A9A-A23D-7C5D3C4E5381.png",
    "size": 37880,
    "url": "http://cdn.domain.com/201610/20/2a1ef8f6-80c6-4e50-8d00-6fcacb652f73.jpg"
  },
  {
    "extension": "jpg",
    "filename": "201610/20/d7c3aa81-d151-4363-87e5-e2b3906864c2.jpg",
    "mime": "image/jpeg",
    "original": "B172DD82-6DDE-4A9A-A23D-7C5D3C4E5381.png",
    "size": 37880,
    "url": "http://cdn.domain.com/201610/20/d7c3aa81-d151-4363-87e5-e2b3906864c2.jpg"
  }
]
```
## GET /oplog

**获取操作日志列表**

*详细描述*

### 请求

#### Body 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| end_time | String | NO | 记录结束时间 |
| start_time | String | NO | 记录开始时间 |
| offset | Int | NO | 数据偏移量，默认为0 |
| limit | Int | NO | 默认值: 10|


### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| oplogs | Objects | Yes | 操作日志 |
| total_count | Int | Yes | 根据过滤条件得到的总数 |

### oplogs

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| action | String | Yes | 操作行文 |
| resource_id | String | Yes | 资源的id |
| result | String | Yes | 结果(success,fail) |
| message | String | Yes | 错误内容 |
| create_time | Double | Yes | 创建时间 |

## GET /rent_info/:order_number

**获取租赁信息**

*详细描述*

### 请求

#### Query 参数
| 参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_no | String | Yes | 订单编号 |

### 服务端响应

#### 响应头信息

`NULL`

#### 响应 Body 信息

|参数名 | 类型 | 是否必选 | 描述 |
| :-- | :-- | :-- | :-- |
| order_no | String | Yes | 订单编号 |
| price | Double | Yes | 订单价格 |
| payment_type | String | Yes | 支付方式 |
| payment_month | Int | Yes | 支付月数 |
| create_time | String | Yes | 开始时间 |
| end_time | String | Yes | 结束时间 |



### 同步 Action 翻译
| code | means |
| :-- | :-- |
| DeleteLoadBalancerListeners | 删除负载均衡器监听器 |
| AddLoadBalancerListeners | 创建负载均衡器监听器 |
| ModifyLoadBalancerListenerAttributes | 修改负载均衡器监听器属性 |
| ModifyLoadBalancerPolicyAttributes | 修改负载均衡器策略 |
| DeleteLoadBalancerPolicies | 删除负载均衡器策略 |
| AddLoadBalancerBackends | 增加负载均衡器后端 |
| DeleteLoadBalancerBackends | 删除负载均衡器后端 |
| ModifyLoadBalancerBackendAttributes | 修改负载均衡器后端属性 |
| CreateServerCertificate | 创建服务器证书 |
| ModifyServerCertificateAttributes | 修改服务证书属性 |
| DeleteServerCertificates | 删除服务器证书 |
| AddLoadBalancerPolicyRules | 增加负载均衡器策略规则 |
| ModifyLoadBalancerPolicyRuleAttributes | 修改负载均衡器策略规则属性 |
| DeleteLoadBalancerPolicyRules | 删除负载均衡器策略规则 |
| ModifyLoadBalancerAttributes | 修改负载均衡器属性 |
| CreateLoadBalancerPolicy | 创建负载均衡器策略 |
| ModifyEipAttributes | 修改公网IP属性 |
| RevokeImageFromUsers | 取消共享镜像 |
| GrantImageToUsers | 共享镜像给其他用户 |
| ModifyImageAttributes | 修改镜像属性 |
| modifyRouterAttributes | 修改路由器属性 |
| AddRouterStatics | 增加路由器规则 |
| ModifyRouterStaticAttributes | 修改路由器规则属性 |
| DeleteRouterStatics | 删除路由器规则 |
| AddRouterStaticEntries | 增加路由器规则条目 |
| DeleteRouterStaticEntries | 删除路由器规则条目 |
| ModifyRouterStaticEntries | 修改路由器规则条目 |
| CreateVxnet | 创建私网 |
| ModifyVxnetAttributes | 修改私网属性 |
| CreateWorkSheet | 创建工单 |
| ModifyVolumeAttributes| 修改硬盘属性 |
| ModifySnapshotAttributes| 修改备份属性 |


