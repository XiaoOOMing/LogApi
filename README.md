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
