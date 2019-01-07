## 订单信息推送结构
### 1.实时推送线上订单信息至商户方
#### 1.1 结构描述
* 该过程由b_trades,b_trades_goods两个表构成
* 实时推送订单信息到商户方，暂定付款成功或退款成功状态实时推送订单信息，或由双方进一步确认其它状态
* 付款推送或退款推送的字段都保持一致，字段值有局部差异
* 同订单的付款推送和退款推送的订单号保持一致
* 提供每小时批量推送过去一小时因任何原因推送失败的订单
* 提供每天23点批量推送过去一天因任何原因推送失败的订单
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
| trades_source   | 下单来源     | 整型    | 160    |订单来源: </br>110 (网站)，</br>120（微信），</br>130（app）, </br>140（店员帮用户下单）,</br>160 (支付宝生活号)，</br>9999（其它）|
| trades_status   | 订单状态     | 整型    | 11    |订单状态：1：已付款（未退款），0：已退款|
| receiver_name   | 收货人名称     | 字符串    | 20    |收货人名称|
| receiver_mobile   | 收货人手机     | 字符串    | 20    |收货人手机|
| receiver_address   | 收货人地址     | 字符串    | 255    |收货人地址|
| create_time   |      | timestamp    |     | |
| update_time   |      | timestamp    |     | |
--------------------- 
```
script for ms-sqlserver
------------------------
create table b_trades
(
 trades_id varchar(20) not null
  primary key,
 unit_id varchar(11) not null,
 total_pay numeric(16,4),
 pay_style varchar(30),
 post_style numeric(16,4),
 discount numeric(16,4),
 goods_fee numeric(16,4),
 post_fee numeric(16,4),
 member_mobile varchar(20),
 trades_source int(11),
 trades_status int(11),
 receiver_name varchar(20),
 receiver_mobile varchar(20),
 receiver_address varchar(255),
 update_time datetime,
 create_time datetime
)
```
#### 1.6 商品表(b_trades_goods)结构
| 字段名称 | 字段释义 | 数据类型 | 长度 | 备注 | 
| :---         |     :---      |     :--- | :---      | :---      | 
| trades_id   | 订单ID     | 字符串    | 20    |订单唯一标识|
| goods_code   | 商品编码     | 字符串    | 20    | |
| goods_price   | 商品价格     | 整型    | 11    |商品价格，单位:分(RMB)|
| goods_specification   | 商品规格     | 字符串    | 255    |  |
| goods_num   | 商品购买数量     | 整型    | 11    | |
--------------------- 
```
script for ms-sqlserver
------------------------
create table b_trades_goods
(
 trades_id varchar(20) not null
  primary key,
 goods_code varchar(20),
 goods_price numeric(16,4),
 goods_specification varchar(255),
 goods_num numeric(16,4)
)
```
#### 1.7 特殊说明
* store_user_mobile字段目前仅提供给100309
* trades_source字段目前仅提供给100271
