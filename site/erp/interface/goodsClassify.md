## 商品分类信息同步
### 1.实时商品分类信息同步
#### 1.1 接口描述
* 商品数据同步的主要目的在于提供线上系统使用，因此分类信息以线上系统为准
* ERP维护一份线上系统的商品分类信息，经过正确匹配之后，与商品信息一起同步
#### 1.2 请求方式
> POST
#### 1.3 url
* 线上系统：
> /goods/goodsClassify
#### 1.4 数据方向
> 线上系统-->ERP
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| siteId   | String     | 是    | 100320    | 商户ID |
| cateGrade | Integer | 是 | 1 | 分类等级，1：一级分类 2：二级分类 3：三级分类（最多只有三级）|
| cateName | String | 是 | 中西药品 | 分类名称 |
| imgUrl | String | 是 | http://abc.com/a.jpg | 分类图片地址 |

--------------------- 
#### 1.6 请求参数格式
 ```
 {
    "siteId":100320,
    "data":{
       "cateGrade":1,
       "context":[{
          "cateName":"一级分类",
          "imgUrl":"http://abc.com/a.jpg",
          "data":{
             "cateGrade":2,
             "context":[{
                "cateName":"二级分类-1",
                "imgUrl":"http://abc.com/a1.jpg",
                "data":{
                   "cateGrade":3,
                   "context":[{
                      "cateName":"三级分类-1-1",
                      "imgUrl":"http://abc.com/a11.jpg"
                   },{
                      "cateName":"三级分类-1-2",
                      "imgUrl":"http://abc.com/a12.jpg"
                   },{
                      "cateName":"三级分类-1-3",
                      "imgUrl":"http://abc.com/a13.jpg"
                   }]
                }
             },{
                "cateName":"二级分类-2",
                "imgUrl":"http://abc.com/a2.jpg",
                "data":{
                   "cateGrade":3,
                   "context":[{
                      "cateName":"三级分类-2-1",
                      "imgUrl":"http://abc.com/a21.jpg"
                   },{
                      "cateName":"三级分类-2-2",
                      "imgUrl":"http://abc.com/a22.jpg"
                   }]
                }
             }]
          }
       },{
          "cateName":"中西药品",
          "imgUrl":"http://abc.com/b.jpg",
          "data":{
             "cateGrade":2,
             "context":[{
                "cateName":"胃肠疾病",
                "imgUrl":"http://abc.com/b1.jpg",
                "data":{
                   "cateGrade":3,
                   "context":[{
                      "cateName":"消化不良",
                      "imgUrl":"http://abc.com/b11.jpg"
                   },{
                      "cateName":"便秘",
                      "imgUrl":"http://abc.com/b12.jpg"
                   }]
                }
             },{
                "cateName":"抗菌消炎",
                "imgUrl":"http://abc.com/b2.jpg",
                "data":{
                   "cateGrade":3,
                   "context":[{
                      "cateName":"消炎类",
                      "imgUrl":"http://abc.com/b21.jpg"
                   },{
                      "cateName":"清热解毒类",
                      "imgUrl":"http://abc.com/b22.jpg"
                   },{
                      "cateName":"抗炎镇痛类",
                      "imgUrl":"http://abc.com/b23.jpg"
                   },{
                      "cateName":"抗真菌",
                      "imgUrl":"http://abc.com/b24.jpg"
                   }]
                }
             }]
          }
       }]
    }
 }
 
 ```
--------------------- 
#### 1.5 返回参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| code   | 字符串     | 是    | 10000    | 请求状态值，10000:成功;20000:失败 |
| msg   | 字符串    | 是    | 成功    | 成功或失败消息 |

--------------------- 
#### 1.6 返回成功(匹配到库存信息)
 ``` 
{
    "code" : 10000,
    "msg" : "成功"
}
```
#### 1.7 请求失败
```
{
  "code": 20000,
  "msg" : "失败,相关原因"
}
```

