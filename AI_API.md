## AI App APIs

- 测试服务器: http://192.168.1.200:5054/

#### 验证方式

GET或POST，头部格式

| Key              |  Value             |
|------------------|--------------------|
| Authorization    |  Bearer ${token}   |

------------------------------------------------------------------------------------------

#### 主要API

<details>
 <summary><code>GET</code> <code><b>/</b></code> <code>访问Root, 测试用. 无需验证</code></summary>

##### Parameters

> None

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `text/plain;charset=UTF-8`        |                                                                     |

##### Example cURL

> ```
>  curl -X GET -H "Content-Type: application/json" http://localhost:8889/
> ```

</details>

<details>
 <summary><code>POST</code> <code><b>/login</b></code> <code>登录</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | Required | long           | 手机号                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `text/plain;charset=UTF-8`        | OK (返回新token) 					 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

</details>

------------------------------------------------------------------------------------------

- https://gist.github.com/azagniotov/a4b16faf0febd12efbc6c3d7370383a6
