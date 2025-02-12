---
title: '@@DBTS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@DBTS_TSQL'
- '@@DBTS'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@DBTS function'
- timestamp data type
ms.assetid: 91842ddd-91c0-4445-a03f-116f6bc991d0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 61743139f35ed3e8a5dd4bbac9bd1f4660cb2ec2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68136034"
---
# <a name="x40x40dbts-transact-sql"></a>&#x40;&#x40;DBTS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

此函式會傳回目前資料庫的目前 **timestamp** 資料類型值。 目前的資料庫將會有保證唯一的時間戳記值。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```
@@DBTS  
```  
  
## <a name="return-types"></a>傳回類型
**varbinary**
  
## <a name="remarks"></a>Remarks  
@@DBTS 會傳回前次使用的目前資料庫時間戳記值。 插入或更新含有 **timestamp** 資料行的資料列會產生新的時間戳記值。
  
變更交易隔離等級不會影響 @@DBTS 函式。
  
## <a name="examples"></a>範例  
此範例會傳回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫目前的 **timestamp**。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@DBTS;  
```  
  
## <a name="see-also"></a>另請參閱
[組態函式 &#40;Transact-SQL&#41;](../../t-sql/functions/configuration-functions-transact-sql.md)  
[資料指標並行 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/properties/cursor-concurrency-odbc.md)  
[資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
[MIN_ACTIVE_ROWVERSION &#40;Transact-SQL&#41;](../../t-sql/functions/min-active-rowversion-transact-sql.md)
  
  
