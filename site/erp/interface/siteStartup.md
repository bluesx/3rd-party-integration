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
| :---         |  :----  |     :--- | :--- | :--- |
| merchantName | 字符串 | 是 | 51健康 | 商家名称 |
| merchantShopDesc | 字符串 | 是 | 51健康 | 商家简介 |
| merchantExtLegalPerson | 字符串 | 是 | -- | 公司法人 |
| merchantCompanyName | 字符串 | 是 | -- | 公司名称 |
| merchantShopArea | 整型 | 是 | 310109 | 公司所在区域编码 |
| merchantShopAddress | 字符串 | 是 | 四川北路 | 公司地址 |
| merchantServicePhone | 字符串 | 是 | 0550123456 | 客服电话 |
| merchantLegalName | 字符串 | 是 | 张三 | 负责人姓名 |
| merchantLegalMobile | 字符串 | 是 | 13322221111 | 负责人电话 |
| merchantCompanyEmail | 字符串 | 否 | -- | 公司邮箱地址 |
| merchantShopQQ | 字符串 | 否 | -- | 公司QQ |
| merchantCardId | 字符串 | 否 | -- | 商家会员卡 |
| merchantShortMessageSign | 字符串 | 是 | -- | 短信签名 |
| merchantExtTradeCertNumber | 字符串 | 否 | -- | 互联网药品交易资格证 |
| merchantShopWxUrl | 字符串 | 否 | -- | 微信域名 |
| merchantShopWeixin | 字符串 | 否 | -- | 微信服务号 |
| merchantExtWxAppid | 字符串 | 否 | -- | 微信appid |
| merchantExtWxSecret | 字符串 | 否 | -- | 微信appsecret |
| merchantExtWxOriginalId | 字符串 | 否 | -- | 微信的原始id |
| merchantExtIntegralName | 字符串 | 否 | -- | 积分名称 |
| merchantExtAlipayAccount | 字符串 | 是 | 13322221111 | 支付宝账号 |
| merchantPayeeName | 字符串 | 是 | admin | 收款人名称 |
| merchantShopTitle | 字符串 | 是 | -- | 网站名称 |
| merchantShopUrl | 字符串 | 是 | www.a.com |  网站域名 |
| merchantExtShopIp | 字符串 | 是 | 10.10.10.10 | 网站IP地址 |
| merchantExtStoreUrl | 字符串 | 是 | www.a.com | 门店域名 |
| merchantSiteRecord | 字符串 | 是 | 12332100000000 | 网站备案号 |
| merchantShopLogoUrl | 字符串 | 是 | -- | 网站LOGO |
| merchantShopWatermark | 字符串 | 否 | -- | 图片防盗水印 |
| merchantExtCompanyQualUrl | 字符串 | 是 | -- | 营业执照 |
| merchantExtTaxCertificate | 字符串 | 是 | -- | 税务登记证 |
| merchantExtOrganizationCodecert | 字符串 | 是 | -- | 组织机构代码证 |
| merchantExtGspApprove | 字符串 | 是 | -- | 药品经营质量管理<br/>规范认证证书 |
| merchantExtDrugCert | 字符串 | 是 | -- | 药品经营许可证 |
| merchantExtMedicalCert | 字符串 | 否 | -- | 执业药师/医师证 |
| merchantExtMedicalequiCert | 字符串 | 否 | http://a.com/a.png | 医疗器械经营许可证 |
| merchantExtFdcirculationCert | 字符串 | 否 | http://a.com/a.png | 食品流通证 |
| merchantExtInterDrugInformCert | 字符串 | 否 | http://a.com/a.png | 互联网药品信息服务证 |
| merchantExtInterDrugTradCert | 字符串 | 否 | -- | 互联网药品交易服务证 |
| merchantSellerNick | 字符串 | 是 | admin | 管理员账号 |
| merchantSellerPwd | 字符串 | 是 | 123456 | 登录密码 |
| merchantIsFrozen | 整型 | 是 | 1 | 是否允许登录，<br/>1：不允许（默认） <br/>0：允许 |
| merchantSiteStatus | 整型 | 是 | 110 | 网站运行状态，<br/>110：审核中（默认） <br/>120：试运行（限制交易）<br/>130：正常运行 <br/>999：封网|
| merchantWxSiteStatus | 整型 | 是 | 110 | 微信站运行状态，<br/>110：审核中（默认） <br/>120：试运行（限制交易）<br/>130：正常运行 <br/>999：封网 |
| merchantExtAllowRefund | 整型 | 是 | 1 | 退款设置，<br/>1：允许在线退款 <br/>0：不允许在线退款 |
| merchantExtRecipeFrontendSetting | 整型 | 是 | 110 | 处方药设置，<br/>110：商品相关设置<br/>（电脑端和移动端） <br/>120：网站隐藏设置<br/>（电脑端和移动端）<br/>140：订单相关设置<br/>（电脑端和移动端） |
| merchantExtLogisticsFlagJk | 整型 | 是 | 1 | 默认物流，<br/>1：启用（默认）<br/>0：不启用 |
| merchantExtRemark | 字符串 | 否 | -- | 备注（最大长度255） |
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

