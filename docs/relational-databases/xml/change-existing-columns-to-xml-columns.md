---
title: 將現有資料行變更為 XML 資料行 | Microsoft Docs
ms.custom: fresh2019may
ms.date: 05/22/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 605911ebe60c7467db2792737426cc98ce67b52d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68113127"
---
# <a name="change-existing-columns-to-xml-columns"></a>將現有資料行變更為 XML 資料行

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

ALTER TABLE 陳述式支援 **xml** 資料類型。 例如，您可以將任何字串類型資料行修改成 **xml** 資料類型。 請注意在這些情況下，資料行中所包含的文件必須格式正確。 另外，如果您要將資料行的類型從字串變更為具 xml 類型，將會根據指定的 XSD 結構描述來驗證資料行中的文件。  
  
```sql
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max));
GO  
INSERT INTO T   
  VALUES (1, '<Root><Product ProductID="1"/></Root>');
GO  
ALTER TABLE T   
  ALTER COLUMN Col2 xml;
```  
  
您可以將 `xml` 類型的資料行從不具類型的 XML 變更為具 XML 類型。 例如：  
  
```sql
CREATE TABLE T (Col1 int primary key, Col2 xml);
GO  
INSERT INTO T   
  values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>');
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
  ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection);
```  
  
> [!NOTE]  
> 指令碼將會針對 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫來執行，因為所建立的 XML 結構描述集合 `Production.ProductDescriptionSchemaCollection`是屬於 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫的一部份。  
  
 在上述範例中，將會根據指定集合中的 XSD 結構描述，來驗證所有儲存在資料行中的執行個體並設定其類型。 根據指定的結構描述，如果資料行包含一個或多個無效的 XML 執行個體， `ALTER TABLE` 陳述式將會失敗，而且將無法使不具類型的 XML 資料行變更為具類型的 XML。  
  
> [!NOTE]  
> 如果資料表很大，修改 **xml** 類型的資料行可能會很費時。 這是因為每個文件都必須檢查其格式是否正確、是否具 XML 類型，而且也必須加以驗證。  
  
如需具類型之 XML 的詳細資訊，請參閱 [比較具類型的 XML 與不具類型的 XML](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)。  
