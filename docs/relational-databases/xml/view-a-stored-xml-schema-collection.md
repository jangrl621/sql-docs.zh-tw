---
title: 檢視儲存的 XML 結構描述集合 | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- schema collections [SQL Server], viewing
- XML schemas [SQL Server], viewing
- CREATE XML SCHEMA COLLECTION statement
- xml_schema_namespace function
- XML schema collections [SQL Server], viewing
- displaying XML schema collections
- viewing XML schema collections
ms.assetid: e38031af-22df-4cd9-a14e-e316b822f91b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e62fd82b302576dfbaf45cbb8073c2e94f7a67e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68096969"
---
# <a name="view-a-stored-xml-schema-collection"></a>檢視儲存的 XML 結構描述集合
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  使用 [CREATE XML SCHEMA COLLECTION](../../t-sql/statements/create-xml-schema-collection-transact-sql.md)匯入 XML 結構描述集合之後，即會將結構描述元件儲存在中繼資料中。 您可以使用 [xml_schema_namespace](../../t-sql/xml/xml-schema-namespace.md)內建函數以重建 XML 結構描述集合。 這個函數會傳回 **xml** 資料類型執行個體。  
  
 例如，下列查詢會從`ProductDescriptionSchemaCollection`資料庫的生產關聯式結構描述擷取 XML 結構描述集合 ( [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] )。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection')  
GO  
```  
  
 如果您只想查看 XML 結構描述集合的一個結構描述，則可以針對 **傳回的** xml `xml_schema_namespace`類型結果指定 XQuery。  
  
```  
SELECT xml_schema_namespace(N'RelationalSchemaName',N'XmlSchemaCollectionName').query('  
/xs:schema[@targetNamespace="TargetNameSpace"]  
')  
GO  
```  
  
 例如，下列查詢可從 `ProductDescriptionSchemaCollection` XML 結構描述集合擷取產品保證和維護 XML 結構描述資訊。  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection').query('  
/xs:schema[@targetNamespace="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain"]  
')  
GO  
```  
  
 您也可以將選擇性的目標命名空間當做第三個參數傳遞至 `xml_schema_namespace` 函數，以擷取集合中的特定結構描述，如下列查詢所示：  
  
```  
SELECT xml_schema_namespace(N'Production',N'ProductDescriptionSchemaCollection', N'https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelWarrAndMain')  
GO  
```  
  
 當使用資料庫中的 CREATE XML SCHEMA COLLECTION 來建立 XML 結構描述集合時，陳述式會在中繼資料內儲存結構描述元件。 請注意只會儲存 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可辨識的結構描述元件。 不會儲存任何註解或非 XSD 屬性。 因此， **xml_schema_namespace** 重新建構的結構描述在功能上等於原始結構描述，但是它看起來不一定相同。 例如，您將看不到與原始結構描述中相同的前置詞。 **xml_schema_namespace** 傳回的結構描述使用 **t** 作為目標命名空間以及其他命名空間 **ns1**、 **ns2**等的前置詞。  
  
 如果您想要保留一份完全相同的 XML 結構描述，您應該將 XML 結構描述儲存在檔案或資料庫資料表的 **xml** 類型資料行中。  
  
 [sys.xml_schema_collections](../../relational-databases/system-catalog-views/sys-xml-schema-collections-transact-sql.md) 目錄檢視也會傳回 XML 結構描述集合的資訊。 此資訊包含集合的名稱、建立日期以及集合的擁有者。  
  
## <a name="see-also"></a>另請參閱  
 [XML 結構描述集合 &#40;SQL Server&#41;](../../relational-databases/xml/xml-schema-collections-sql-server.md)  
  
  
