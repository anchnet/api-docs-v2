# 操作日志

## GET /v2/zone/{zone}/job/{job_id}

**查询 JOB 状态**

*详细描述*

### 服务端响应

#### 响应 Body 信息


|参数名 | 类型 | 必含 | 描述 |
| :-- | :-- | :-- | :-- |
| job_id | String | Yes | 任务 ID |
| id_prefix | String | Yes | 任务 ID 前缀 |
| action | String | Yes | 动作 |
| request_id | String | Yes | 请求唯一 ID |
| status | String | Yes | 任务状态 <br>**pending** 待处理 <br>**working** 处理中<br>**failed** 处理失败<br>**successful** 处成功<br>|
| create_time | String | Yes | 创建时间 |
| begin_time | String | Yes | 开始时间 |
| finished_time | String | Yes | 完成时间 |
| info | String | Yes | 错误信息 |
| extra | String | Yes | 附加字段 |

### 示例

```sh
$ curl -XGET "http://api.51idc.com/v2/zone/ac2/job/92961ef1-0760-4ac4-97fd-98c2d0604d8f"
```

#### 响应内容:

```json
{
  "job_id":"92961ef1-0760-4ac4-97fd-98c2d0604d8f",
  "id_prefix":"",
  "action":"RunInstances",
  "request_id":"22951ef1-0740-4ay4-97vd-98c2d0602d8f",
  "status":"pending",
  "create_time":"2016-06-23T08:23:25Z",
  "begin_time":"2016-06-23T08:24:25Z",
  "finished_time":"2016-06-23T08:28:25Z",
  "info":"",
  "extra":""
}
```