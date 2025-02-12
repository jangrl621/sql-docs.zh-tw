---
title: 資料來源物件 (OLE DB) |Microsoft Docs
description: 資料來源物件 (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], data source objects
- OLE DB Driver for SQL Server, data source objects
- MSOLEDBSQL, data source objects
- OLE DB Driver for SQL Server, data source objects
- OLE DB data source objects [OLE DB Driver for SQL Server]
- data source objects [OLE DB]
- CLSID
author: pmasl
ms.author: pelopes
ms.openlocfilehash: e0394c5fd3b72c538904c9b8cf946316e76e6650
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015919"
---
# <a name="data-source-objects-ole-db"></a>資料來源物件 (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server 會針對用於建立資料存放區連結的 OLE DB 介面集合，使用資料來源這個詞；例如，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。 建立提供者之資料來源物件的實例是 SQL Server 取用者之 OLE DB 驅動程式的第一項工作。  
  
 每個 OLE DB 提供者都會為自己宣告一個類別識別碼 (CLSID)。 SQL Server 的 OLE DB 驅動程式的 CLSID 是 C/C++ GUID CLSID_MSOLEDBSQL (符號 MSOLEDBSQL_CLSID 會解析為您參考的內含 msoledbsql.h 檔案中正確的 progid)。 透過 CLSID，取用者會使用 OLE **CoCreateInstance** 函式來製造資料來源物件的執行個體。  
  
 SQL Server 的 OLE DB 驅動程式是同進程伺服器。 OLE DB Driver for SQL Server 物件的執行個體會使用 CLSCTX_INPROC_SERVER 巨集來建立，以便指示可執行的內容。  
  
 OLE DB Driver for SQL Server 資料來源物件會公開允許取用者連線到現有 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的 OLE DB 初始化介面。  
  
 透過的 OLE DB 驅動程式所建立 SQL Server 的每個連接都會自動設定這些選項:  
  
-   SET ANSI_WARNINGS ON  
  
-   SET ANSI_NULLS ON  
  
-   SET ANSI_PADDING ON  
  
-   SET ANSI_NULL_DFLT_ON ON  
  
-   SET QUOTED_IDENTIFIER ON  
  
-   SET CONCAT_OF_NULL_YIELDS_NULL ON  
  
 此範例會使用類別識別碼巨集來建立 OLE DB Driver for SQL Server 資料來源物件，並取得其 **IDBInitialize** 介面的參考。  
  
```  
IDBInitialize*   pIDBInitialize;  
HRESULT          hr;  
  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL, CLSCTX_INPROC_SERVER,  
    IID_IDBInitialize, (void**) &pIDBInitialize);  
  
if (SUCCEEDED(hr))  
{  
    //  Perform necessary processing with the interface.  
    pIDBInitialize->Uninitialize();  
    pIDBInitialize->Release();  
}  
else  
{  
    // Display error from CoCreateInstance.  
}  
```  
  
 成功建立 OLE DB Driver for SQL Server 資料來源物件的執行個體之後，取用者應用程式就可以透過初始化資料來源並建立工作階段來繼續。 OLE DB 工作階段會顯示允許資料存取與操作的介面。  
  
 OLE DB Driver for SQL Server 會在成功初始化資料來源後，先建立指定之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的連線。 只要在任何資料來源初始化介面上維持參考，或是在呼叫 **IDBInitialize::Uninitialize** 方法前，都會維持連線。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [資料來源屬性 &#40;OLE DB&#41;](../../oledb/ole-db-data-source-objects/data-source-properties-ole-db.md)  
  
-   [資料來源資訊屬性](../../oledb/ole-db-data-source-objects/data-source-information-properties.md)  
  
-   [初始化和授權屬性](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)  
  
-   [工作階段](../../oledb/ole-db-data-source-objects/sessions.md)  
  
-   [工作階段屬性 - OLE DB Driver for SQL Server](../../oledb/ole-db-data-source-objects/session-properties-oledb-driver-for-sql-server.md)  
  
-   [保存的資料來源物件](../../oledb/ole-db-data-source-objects/persisted-data-source-objects.md)  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 程式設計](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)  
  
  
