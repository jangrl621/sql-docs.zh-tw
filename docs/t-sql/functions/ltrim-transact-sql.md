---
title: LTRIM (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LTRIM
- LTRIM_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- leading blanks
- deleting blank spaces
- characters [SQL Server], blanks
- removing blank spaces
- LTRIM function
- blank characters [SQL Server]
ms.assetid: 369ed340-1a09-4597-a9eb-6720156cd39a
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0f3e52b291c9a91e1135d41ab6843ef97f53d17d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68130379"
---
# <a name="ltrim-transact-sql"></a>LTRIM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回移除開頭空白的字元運算式。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
LTRIM ( character_expression )  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 這是字元或二進位資料的[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 *character_expression* 可以是常數、變數或資料行。 *character_expression* 必須是可隱含地轉換為 **varchar**的資料類型，但是 **text** **ntext** 和 **image** 除外。 否則，請使用 [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) 來明確轉換 *character_expression*。  
  
## <a name="return-type"></a>傳回類型  
 **varchar** 或 **nvarchar**  
  
## <a name="examples"></a>範例  

### <a name="a-simple-example"></a>A. 簡單範例   

 下列範例會利用 LTRIM 來移除字元運算式中的開頭空白。  
  
```sql  
SELECT LTRIM('     Five spaces are at the beginning of this string.') FROM sys.databases;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 ---------------------------------------------------------------  
  Five spaces are at the beginning of this string.
  ```  

### <a name="b-example-using-a-variable"></a>B：使用變數的範例   
  
 下列範例會利用 `LTRIM` 來移除字元變數中的開頭空白。  
  
```  
DECLARE @string_to_trim varchar(60);  
SET @string_to_trim = '     5 spaces are at the beginning of this string.';  
SELECT 
    @string_to_trim AS 'Original string',
    LTRIM(@string_to_trim) AS 'Without spaces';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Original string Without spaces
--------------------------------------------------- ---------------------------------------------
     5 spaces are at the beginning of this string.  5 spaces are at the beginning of this string.
```  
  
## <a name="see-also"></a>另請參閱  
 [LEFT &#40;Transact-SQL&#41;](../../t-sql/functions/left-transact-sql.md)  
 [RIGHT &#40;Transact-SQL&#41;](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM &#40;Transact-SQL&#41;](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT &#40;Transact-SQL&#41;](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING &#40;Transact-SQL&#41;](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM &#40;Transact-SQL&#41;](../../t-sql/functions/trim-transact-sql.md)  
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [字串函數 &#40;Transact-SQL&#41;](../../t-sql/functions/string-functions-transact-sql.md)  
  
  


