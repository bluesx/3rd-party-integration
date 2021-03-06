## 订单同步
### 1.订单批量查询
#### 1.1 接口描述
> 系统方提供本接口供商户方查询
#### 1.2 请求方式
> get
#### 1.3 url
> /merchant/getOrderList
#### 1.4 数据方向
> 系统方至商户方
#### 1.5 请求参数
| 参数名称 | 参数类型| 是否必须| 示例值 | 参数描述  |
| :---         |:-------|:--------| :--- | :--- |
| queryDate   | 字符串     | 是    | "2019-05"    | 查询月份 |
#### 1.6 请求示例
>/merchant/getOrderList?queryDate=2019-05
--------------------- 
#### 1.7 返回参数(JSON)
| 参数名称 | 参数类型| 是否必须| 示例值 | 参数描述  |
| :---         |:-------|:--------| :--- | :--- |
| code   | 字符串     | 是            | 10000   |返回结果标识:10000:成功</br>,20000:失败|
| msg   | 字符串     | 是    | 成功   |返回结果描述|
| discount   | 整型     | 是    | 0   |优惠金额，单位:分(RMB)|
| tradesSource   | 字符串     | 是    | 170  |订单来源: </br>110 (网站)，</br>120（微信），</br>130（app）, </br>140（店员帮用户下单）,</br>160 (支付宝生活号)，</br>170 (平安健康)，</br>9999（其它）|
| recevierName   | 字符串     | 是    | 测试   |收货人|
| file   | 字符串     | 是    | 2019022288927048769   |处方单号|
| storeName   | 字符串     | 是    | 61^呼市车站西街店   |服务门店名称|
| settlementStatus   | 字符串     | 是    | 200   |结算状态:</br>100(不结算),</br>150(待结算),</br>200(可结算), </br>250(已结算)|
| payStyle   | 字符串     | 是    | cash   |支付方式:</br>ali (支付宝) ，</br>wx (微信)，</br> bil(快钱)，</br> unionPay(银联)，</br> health_insurance（医保），</br>cash（现金）,</br>prePaid(储值卡),</br>coupon(购物券) |
| mobile   | 字符串     | 是    | 13120800149  |会员手机号|
| orderNo   | 字符串     | 是    | 9e84c3cb6912e4e1016913  |平安交易单号|
| payTime   | 字符串     | 是    | 2019-05-05 16:50:33  |订单支付时间，格式：<br/>yyyy-MM-dd HH:mm:ss||
| postFee   | 整型     | 是    | 0  |运费，单位:分(RMB)|
| receiverPhone   | 字符串     | 是    | 13120800149  |联系电话|
| tradesStatus   | 字符串     | 是    | 230  |交易状态:</br>110(等待买家付款),</br>120(等待卖家发货),</br>130(等待买家确认收货),</br>140(买家已签收，货到付款专用),</br>150(交易成功),</br>230(门店确认收货)|
| createTime   | 字符串     | 是    | 2019-05-05 11:11:22  |订单创建时间，<br/>格式：yyyy-MM-dd HH:mm:ss|
| storesNumber   | 字符串     | 是    | 8065  |服务门店编码|
| totalFee   | 整型     | 是    | 50  |商品总价,单位:分(RMB)|
| postStyle   | 字符串     | 是    | 150  |购买方式:</br>150：送货上门；</br>160：门店自提；</br>170：门店直购 |
| tradesId   | 字符串     | 是    | 1001901550802714310  |51订单号|
| receiverAddress    | 字符串     | 是    | 内蒙古自治区呼和浩特市新城区</br>铁建家园一号楼6单元一层西户  |收货地址|
| realPay   | 字符串     | 是    | 50  |实付款，单位:分(RMB)，</br>即实收金额|
#### 1.8 返回示例(请求成功)
 ``` 
{
  "code": "10000",
  "msg": "成功",
  "data": [
    {
      "discount": 0,//优惠金额
      "tradesSource": "170",//订单来源
      "recevierName": "测试",//收货人姓名
      "file": "2019022288927048769",//处方单号
      "storName": "61^呼市车站西街店",//服务门店名称
      "settlementStatus": "200",//结算状态
      "payStyle": "cash",//支付方式
      "mobile": "13120800149",//会员手机号
      "orderNo": "9e84c3cb6912e4e10169130b60c217b0",//平安交易单号
      "payTime": "2019-05-05 16:50:33",//订单支付时间
      "postFee": 0,//运费，单位:分(RMB)
      "receiverPhone": "13120800149",//联系电话
      "tradesStatus": "230",//交易状态
      "createTime": "2019-05-05 11:11:22",//订单创建时间
      "storesNumber": "8065",//服务门店编码
      "totalFee": 50,//商品总价,单位:分(RMB)
      "postStyle": "150",//购买方式
      "tradesId": 1001901550802714310,//51订单号
      "receiverAddress": "内蒙古自治区呼和浩特市新城区铁建家园一号楼6单元一层西户",//收货地址
      "realPay": 50//实付款，单位:分(RMB)，即实收金
    }
  ]
}
```
#### 1.9 返回示例(请求失败)
```
{
  "code":"20000",
  "msg": "请求失败,缺少必要参数！"
}
```
