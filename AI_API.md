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

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `text/plain;charset=UTF-8`        | OK								 |

##### Example cURL

> ```
> curl -X GET -H "Content-Type: application/json" http://192.168.1.200:5054/
> ```

</details>

<details>
	<summary><code>POST</code> <code><b>/sendSms</b></code> <code>获取验证码</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`        | OK (返回JSON)						 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |

##### JSON返回示例

```
{
	"verifyCode": 123456
}
```

</details>

<details>
	<summary><code>POST</code> <code><b>/verifySmsCode</b></code> <code>验证验证码</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |
> | verifyCode       | required | int            | 验证码                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON)                       |
> | `401`       | `text/plain;charset=UTF-8`        | 验证码无效                          |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |

##### JSON返回示例

```
{
	"token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjRmNGZkYjE3LTFjMmUtNDg4OC04ZGYzLTg1ZjA5MTlmZDA0ZCIsImVtYWlsIjoiMTU5MDE0Mjk4MTYiLCJqdGkiOiIwMTcyODg5MC05ZmQ0LTQ4YjgtOTkzMi04NzAzZTg5MWJjZWEiLCJuYmYiOjE3MTUzOTQwNTMsImV4cCI6MTcxNTk5ODg1MywiaWF0IjoxNzE1Mzk0MDUzLCJpc3MiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8iLCJhdWQiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8ifQ.vSVHrVR4aQB5xEwutLglW0AXKNzSKcwu7dS2AiFQxMlVH9vCHvK6eL467yEpF2o0FwLKIaJsq6ic-dQsvONGPw"
}
```

</details>

<details>
	<summary><code>POST</code> <code><b>/user/login</b></code> <code>登录</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON) 		             			 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```
{
  "new_token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjRmNGZkYjE3LTFjMmUtNDg4OC04ZGYzLTg1ZjA5MTlmZDA0ZCIsImVtYWlsIjoiMTU5MDE0Mjk4MTYiLCJqdGkiOiIwMTcyODg5MC05ZmQ0LTQ4YjgtOTkzMi04NzAzZTg5MWJjZWEiLCJuYmYiOjE3MTUzOTQwNTMsImV4cCI6MTcxNTk5ODg1MywiaWF0IjoxNzE1Mzk0MDUzLCJpc3MiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8iLCJhdWQiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8ifQ.vSVHrVR4aQB5xEwutLglW0AXKNzSKcwu7dS2AiFQxMlVH9vCHvK6eL467yEpF2o0FwLKIaJsq6ic-dQsvONGPw",
  "userInfo": {}
}
```

</details>

<details>
  <summary><code>POST</code> <code><b>/user/register</b></code> <code>注册用户</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |
> | age      | required | int           | 年龄                               |
> | gender      | required | int           | 0 = 男, 1 = 女                               |
> | profession      | required | int           | 职业, 读表数据                               |
> | interests      | required | int[]           | 标签, int数组, 读表                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

</details>

<details>
  <summary><code>POST</code> <code><b>/user/update</b></code> <code>更新用户数据 TODO</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON)                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```
{
  "new_token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjRmNGZkYjE3LTFjMmUtNDg4OC04ZGYzLTg1ZjA5MTlmZDA0ZCIsImVtYWlsIjoiMTU5MDE0Mjk4MTYiLCJqdGkiOiIwMTcyODg5MC05ZmQ0LTQ4YjgtOTkzMi04NzAzZTg5MWJjZWEiLCJuYmYiOjE3MTUzOTQwNTMsImV4cCI6MTcxNTk5ODg1MywiaWF0IjoxNzE1Mzk0MDUzLCJpc3MiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8iLCJhdWQiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8ifQ.vSVHrVR4aQB5xEwutLglW0AXKNzSKcwu7dS2AiFQxMlVH9vCHvK6eL467yEpF2o0FwLKIaJsq6ic-dQsvONGPw",
  "userInfo": {}
}
```

</details>

<details>
  <summary><code>GET</code> <code><b>/type/list</b></code> <code>获取类型列表 TODO</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON)                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```
{
  "new_token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjRmNGZkYjE3LTFjMmUtNDg4OC04ZGYzLTg1ZjA5MTlmZDA0ZCIsImVtYWlsIjoiMTU5MDE0Mjk4MTYiLCJqdGkiOiIwMTcyODg5MC05ZmQ0LTQ4YjgtOTkzMi04NzAzZTg5MWJjZWEiLCJuYmYiOjE3MTUzOTQwNTMsImV4cCI6MTcxNTk5ODg1MywiaWF0IjoxNzE1Mzk0MDUzLCJpc3MiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8iLCJhdWQiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8ifQ.vSVHrVR4aQB5xEwutLglW0AXKNzSKcwu7dS2AiFQxMlVH9vCHvK6eL467yEpF2o0FwLKIaJsq6ic-dQsvONGPw",
  "userInfo": {}
}
```

</details>

<details>
	<summary><code>GET</code> <code><b>/search/type</b></code> <code>按类型搜索</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | id      	    	 | required | int            | 类型id                               |
> | limit      	  	 | opt      | int            | 条数                                 |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON) 		            			 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### Example cURL

> ```
> curl -X GET https://localhost:7278/search/type?id=0
> ```

##### JSON返回示例

```
{
  "tags": [
    {
      "id": 1,
      "name": "校园"
    },
    {
      "id": 2,
      "name": "乙女"
    }
  ],
  "agents": [
    {
      "id": 2,
      "name": "毛利兰",
      "gender": 1,
      "type": 0,
      "dify_id": null,
      "public": true,
      "avatar": null,
      "tags": []
    },
    {
      "id": 1,
      "name": "段飞",
      "gender": 0,
      "type": 0,
      "dify_id": null,
      "public": true,
      "avatar": null,
      "tags": [
        2,
        1
      ]
    },
    {
      "id": 3,
      "name": "随便你",
      "gender": 2,
      "type": 0,
      "dify_id": null,
      "public": true,
      "avatar": null,
      "tags": []
    }
  ]
}
```

</details>

<details>
  <summary><code>POST</code> <code><b>/dify/chat-messages</b></code> <code>Dify聊天</code></summary>

##### Headers

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | dify_id      | required | string           | Dify应用Id                               |
> 
> 
##### Parameters

> <b>使用Dify的body</b>

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (Dify返回格式)                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

</details>

------------------------------------------------------------------------------------------

https://gist.github.com/azagniotov/a4b16faf0febd12efbc6c3d7370383a6