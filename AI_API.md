# AI App APIs

- 测试服务器: http://192.168.1.200:5054/

#### 验证方式

GET或POST，头部格式

| Key              |  Value             |
|------------------|--------------------|
| Authorization    |  Bearer ${token}   |

------------------------------------------------------------------------------------------

## 主要API

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
> curl -X GET -H 'Content-Type: application/json' 'http://192.168.1.200:5054/'
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
> | `200`       | `application/json`                | OK                                 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |

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

```js
{
	"token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjRmNGZkYjE3LTFjMmUtNDg4OC04ZGYzLTg1ZjA5MTlmZDA0ZCIsImVtYWlsIjoiMTU5MDE0Mjk4MTYiLCJqdGkiOiIwMTcyODg5MC05ZmQ0LTQ4YjgtOTkzMi04NzAzZTg5MWJjZWEiLCJuYmYiOjE3MTUzOTQwNTMsImV4cCI6MTcxNTk5ODg1MywiaWF0IjoxNzE1Mzk0MDUzLCJpc3MiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8iLCJhdWQiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8ifQ.vSVHrVR4aQB5xEwutLglW0AXKNzSKcwu7dS2AiFQxMlVH9vCHvK6eL467yEpF2o0FwLKIaJsq6ic-dQsvONGPw"
}
```

</details>

<details>
	<summary><code>POST</code> <code><b>/user/login</b></code> <code>登录</code></summary>

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON) 		             			 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```js
{
  "new_token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjYyOTU2MjAzLTA2YTItNGM2NS1iM2M2LTMwNTY2NjI2ZTYyNiIsInVpZCI6IjMiLCJqdGkiOiI2MmZlYWVhYS0zMTI0LTQ1NjAtYjVmMi03ZDYxZmYzNmJhMjMiLCJuYmYiOjE3MTU1OTcwOTMsImV4cCI6MTcxNjIwMTg5MywiaWF0IjoxNzE1NTk3MDkzLCJpc3MiOiJodHRwczovL2Rxc2R4LmNuLyIsImF1ZCI6Imh0dHBzOi8vZHFzZHguY24vIn0.95kL6gLjhPCLECZ7QgUQr5hHdfLkFHYY5yWZskt2ipjIZk2KFaELZdft2Nf_fLYBB82CffGR9pzMFDKFuXl-2g",
  "userInfo": {
    "id": 3,
    "name": "mingzi",
    "avatar": null,
    "diamonds": 0,
    "phoneNumber": 15901429816,
    "age": 113,
    "gender": 0,
    "interests": [
      1,
      2
    ],
    "profession": 1,
    "created_at": "2024-05-13T18:34:43"
  }
}
```

</details>

<details>
  <summary><code>POST</code> <code><b>/user/register</b></code> <code>注册用户</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | name      | required | string           | 姓名                               |
> | age      | required | int           | 年龄                               |
> | gender      | required | int           | 0 = 男, 1 = 女                               |
> | profession      | required | int           | 职业, 读表数据                               |
> | interests      | required | int[]           | 标签, int数组, 读表                               |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `text/plain;charset=UTF-8`                | OK                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON发送示例

```js
{
    "name": "田帅帅",
    "interests": [
        1,
        2
    ],
    "age": 11,
    "gender": 0,
    "profession": 1
}
```

</details>

<details>
  <summary><code>GET</code> <code><b>/search/keyword</b></code> <code>按关键字搜索</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | value               | required | string            | 关键字（标签名称或agent名称） |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK（返回JSON，固定最大15条）                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### Example cURL

> ```
> curl -v -X GET 'https://localhost:7278/search/keyword?value=男'
> ```

##### JSON示例

```js
{
  "tags": [
    {
      "id": 1,
      "name": "校园"
    }
  ],
  "agents": [
    {
      "id": 7,
      "name": "暖男",
      "gender": 0,
      "type": 1,
      "dify_id": "40c55ab4-907a-484e-a0f1-adc2197fd124",
      "public": true,
      "avatar": null,
      "desc": "你好，我是心理咨询师暖男。很高兴与你相识，有什么想聊的都可以告诉我哦。无论是关于工作、生活还是情感方面的问题，我都会尽力帮助你解答和提供建议。",
      "tags": [
        1
      ]
    },
    {
      "id": 8,
      "name": "渣男",
      "gender": 0,
      "type": 1,
      "dify_id": "e8e714bf-1275-4988-b13a-425ab3c5bf5c",
      "public": true,
      "avatar": null,
      "desc": "我是李煜辰，一个金融公司的高级管理层。我热衷于钢琴和高尔夫球，同时也在社交场合中展现出自己的魅力和影响力。",
      "tags": [
        1
      ]
    }
  ]
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
> curl -v -X GET 'https://localhost:7278/search/type?id=0'
> ```

##### JSON返回示例

```js
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
      "desc": "本人性格开朗、稳重、有活力，待人热情、真诚。工作认真负责，积极主动，能吃苦耐劳；喜欢思考，虚心与人交流,以取长补短。有较强的组织能力、实际动手能力和团体协",
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
      "desc": "本人性格开朗、稳重、有活力，待人热情、真诚。工作认真负责，积极主动，能吃苦耐劳；喜欢思考，虚心与人交流,以取长补短。有较强的组织能力、实际动手能力和团体协",
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
      "desc": "本人性格开朗、稳重、有活力，待人热情、真诚。工作认真负责，积极主动，能吃苦耐劳；喜欢思考，虚心与人交流,以取长补短。有较强的组织能力、实际动手能力和团体协",
      "tags": []
    }
  ]
}
```

