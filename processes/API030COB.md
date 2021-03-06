# API030COB

##### [文档首页](../index.md)>[HugeVision-SCM API开发手册向导页](../api.md)>API030COB

---

## API概述

创建 **销售订单** 并单据操作提交。

|功能类型|处理类型|
|:--|:--|
|创建业务数据|异步|

**此API调用后，还得调用API030NNF查询处理结果。**

##  Request

 ```POST```  https://*{ HVS的URL }*/api/v1/processes/**importsalesorder_co_b**
  
###  Request Header

请参考API共通

###  Request Body

做成如下JSON格式，与API030COF相同

|名称|类型|长度|必填项|附注|
|:--|:--|:--|:--|:--|
|requestId|string|36|✓|每次处理唯一的ID|
|requestTime|timestamp|19|✓|请求时间。格式为yyyy-MM-dd hh24:mi:ss。|
|docList|list||✓|单据列表|
|&nbsp; &nbsp; docNo|string|20|✓|外部系统的单据号|
|&nbsp; &nbsp; org_Text|string|60||组织的编码/名称/编码_名称。不填写时取得登录用户组织。|
|&nbsp; &nbsp; doctype_Name|string|60|✓|单据类型的名称。<br>可填写如下单据类型<br>&nbsp; 销售订单-信用<br>&nbsp; 销售订单-预收<br>&nbsp; 销售订单-出口|
|&nbsp; &nbsp; dateOrdered|date|10||订单日期。格式为yyyy-MM-dd。不填写时取得当前日期。|
|&nbsp; &nbsp; salesOpportunity_Text|string|60||销售机会的单据号。|
|&nbsp; &nbsp; description|string|255||单据的附注|
|&nbsp; &nbsp; bpartner_Value|string|40|条件|业务伙伴的编码。编码或名称为必填。|
|&nbsp; &nbsp; bpartner_Name|string|60|条件|业务伙伴的名称。编码或名称为必填。|
|&nbsp; &nbsp; location_Text|string|60|条件|业务伙伴地址的名称。多地址的情况必填。|
|&nbsp; &nbsp; billpartner_Value|string|40||发票伙伴的编码。不填写时取得业务伙伴。|
|&nbsp; &nbsp; billpartner_Name|string|60||发票伙伴的名称。不填写时取得业务伙伴。|
|&nbsp; &nbsp; billLocation_Text|string|60||发票伙伴地址的名称。不填写时取得发票伙伴的发票地址。|
|&nbsp; &nbsp; tradeTerms_Text|string|60|条件|贸易方式的名称。销售订单-出口时必填。<br>可填写如下贸易方式<br>&nbsp; L/C<br>&nbsp; 后T/T<br>&nbsp; 混合式T/T<br>&nbsp; 前T/T|
|&nbsp; &nbsp; warehouse_Text|string|60||仓库的编码/名称。不填写时取得收货地址的发货默认仓库。|
|&nbsp; &nbsp; deliveryViaRule_Text|string|60||发货方式的名称。不填写时取得收货地址的发货方式。<br>可填写如下发货方式<br>&nbsp; 配送<br>&nbsp; 自提<br>&nbsp; 直送|
|&nbsp; &nbsp; shipper_Text|string|60||物流公司的名称。不填写时取得仓库的物流公司。|
|&nbsp; &nbsp; country_Name|string|60||国家的名称。不填写时取得实体的国家。|
|&nbsp; &nbsp; region_Name|string|60|条件|省份的名称。一次性交易时必填。|
|&nbsp; &nbsp; city_Name|string|60|条件|城市的名称。一次性交易时必填。|
|&nbsp; &nbsp; address1|string|60|条件|地址1。一次性交易时必填。|
|&nbsp; &nbsp; address2|string|60||地址2。|
|&nbsp; &nbsp; contact_Name|string|60|条件|联系人的名称。一次性交易时必填。|
|&nbsp; &nbsp; phone|string|60|条件|电话。一次性交易时必填。|
|&nbsp; &nbsp; priceList_Text|string|60||价格表的名称。不填写时取得业务伙伴的价格表。|
|&nbsp; &nbsp; settlementRate|bigdecimal|16,10||结算汇率。不填写时取得订单日期当天的汇率。|
|&nbsp; &nbsp; isFixedRate|string|1||固定汇率。格式为Y/N。不填写时为N。|
|&nbsp; &nbsp; lineList|list||✓|单据行列表|
|&nbsp; &nbsp; &nbsp; &nbsp; lineId|string|20||外部系统的行号|
|&nbsp; &nbsp; &nbsp; &nbsp; locator_Text|string|60||库位的编码/名称/编码_名称。不填写时取得仓库的默认库位。|
|&nbsp; &nbsp; &nbsp; &nbsp; product_Value|string|40|条件|产品的编码。编码或名称为必填。|
|&nbsp; &nbsp; &nbsp; &nbsp; product_Name|string|60|条件|产品的名称。编码或名称为必填。|
|&nbsp; &nbsp; &nbsp; &nbsp; qty|bigdecimal|16,6|✓|数量。必须大于0。|
|&nbsp; &nbsp; &nbsp; &nbsp; price|bigdecimal|16,6||单价。必须大于0。不填写时取得价格表维护的价格。|
|&nbsp; &nbsp; &nbsp; &nbsp; tax_Text|string|60||税率的名称/附注。不填写时取得产品的税率。|
|&nbsp; &nbsp; &nbsp; &nbsp; lineDescription|string|255||单据行的附注|

JSON格式样例
```
(待补充)
```

##  Response
 
###  Response Header

无特别描述

###  Response Body

创建业务数据异步处理的响应格式

&nbsp;&nbsp;&nbsp;&nbsp;→&nbsp;[响应格式&样例](Response_Body_01.md)

