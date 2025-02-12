---
title: _db_objects_disabled_on_compatibility_level_change (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_db_objects_disabled_on_compatibility_level_change
- dm_db_objects_disabled_on_compatibility_level_change_TSQL
- sys.dm_db_objects_disabled_on_compatibility_level_change
- sys.dm_db_objects_disabled_on_compatibility_level_change_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_objects_disabled_on_compatibility_level_change catalog view
ms.assetid: a5d70064-0330-48b9-b853-01eba50755d0
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 30c3a5d7358e49c1e1762fbb9851066bdaf30871
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68809899"
---
# <a name="spatial-data---sysdm_db_objects_disabled_on_compatibility_level_change"></a>空間資料-sys. dm _db_objects_disabled_on_compatibility_level_change
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  列出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中因為相容性層級變更而停用的索引和條件約束。 包含保存計算資料行 (其運算式使用空間 UDT) 的索引和條件約束會在升級或變更相容性層級後停用。 使用此動態管理函數指定相容性層級變更的影響。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```sql  
sys.dm_db_objects_disabled_on_compatibility_level_change ( compatibility_level )   
```  
  
##  <a name="Arguments"></a> 引數  
 *compatibility_level*  
 **int** , 可識別您打算設定的相容性層級。  
  
## <a name="table-returned"></a>傳回的資料表  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**class**|**int**|1 = 條件約束<br /><br /> 7 = 索引和堆積|  
|**class_desc**|**nvarchar(60)**|條件約束的 OBJECT 或 COLUMN<br /><br /> 索引和堆積的 INDEX|  
|**major_id**|**int**|條件約束的 OBJECT ID<br /><br /> 包含索引和堆積的資料表 OBJECT ID|  
|**minor_id**|**int**|條件約束的 NULL<br /><br /> 索引和堆積的 Index_id|  
|**dependency**|**nvarchar(60)**|導致條件約束或索引停用的相依性說明。 升級期間所引發的警示也會使用相同的值。 範例包括：<br /><br /> 內建的 "space"<br /><br /> 系統 UDT 的 "geometry"<br /><br /> 系統 UDT 之方法的 "geography::Parse"|  
  
## <a name="general-remarks"></a>一般備註  
 當相容性層級變更時，將會停用使用內建函數的保存計算資料行。 除此之外，當資料庫升級時，也會停用使用幾何或地理方法的保存計算資料行。  
  
### <a name="which-functions-cause-persisted-computed-columns-to-be-disabled"></a>哪些函數會造成保存計算資料行停用？  
 當保存計算資料行的運算式中使用了下列函數，而相容性層級從 80 變更為 90 時，將會導致參考這些資料行的索引和條件約束停用：  
  
-   **IsNumeric**  
  
 當保存計算資料行的運算式中使用了下列函數，而相容性層級從 100 變更為 110 或更高層級時，將會導致參考這些資料行的索引和條件約束停用：  
  
-   **Soundex**  
  
-   **Geography::GeomFromGML**  
  
-   **Geography::STGeomFromText**  
  
-   **Geography::STLineFromText**  
  
-   **Geography::STPolyFromText**  
  
-   **Geography::STMPointFromText**  
  
-   **Geography::STMLineFromText**  
  
-   **Geography::STMPolyFromText**  
  
-   **Geography::STGeomCollFromText**  
  
-   **Geography::STGeomFromWKB**  
  
-   **Geography::STLineFromWKB**  
  
-   **Geography::STPolyFromWKB**  
  
-   **Geography::STMPointFromWKB**  
  
-   **Geography::STMLineFromWKB**  
  
-   **Geography::STMPolyFromWKB**  
  
-   **Geography::STUnion**  
  
-   **Geography::STIntersection**  
  
-   **Geography::STDifference**  
  
-   **Geography::STSymDifference**  
  
-   **Geography::STBuffer**  
  
-   **Geography::BufferWithTolerance**  
  
-   **Geography::分析**  
  
-   **Geography::減少**  
  
### <a name="behavior-of-the-disabled-objects"></a>停用物件的行為  
 **[索引]**  
  
 如果叢集索引已停用, 或強制執行非叢集索引, 則會引發下列錯誤:「查詢處理器無法產生計畫, 因為索引 '%。\*在資料表或視圖 '% 上的 ls '。\*ls ' 已停用」。 若要重新啟用這些物件, 請在升級之後藉由呼叫**ALTER INDEX ON ... 來重建索引。REBUILD**。  
  
 **堆積**  
  
 如果使用了內含停用之堆積的資料表，將會引發下列錯誤。 若要重新啟用這些物件, 請在升級之後, **藉由呼叫 ALTER INDEX ALL ON .。。REBUILD**。  
  
```  
// ErrorNumber: 8674  
// ErrorSeverity: EX_USER  
// ErrorFormat: The query processor is unable to produce a plan because the table or view '%.*ls' is disabled.  
// ErrorCause: The table has a disabled heap.   
// ErrorCorrectiveAction: Rebuild the disabled heap to enable it.   
// ErrorInserts: table or view name   
// ErrorOwner: mtintor   
// ErrorFirstProduct: SQL11  
```  
  
 如果您嘗試在線上操作期間重建堆積, 則會引發錯誤。  
  
 **檢查條件約束和外鍵**  
  
 停用檢查條件約束和外部索引鍵不會引發錯誤。 但資料列如果有所修改，將不會強制執行條件約束。 若要重新啟用這些物件, 請在升級之後檢查條件約束 **, 方法是呼叫 ALTER TABLE .。。CHECK 條件**約束。  
  
 **保存的計算資料行**  
  
 由於無法停用單一資料行，因此，如果要停用整份資料表，必須停用叢集索引或堆積。  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>Permissions  
 需要 VIEW DATABASE STATE 權限。  
  
## <a name="example"></a>範例  
 下列範例顯示在 **_db_objects_disabled_on_compatibility_level_change**上的查詢, 以尋找受影響的物件, 並將相容性層級變更為120。  
  
```sql  
SELECT * FROM sys.dm_db_objects_disabled_on_compatibility_level_change(120);  
GO  
  
```  
  
  
