# 身份授权

<!-- toc -->


### 重定向 URL

GET  /v2/zone/ac2/identity/{redirect_url}

URI Path 参数

| 参数 | 类型 | 描述
|---|---|---|
|redirect_url|string|重定向 URL <br>*URL 必须为完整 url 包含 http:// 且需经base64编码*|


案例

```bash
# http://www.51idc.com  ----base64--->   aHR0cDovL3d3dy41MWlkYy5jb20=

$ curl -i -XGET https://api.51idc.com/v2/zone/ac2/identity/aHR0cDovL3d3dy41MWlkYy5jb20= --cookie 'GWSession=vn0gp1cgK1VH2Ah6BpS5NaePtDJywcpKrbcZ8AqJeqGkve5jo0UiKQiCnGEoTr9P'
```

HTTP 响应
```bash
HTTP/1.1 302 Found
Location: http://www.51idc.com   # 重定向 URL
Date: Fri, 29 Jul 2016 03:24:10 GMT
Content-Length: 43
Content-Type: text/html; charset=utf-8

<a href="http://www.51idc.com">Found</a>.
```

