# 登录API

- 接口地址：http://localhost/api/login
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/login?username=usr&passwd=123

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
username | true | String | 用户名
passwd | true | String | 密码

### 成功返回值

```
{
  "result":"success",
  "uid":123,
  "real_name":"舒磊明",
  "avatar":"https://ss2.bdstatic.com/70cFvnSh_Q1YnxGkpoWK1HF6hhy/it/u=4001431513,4128677135&fm=27&gp=0.jpg",
  "group":"contributor",
  "msg":"登录成功"
}
```

### 失败返回值

```
{
  "result":"false",
  "msg":"账号或密码错误"
}
```

# 文章获取API

- 接口地址：http://localhost/api/posts
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/posts?page=1&pagenum=10&sort_id=1&keyword=hello

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
page | true | Int | 当前页码
pagenum | false | Int | 每页文章数量，可不填。默认10
sort_id | false | Int | 筛选项：分类ID，可不填
keyword | false | String | 筛选项：关键字搜索，可不填

### 成功返回值

```
{
  "result":"success",
  "data": [
    {
      "id":42,
      "avatar":"https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=880654418,863934247&fm=27&gp=0.jpg",
      "uid":2,
      "username":"装逼王",
      "sort_id":1,
      "sort_name":"巴基斯坦30吨",
      "content":"我是内容",
      "pictures"：[        
        "https://ss3.bdstatic.com/70cFv8Sh_Q1YnxGkpoWK1HF6hhy/it/u=880654418,863934247&fm=27&gp=0.jpg",
        "https://ss0.bdstatic.com/70cFvHSh_Q1YnxGkpoWK1HF6hhy/it/u=1129051769,4107945695&fm=27&gp=0.jpg",
        "https://ss1.bdstatic.com/70cFvXSh_Q1YnxGkpoWK1HF6hhy/it/u=2897931462,2821633511&fm=27&gp=0.jpg"
      ],
      "created_at":"2019-02-15 10:32:59",
      "updated_at":"2019-02-15 10:33:03",
      "likes":[
        "张三","李四","王五"
      ],
      "comments":[
        {
          "id":1,
          "username":"张三",
          "content":"Hello world",
          "parent": 0
        },
        {
          "id":2,
          "username":"李四",
          "content":"你好世界",
          "parent": 1
        },
      ]
    }
  ]
}
```

### 失败返回值

```
{
  "result":"false",
  "msg":"服务器繁忙，请稍后重试"
}
```

# 图集列表API

- 接口地址：http://localhost/api/pictures
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/pictures?page=1&pagenum=10

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
page | true | Int | 当前页码
pagenum | false | Int | 每页数量，默认为10.（注意：10条数据 = 10天的数据，不要理解为10张图片）

### 成功返回值：

```
{
  "result":"success",
  "data":[
    {
      "date":"今天",
      "pictures": [
        {
          "id":1,
          "url":"https://www.meckey.com/demo.png"
        },
        {
          "id":2,
          "url":"https://www.meckey.com/demo.png"
        }
      ]
    }
  ]
}
```

### 失败返回值：

```
{
  "result":"false",
  "msg":"服务器繁忙，请稍后重试"
}
```

# 查看图集详细API

- 接口地址：http://localhost/api/pictures
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/pictures?picture_id=1

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
picture_id | true | Int | 图集中的图片ID

> 说明：只需传入一个图片ID，即可返回和该图片同日的所有图片详情。

### 成功返回值：

```
{
  "result":"success",
  "data":[
    {
      "date":"今天",
      "pictures": [
        {
          "post_id":1,
          "url":"https://www.meckey.com/demo.png",
          "author":"舒磊明",
          "sort_name":"默认分类",
          "content":"我是文字内容",
          "created_at":"2019-02-18 00:00:00"
        },
        {
          "post_id":2,
          "url":"https://www.meckey.com/demo.png",
          "author":"舒磊明",
          "sort_name":"默认分类",
          "content":"我是文字内容",
          "created_at":"2019-02-18 00:00:00"
        },
      ]
    }
  ]
}
```

### 失败返回值：

```
{
  "result":"false",
  "msg":"服务器繁忙，请稍后重试"
}
```
