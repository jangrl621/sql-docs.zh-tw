---
title: _db_persisted_sku_features (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/23/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_db_persisted_sku_features_TSQL
- sys.dm_db_persisted_sku_features
- dm_db_persisted_sku_features_TSQL
- dm_db_persisted_sku_features
dev_langs:
- TSQL
helpviewer_keywords:
- editions [SQL Server], feature restrictions
- sys.dm_db_persisted_sku_features dynamic management view
ms.assetid: b4b29e97-b523-41b9-9528-6d4e84b89e09
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd8c4d6fb71e98a13cab1b01f34b7c5dc7e99331
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/19/2019
ms.locfileid: "68345074"
---
# <a name="sysdmdbpersistedskufeatures-transact-sql"></a>sys.dm_db_persisted_sku_features (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的某些功能會變更 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 將資訊儲存在資料庫檔案中的方式， 這些功能受限為特定版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 包含這些功能的資料庫無法移至不支援它們的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。 使用 _db_persisted_sku_features 動態管理檢視, 列出目前資料庫中已啟用的版本特定功能。
  
**適用於**：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|feature_name|**sysname**|資料庫中已啟用，但是所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本上不支援之功能的外部名稱。 此功能必須先移除，資料庫才可以移轉到所有可用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本。|  
|feature_id|**int**|與此功能相關聯的功能識別碼。 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)].|  
  
## <a name="permissions"></a>Permissions  
 需要資料庫的 VIEW DATABASE STATE 權限。  
  
## <a name="remarks"></a>備註  
 如果資料庫未使用特定版本可能會限制的功能, 則此視圖不會傳回任何資料列。  
  
 _db_persisted_sku_features 可能會列出下列僅限於特定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本的資料庫變更功能:  
  
-   **ChangeCapture**:表示資料庫已啟用「變更資料捕獲」。 若要移除變更資料捕獲, 請使用[sp_cdc_disable_db](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md)預存程式。 如需詳細資訊，請參閱[關於異動資料擷取 &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)。  
  
-   **ColumnStoreIndex**:表示至少有一個資料表具有資料行存放區索引。 若要讓資料庫移到不支援這項功能[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的版本, 請使用[DROP INDEX](../../t-sql/statements/drop-index-transact-sql.md)或[ALTER INDEX](../../t-sql/statements/alter-index-transact-sql.md)語句來移除資料行存放區索引。 如需詳細資訊, 請參閱資料行存放區[索引](../../relational-databases/indexes/columnstore-indexes-overview.md)。  
  
    **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。  
  
-   **壓縮**:表示至少有一個資料表或索引使用資料壓縮或 vardecimal 儲存格式。 若要讓資料庫移到不支援這項功能[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的版本, 請使用[alter TABLE](../../t-sql/statements/alter-table-transact-sql.md)或[alter INDEX](../../t-sql/statements/alter-index-transact-sql.md)語句來移除資料壓縮。 若要移除 Vardecimal 儲存格式，請使用 sp_tableoption 陳述式。 如需詳細資訊，請參閱 [Data Compression](../../relational-databases/data-compression/data-compression.md)。  
  
-   **MultipleFSContainers**:指出資料庫使用多個 FILESTREAM 容器。 資料庫具有具有多個容器 (檔案) 的 FILESTREAM 檔案群組。 如需詳細資訊，請參閱 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)。  
  
-   **InMemoryOLTP**:指出資料庫使用記憶體內部 OLTP。 資料庫具有 MEMORY_OPTIMIZED_DATA 檔案群組。 如需詳細資訊，請參閱[記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
  **適用於**： [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])。 
  
-   **性別.** 指出資料庫包含分割區資料表、分割區索引、分割區配置或分割區函數。 若要讓資料庫移到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本，而不是 Enterprise 或 Developer，修改位於單一分割區上的資料表是不夠的， 您必須移除分割區資料表。 如果此資料表包含資料，請使用 SWITCH PARTITION 將每一個分割區轉換成非分割區資料表， 然後刪除分割區資料表、分割區配置和分割區函數。  
  
-   **TransparentDataEncryption.** 指出資料庫的加密方式為透明資料加密。 若要移除透明資料加密，請使用 ALTER DATABASE 陳述式。 如需詳細資訊，請參閱[透明資料加密 &#40;TDE&#41;](../../relational-databases/security/encryption/transparent-data-encryption.md)。  

> [!NOTE]
> 從 Service Pack 1 開始, 這些功能 (TransparentDataEncryption 除外) **。** [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 可跨多個[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本使用, 而不限於 Enterprise 或 Developer edition。

 若要判斷資料庫是否使用任何受限於特定版本的功能，請在資料庫中執行下列陳述式：  
  
```sql  
SELECT feature_name FROM sys.dm_db_persisted_sku_features;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [資料庫相關的動態管理&#40;Views transact-sql&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [SQL Server 2016 的版本與支援功能](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [版本及支援的 SQL Server 2017 功能](../../sql-server/editions-and-components-of-sql-server-2017.md)  
  
