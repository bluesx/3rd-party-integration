## 盘点审批商品回传
### 1.获取商品对应门店库存信息
#### 1.1 接口描述
> 系统方商户后台审批完成后回传传递盘点差异数量至商户方
#### 1.2 请求方式
> POST
#### 1.3 触发条件
> 盘点单审批通过
#### 1.3 url
> ERP：
> /inventory/approve
#### 1.4 数据方向
> 系统方至商户方
#### 1.5 请求参数
| 参数名称 | 参数类型 | 是否必须 | 示例值 | 参数描述  |
| :---         |     :---      |     :--- | :--- | :--- |
| pandian_num   | 字符串     | 是    | PD100190170003    | 盘点单号 |
| stores_number   | 字符串    | 是    | 1192    | 门店编号 |
| goods_code   | 字符串    | 是    | AW020785    | 商品编码 |
| drug_name   | 字符串    | 是    | 复方黄松洗液    | 药品名称 |
| batch_number   | 字符串    | 是    | AC321321    | 批号 |
| specif_cation   | 字符串    | 否    | 200毫升    | 规格（非必传字段） |
| goods_company   | 字符串    | 否    | 国药    | 生产商家 |
| inventory_accounting   | 字符串    | 是    | 2   | 账面库存数 |
| actual_store   | 字符串    | 是    | 12    | 实际盘点数 |
| quality   | 字符串    | 是    | 好    | 质量 |
| inventory_checker   | 字符串    | 是    | 李浩    | 盘点人(姓名) |
| confirm_checker   | 字符串    | 是    | 李浩    | 监盘人(姓名) |
| audit_checker   | 字符串    | 是    | 李浩   | 审核人(姓名) |
--------------------- 
#### 1.5 返回参数
暂无要求，可双方协商
#### 1.6 请求示例
 ``` 
[
	{
		“pandian_num“:” PD100190170003”,//盘点单号
“stores_number“:“1192”
“goods_code“: ” AW020785”,//商品编码
“drug_name“: "复方黄松洗液",//药品名称（非必传字段）
“batch_number“: “AC321321”,//批号
“specif_cation“: "200毫升",//规格（非必传字段）
“goods_company“: "国药",//生产商家（非必传字段）
“inventory_accounting“:2,//账面库存数
“actual_store“:12,//实际盘点数
“quality“:“好”,//质量
“inventory_checker“: “李浩”,//盘点人(姓名)
“confirm_checker“: “李浩”,//监盘人 (姓名)
“audit_checker“: “李浩”,//审核人(姓名)
}，
……
]
```
#### 1.7 返回成功(未匹配到库存信息)
```
{
  "code": 1,
  "info": [],
  "msg":"成功"
}
```
#### 1.8 请求失败
```
{
  "code": 0,
  "info": [],
  "msg":"失败,相关原因"
}
```

