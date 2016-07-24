# 操作日志

## GET /v2/zone/{zone}/job/{job_id}

**查询 JOB 状态**

*详细描述*

### 请求

#### QueryString 参数
`无`

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