</details>

<details>
  <summary><code>POST</code> <code><b>/upload/image</b></code> <code>上传图片</code></summary>

##### Headers

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | Content-Type     | required | string         | image/png或image/jpeg               |

##### Parameters

> <b>Body部分直接传入文件二进制</b>

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON, 含相对路径)            |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```js
{
  "relativePath": "images/1715765038676.png"
}
```

</details>

<details>
  <summary><code>POST</code> <code><b>/query/tags</b></code> <code>查询tag信息</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | tags               | required | int[]            | int类型json数组, 值为tag的id  |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON)                        |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### 请求Body

```js
{
  "tags": [
    1,2,3,4,5
  ]
}
````

##### JSON返回示例

```js
[
  {
    "id": 1,
    "name": "校园"
  },
  {
    "id": 2,
    "name": "乙女"
  },
  {
    "id": 4,
    "name": "三个字"
  },
  {
    "id": 5,
    "name": "1"
  }
]
```

</details>

### Agent相关接口

<details>
  <summary><code>POST</code> <code><b>/create/agent</b></code> <code>创建AI Agent</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | name             | required | string         | 名字                                 |
> | gender           | required | int            | 性别                                 |
> | desc             | required | string         | 描述                                 |
> | type             | required | int            | 分类类型                              |
> | icon             | required | string         | 头像Icon URL相对路径                  |
> | prompt           | required | string         | 提示词                                |
> | tags           | required | int[]         | tags数组                                |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK                    |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |


##### JSON请求示例

```js
{
  "name": "测试",
  "desc": "测试agent",
  "gender": 1,
  "type": 1,
  "icon": "someurl",
  "prompt": "测试prompt",
  "tags": [1,2,3,4,5]
}
```

</details>

<details>
  <summary><code>GET</code> <code><b>/query/agent</b></code> <code>查询Agent信息</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | id               | required | int            | Agent Id                            |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK（返回Agent Json）                |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```js
{
  "id": 1,
  "name": "段飞",
  "gender": 0,
  "type": 1,
  "dify_id": "1606443f-c015-4245-b8c4-a54dc13db4bd",
  "public": true,
  "avatar": null,
  "intimacy": 11  // 亲密度
}
```

</details>

------------------------------------------------------------------------------------------

## Dify相关接口

<details>
  <summary><code>GET</code> <code><b>/dify/startConversation</b></code> <code>会话开始前调用</code></summary>

##### Parameters

> | Key              | Type     | Data type      | Description                         |
> |------------------|----------|----------------|-------------------------------------|
> | agent_id         | required | int            | agent id                            |

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK                                 |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

</details>

<details>
  <summary><code>POST</code> <code><b>/dify/chat-messages</b></code> <code>Dify聊天</code></summary>

##### Headers

> | Key              | Type     | Data type      | Description                     |
> |------------------|----------|----------------|---------------------------------|
> | agent_id         | required | int         | Agent Id                        |
> | dify_id          | required | string         | Dify应用Id                       |

##### Parameters

> <b>使用Dify的body</b>

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (Dify返回格式)                   |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

</details>

------------------------------------------------------------------------------------------

TODO

<details>
  <summary><code>POST</code> <code><b>/user/update</b></code> <code>更新用户数据 TODO</code></summary>

##### Responses

> | Code        | Content-Type                      | Response                           |
> |-------------|-----------------------------------|------------------------------------|
> | `200`       | `application/json`                | OK (返回JSON)                       |
> | `400`       | `text/plain;charset=UTF-8`        | BadRequest                         |
> | `401`       | `text/plain;charset=UTF-8`        | 验证失败                            |

##### JSON返回示例

```js
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

```js
{
  "new_token": "eyJhbGciOiJIUzUxMiIsInR5cCI6IkpXVCJ9.eyJJZCI6IjRmNGZkYjE3LTFjMmUtNDg4OC04ZGYzLTg1ZjA5MTlmZDA0ZCIsImVtYWlsIjoiMTU5MDE0Mjk4MTYiLCJqdGkiOiIwMTcyODg5MC05ZmQ0LTQ4YjgtOTkzMi04NzAzZTg5MWJjZWEiLCJuYmYiOjE3MTUzOTQwNTMsImV4cCI6MTcxNTk5ODg1MywiaWF0IjoxNzE1Mzk0MDUzLCJpc3MiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8iLCJhdWQiOiJodHRwczovL2pveWRpcGthbmppbGFsLmNvbS8ifQ.vSVHrVR4aQB5xEwutLglW0AXKNzSKcwu7dS2AiFQxMlVH9vCHvK6eL467yEpF2o0FwLKIaJsq6ic-dQsvONGPw",
  "userInfo": {}
}
```

</details>

------------------------------------------------------------------------------------------

https://gist.github.com/azagniotov/a4b16faf0febd12efbc6c3d7370383a6
