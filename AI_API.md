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
>  curl -X GET -H "Content-Type: application/json" http://192.168.1.200:5054/
> ```

</details>

<details>
	<summary><code>POST</code> <code><b>/login</b></code> <code>登录</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | phoneNumber      | required | long           | 手机号                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `text/plain;charset=UTF-8`        | OK (返回新token) 					 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

</details>

<details>
	<summary><code>GET</code> <code><b>/search/type</b></code> <code>按类型搜索</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | id      		 | required | int            | 类型id                               |
> | limit      		 | opt      | int            | 条数                                 |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `text/plain;charset=UTF-8`        | OK (返回JSON) 					 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### Example cURL

> ```
>  curl -X GET https://localhost:7278/search/type?id=0
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

------------------------------------------------------------------------------------------

https://gist.github.com/azagniotov/a4b16faf0febd12efbc6c3d7370383a6
