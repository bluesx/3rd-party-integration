## 订单信息推送结构
### 1.实时推送线上订单信息至商户方数据库
#### 1.1 结构描述
> * 系统方订单已支付，已退款时触发订单同步到商户方ERP.
> * 该过程由b_trades,b_trades_goods两个表构成
#### 1.2 请求方式
> sql-insert,sql-update
#### 1.3 url
> 商户方数据库地址，端口，数据库名称，访问用户，访问密码
#### 1.4 数据方向
> 系统方至商户方
#### 1.5 订单表(b_trades)结构
| 字段名称 | 字段释义 | 数据类型 | 长度 | 备注 | 
| :---         |     :---      |     :--- | :---      | :---      | 
| trades_id   | 订单ID     | 字符串    | 20    |订单唯一标识|
| unit_id   | 门店编码     | 字符串    | 20    |商户下单门店编码，商户范围内唯一|
| store_user_mobile   | 店员手机     | 字符串    | 20    |本订单下单店员手机|
| total_pay   | 实付款     | 整型    | 11    |实付金额，单位:分(RMB)|
| pay_style   | 支付方式     | 字符串    | 30    |ali (支付宝) ，wx (微信)， </br>bil(快钱)， unionPay(银联)，</br> health_insurance（医保），cash（现金）|
| post_style   | 配送方式     | 整型    | 11    |商户门店编码，商户范围内唯一|
| discount   | 优惠金额     | 整型    | 11    |优惠金额，单位:分(RMB)|
| goods_fee   | 商品金额     | 整型    | 11    |商品金额，单位:分(RMB)|
| post_fee   | 运费     | 整型    | 11    |实付金额，单位:分(RMB)|
| member_mobile   | 下单会员手机     | 字符串    | 20    |下单会员手机|
| trades_status   | 订单状态     | 整型    | 11    |订单状态：1：已付款（未退款），0：已退款|
| receiver_name   | 收货人名称     | 字符串    | 20    |收货人名称|
| receiver_mobile   | 收货人手机     | 字符串    | 20    |收货人手机|
| receiver_address   | 收货人地址     | 字符串    | 255    |收货人地址|
| create_time   |      | timestamp    |     | |
| update_time   |      | timestamp    |     | |
--------------------- 
#### 1.6 商品表(b_trades_goods)结构
| 字段名称 | 字段释义 | 数据类型 | 长度 | 备注 | 
| :---         |     :---      |     :--- | :---      | :---      | 
| trades_id   | 订单ID     | 字符串    | 20    |订单唯一标识|
| goods_code   | 商品编码     | 字符串    | 20    | |
| goods_price   | 商品价格     | 整型    | 11    |实付金额，单位:分(RMB)|
| goods_specification   | 商品规格     | 字符串    | 255    |  |
| goods_num   | 商品购买数量     | 整型    | 11    | |
--------------------- 
#### 1.7 特殊说明
* store_user_mobile字段目前仅提供给100309
