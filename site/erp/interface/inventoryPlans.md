## 盘点计划生成通知接口
### 1.获取盘点计划生成通知以便读取盘点计划
#### 1.1 接口描述
> 盘点计划生成时通知到系统方
#### 1.2 请求方式
> POST
#### 1.3 url
> /orders/storage
#### 1.4 数据方向
> 商户方至系统方
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| goodsno   | 字符串     | 是    | 90301104,90301105    | 商品编码，支持多值，多值之间逗号(,)分割 |
| uid   | 字符串    | 是    | 2，4    | 门店编号，支持多值，多值之间逗号(,)分割 |
--------------------- 
#### 1.5 返回参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| code   | 字符串     | 是    | 1    | 请求状态值，1:成功;0:失败 |
| msg   | 字符串    | 是    | 成功    | 成功或失败消息 |
| uid   | 字符串    | 是    | 2    | 门店id |
| goodsno   | 字符串    | 是    |   90301104  | 商品编码 |
| spec   | 字符串    | 是    |   10*10  | 商品规格 |
| state   | 整型    | 是    |   0  | 商品状态： 0 正常，1不正常，2删除|
| qty   | 浮点型    | 是    |   39.0  | 商品状态： 0 正常，1不正常，2删除|
--------------------- 
#### 1.6 返回成功(匹配到库存信息)
 ``` 
{
    "code" : 1,
    "msg" : "成功",
    "info" : [{
        "UID" : "2",
        "GOODSNO" : "90301104",
        "SPEC" : "90301104",
        "STATE" : "0",//状态 0 正常，1不正常，2删除
        "kcqty" : "16.0"
    }, {
        "UID" : "4",
        "GOODSNO" : "90301104",
        "SPEC" : "90301104",
        "STATE" : "0",//状态 0 正常，1不正常，2删除
        "kcqty" : "39.0"
   }]
}
```
#### 1.7 返回成功(未匹配到库存信息)
```
{
  "code": 1,
  "info": [],
  "msg":"成功"
}
```
#### 1.8 请求失败
```
{
  "code": 0,
  "info": [],
  "msg":"失败,相关原因"
}
```

