---
title: FIRST_VALUE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FIRST_VALUE_TSQL
- FIRST_VALUE
dev_langs:
- TSQL
helpviewer_keywords:
- FIRST_VALUE function
- analytic functions, FIRST_VALUE
ms.assetid: 1990c3c7-dad2-48db-b2cd-3e8bd2c49d17
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: d5954a1b090be1749c07c09a83d4c2cfbf441f6a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071377"
---
# <a name="firstvalue-transact-sql"></a>FIRST_VALUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  傳回 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中排序值集的第一個值。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
FIRST_VALUE ( [scalar_expression ] )   
    OVER ( [ partition_by_clause ] order_by_clause [ rows_range_clause ] )  
  
```  
  
## <a name="arguments"></a>引數  
 *scalar_expression*  
 要傳回的值。 *scalar_expression* 可以是資料行、子查詢，或其他結果為單一值的任意運算式。 不允許其他分析函數。  
  
 OVER **(** [ *partition_by_clause* ] *order_by_clause* [ *rows_range_clause* ] **)**  
 *partition_by_clause* 會將 FROM 子句產生的結果集分割成函數所要套用的分割區。 如未指定，此函數會將查詢結果集的所有資料列視為單一群組。 *order_by_clause* 可決定執行作業的邏輯順序。 *order_by_clause* 為必要項目。 *rows_range_clause* 會指定起始點及結束點，以進一步限制分割區中的資料列數。 如需詳細資訊，請參閱 [OVER 子句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)。  
  
## <a name="return-types"></a>傳回類型  
 為與 *scalar_expression* 相同的類型。  
  
## <a name="general-remarks"></a>一般備註  
 FIRST_VALUE 不具決定性。 如需詳細資訊，請參閱 [決定性與非決定性函數](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)。  
  
## <a name="examples"></a>範例  
  
### <a name="a-using-firstvalue-over-a-query-result-set"></a>A. 針對查詢結果集使用 FIRST_VALUE  
 下列範例使用 FIRST_VALUE 傳回給定產品類別目錄中最便宜產品的名稱。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, ListPrice,   
       FIRST_VALUE(Name) OVER (ORDER BY ListPrice ASC) AS LeastExpensive   
FROM Production.Product  
WHERE ProductSubcategoryID = 37;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
Name                    ListPrice             LeastExpensive  
----------------------- --------------------- --------------------  
Patch Kit/8 Patches     2.29                  Patch Kit/8 Patches  
Road Tire Tube          3.99                  Patch Kit/8 Patches  
Touring Tire Tube       4.99                  Patch Kit/8 Patches  
Mountain Tire Tube      4.99                  Patch Kit/8 Patches  
LL Road Tire            21.49                 Patch Kit/8 Patches  
ML Road Tire            24.99                 Patch Kit/8 Patches  
LL Mountain Tire        24.99                 Patch Kit/8 Patches  
Touring Tire            28.99                 Patch Kit/8 Patches  
ML Mountain Tire        29.99                 Patch Kit/8 Patches  
HL Road Tire            32.60                 Patch Kit/8 Patches  
HL Mountain Tire        35.00                 Patch Kit/8 Patches  
  
```  
  
### <a name="b-using-firstvalue-over-partitions"></a>B. 針對整個分割區使用 FIRST_VALUE  
 下列範例使用 FIRST_VALUE 傳回相同職稱的員工中，休假時數最少的員工。 PARTITION BY 子句會依職稱分割員工，而 FIRST_VALUE 函數會個別套用至每個分割區。 OVER 子句中指定的 ORDER BY 子句，可決定 FIRST_VALUE 函數套用至每個分割區中之資料列的邏輯順序。 ROWS UNBOUNDED PRECEDING 子句會將視窗起點指定為每個分割區的第一列。  
  
```  
USE AdventureWorks2012;   
GO  
SELECT JobTitle, LastName, VacationHours,   
       FIRST_VALUE(LastName) OVER (PARTITION BY JobTitle   
                                   ORDER BY VacationHours ASC  
                                   ROWS UNBOUNDED PRECEDING  
                                  ) AS FewestVacationHours  
FROM HumanResources.Employee AS e  
INNER JOIN Person.Person AS p   
    ON e.BusinessEntityID = p.BusinessEntityID  
ORDER BY JobTitle;  
```  
  
 以下為部分結果集。  
  
```  
  
JobTitle                            LastName                  VacationHours FewestVacationHours  
----------------------------------- ------------------------- ------------- -------------------  
Accountant                          Moreland                  58            Moreland  
Accountant                          Seamans                   59            Moreland  
Accounts Manager                    Liu                       57            Liu  
Accounts Payable Specialist         Tomic                     63            Tomic  
Accounts Payable Specialist         Sheperdigian              64            Tomic  
Accounts Receivable Specialist      Poe                       60            Poe  
Accounts Receivable Specialist      Spoon                     61            Poe  
Accounts Receivable Specialist      Walton                    62            Poe  
```  
  
## <a name="see-also"></a>另請參閱  
 [OVER 子句 &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)  
  
  
