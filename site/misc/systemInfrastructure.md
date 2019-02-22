## 系统部署基础设施

| 设施名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---  |   :-------    |    :---   | :---        | :---        |
| siteId   | 字符串     | 是            | 100150   |商户ID|
| tradesId   | 字符串     | 是            | 1002241501752197580   |订单唯一标识(pre:tId)|
| realPay   | 整型     | 是    | 120   |实付款，单位:分(RMB)，即实收金额|
| receiverName   | 字符串    | 是    | 老王  | 收货人姓名|
| receiverMobile   | 字符串     | 是    | 13800001111   | 收货人手机 |
| receicerAddress   | 字符串     | 是    | 北美市美帝路111号   | 收货人地址 |
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
| orderCreateTime   | 时间     | 是    | 2019-01-23 12:43:43   | 订单创建时间，<br/>格式：yyyy-MM-dd HH:mm:ss|
| orderPaymentTime   | 时间     | 是    | 2019-01-23 12:43:43   | 订单支付时间，<br/>格式：yyyy-MM-dd HH:mm:ss|
---------------------
