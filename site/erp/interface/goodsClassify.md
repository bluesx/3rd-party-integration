## 商品分类信息同步
### 1.实时商品分类信息同步
#### 1.1 接口描述
* 商品数据同步的主要目的在于提供线上系统使用，因此分类信息以线上系统为准
* ERP维护一份线上系统的商品分类信息，经过正确匹配之后，与商品信息一起同步
#### 1.2 请求方式
> POST
#### 1.3 url
* 线上系统：
> /goods/classify
#### 1.4 数据方向
> 线上系统-->ERP
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| siteId   | String     | 是    | 90301105    | 商户ID |
| parentId   | Integer     | 是    | 0    | 父类ID: 0(表示顶级分类)，其它数字为分类的ID即分类表主键 |
| cateCode | String | 是 | 1000 | 商品分类 eg：一级分类（1000）、二级分类（10001000）、三级分类（100010001000）|
| cateName | String | 是 | 处方药 | 分类名称 |
| 
--------------------- 
#### 1.5 返回参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| code   | 字符串     | 是    | 10000    | 请求状态值，10000:成功;20000:失败 |
| msg   | 字符串    | 是    | 成功    | 成功或失败消息 |
| storeNumber   | 字符串    | 是    | 1192    | 门店编号 |
| goodsCode   | 字符串    | 是    | AW020785    | 商品编码 |
| drugName   | 字符串    | 是    | 复方黄松洗液    | 药品名称 |
| batchNumber   | 字符串    | 是    | AC321321    | 批号 |
| specification   | 字符串    | 否    | 200毫升    | 规格 |
| manufacturer   | 字符串    | 否    | 国药    | 生产商家 |
| accountQuantity   | 浮点    | 是    | 2.00   | 账面库存数，保留两位小数 |
| expiryDate   | 日期    | 否    | 2019-09-09   | 有效期 yyy-MM-dd |
--------------------- 
#### 1.6 返回成功(匹配到库存信息)
 ``` 
{
    "code" : 10000,
    "msg" : "成功"
    "data" : {
      "storeNumber" : "1192",
      "goodsList" : [{
      "goodsCode" : "AW020785",
      "drugName" : "复方黄松洗液",
      "batchNumber" : "AC321321",
      "specification" : "200毫升",
      "manufacturer" : "国药",
      "accountQuantity" : 2,
      "expiryDate" : "2019-09-09"
    },
    {
      "goodsCode" : "AW020786",
      "drugName" : "孟鲁司特钠片",
      "batchNumber" : "AC321322",
      "specification" : "10毫克×5片",
      "manufacturer" : "国药",
      "accountQuantity" : 12,
      "expiryDate" : "2020-09-09"
    }
    ]
    }
}
```
#### 1.7 请求失败
```
{
  "code": 20000,
  "msg" : "失败,相关原因"
}
```

