## 订单同步接口
### 1.订单实时推送
#### 1.1 接口描述
* 实时推送订单信息到商户方，暂定付款成功或退款成功状态推送订单信息，或由双方进一步确认其它状态
* 付款推送或退款推送的属性都保持一致，属性值有局部差异
* 同订单的付款推送和退款推送的订单号保持一致
* 提供每小时批量推送过去一小时因任何原因推送失败的订单
* 提供每天23点批量推送过去一天因任何原因推送失败的订单
#### 1.2 请求方式
> POST
#### 1.3 url
ERP：
> /orders/receive
#### 1.4 数据方向
> 线上系统-->ERP
#### 1.5 请求参数(JSON)
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---  |   :-------    |    :---   | :---        | :---        |
| siteId   | 字符串     | 是            | 100150   |商户ID|
| tradesId   | 字符串     | 是            | 1002241501752197580   |订单唯一标识(pre:tId)|
| realPay   | 整型     | 是    | 120   |实付款，单位:分(RMB)，即实收金额|
| receiverName   | 字符串    | 是    | 老王  | 收货人姓名|
| receiverMobile   | 字符串     | 是    | 13800001111   | 收货人手机 |
| receiverAddress   | 字符串     | 是    | 北美市美帝路111号   | 收货人地址 |
| postFee   | 整型     | 是    | 150   | 运费，单位:分(RMB) |
| goodsPrice   | 整型     | 是    | 1500   | 商品价格，单位:分(RMB)(pre:gprice) |
| goodsSpecification   | 字符串     | 是    | 10mg*100s   | 商品规格(pre:gsc) |
| goodsCode   | 字符串     | 是    | 20058962   | 商品编码(pre:gcode) |
| goodsNumber   | 整型     | 是    | 1   | 购买数量(pre:gnum) |
| discount   | 整型     | 否    | 1   | 优惠金额，单位:分(RMB) |
| paystyle   | 字符串     | 是    | wx   | 支付方式::</br>ali (支付宝) ，</br>wx (微信)，</br> bil(快钱)，</br> unionPay(银联)，</br> health_insurance（医保），</br>cash（现金）,</br>prePaid(储值卡),</br>coupon(购物券) |
| poststyle   | 字符串     | 否    | 170   | 购买方式::</br>150：送货上门；</br>160：门店自提；</br>170：门店直购 |
| storeNumber   | 字符串     | 否    | 120   | 门店编码(pre:uid) |
| storeUserMobile   | 字符串     | 否    | 13833334444   | 下单店员手机 |
| totalPay   | 整型     | 是    | 180   | 总金额(商品金额+运费)，单位:分(RMB)，即应收金额 |
| totalFee   | 整型     | 否    | 180   | 商品金额，单位:分(RMB) |
| tradesSource   | 整型     | 否    | 160   | 订单来源: </br>110 (网站)，</br>120（微信），</br>130（app）, </br>140（店员帮用户下单）,</br>160 (支付宝生活号)，</br>170 (平安健康)，</br>9999（其它） |
| memberMobile   | 字符串     | 是    |  13833334444  | 订单所属会员手机 |
| memberName   | 字符串     | 是    |  老王  | 订单所属会员姓名 |
| status   | 整型     | 是    | 1   | 订单状态::1：已付款（未退款），0：已退款 |
| cardNo   | 字符串     | 否    | 100159   | 会员卡号 |
| orderCreateTime   | 时间     | 是    | 2019-01-23 12:43:43   | 订单创建时间，<br/>格式：yyyy-MM-dd HH:mm:ss|
| orderPaymentTime   | 时间     | 是    | 2019-01-23 12:43:43   | 订单支付时间，<br/>格式：yyyy-MM-dd HH:mm:ss|
| drugName   | 字符串     | 否    | 肾石通颗粒   | 药品通用名 |
| goodsCompany   | 字符串     | 否    | 辉瑞制药有限公司   | 生产厂家 |
| barCode   | 字符串     | 否    | 6923404010175   | 条形码 |

--------------------- 
#### 1.6 返回参数(JSON)
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---  |   :-------    |    :---   | :---        | :---        |
| code   | 字符串     | 是            | 10000   |返回结果标识::10000:成功,20000:失败|
| msg   | 字符串     | 是    | 推送成功   |返回结果描述|
#### 1.7 请求示例
 ``` 
{
  "msg": "订单查询成功",
  "code": 10000,//10000:成功，20000：失败
  "data":
    {
        "realPay": 180,//实付款，即实收金额
        "receiverName": "老王",//收货人姓名
        "receiverMobile": "13800001111",//收货人手机号码
        "postFee": 0,//运费
        "discount": 0,//优惠金额
        "payList": [
        {
           "paystyle": "wx",//支付方式:ali (支付宝) ，wx (微信)， bil(快钱)， unionPay(银联)， health_insurance（医保），cash（现金），prePaid(储值卡),coupon(购物券)
           "paymentAmount": 100
        },
        {
           "paystyle": "wx",//支付方式:ali (支付宝) ，wx (微信)， bil(快钱)， unionPay(银联)， health_insurance（医保），cash（现金），prePaid(储值卡),coupon(购物券)
           "paymentAmount": 80
        }
        ],
        "drugName":"肾石通颗粒",//药品通用名
        "goodsCompany":"辉瑞制药有限公司",//厂家
        "barCode":"6923404010175",//条形码
        "poststyle": 170,//购买方式::150：送货上门；160：门店自提；170：门店直购
        "tradesId": 1002241501752197580,//订单编号
        "siteId": "100150",//商户ID
        "storeNumber": "123",//门店编码
        "storeUserMobile":"13811112222",//下单店员手机
        "totalPay": 180,//商品金额+运费，即应收金额
        "totalFee": 180,//商品金额
        "receicerAddress": "",//收货地址
        "tradesSource":"160",//订单来源
        "memberMobile": "13800001111",//订单所属会员手机号码
        "memberName":"老张",//订单所属会员名字
        "status": 1//订单状态：1：已付款（未退款），0：已退款
        "orderCreateTime":"2019-01-23 12:43:43",//订单创建时间
        "orderPaymentTime":"2019-01-23 12:43:43",//订单支付时间
        "goodsList": [//商品列表
          {
            "goodsPrice": 100,//商品价格
            "goodsSpecification": "10mg*100s",//商品规格
            "goodsCode": "32301029",//商品编码
            "goodsNumber": 1//购买数量
            "drugName":"肾石通颗粒",//药品通用名
            "goodsCompany":"辉瑞制药有限公司",//生产厂家
            "barCode":"6923404010175"//条形码
          },
          {
            "goodsPrice": 102,//商品价格
            "goodsSpecification": "10mg*100s",//商品规格
            "goodsCode": "32301039",//商品编码
            "goodsNumber": "1",//购买数量
             "drugName":"肾石通颗粒",//药品通用名
            "goodsCompany":"辉瑞制药有限公司",//生产厂家
            "barCode":"6923404010175"//条形码
          }
        ]
    }
}
```
#### 1.8 返回示例
```
{
  "code":"10000",
  "msg":"推送成功"
}
```
#### 1.9 特殊说明
* storeUserMobile属性目前仅提供给100309
* tradesSource属性目前仅提供给100271
* siteId字段会推送出来，ERP方看需要获取
* drugName,goodsCompany,barCode三个属性目前仅提供给100320
