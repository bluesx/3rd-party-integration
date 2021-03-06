

## 获取授权信息

1.**授权信息**

#### 1.1 接口描述

* 获取access_token&ticket

* 申请accessToken,参考[访问权限](https://github.com/bluesx/3rd-party-integration/blob/master/site/erp/interface/accessToken.md)

  

#### 1.2 请求方式

> post

#### 1.3 url

> /offline/getAccessTokenAndTicket

#### 1.4 数据方向

> 线上系统-->商户

#### 1.5 请求参数

| 参数名称    | 参数类型 | 是否必须 | 示例值               | 说明        |
| :---------- | :------- | :------- | :------------------- | ----------- |
| siteId      | 字符串   | 是       | 100190               | 商户id      |
| accessToken | 字符串   | 是       | acfde325c8b9bbgyR57B | accessToken |

#### 1.6 返回参数

| 参数名称 | 参数类型 | 是否必须 | 示例值                   | 说明   |
| :------- | :------- | :------- | :----------------------- | ------ |
| wxToken  | 字符串   | 是       | EOQPHiTXVHl2PXJZDRoXXXX  | token  |
| wxTicket | 字符串   | 是       | Ngv8u5fhpizQZv9x1dtqXXXX | ticket |
| code     | 字符串   | 是       | 10000                    | 状态码 成功：10000,失败：20000|
| msg      | 字符串   | 是       | 获取成功                 | 返回消息   |

#### 1.7 请求示例

```java

{	
    "siteId":"100190",
    "accessToken":"acfde325c8b9bbgyR57B",
}


```

----



#### 1.8 返回示例(请求成功)

```
{
  "code":"10000",
  "wxToken":"EOQPHiTXVHl2PXJZDRoXXXXXXXXX",
  "wxTicket"："Ngv8u5fhpizQZv9x1dtqXXXXXXX"
  "msg": "获取成功"
}
```

#### 1.9 返回示例(请求失败)

```
{
  "code":"20000",
  "msg": "失败,相关原因！"
}
```

