---
title: ISNUMERIC (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ISNUMERIC
- ISNUMERIC_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- expressions [SQL Server], valid numeric type
- numeric data
- ISNUMERIC function
- verifying valid numeric type
- valid numeric type [SQL Server]
- checking valid numeric type
ms.assetid: 7aa816de-529a-4f6c-a99f-4d5a9ef599eb
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4771c6d611292157caf8247288f36648c8ad5179
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68109393"
---
# <a name="isnumeric-transact-sql"></a>ISNUMERIC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  判斷運算式是否為有效的數值類型。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
ISNUMERIC ( expression )  
```  
  
## <a name="arguments"></a>引數  
 *expression*  
 為要評估的[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。  
  
## <a name="return-types"></a>傳回類型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 當輸入運算式評估為有效數值資料類型時，ISNUMERIC 就會傳回 1，否則便傳回 0。 有效的[數值資料類型](../../t-sql/data-types/numeric-types.md)包括下列各種類型：  

|||
|-|-|
| [精確數值](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md) | **bigint**、**int**、**smallint**、**tinyint**、**bit** |
| [固定有效位數](../../t-sql/data-types/decimal-and-numeric-transact-sql.md) | **decimal**、**numeric** |
| [Approximate](../../t-sql/data-types/float-and-real-transact-sql.md) | **float**、**real** |
| [貨幣值](../../t-sql/data-types/money-and-smallmoney-transact-sql.md) | **money**、 **smallmoney** |

  
> [!NOTE]  
>  ISNUMERIC 會針對某些不是數字的字元傳回 1，例如加號 (+)、減號 (-) 和有效貨幣符號 (如錢幣符號 ($))。 如需貨幣符號的完整清單，請參閱 [money 和 smallmoney &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/money-and-smallmoney-transact-sql.md)。  
  
## <a name="examples"></a>範例  
 下列範例會使用 `ISNUMERIC`，傳回所有非數值的郵遞區號。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT City, PostalCode  
FROM Person.Address   
WHERE ISNUMERIC(PostalCode)<> 1;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例會使用 `ISNUMERIC`，傳回所有非數值的郵遞區號。  
  
```  
USE master;  
GO  
SELECT name, isnumeric(name) AS IsNameANumber, database_id, isnumeric(database_id) AS IsIdANumber   
FROM sys.databases;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [系統函數 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)  
  
  

