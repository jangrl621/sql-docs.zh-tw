---
title: 範例指定 ID 和 IDREF 指示詞 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- IDREF directive
- ID directive
ms.assetid: 7ff1ea73-71ca-4786-bd42-564f1b5de2d9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76e471b3e6e35e3c6f0568c446b9650466ffa542
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006693"
---
# <a name="example-specifying-the-id-and-idref-directives"></a>範例指定 ID 和 IDREF 指示詞

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

此範例幾乎與＜ [指定 ELEMENTXSINIL 指示詞](../../relational-databases/xml/example-specifying-the-elementxsinil-directive.md) ＞範例相同。 唯一的差異在於查詢會指定 **ID** 和 **IDREF** 指示詞。 這些指示詞會覆寫 <`OrderHeader`> 和 <`OrderDetail`> 元素中的 **SalesPersonID** 屬性類型。 這會形成內部文件連結。 您需要結構描述，才能查看被覆寫的類型。 因此，查詢會在 FOR XML 子句中指定 **XMLDATA** 選項，以擷取結構描述。  
  
```sql
USE AdventureWorks2012;  
GO  
SELECT  1 as Tag,  
        0 as Parent,  
        SalesOrderID  as [OrderHeader!1!SalesOrderID!id],  
        OrderDate     as [OrderHeader!1!OrderDate],  
        CustomerID    as [OrderHeader!1!CustomerID],  
        NULL          as [SalesPerson!2!SalesPersonID],  
        NULL          as [OrderDetail!3!SalesOrderID!idref],
        NULL          as [OrderDetail!3!LineTotal],  
        NULL          as [OrderDetail!3!ProductID],  
        NULL          as [OrderDetail!3!OrderQty]  
FROM   Sales.SalesOrderHeader  
WHERE  SalesOrderID=43659 or SalesOrderID=43661  

UNION ALL   
SELECT 2 as Tag,  
       1 as Parent,  
        SalesOrderID,   
        NULL,  
        NULL,  
        SalesPersonID,    
        NULL,           
        NULL,           
        NULL,  
        NULL           
FROM   Sales.SalesOrderHeader  
WHERE  SalesOrderID=43659 or SalesOrderID=43661  

UNION ALL  
SELECT 3 as Tag,  
       1 as Parent,  
        SOD.SalesOrderID,  
        NULL,  
        NULL,  
        SalesPersonID,  
        SOH.SalesOrderID,  
        LineTotal,  
        ProductID,  
        OrderQty     
FROM    Sales.SalesOrderHeader SOH,
        Sales.SalesOrderDetail SOD  
WHERE   SOH.SalesOrderID = SOD.SalesOrderID  
AND     (SOH.SalesOrderID=43659 or SOH.SalesOrderID=43661)
ORDER BY [OrderHeader!1!SalesOrderID!id],
         [SalesPerson!2!SalesPersonID],  
         [OrderDetail!3!SalesOrderID!idref],
         [OrderDetail!3!LineTotal]

FOR XML EXPLICIT, XMLDATA;
```  
  
 以下是部份結果。 請注意在結構描述中，**ID** 和 **IDREF** 指示詞已覆寫 <`OrderHeader`> 和 <`OrderDetail`> 元素中 **SalesOrderID** 屬性的資料類型。 如果您移除這些指示詞，結構描述就會傳回這些屬性的原始類型。  
  
```xml
<Schema
       name="Schema1"
       xmlns="urn:schemas-microsoft-com:xml-data"
       xmlns:dt="urn:schemas-microsoft-com:datatypes">  
  <ElementType name="OrderHeader" content="mixed" model="open">  
    <AttributeType name="SalesOrderID" dt:type="id" />  
    <AttributeType name="OrderDate" dt:type="dateTime" />  
    <AttributeType name="CustomerID" dt:type="i4" />  
    <attribute type="SalesOrderID" />  
    <attribute type="OrderDate" />  
    <attribute type="CustomerID" />  
  </ElementType>  
  <ElementType name="SalesPerson" content="mixed" model="open">  
    <AttributeType name="SalesPersonID" dt:type="i4" />  
    <attribute type="SalesPersonID" />  
  </ElementType>  
  <ElementType name="OrderDetail" content="mixed" model="open">  
    <AttributeType name="SalesOrderID" dt:type="idref" />  
    <AttributeType name="LineTotal" dt:type="number" />  
    <AttributeType name="ProductID" dt:type="i4" />  
    <AttributeType name="OrderQty" dt:type="i2" />  
    <attribute type="SalesOrderID" />  
    <attribute type="LineTotal" />  
    <attribute type="ProductID" />  
    <attribute type="OrderQty" />  
  </ElementType>  
</Schema>  
<OrderHeader
       xmlns="x-schema:#Schema1"
       SalesOrderID="43659"
       OrderDate="2001-07-01T00:00:00"
       CustomerID="676">  
  <SalesPerson SalesPersonID="279" />  
  <OrderDetail
         SalesOrderID="43659"
         LineTotal="10.373000"
         ProductID="712"
         OrderQty="2" />  
  ...  
</OrderHeader>  
...  
```  
  
## <a name="see-also"></a>另請參閱  
 [搭配 FOR XML 使用 EXPLICIT 模式](../../relational-databases/xml/use-explicit-mode-with-for-xml.md)  
  
  
