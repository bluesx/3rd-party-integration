## 会员系统积分接口交互
### 交互图
![](https://github.com/bluesx/3rd-party-integration/blob/master/site/images/member-points.png)
<br/>
### 交互说明
* 1.线上系统创建盘点计划，创建就绪即从ERP读取库存商品数据。
* 2.线上系统成功读取盘点商品数据之后，各门店开始盘点，盘点过程中，会实时读取当前商品库存数据，对照实际库存
* 3.门店盘点完成之后，开始执行盘点数据回传。
* 4.ERP接收到盘点数据回传，尝试生成差异。



