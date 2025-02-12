---
title: SET ARITHABORT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ARITHABORT_TSQL
- ARITHABORT
- SET ARITHABORT
- SET_ARITHABORT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- terminating queries
- queries [SQL Server], terminating
- overflow errors [SQL Server]
- ARITHABORT option
- divide-by-zero errors
- SET ARITHABORT statement
- ending queries [SQL Server]
- stopping queries
ms.assetid: f938a666-fdd1-4233-b97f-719f27b1a0e6
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da408c690622f5ba1ef45fa2466ed396d0022599
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064610"
---
# <a name="set-arithabort-transact-sql"></a>SET ARITHABORT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

查詢執行期間發生溢位或除以零錯誤時結束查詢。  
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```
-- Syntax for SQL Server and Azure SQL Database
  
SET ARITHABORT { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ARITHABORT ON
```
  
## <a name="remarks"></a>Remarks  
在登入工作階段中一律將 ARITHABORT 設為 ON。 將 ARITHABORT 設為 OFF 可能會對查詢最佳化造成負面影響，進而導致效能問題。  
  
> [!WARNING]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的預設 ARITHABORT 設定是 ON。 將 ARITHABORT 設為 OFF 的用戶端應用程式可能會收到不同的查詢計劃，導致難以針對效能不良的查詢進行疑難排解。 也就是說，相同查詢的執行速度在 Management Studio 中可能很快，但在應用程式中可能很慢。 使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 進行查詢的疑難排解時，一律要符合用戶端 ARITHABORT 設定。  
  
當 SET ARITHABORT 和 SET ANSI WARNINGS 都是 ON 時，這些錯誤狀況會導致查詢結束。  
  
當 SET ARITHABORT 為 ON，而 SET ANSI WARNINGS 為 OFF 時，這些錯誤狀況會導致批次結束。 如果交易發生這些錯誤，就會回復交易。 當 SET ARITHABORT 為 OFF 且發生這其中一個錯誤時，就會出現一則警告訊息，而算術運算的結果會是 NULL。  
  
如果 SET ARITHABORT 和 SET ANSI WARNINGS 都是 OFF，且發生這其中一個錯誤，就會出現一則警告訊息，而算術運算的結果會是 NULL。  
  
> [!NOTE]  
>  如果 SET ARITHABORT 和 SET ARITHIGNORE 都不是 ON，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會傳回 NULL，並在查詢執行之後，傳回一則警告訊息。  
  
當資料庫的相容性層級設定為 90 或以上時，將 ANSI_WARNINGS 設定為 ON 也會將 ARITHABORT 隱含設定為 ON。 如果資料庫的相容性層級設定為 80 或更低，ARITHABORT 選項就必須明確地設定為 ON。  
  
進行運算式評估時，如果 SET ARITHABORT 為 OFF，而且 INSERT、UPDATE 或 DELETE 陳述式遇到算術、溢位、除以零或網域錯誤，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就會插入或更新 NULL 值。 如果目標資料行不可為 Null，插入或更新動作就會失敗，而使用者會看見錯誤。  
  
當 SET ARITHABORT 或 SET ARITHIGNORE 都不是 OFF，而 SET ANSI_WARNINGS 為 ON 時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仍將在遇到除以零或溢位錯誤時傳回錯誤訊息。  
  
當 SET ARITHABORT 為 OFF，且在 IF 陳述式的布林值條件評估期間發生中止錯誤時，就會執行 FALSE 分支。
  
當您在計算資料行或已編製索引的檢視上建立或變更索引時，SET ARITHABORT 必須是 ON。 如果 SET ARITHABORT 為 OFF，在計算資料行或已編製索引的檢視上含有索引之資料表上的 CREATE、UPDATE、INSERT 和 DELETE 陳述式就會失敗。
  
SET ARITHABORT 的設定會在執行階段發生，而非剖析階段。  
  
若要檢視 SET ARITHABORT 的目前設定，請執行下列查詢：
  
```  
DECLARE @ARITHABORT VARCHAR(3) = 'OFF';  
IF ( (64 & @@OPTIONS) = 64 ) SET @ARITHABORT = 'ON';  
SELECT @ARITHABORT AS ARITHABORT;  
  
```  
  
## <a name="permissions"></a>權限  
需要 **public** 角色的成員資格。  
  
## <a name="examples"></a>範例  
下列範例示範具有 `SET ARITHABORT` 設定的除以零和溢位錯誤。  
  
```  
-- SET ARITHABORT  
-------------------------------------------------------------------------------  
-- Create tables t1 and t2 and insert data values.  
CREATE TABLE t1 (  
   a TINYINT,   
   b TINYINT  
);  
CREATE TABLE t2 (  
   a TINYINT  
);  
GO  
INSERT INTO t1   
VALUES (1, 0);  
INSERT INTO t1   
VALUES (255, 1);  
GO  
  
PRINT '*** SET ARITHABORT ON';  
GO  
-- SET ARITHABORT ON and testing.  
SET ARITHABORT ON;  
GO  
  
PRINT '*** Testing divide by zero during SELECT';  
GO  
SELECT a / b AS ab   
FROM t1;  
GO  
  
PRINT '*** Testing divide by zero during INSERT';  
GO  
INSERT INTO t2  
SELECT a / b AS ab    
FROM t1;  
GO  
  
PRINT '*** Testing tinyint overflow';  
GO  
INSERT INTO t2  
SELECT a + b AS ab   
FROM t1;  
GO  
  
PRINT '*** Resulting data - should be no data';  
GO  
SELECT *   
FROM t2;  
GO  
  
-- Truncate table t2.  
TRUNCATE TABLE t2;  
GO  
  
-- SET ARITHABORT OFF and testing.  
PRINT '*** SET ARITHABORT OFF';  
GO  
SET ARITHABORT OFF;  
GO  
  
-- This works properly.  
PRINT '*** Testing divide by zero during SELECT';  
GO  
SELECT a / b AS ab    
FROM t1;  
GO  
  
-- This works as if SET ARITHABORT was ON.  
PRINT '*** Testing divide by zero during INSERT';  
GO  
INSERT INTO t2  
SELECT a / b AS ab    
FROM t1;  
GO  
PRINT '*** Testing tinyint overflow';  
GO  
INSERT INTO t2  
SELECT a + b AS ab   
FROM t1;  
GO  
  
PRINT '*** Resulting data - should be 0 rows';  
GO  
SELECT *   
FROM t2;  
GO  
  
-- Drop tables t1 and t2.  
DROP TABLE t1;  
DROP TABLE t2;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ARITHIGNORE &#40;Transact-SQL&#41;](../../t-sql/statements/set-arithignore-transact-sql.md)   
 [SESSIONPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
