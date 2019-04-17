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
| merchantName | String | 是 | 51健康 | 商家名称 |
| merchantShopDesc | String | 是 | 51健康 | 商家简介 |
| merchantExtLegalPerson | String | 是 | -- | 公司法人 |
| merchantCompanyName | String | 是 | -- | 公司名称 |
| merchantShopArea | Integer | 是 | 310109 | 公司所在区域编码 |
| merchantShopAddress | String | 是 | 四川北路 | 公司地址 |
| merchantServicePhone | String | 是 | 0550123456 | 客服电话 |
| merchantLegalName | String | 是 | 张三 | 负责人姓名 |
| merchantLegalMobile | String | 是 | 13322221111 | 负责人电话 |
| merchantCompanyEmail | String | 否 | -- | 公司邮箱地址 |
| merchantShopQQ | String | 否 | -- | 公司QQ |
| merchantCardId | String | 否 | -- | 商家会员卡 |
| merchantShortMessageSign | String | 是 | -- | 短信签名 |
| merchantExtTradeCertNumber | String | 否 | -- | 互联网药品交易资格证 |
| merchantShopwxUrl | String | 否 | -- | 微信域名 |
| merchantShopWeixin | String | 否 | -- | 微信服务号 |
| merchantExtWxAppid | String | 否 | -- | 微信appid |
| merchantExtWxSecret | String | 否 | -- | 微信appsecret |
| merchantExtWxOriginalId | String | 否 | -- | 微信的原始id |
| merchantExtIntegralName | String | 否 | -- | 积分名称 |
| merchantExtAlipayAccount | String | 是 | 13322221111 | 支付宝账号 |
| merchantPayeeName | String | 是 | admin | 收款人名称 |
| merchantShopTitle | String | 是 | -- | 网站名称 |
| merchantShopUrl | String | 是 | www.houtaiceshi.com |  网站域名 |
| merchantExtShopIp | String | 是 | 10.10.10.10 | 网站IP地址 |
| merchantExtStoreUrl | String | 是 | www.store.com | 门店域名 |
| merchantSiteRecord | String | 是 | 12332100000000 | 网站备案号 |
| merchantShopLogurl | String | 是 | -- | 网站LOGO |
| merchantShopWatermark | String | 否 | -- | 图片防盗水印 |
| merchantExtCompanyQualurl | String | 是 | -- | 营业执照 |
| merchantExtTaxCertificate | String | 是 | -- | 税务登记证 |
| merchantExtOrganizationCodecert | String | 是 | -- | 组织机构代码证 |
| merchantExtGspApprove | String | 是 | -- | 药品经营质量管理规范认证证书 |
| merchantExtDrugCert | String | 是 | -- | 药品经营许可证 |
| merchantExtMedicalCert | String | 否 | -- | 执业药师/医师证 |
| merchantExtMedicalequiCert | String | 否 | -- | 医疗器械经营许可证 |
| merchantExtFdcirculationCert | String | 否 | -- | 食品流通证 |
| merchantExtInterDrugInformCert | String | 否 | -- | 互联网药品信息服务证 |
| merchantExtInterDrugTradCert | String | 否 | -- | 互联网药品交易服务证 |
| merchantSellerNick | String | 是 | admin | 管理员账号 |
| merchantSellerPwd | String | 是 | 123456 | 登录密码 |
| merchantIsFrozen | Integer | 是 | 1 | 是否允许登录，1：不允许（默认） 0：允许 |
| merchantSiteStatus | Integer | 是 | 110 | 网站运行状态，110：审核中（默认） 120：试运行（限制交易）130：正常运行 999：封网|
| merchantWxSiteStatus | Integer | 是 | 110 | 微信站运行状态，110：审核中（默认） 120：试运行（限制交易）130：正常运行 999：封网 |
| merchantExtAllowRefund | Integer | 是 | 1 | 退款设置，1：允许用户在线退款 0：不允许用户在线退款 |
| merchantExtRecipeFrontendSetting | Integer | 是 | 110 | 处方药设置，110：商品相关设置（电脑端和移动端） 120：网站隐藏设置（电脑端和移动端）140：订单相关设置（电脑端和移动端） |
| merchantExtLogisticsFlagJk | Integer | 是 | 1 | 默认物流，1：启用（默认）0：不启用 |
| merchantExtRemark | String | 否 | -- | 备注（最大长度255） |
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
#### 1.7 请求失败
{
  "code": 20000,
  "msg" : "失败,相关原因"
}
```

