
# GET /v2/zone/{zone}/identity

**检测当前登录用户身份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/identity" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/job/:id

**JOB 信息**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/job/:id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances

**新建主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/instances

**查询主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/instances" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/instances

**修改主机属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/instances" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances_product

**打包产品**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances_product" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances/start

**启动主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/start" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances/stop

**关闭主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/stop" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances/restart

**重启主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/restart" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances/reset

**重置主机至初始状态**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/reset" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/instances/resize

**修改主机配置**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/instances/resize" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/instances/:ins_id

**销毁主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/instances/:ins_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volumes

**创建磁盘**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/volumes

**获取磁盘列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/volumes" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/volumes/:vol_id

**删除磁盘**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/volumes/:vol_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/volumes

**修改磁盘属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/volumes" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volumes/resize

**批量调整磁盘大小**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/resize" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volumes/attach

**挂载磁盘**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/attach" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volumes/detach

**卸载磁盘**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volumes/detach" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/volume_snapshots

**查询磁盘备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/volume_snapshots" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volume_snapshots

**创建磁盘备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/volume_snapshots

**修改磁盘备份属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/volume_snapshots" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/volume_snapshots/:snapshot_id

**删除磁盘备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/volume_snapshots/:snapshot_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volume_snapshots/apply

**回滚到指定备份点**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/apply" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volume_snapshots/capture_instance

**将指定备份导出为映像**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/capture_instance" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/volume_snapshots/create_volume

**将指定备份导出为硬盘**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/volume_snapshots/create_volume" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/loadbalancers/listeners

**获取监听器列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/listeners" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/listeners/add

**创建监听器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/listeners/add" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/loadbalancers_listeners/:lb_listener_id

**删除监听器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/loadbalancers_listeners

**修改监听器属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/loadbalancers_listener_backends

**修改监听器后端属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/loadbalancers_listener_backends/:lb_listener_backends_id

**删除监听器后端**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_listener_backends/:lb_listener_backends_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers_listeners/:lb_listener_id/backends/add

**增加监听器后端**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_listeners/:lb_listener_id/backends/add" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/loadbalancers/listeners/backends

**获取监听器后端列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers/listeners/backends" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers_policy

**创建负载均衡器策略**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers_policy/:lb_ld_policy/apply

**应用负载均衡器策略**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/apply" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/loadbalancers_policy/:lb_ld_policy

**删除负载均衡器策略**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/loadbalancers_policy

**获取负载均衡器策略列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/loadbalancers_policy

**修改负载均衡器策略属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/loadbalancers_policy_rules/:lb_ld_policy_rules

**删除策略规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules/:lb_ld_policy_rules" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/loadbalancers_policy_rules

**修改策略规则属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy_rules" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers_policy/:lb_ld_policy/rules/add

**增加策略规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/:lb_ld_policy/rules/add" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/loadbalancers_policy/rules

**获取策略规则列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers_policy/rules" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/eips/dissociate

**从负载均衡器中解绑公网IP**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/eips/dissociate" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/eips/associate

**绑定公网IP到负载均衡器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/eips/associate" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/resize

**调整负载均衡器容量**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/resize" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/apply

**应用负载均衡器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/apply" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/stop

**关闭负载均衡器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/stop" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers/:lb_id/start

**启动负载均衡器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id/start" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/loadbalancers

**修改负载均衡器属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/loadbalancers" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/loadbalancers/:lb_id

**删除负载均衡器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/loadbalancers/:lb_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/loadbalancers

**获取负载均衡器列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/loadbalancers" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/loadbalancers

**创建负载均衡器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/loadbalancers" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/vxnets

**创建私有网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/vxnets" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/vxnets/:vxnet_id

**删除私有网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/vxnets/:vxnet_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/vxnets/join

**加入私有网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/vxnets/join" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/vxnets/leave

**离开私有网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/vxnets/leave" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/vxnets/:vxnet_id

**修改私有网络属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/vxnets/:vxnet_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/vxnets

**查询私有网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/vxnets" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/eips

**修改公网IP 属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/eips" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/eips/change_billing_mode

**改变公网IP 计费方式**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/change_billing_mode" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/eips/change_bandwidth

**改变公网IP 带宽**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/change_bandwidth" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/eips/associate

