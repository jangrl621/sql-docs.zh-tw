---
title: DROP SYNONYM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/26/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP SYNONYM
- DROP_SYNONYM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting synonyms
- synonyms [SQL Server], removing
- removing synonyms
- DROP SYNONYM statement
- dropping synonyms
ms.assetid: 23578932-e4de-4c39-a5a0-ce45139c4269
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 59c26a7e490edb120d8819d8e2b16158b5b41e76
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072133"
---
# <a name="drop-synonym-transact-sql"></a>DROP SYNONYM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  從指定的結構描述中移除同義字。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
DROP SYNONYM [ IF EXISTS ] [ schema. ] synonym_name  
```  
  
## <a name="arguments"></a>引數  
 *IF EXISTS*  
**適用於**：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至[目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 只有在同義字已存在時，才能有條件地將其卸除。  
  
 *schema*  
 指定同義字所在的結構描述。 如果未指定 schema，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會使用目前使用者的預設結構描述。  
  
 *synonym_name*  
 這是要卸除的同義字名稱。  
  
## <a name="remarks"></a>Remarks  
 同義字參考並未與結構描述繫結；因此，您可以隨時卸除同義字。 不過已卸除的同義字之參考，只有在執行階段才找得到。  
  
 動態 SQL 中的同義字可以建立、卸除和參考。  
  
## <a name="permissions"></a>權限  
 使用者至少必須符合下列一個條件，才能卸除同義字。 使用者必須是：  
  
-   同義字的目前擁有者。  
  
-   對同義字擁有 CONTROL 權限的被授與者。  
  
-   對包含結構描述擁有 ALTER SCHEMA 權限的被授與者。  
  
## <a name="examples"></a>範例  
 下列範例會先建立一個同義字 `MyProduct`，再卸除該同義字。  
  
```  
USE tempdb;  
GO  
-- Create a synonym for the Product table in AdventureWorks2012.  
CREATE SYNONYM MyProduct  
FOR AdventureWorks2012.Production.Product;  
GO  
-- Drop synonym MyProduct.  
USE tempdb;  
GO  
DROP SYNONYM MyProduct;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE SYNONYM &#40;Transact-SQL&#41;](../../t-sql/statements/create-synonym-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  
