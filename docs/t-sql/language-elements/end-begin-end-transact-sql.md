---
title: END (BEGIN...END) (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- END
- END_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- enclosing statements [SQL Server]
- END keyword
- BEGIN...END keyword
- END (BEGIN...END) keyword
ms.assetid: 354c4935-1375-4141-8195-61326662f4d2
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e7aff4c7bdc1ec9edb93f8a207bd2166bcb3b084
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075299"
---
# <a name="end-beginend-transact-sql"></a>END (BEGIN...END) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  含括將以群組方式來執行的序列 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。 BEGIN...END 區塊可以有巢狀結構。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
BEGIN   
     { sql_statement | statement_block }   
END   
```  
  
## <a name="arguments"></a>引數  
 { *sql_statement*| *statement_block*}  
 這是利用陳述式區塊來定義的任何有效 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式或陳述式分組。 若要定義陳述式區塊 (批次)，請使用流程控制語言關鍵字 BEGIN 和 END。 雖然 BEGIN...END 區塊中所有的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式都是有效的，但某些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式不應在同一批次 (陳述式區塊) 中群組在一起。  
  
## <a name="result-types"></a>結果類型  
 **布林**  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 在下列範例中，`BEGIN` 和 `END` 會定義一系列同時執行的 [!INCLUDE[DWsql](../../includes/dwsql-md.md)] 陳述式。 如果未包含 `BEGIN...END` 區塊，則下列範例將處於持續不斷的迴圈狀態。  
  
```  
-- Uses AdventureWorks  
  
DECLARE @Iteration Integer = 0  
WHILE @Iteration <10  
BEGIN  
    SELECT FirstName, MiddleName   
    FROM dbo.DimCustomer WHERE LastName = 'Adams';  
SET @Iteration += 1  
END;  
  
```  
  
## <a name="see-also"></a>另請參閱  
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [BEGIN...END &#40;Transact-SQL&#41;](../../t-sql/language-elements/begin-end-transact-sql.md)   
 [流程控制語言 &#40;Transact-SQL&#41;](~/t-sql/language-elements/control-of-flow.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [ELSE &#40;IF...ELSE&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/else-if-else-transact-sql.md)   
 [IF...ELSE &#40;Transact-SQL&#41;](../../t-sql/language-elements/if-else-transact-sql.md)   
 [WHILE &#40;Transact-SQL&#41;](../../t-sql/language-elements/while-transact-sql.md)  
  
  


