## 盘点审批商品数据
### 1.提供盘点审批商品数据查询
#### 1.1 接口描述
* 系统方商户后台审批完成后回传传递盘点差异数量至商户方
* 如果批量传输，暂定单次传输不超过1000个商品
#### 1.2 请求方式
> GET
#### 1.3 触发条件
> 盘点单审批通知成功
#### 1.3 url
* ERP：
> /inventory/approvedGoods
#### 1.4 数据方向
> 线上系统-->ERP
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| inventoryNo   | 字符串     | 是    | PD100190170003    | 盘点单号 |
--------------------- 
#### 1.6 返回参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| code   | 字符串     | 是    | 10000    | 返回代码，10000(查询成功)，20000(查询失败) |
| msg   | 字符串    | 是    | 回传成功    | 返回消息描述 |
| unitNo   | 字符串    | 是    | 1192    | 门店编号 |
| goodsCode   | 字符串    | 是    | AW020785    | 商品编码 |
| drugName   | 字符串    | 是    | 复方黄松洗液    | 药品名称 |
| batchNumber   | 字符串    | 是    | AC321321    | 批号 |
| specification   | 字符串    | 否    | 200毫升    | 规格 |
| manufacturer   | 字符串    | 否    | 国药    | 生产商家 |
| accountQuatity   | 数值    | 是    | 2   | 账面库存数 |
| actualInventoryQuatity   | 数值    | 是    | 12    | 实际盘点数 |
| quality   | 字符串    | 是    | 好    | 质量 |
| inventoryChecker   | 字符串    | 是    | 李浩    | 盘点人(姓名) |
| confirmChecker   | 字符串    | 是    | 李浩    | 监盘人(姓名) |
| auditChecker   | 字符串    | 是    | 李浩   | 审核人(姓名) |
--------------------- 
#### 1.7 请求示例
 ``` 
 "code" : 10000,
 "msg" : "回传成功",
 "data"{
   "inventoryNo":"PD100190170003",//盘点单号
   "inventoryChecker": "李浩",//盘点人(姓名)
   "confirmChecker": "李浩",//监盘人 (姓名)
   "auditChecker": "李浩",//审核人(姓名)
   "unitNo“:"1192",
   "goodsList":[
	{
	  "goodsCode": "AW020785",//商品编码
	  "drugName": "复方黄松洗液",//药品名称（非必传字段）
	  "batchNumber": "AC321321",//批号
	  "specification": "200毫升",//规格（非必传字段）
	  "manufacturer": "国药",//生产商家（非必传字段）
	  "quality":"好",//质量
	  "accountQuatity":"2",//账面库存数
	  "actualInventoryQuatity":"12",//实际盘点数
	 },
	  "goodsCode": "AW020786",//商品编码
	  "drugName": "复方黄松洗液",//药品名称（非必传字段）
	  "batchNumber": "AC321322",//批号
	  "specification": "200毫升",//规格（非必传字段）
	  "manufacturer": "国药",//生产商家（非必传字段）
	  "quality":"好",//质量
	  "accountQuatity":"2",//账面库存数
	  "actualInventoryQuatity":"12",//实际盘点数
	 }
      ]
 }
```
#### 1.8 返回成功(未匹配到库存信息)
```
{
  "code": 10000,
  "data": {},
  "msg":"回传成功"
}
```
#### 1.9 请求失败
```
{
  "code": 20000,
  "data": {},
  "msg":"回传失败，无法匹配商品，商品编码：20056508"
}
```

