---
title: 稀疏資料行支援 (OLE DB) |Microsoft Docs
description: 疏鬆資料行支援 (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 701b2d9e7a6d51b7fa13f797c6c5c9de75bed5d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67993856"
---
# <a name="sparse-columns-support-ole-db"></a>疏鬆資料行支援 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  本主題提供 OLE DB 驅動程式的相關資訊, 以取得稀疏資料行的 SQL Server 支援。 如需稀疏資料行的詳細資訊, 請參閱[SQL Server OLE DB 驅動程式中的稀疏資料行支援](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)。 如需範例，請參閱[顯示資料行與疏鬆資料行的目錄中繼資料 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md)。  
  
## <a name="ole-db-statement-metadata"></a>OLE DB 陳述式中繼資料  
 從 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 開始，提供新的 DBCOLUMNFLAGS 旗標值 DBCOLUMNFLAGS_SS_ISCOLUMNSET。 此值應該針對 **column_set** 值的資料行設定。 DBCOLUMNFLAGS 旗標可以透過 IColumnsInfo:: Getcolumnsinfo 所的*dwFlags*參數, 以及 DBCOLUMN_FLAGS:: IColumnsRowset 所傳回之資料列集的 GetColumnsRowset 資料行來抓取。  
  
## <a name="ole-db-catalog-metadata"></a>OLE DB 目錄中繼資料  
 系統已經將兩個額外的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 專用資料行加入到 DBSCHEMA_COLUMNS 中。  
  
|資料行名稱|資料類型|值/註解|  
|-----------------|---------------|---------------------|  
|SS_IS_SPARSE|DBTYPE_BOOL|如果資料行為疏鬆資料行，這個值為 VARIANT_TRUE，否則為 VARIANT_FALSE。|  
|SS_IS_COLUMN_SET|DBTYPE_BOOL|如果資料行為疏鬆資料行 **column_set**，這個值為 VARIANT_TRUE；否則為 VARIANT_FALSE。|  
  
 系統也已經加入兩個額外的結構描述資料列集。 這些資料列集與 DBSCHEMA_COLUMNS 的結構相同，但傳回不同的內容。 DBSCHEMA_COLUMNS_EXTENDED 會傳回所有資料行而不管 **column_set** 成員資格為何。 DBSCHEMA_SPARSE_COLUMN_SET 僅會傳回屬於疏鬆 **column_set** 成員的資料行。  
  
## <a name="ole-db-datatypecompatibility-behavior"></a>OLE DB DataTypeCompatibility 行為  
 **DataTypeCompatibility = 80** (在連接字串中) 的行為與[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)]用戶端一致, 如下所示:  
  
-   您看不到新的結構描述資料列集，而且在結構描述資料列集中沒有它們的資料列。  
  
-   您看不到 COLUMNS 資料列集中的新資料行。  
  
-   **column_set** 資料行不會設定 DBCOLUMNFLAGS_SS_ISCOLUMNSET。  
  
-   **column_set** 資料行會設定 DBCOMPUTEMODE_NOTCOMPUTED。  
  
## <a name="ole-db-support-for-sparse-columns"></a>疏鬆資料行的 OLE DB 支援  
 下列 OLE DB 介面已在 OLE DB 驅動 SQL Server 程式中修改, 以支援稀疏資料行:  
  
|類型或成員函數|Description|  
|-----------------------------|-----------------|  
|IColumnsInfo::GetColumnsInfo|在 *dwFlags* 中，系統會設定 **column_set** 資料行的新 DBCOLUMNFLAGS 旗標值 DBCOLUMNFLAGS_SS_ISCOLUMNSET。<br /><br /> **column_set** 資料行會設定 DBCOLUMNFLAGS_WRITE。|  
|IColumsRowset::GetColumnsRowset|在 DBCOLUMN_FLAGS 中，系統會設定 **column_set** 資料行的新 DBCOLUMNFLAGS 旗標值 DBCOLUMNFLAGS_SS_ISCOLUMNSET。<br /><br /> DBCOLUMN_COMPUTEMODE 會針對 **column_set** 資料行，設定為 DBCOMPUTEMODE_DYNAMIC。|  
|IDBSchemaRowset::GetSchemaRowset|DBSCHEMA_COLUMNS 會傳回兩個新的資料行：SS_IS_COLUMN_SET 和 SS_IS_SPARSE。<br /><br /> DBSCHEMA_COLUMNS 僅會傳回不屬於 **column_set** 成員的資料行。<br /><br /> 系統已加入兩個新的結構描述資料列集：DBSCHEMA_COLUMNS_EXTENDED 將會傳回所有資料行，而不管 **column_set** 成員資格的疏鬆度。 DBSCHEMA_SPARSE_COLUMN_SET 僅會傳回屬於 **column_set** 成員的資料行。 這些新的資料列集與 DBSCHEMA_COLUMNS 的資料行和限制相同。|  
|IDBSchemaRowset::GetSchemas|IDBSchemaRowset::GetSchemas 在可用結構描述資料列集的清單中，包含用於新資料列集 DBSCHEMA_COLUMNS_EXTENDED 和 DBSCHEMA_SPARSE_COLUMN_SET 的 GUID。|  
|ICommand::Execute|如果使用 **select \* from** *table*，它會傳回不屬於疏鬆 **column_set** 成員的所有資料行，加上包含屬於疏鬆 **column_set** 成員之所有非 Null 資料行值的 XML 資料行 (如果有的話)。|  
|IOpenRowset::OpenRowset|IOpenRowset:: OpenRowset 會傳回具有與 ICommand:: Execute 相同之資料行的資料列集, 並在相同的資料表上使用**select \*** 查詢。|  
|ITableDefinition|對於疏鬆資料行或 **column_set** 資料行的這個介面，則沒有任何變更。 需要修改結構描述的應用程式必須直接執行適當的 [!INCLUDE[tsql](../../../includes/tsql-md.md)]。|  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 程式設計](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
