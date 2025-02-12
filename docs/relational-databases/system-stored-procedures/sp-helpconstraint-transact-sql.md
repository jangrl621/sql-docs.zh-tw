---
title: sp_helpconstraint (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpconstraint
- sp_helpconstraint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpconstraint
ms.assetid: 29d6cd36-535d-4765-bca8-62f9d9886ff5
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d722d3b54c2f0b6d73660e2195aed4039e1eda2c
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771080"
---
# <a name="sphelpconstraint-transact-sql"></a>sp_helpconstraint (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  傳回所有條件約束類型、其使用者自訂或系統提供的名稱、其定義資料行，以及定義條件約束之運算式 (只針對 DEFAULT 和 CHECK 條件約束) 的清單。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helpconstraint [ @objname = ] 'table'   
     [ , [ @nomsg = ] 'no_message' ]   
```  
  
## <a name="arguments"></a>引數  
`[ @objname = ] 'table'`這是要傳回哪些條件約束資訊的資料表。 指定的資料表必須是目前資料庫的本機資料表。 *table*是**Nvarchar (776)** , 沒有預設值。  
  
`[ @nomsg = ] 'no_message'`這是列印資料表名稱的選擇性參數。 *no_message*是**Varchar (5)** , 預設值是**msg**。**nomsg**會抑制列印。  
  
## <a name="return-code-values"></a>傳回碼值  
 0 (成功) 或 1 (失敗)  
  
## <a name="result-sets"></a>結果集  
 如果**sp_helpconstraint**參與主鍵, 則會顯示遞減的索引資料行。 遞減索引資料行會列在結果集中，名稱後面會有一個減號 (-)。 預設值是遞增索引資料行，會單獨列出名稱。  
  
## <a name="remarks"></a>備註  
 執行**sp_help**_資料表_會報告指定之資料表的所有相關資訊。 若只要查看條件約束資訊, 請使用**sp_helpconstraint**。  
  
## <a name="permissions"></a>Permissions  
 需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
 下列範例會顯示 `Product` 資料表的所有條件約束。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpconstraint 'Production.Product';  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料庫引擎預存&#40;程式 transact-sql&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.databases _constraints &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [check_constraints &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [default_constraints &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)  
  
  
