---
title: FILEPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 79be8af32c13b9e910b94b40bd3c1bf9b2c0e2c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071402"
---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定了目前資料庫中的檔案名稱和屬性名稱時，傳回指定的檔案名稱屬性值。 針對不在目前資料庫中的檔案，傳回 NULL。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>引數  
 *file_name*  
 這是包含傳回屬性資訊所屬的目前資料庫之相關聯檔案名稱的運算式。 *file_name* 為 **nchar(128)** 。  
  
 *property*  
 這是包含要傳回之檔案屬性名稱的運算式。 *property* 為 **varchar(128)** ，而且可以是下列值之一。  
  
|ReplTest1|Description|傳回的值|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|檔案群組是唯讀的。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 輸入無效。|  
|**IsPrimaryFile**|檔案是主要檔案。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 輸入無效。|  
|**IsLogFile**|檔案是記錄檔。|1 = True<br /><br /> 0 = False<br /><br /> NULL = 輸入無效。|  
|**SpaceUsed**|指定檔案所用的空間量。|檔案中所配置的頁數|  
  
## <a name="return-types"></a>傳回類型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 *file_name* 對應於 **sys.master_files** 或 **sys.database_files** 目錄檢視中的 **name** 資料行。  
  
## <a name="examples"></a>範例  
 下列範例會傳回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫中 `IsPrimaryFile` 檔案名稱的 `AdventureWorks_Data` 屬性設定。  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另請參閱  
 [FILEGROUPPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [中繼資料函數 &#40;Transact-SQL&#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
