---
title: UPPER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- UPPER_TSQL
- UPPER
dev_langs:
- TSQL
helpviewer_keywords:
- UPPER function
- characters [SQL Server], lowercase
- converting lowercase to uppercase
- uppercase characters [SQL Server]
- characters [SQL Server], uppercase
- lowercase characters
ms.assetid: 5ced55f7-ac89-4cf2-9465-f63f4dc480db
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d91870e53e5976ba5d52b83f086a57fa552ad1ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67927621"
---
# <a name="upper-transact-sql"></a>UPPER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回小寫字元資料轉換成大寫的字元運算式。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
UPPER ( character_expression )  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 這是字元資料的[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 *character_expression* 可以是字元或二進位資料的常數、變數或資料行。  
  
 *character_expression* 必須是可以隱含轉換成 **varchar** 的資料類型。 否則，請使用 [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) 來明確轉換 *character_expression*。  
  
## <a name="return-types"></a>傳回類型  
 **varchar** 或 **nvarchar**  
  
## <a name="examples"></a>範例  
 下列範例會利用 `UPPER` 和 `RTRIM` 函數來傳回 `dbo.DimEmployee` 資料表中的人員姓氏，因此，這些姓氏是大寫、修剪過，且與名字串連起來。  
  
```  
-- Uses AdventureWorks  
  
SELECT UPPER(RTRIM(LastName)) + ', ' + FirstName AS Name  
FROM dbo.DimEmployee  
ORDER BY LastName;  
```  
  
 以下為部分結果集。  
  
 ```
Name
------------------------------
ABBAS, Syed
ABERCROMBIE, Kim
ABOLROUS, Hazem
 ```  
  
## <a name="see-also"></a>另請參閱  
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [字串函數 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
 [LOWER &#40;Transact-SQL&#41;](../../t-sql/functions/lower-transact-sql.md)  
  
  

