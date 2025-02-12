---
title: SELECT @local_variable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- variable_TSQL
- '@loca_variable'
- '@local'
- variable
- '@loca_variable_TSQL'
- '@local_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- variables [SQL Server], assigning
- SELECT statement [SQL Server], @local_variable
- '@local_variable'
- local variables [SQL Server]
ms.assetid: 8e1a9387-2c5d-4e51-a1fd-a2a95f026d6f
author: rothja
ms.author: jroth
monikerRange: = azuresqldb-current ||>= sql-server-2016 ||= azure-sqldw-latest||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 6a274535d53b7eec57fdf257425f855eded5d046
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68121783"
---
# <a name="select-localvariable-transact-sql"></a>SELECT @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  將區域變數設為運算式的值。  
  
 對於指派變數，我們建議您使用 [SET @local_variable](../../t-sql/language-elements/set-local-variable-transact-sql.md)，而不是 SELECT @*local_variable*。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SELECT { @local_variable { = | += | -= | *= | /= | %= | &= | ^= | |= } expression } 
    [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>引數  
@*local_variable*  
 這是將指派值的宣告變數。  
  
{= | += | -= | \*= | /= | %= | &= | ^= | |= }   
將右邊的值指派給左邊的變數。  
  
複合指派運算子：  
  |! 運算子之後 |action |   
  |-----|-----|  
  | = | 將後面的運算式指派給變數。 |  
  | += | 加並指派 |   
  | -= | 減並指派 |  
  | \*= | 乘並指派 |  
  | /= | 除並指派 |  
  | %= | 取餘數並指派 |  
  | &= | 位元 AND 並指派 |  
  | ^= | 位元 XOR 並指派 |  
  | \|= | 位元 OR 並指派 |  
  
 *expression*  
 這是任何有效的[運算式](../../t-sql/language-elements/expressions-transact-sql.md)。 其中包括純量子查詢。  
  
## <a name="remarks"></a>Remarks  
 SELECT @*local_variable* 通常用來將單一值傳回給變數。 不過，當 *expression* 是資料行名稱時，它可以傳回多個值。 如果 SELECT 陳述式傳回多個值，就會將最後傳回的值指派給變數。  
  
 如果 SELECT 陳述式未傳回任何資料列，變數會保留它目前的值。 如果 *expression* 是未傳回任何值的純量子查詢，變數會設為 NULL。  
  
 一個 SELECT 陳述式可以初始化多個本機變數。  
  
> [!NOTE]  
>  您不能也利用包含變數指派的 SELECT 陳述式來執行一般結果集擷取作業。  
  
## <a name="examples"></a>範例  
  
### <a name="a-use-select-localvariable-to-return-a-single-value"></a>A. 使用 SELECT @local_variable 傳回單一值  
 在下列範例中，`@var1` 變數指派了 `Generic Name` 來作為值。 針對 `Store` 資料表的查詢不會傳回任何資料列，因為資料表中並沒有指定給 `CustomerID` 的值。 變數會保留 `Generic Name` 值。  
  
```sql  
-- Uses AdventureWorks    
  
DECLARE @var1 varchar(30);         
SELECT @var1 = 'Generic Name';         
SELECT @var1 = Name         
FROM Sales.Store         
WHERE CustomerID = 1000 ;        
SELECT @var1 AS 'Company Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Company Name  
 ------------------------------  
 Generic Name  
 ```  
  
### <a name="b-use-select-localvariable-to-return-null"></a>B. 使用 SELECT @local_variable 傳回 Null  
 在下列範例中，利用子查詢來將值指派給 `@var1`。 由於針對 `CustomerID` 所要求的值並不存在，因此，子查詢不會傳回任何值，變數會設為 `NULL`。  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @var1 varchar(30)   
SELECT @var1 = 'Generic Name'   
SELECT @var1 = (SELECT Name   
FROM Sales.Store   
WHERE CustomerID = 1000)   
SELECT @var1 AS 'Company Name' ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Company Name  
----------------------------  
NULL  
```  
  
## <a name="see-also"></a>另請參閱  
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [複合運算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)  
  
  