**绑定公网IP 到主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/associate" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/eips/dissociate

**从主机解绑公网IP**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips/dissociate" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/eips

**分配公网IP**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/eips" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/eips/:eip_id

**释放公网IP**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/eips/:eip_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/eips

**获取公网IP列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/eips" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/secruity_groups

**创建防火墙**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/secruity_groups

**获取防火墙列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_groups" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/secruity_groups/:sg_id

**删除防火墙 支持批量**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_groups/:sg_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/secruity_groups/apply_instances

**应用防火墙 支持多台主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups/apply_instances" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/secruity_groups/remove_instances

**移除防火墙 支持多台主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups/remove_instances" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/secruity_groups/:sg_id

**修改防火墙属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/secruity_groups/:sg_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/create_default_secruity_groups

**创建默认防火墙**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/create_default_secruity_groups" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/secruity_groups_snapshots

**创建防火墙备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/secruity_groups_snapshots

**获取防火墙备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/secruity_groups_snapshots/:snap_id

**删除防火墙备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_groups_snapshots/:snap_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}secruity_groups_snapshots/rollback

**回滚防火墙备份**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1secruity_groups_snapshots/rollback" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/secruity_group_rules

**获取防火墙规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/secruity_group_rules" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/secruity_group_rules

**添加防火墙规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/secruity_group_rules" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/secruity_group_rules/:rules_id

**删除防火墙规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/secruity_group_rules/:rules_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/secruity_group_rules/:rules_id

**修改防火墙属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/secruity_group_rules/:rules_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/keypairs

**获取秘钥列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/keypairs" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/keypairs

**创建秘钥**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/keypairs/:kp_id

**删除秘钥 支持批量**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/keypairs/attach

**秘钥加载到主机**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/attach" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/keypairs/detach

**秘钥从主机卸载**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/keypairs/detach" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/keypairs/:kp_id

**修改秘钥属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/keypairs/:kp_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router

**创建路由器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/routers/power_on

**启动路由器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/power_on" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/routers/power_off

**关闭路由器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/power_off" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/routers/update

**更新路由器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/routers/update" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/routers/:router_id

**删除路由器**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/routers/:router_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router/:router_id/join

**路由器加入网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/join" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router/:router_id/leave

**路由器离开网络**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/leave" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/router/:router_id

**修改路由器属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/router/:router_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router/:router_id/statics

**添加路由器规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/statics" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/router_static/:router_static_id

**修改路由器规则属性**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/router_static/:router_static_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}router_statics/:router_static_id

**删除路由器规则**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1router_statics/:router_static_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router_static/:router_static_id/entries

**添加路由器规则条目**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router_static/:router_static_id/entries" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# DELETE /v2/zone/{zone}/router_static_entries/:router_static_entry_id

**删除路由器规则条目**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XDELETE "http://api.51idc.com/v2/zone/ac1/router_static_entries/:router_static_entry_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# PUT /v2/zone/{zone}/router_static_entry/:router_static_entry_id

**修改路由器规则条目**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPUT "http://api.51idc.com/v2/zone/ac1/router_static_entry/:router_static_entry_id" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router/:router_id/bind_eip

**关联公网ip**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/bind_eip" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# POST /v2/zone/{zone}/router/:router_id/bind_security_group

**关联防火墙**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

### Body Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XPOST "http://api.51idc.com/v2/zone/ac1/router/:router_id/bind_security_group" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/routers

**查询路由器列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/routers" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/router_statics

**查询路由器规则列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/router_statics" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/router_static_entries

**查询路由器规则条目列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/router_static_entries" `

#### Example Response:

```js
{
    "key": "value"
} 
```



# GET /v2/zone/{zone}/router_vxnets

**查询路由器网络列表**

*详细描述*

## Request

### Request Parameters

|Parameter name | Type | Description | Required|
| -- | -- | -- | -- |
|-|-|-|-|

## Response

### Response Header

`NULL`

### Response Body Parameters

[Job Response](http://www.51idc.com)

OR

|Parameter name | Type | Description | Contained |
| -- | -- | -- | -- |
|-|-|-|-|

## Example

### Example Request

` curl -XGET "http://api.51idc.com/v2/zone/ac1/router_vxnets" `

#### Example Response:

```js
{
    "key": "value"
} 
```



