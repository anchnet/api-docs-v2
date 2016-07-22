# DescribeInstances


获取一个或多个主机

可根据主机ID, 状态, 主机名称, 映像ID 作过滤条件, 来获取主机列表。 如果不指定任何过滤条件, 默认返回你所拥有的所有主机。

### Request Parameters
|Parameter  |     name |   Type  |  Description Required|
| -- | -- | -- | -- |
|instances.n     | String  | 主机ID    |No|
|image_id.n      | String  | 一个或多个映像ID  | No|
|instance_type.n | String  | 主机配置类型  |No|
|instance_class  | Integer | 主机性能类型: 性能型:0 ,超高性能型:1  |No|
|status.n        | String  | 主机状态: pending, running, stopped, suspended, terminated, ceased  |No|
|search_word     | String  | 搜索关键词, 支持主机ID, 主机名称 |No|
|tags.n          | String  | 按照标签ID过滤, 只返回已绑定某标签的资源  |No|
|verbose         | Integer | 是否返回冗长的信息, 若为1, 则返回主机相关其他资源的详细数据。  | No|
|offset          | Integer | 数据偏移量, 默认为0 |No|
|limit           | Integer | 返回数据长度，默认为20，最大100  |No|
|zone            | String  | 区域 ID，注意要小写| Yes|



## Example

#### Example Request

```
https://api.qingcloud.com/iaas/?action=DescribeInstances
&instances.1=i-ogbndull
&status.1=running
&verbose=1
&COMMON_PARAMS
```

#### Example Response:

```js
{
  "action":"DescribeInstancesResponse",
  "instance_set":[
    {
      "vcpus_current":1,
      "instance_id":"i-ogbndull",
      "volume_ids":[
        "vol-g7xy7d6g",
        "vol-jg7326gy"
      ],
      "vxnets":[
        {
          "vxnet_name":"primary vxnet",
          "vxnet_type":1,
          "vxnet_id":"vxnet-0",
          "nic_id":"52:54:ef:0c:ed:66",
          "private_ip":"10.50.13.54"
        }
      ],
      "eip":{
        "eip_id":"eip-1234abcd",
        "eip_addr":"121.201.5.5",
        "bandwidth":"50"
      },
      "memory_current":1024,
      "sub_code":0,
      "transition_status":"",
      "instance_name":"",
      "instance_type":"small_b",
      "create_time":"2013-08-28T14:26:03Z",
      "status":"running",
      "description":null,
      "security_group":{
        "is_default":1,
        "security_group_id":"sg-z13kokni"
      },
      "status_time":"2013-08-28T14:26:03Z",
      "image":{
        "processor_type":"64bit",
        "platform":"linux",
        "image_size":20,
        "image_name":"CentOS 6.4 64bit",
        "image_id":"centos64x64",
        "os_family":"centos",
        "provider":"system"
      },
      "keypair_ids":[
        "kp-bn2n77ow",
        "kp-05vfs7zs"
      ]
    }
  ],
  "ret_code":0,
  "total_count":1
}
```