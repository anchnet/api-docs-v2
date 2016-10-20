# 其他

<!-- toc -->

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

