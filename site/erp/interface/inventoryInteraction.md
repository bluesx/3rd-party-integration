## 盘点系统接口交互
### 交互图
![](https://jkosshash.oss-cn-shanghai.aliyuncs.com/inventoryInteractive.png)
<br/>
### 交互说明
* 1.线上系统创建盘点计划，创建就绪即从ERP读取库存商品数据。
* 2.线上系统成功读取盘点商品数据之后，各门店执行盘点。
* 3.门店盘点完成，审批盘点单，审批通过通知到ERP。
* 4.ERP接收到盘点完成通知，读取线上系统盘点单数据，ERP尝试生成差异。



