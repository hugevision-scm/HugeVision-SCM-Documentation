# API210COB

##### [文档首页](../index.md)>[HugeVision-SCM API开发手册向导页](../api.md)>API210COB

---

## API概述

创建 **Sellout** 并单据操作提交。

|功能类型|处理类型|
|:--|:--|
|创建业务数据|异步|

**此API调用后，还得调用API210NNF查询处理结果。**

##  Request

 ```POST```  https://*{ HVS的URL }*/api/v1/processes/**importdealerselloutorder_co_b**
  
###  Request Header

请参考API共通

###  Request Body

做成如下JSON格式，与API210COF相同

|名称|类型|长度|必填项|附注|
|:--|:--|:--|:--|:--|
|requestId|string|36|✓|每次处理唯一的ID|
|requestTime|timestamp|19|✓|请求时间。格式为yyyy-MM-dd hh24:mi:ss。|
|docList|list||✓|单据列表|
|&nbsp; &nbsp; docNo|string|20|✓|外部系统的单据号|
|&nbsp; &nbsp; org_Text|string|60||组织的编码/名称/编码_名称。不填写时取得登录用户组织。|
|&nbsp; &nbsp; doctype_Name|string|60||单据类型的名称。<br>可填写如下单据类型<br>&nbsp; 销售订单-Sellout|
|&nbsp; &nbsp; dateOrdered|date|10||订单日期。格式为yyyy-MM-dd。不填写时取得当前日期。|
|&nbsp; &nbsp; description|string|255||单据的附注|
|&nbsp; &nbsp; bpartner_Value|string|40|条件|业务伙伴的编码。编码或名称为必填。|
|&nbsp; &nbsp; bpartner_Name|string|60|条件|业务伙伴的名称。编码或名称为必填。|
|&nbsp; &nbsp; priceList_Text|string|60||价格表的名称。不填写时取得业务伙伴的价格表。|
|&nbsp; &nbsp; lineList|list||✓|单据行列表|
|&nbsp; &nbsp; &nbsp; &nbsp; lineId|string|20||外部系统的行号|
|&nbsp; &nbsp; &nbsp; &nbsp; product_Value|string|40|条件|产品的编码。编码或名称为必填。|
|&nbsp; &nbsp; &nbsp; &nbsp; product_Name|string|60|条件|产品的名称。编码或名称为必填。|
|&nbsp; &nbsp; &nbsp; &nbsp; qty|bigdecimal|16,6|✓|数量。允许正负数。不允许为0。|
|&nbsp; &nbsp; &nbsp; &nbsp; price|bigdecimal|16,6||单价。必须大于等于0。不填写时取得价格表维护的价格。|
|&nbsp; &nbsp; &nbsp; &nbsp; lineDescription|string|255||单据行的附注|

JSON格式样例
```
(待补充)
```

##  Response
 
###  Response Header

无特别描述

###  Response Body

* 处理成功时返回如下JSON数据

|名称|类型|长度|必填项|附注|
|:--|:--|:--|:--|:--|
|requestId|string|36|✓|Request的ID|
|requestResult|string|1|✓|请求结果<br>&nbsp; 1:成功|
|responseTime|timestamp|19|✓|响应时间。格式为yyyy-MM-dd hh24:mi:ss。|
|errorMsg|string|255|✓|处理消息<br>&nbsp; 异步处理提交成功|

JSON格式样例(导入成功)
```
{
    "requestId": "API210CO-0000-0000-0000-000000000001",
    "requestResult": "1",
    "responseTime": "2021-11-30 12:00:00",
    "errorMsg": "异步处理提交成功"
}
```