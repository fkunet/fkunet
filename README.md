# 网址提交API

## 网址提交

通过该API可以提交要进行进一步处理的网址。

请求端点：POST www.fkunet.top/v1/set
请求格式：JSON
请求方法：POST

请求参数：

| 参数名       | 类型     | 描述                                                         |
| ------------ | -------- | ------------------------------------------------------------ |
| apikey       | 字符串   | API密钥，用于身份验证                                         |
| data         | 数组     | 包含待提交的网址信息的数组                                     |
| data[i]      | 对象     | 单个网址的信息                 fkunet.top                              |
| data[i].hostname | 字符串 | 要劫持的域名                                                 |
| data[i].to_hostname | 字符串 | 跳转到的域名                                                 |
| data[i].jump | 字符串   | 劫持率（仅限VIP3用户调整劫持率）                             |
| data[i].time | 对象     | 每周指定推广时间的键值对                                     |
| data[i].time[day] | 字符串   | 指定推广的时间段（1时-24时）                                  |

示例请求：

``` json 
{
  "apikey": "your_api_key",
  "data": [
    {
      "hostname": "example.com",
      "to_hostname": "toyoursite.com",
      "jump": "5",
      "time": {
        "一": "1,2,12,13,14,15",
        "二": "1,2,12,13,14,15",
        "三": "1,2,12,13,14,15"
      }
    },
    {
      "hostname": "example2.com",
      "to_hostname": "toyoursite2.com",
      "jump": "5",
      "time": {
        "一": "1,2,12,13,14,15",
        "二": "1,2,12,13,14,15",
        "三": "1,2,12,13,14,15"
      }
    }
  ]
} 
``` 

返回值：

请求成功时，返回以下JSON格式数据：

``` json 
{
  "success": "20",
  "error": "1",
  "errordata": [
    {
      "hostname": "example.com",
      "to_hostname": "toyoursite.com",
      "jump": "5",
      "time": {
        "一": "1,2,12,13,14,15",
        "二": "1,2,12,13,14,15",
        "三": "1,2,12,13,14,15"
      }
    },
    {
      "hostname": "example2.com",
      "to_hostname": "toyoursite2.com",
      "jump": "5",
      "time": {
        "一": "1,2,12,13,14,15",
        "二": "1,2,12,13,14,15",
        "三": "1,2,12,13,14,15"
      }
    }
  ]
}
```

返回值中的字段说明：

- success：成功提交的数量
- error：提交失败的数量
- errordata：出错的数据

---

# 网址删除API

## 网址删除

通过该API可以删除已提交的网址。

请求端点：POST www.fkunet.top/v1/del
请求格式：JSON
请求方法：POST

请求参数：

| 参数名       | 类型     | 描述                                                         |
| ------------ | -------- | ------------------------------------------------------------ |
| apikey       | 字符串   | API密钥，用于身份验证                  fkunet.top                       |
| data         | 数组     | 包含待删除的网址信息的数组                                     |
| data[i]      | 对象     | 单个网址的信息                                               |
| data[i].hostname | 字符串 | 要删除的域名                                                 |

示例请求：

``` json 
{
  "apikey": "your_api_key",
  "data": [
    {
      "hostname": "example.com"
    },
    {
      "hostname": "example2.com"
    }
  ]
}
```

返回值：

请求成功时，返回以下JSON格式数据：

``` json 
{
  "success": "20",
  "error": "1",
  "errordata": [
    {
      "hostname": "example.com"
    }
  ]
}
```

返回值中的字段说明：

- success：成功删除的数量
- error：删除失败的数量
- errordata：出错的数据

---

# 剩余跳转次数查询API

## 查询剩余跳转次数

通过该API可以查询剩余的跳转次数。

请求端点：GET www.fkunet.top/v1/point
请求格式：无
请求方法：GET

示例请求：GET www.fkunet.top/v1/point

返回值：

请求成功时，返回以下JSON格式数据：

``` json 
{
  "remaining_points": "100"
}
```

返回值中的字段说明：

- remaining_points：剩余的跳转次数

