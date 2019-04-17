## 实时建站
### 1.实时建立新的商户站点
#### 1.1 接口描述
* ERP系统提交信息到线上系统，触发线上系统建立新的商户站点
* 一次建立一个站点，要求商户相关信息完善
#### 1.2 请求方式
> POST
#### 1.3 url
* 线上系统：
> /site/startup
#### 1.4 数据方向
> ERP->线上系统
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |

| merchantName | String | 是 | 51健康 | 商户名称 |
| merchantShopDesc | String | 是 | 51健康 | -- |
| merchantExtLegalPerson | String | 是 | -- | -- |
| merchantCompanyName | String | 是 | -- | -- |
| merchantShopArea | Integer | 是 | 310109 | -- |
| merchantShopAddress | String | 是 | 四川北路 | -- |
| merchantServicePhone | String | 是 | 0550123456 | -- |
| merchantLegalName | String | 是 | -- | -- |
| merchantLegalMobile | String | 是 | 13322221111 | -- |
| merchantCompanyEmail | String | 否 | -- | -- |
| merchantShopQQ | String | 否 | -- | -- |
| merchantCardId | String | 否 | -- | -- |
| merchantShortMessageSign | String | 是 | -- | -- |
| merchantExtTradeCertNumber | String | 否 | -- | -- |
| merchantShopwxUrl | String | 否 | -- | -- |
| merchantShopWeixin | String | 否 | -- | -- |
| merchantExtWxAppid | String | 否 | -- | -- |
| merchantExtWxSecret | String | 否 | -- | -- |
| merchantExtWxOriginalId | String | 否 | -- | -- |
| merchantExtIntegralName | String | 否 | -- | -- |
| merchantExtAlipayAccount | String | 是 | 13322221111 | -- |
| merchantPayeeName | String | 是 | admin | -- |
| merchantShopTitle | String | 是 | -- | -- |
| merchantShopUrl | String | 是 | www.houtaiceshi.com | -- |
| merchantExtShopIp | String | 是 | 10.10.10.10 | -- |
| merchantExtStoreUrl | String | 是 | www.store.com | -- |
| merchantSiteRecord | String | 是 | 12332100000000 | -- |
| merchantShopLogurl | String | 是 | -- | -- |
| merchantShopWatermark | String | 否 | -- | -- |
| merchantExtCompanyQualurl | String | 是 | -- | -- |
| merchantExtTaxCertificate | String | 是 | -- | -- |
| merchantExtOrganizationCodecert | String | 是 | -- | -- |
| merchantExtGspApprove | String | 是 | -- | -- |
| merchantExtDrugCert | String | 是 | -- | -- |
| merchantExtMedicalCert | String | 否 | -- | -- |
| merchantExtMedicalequiCert | String | 否 | -- | -- |
| merchantExtFdcirculationCert | String | 否 | -- | -- |
| merchantExtInterDrugInformCert | String | 否 | -- | -- |
| merchantExtInterDrugTradCert | String | 否 | -- | -- |
| merchantSellerNick | String | 是 | admin | -- |
| merchantSellerPwd | String | 是 | 123456 | -- |

| merchantIsFrozen | String | 是 | -- | -- |
| merchantSiteStatus | String | 是 | -- | -- |
| merchantWxSiteStatus | String | 是 | -- | -- |
| merchantExtAllowRefund | String | 是 | -- | -- |
| merchantExtRecipeFrontendSetting | String | 是 | -- | -- |
| merchantExtLogisticsFlagJk | String | 是 | -- | -- |
| merchantExtRemark | String | 否 | -- | -- |

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
}
#### 1.7 请求失败
{
  "code": 20000,
  "msg" : "失败,相关原因"
}
```

