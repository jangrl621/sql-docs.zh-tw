---
title: EXP (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- EXP_TSQL
- EXP
dev_langs:
- TSQL
helpviewer_keywords:
- exponential functions
- EXP function
ms.assetid: 5a9b8c52-6fb6-4e33-8b02-a878785b2f51
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 638e9960af007710b7c9a891109597db14227092
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071587"
---
# <a name="exp-transact-sql"></a>EXP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回指定 **float** 運算式的指數值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
EXP ( float_expression )  
```  
  
## <a name="arguments"></a>引數  
 *float_expression*  
 為 **float** 類型或能夠隱含轉換成 **float** 類型的[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。  
  
## <a name="return-types"></a>傳回類型  
 **float**  
  
## <a name="remarks"></a>Remarks  
 常數 **e** (2.718281...) 是自然對數的基底。  
  
 數字的指數，是提升為數字乘冪的常數 **e**。 例如，EXP(1.0) = e^1.0 = 2.71828182845905 和 EXP(10) = e^10 = 22026.4657948067。  
  
 一個數值的自然對數指數，也是該數值本身：EXP (LOG (*n*)) = *n*。 而一個數值的指數自然對數，也是該數值本身：LOG (EXP (*n*)) = *n*。  
  
## <a name="examples"></a>範例  
  
### <a name="a-finding-the-exponent-of-a-number"></a>A. 尋找數字的指數  
 下列範例會宣告一個變數，並且傳回該指定變數的指數值 (`10`) 以及文字描述。  
  
```  
DECLARE @var float  
SET @var = 10  
SELECT 'The EXP of the variable is: ' + CONVERT(varchar,EXP(@var))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------------------------------------------------------  
The EXP of the variable is: 22026.5  
(1 row(s) affected)  
```  
  
### <a name="b-finding-exponentials-and-natural-logarithms"></a>B. 尋找指數和自然對數  
 下列範例會傳回 `20` 之自然對數的指數值，以及 `20` 之指數的自然對數。 由於這些函數互為反向函數，因此傳回值都是 `20`。  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20))  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
---------------------- ----------------------  
20                     20  
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-finding-the-exponent-of-a-number"></a>C. 尋找數字的指數  
 下列範例會傳回指定值的指數 (`10`)。  
  
```  
SELECT EXP(10);  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
----------  
22026.4657948067  
```  
  
### <a name="d-finding-exponential-values-and-natural-logarithms"></a>D. 尋找指數和自然對數  
 下列範例會傳回 `20` 之自然對數的指數值，以及 `20` 之指數的自然對數。 由於這些函數互為反向函數，因此傳回值都是 `20`。  
  
```  
SELECT EXP( LOG(20)), LOG( EXP(20));  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
-------------- -----------------  
20                  20  
```  
  
## <a name="see-also"></a>另請參閱  
 [數學函數 &#40;Transact-SQL&#41;](../../t-sql/functions/mathematical-functions-transact-sql.md)   
 [LOG &#40;Transact-SQL&#41;](../../t-sql/functions/log-transact-sql.md)   
 [LOG10 &#40;Transact-SQL&#41;](../../t-sql/functions/log10-transact-sql.md)  
  
  

