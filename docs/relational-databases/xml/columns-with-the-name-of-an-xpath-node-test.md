---
title: 具有 XPath 節點測試名稱的資料行 | Microsoft 文件
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
- XPath node test
ms.assetid: b48adccd-3b6b-486a-b326-20f57170186f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e1b4811e15d9f6927d06a4d4f9ff99466eb164c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68112913"
---
# <a name="columns-with-the-name-of-an-xpath-node-test"></a>具有 XPath 節點測試名稱的資料行
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  如果資料行名稱是其中一個 XPath 節點測試，將會對應內容，如下表所示。 如果資料行名稱是 XPath 節點測試，會將內容對應至對應的節點。 如果資料行的 SQL 類型是 **xml**，就會傳回錯誤。  
  
|資料行名稱|行為|  
|-----------------|--------------|  
|text()|對於有 text() 名稱的資料行，將會以文字節點加入該資料行中的字串值。|  
|comment()|對於有 comment() 名稱的資料行，將會以 XML 註解加入該資料行中的字串值。|  
|node()|對於有 node() 名稱的資料行，其結果與資料行名稱為萬用字元 (*) 的結果相同。|  
|processing-instruction(name)|對於有處理指示名稱的資料行，將會以處理指示目標名稱的 PI 值加入該資料行中的字串值。|  
  
 下列查詢會將節點測試的用途顯示為資料行名稱。 它會在產生的 XML 中加入文字節點和註解。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT E.BusinessEntityID "@EmpID",   
        'Example of using node tests such as text(), comment(), processing-instruction()'                as "comment()",  
        'Some PI'                   as "processing-instruction(PI)",  
        'Employee name and address data' as "text()",  
        'middle name is optional'        as "EmpName/text()",  
        FirstName                        as "EmpName/First",   
        MiddleName                       as "EmpName/Middle",   
        LastName                         as "EmpName/Last",  
        AddressLine1                     as "Address/AddrLine1",  
        AddressLine2                     as "Address/AddrLIne2",  
        City                             as "Address/City"  
FROM   HumanResources.Employee AS E  
INNER JOIN Person.Person AS P   
    ON P.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.BusinessEntityAddress AS BAE  
    ON BAE.BusinessEntityID = E.BusinessEntityID  
INNER JOIN Person.Address AS A  
    ON BAE.AddressID = A.AddressID  
WHERE  E.BusinessEntityID=1  
FOR XML PATH;  
```  
  
 以下是結果：  
  
 `<row EmpID="1">`  
  
 `<!--Example of using node tests such as text(), comment(), processing-instruction() -->`  
  
 `<?PI Some PI?>`  
  
 `Employee name and address data`  
  
 `<EmpName>middle name is optional`  
  
 `<First>Ken</First>`  
  
 `<Last>Sánchez</Last>`  
  
 `</EmpName>`  
  
 `<Address>`  
  
 `<AddrLine1>4350 Minute Dr.</AddrLine1>`  
  
 `<City>Minneapolis</City>`  
  
 `</Address>`  
  
 `</row>`  
  
## <a name="see-also"></a>另請參閱  
 [搭配 FOR XML 使用 PATH 模式](../../relational-databases/xml/use-path-mode-with-for-xml.md)  
  
  
