- [登录API（完成）](#登录API)
- [文章获取API（完成）](#文章获取API)
- [点赞API(完成)](#点赞API)
- [评论API(完成)](#评论API)
- [图集列表API)(修改中)](#图集列表API)
- [查看图集详细API(修改中)](#查看图集详细API)
- [获取分类API(完成)](#获取分类API)
- [图片上传(完成)](#图片上传)
- [发送工作圈(完成)](#发送工作圈)
- [我发送的列表(完成)](#我发送的列表)

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
post_id | false | Int | 文章ID，当只需要一篇文章时使用
uid | false | Int | 用户ID，筛选指定用户文章

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
      "created_at":"2分钟前",
      "real_time":"2019-02-15 10:32:59",
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

# 点赞API

- 接口地址：http://localhost/api/support
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/support?id=1&uid=1

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
id | true | Int | 工作圈ID
uid | true | Int | 用户ID

### 成功返回值：

```
// 点赞返回值
{
  "result":"success",
  "status":2, // status = 1为取消点赞
  "msg":"点赞成功",
  "likeList":[
    "Alice","Bob","Mike"
  ]
}
```

# 评论API

- 接口地址：http://localhost/api/comment
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/comment?id=1&uid=1&content=HelloWorld&parent=0

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
id | true | Int | 工作圈ID
uid | true | Int | 评论用户ID
content | true | String | 评论内容
parent | true | Int | 与评论ID关联。0为顶级评论，否则为回复评论

### 成功返回值:

```
{
  "result":"success",
  "msg":"评论成功",
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
```

# 图集列表API

- 接口地址：http://localhost/api/pictures
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/pictures?page=1&pagenum=10&sort_id=1

### 请求参数说明：

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
page | true | Int | 当前页码
pagenum | false | Int | 每页数量，默认为10.（注意：10条数据 = 10天的数据，不要理解为10张图片）
sort_id | false | Int | 筛选分类ID

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
          "url":"https://localhost/demo.png"
        },
        {
          "id":2,
          "url":"https://localhost/demo.png"
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
          "url":"http://localhost/demo.png",
          "author":"舒磊明",
          "sort_name":"默认分类",
          "content":"我是文字内容",
          "created_at":"2019-02-18 00:00:00"
        },
        {
          "post_id":2,
          "url":"http://localhost/demo.png",
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

# 获取分类API

- 接口地址：http://localhost/api/sort
- 返回格式：JSON
- 请求方式：get/post
- 请求示范：http://localhost/api/sort

### 成功返回值：

```
{
  "result":"success",
  "data": [
    {
      "id":1,
      "sort_name":"默认分类",
      "article_count":99,
      "picture_count":99,
    }
  ]
}
```

# 图片上传

- 接口地址：http://localhost/api/uploadImage
- 返回格式：JSON
- 请求方式：post

### 说明

- 图片后缀.jpg 视频后缀.mp4
- 图片名称： xxx.jpg 缩略图名称：xxx_thumb.jpg
- 视频名称：xxx.mp4 截图名称：xxx.mp4.jpg

### 成功返回值：

```
{
  "result": "success",
  "filename": [
    "http://localhost/uploads/20190306/09013414b7367a28377d4d513a4d3349861d2f.jpg",
    "http://localhost/uploads/20190306/0901342377f9eb902f3c5855aca19197689b14.mp4"
  ]
}
```

# 发送工作圈

- 接口地址：http://localhost/api/send
- 返回格式：JSON
- 请求方式：post

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
uid | true | Int | 作者ID
content| true | String | 内容
sort_id | true | Int | 分类ID
pictures | true | Json | 图片地址: ["test1.jpg", "test2.mp4" ...]

# 我发送的列表

- 接口地址：http://localhost/api/send
- 返回格式：JSON
- 请求方式：post/get

名称 | 必填 | 类型 | 说明
--- | --- | --- | ---
uid | true | Int | 作者ID

### 返回值：

```
[
  {
    "sort_id": 1,
    "name": "缅甸100吨",
    "number": 10
  },
  {
    "sort_id": 2,
    "name": "巴西200吨",
    "number": 14
  }
]
```
