---
title: 使用 Multiple Active Result Sets (MARS) |Microsoft Docs
description: 使用 Multiple Active Result Sets (MARS)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, MARS
- MSOLEDBSQL, MARS
- data access [OLE DB Driver for SQL Server], MARS
- Multiple Active Result Sets
- OLE DB Driver for SQL Server, MARS
- MARS [SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 8174333abc11b47d62c154171726afebee24824f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988808"
---
# <a name="using-multiple-active-result-sets-mars"></a>使用 Multiple Active Result Sets (MARS)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 在存取 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的應用程式中導入了對 Multiple Active Result Set (MARS) 的支援。 在舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中，資料庫應用程式無法在連接上維持多個作用中陳述式。 當使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預設結果集時，應用程式必須從一個批次處理或取消所有結果集，然後才能夠在該連接上執行任何其他批次。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 導入了新的連接屬性，好讓應用程式在每個連接上可以有一個以上的暫止要求，而且特別是每個連接上可以有一個以上的使用中預設結果集。  
  
 MARS 會使用以下的新功能來簡化應用程式設計：  
  
-   應用程式可以開啟多個預設結果集，而且可以交錯讀取這些結果集。  
  
-   當開啟預設結果集時，應用程式可以執行其他陳述式 (例如 INSERT、UPDATE、DELETE 和預存程序呼叫)。  
  
 以下的指導方針對於使用 MARS 的應用程式非常有用：  
  
-   預設結果集應該用於單一 SQL 陳述式 (SELECT、DML with OUTPUT、RECEIVE、READ TEXT 等等) 所產生的短期或簡短結果集。  
  
-   伺服器資料指標應該用於單一 SQL 陳述式所產生的較長期或大型結果集。  
  
-   一定要針對程序要求 (不論它們是否會傳回結果) 以及可傳回多個結果的批次讀取到結果結尾。  
  
-   盡可能使用 API 呼叫來變更連接屬性，並優先管理交易，而非 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式。  
  
-   在 MARS 中，當執行並行批次時會禁止工作階段範圍的模擬。  
  
> [!NOTE]  
>  預設不會啟用 MARS 功能。 若要在使用 SQL Server 的[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] OLE DB 驅動程式連接到時使用 MARS, 您必須在連接字串中明確加以啟用。 如需詳細資訊, 請參閱本主題稍後的 SQL Server 區段的 OLE DB 驅動程式。  
  
 SQL Server 的 OLE DB 驅動程式不會限制連接上作用中的語句數目。  
  
 不需要有多個單一多重陳述式批次或預存程序同時執行的一般應用程式將會因為 MARS 而受益，而不必了解 MARS 的實作方式。 但是，具有更複雜需求的應用程式確實需要考量這件事。  
  
 MARS 可啟用單一連接內多個要求的交錯執行。 也就是說，它可允許批次執行，而且當它執行時，可允許其他要求執行。 但是請注意，MARS 是以交錯來定義，而不是以平行執行來定義。  
  
 MARS 基礎結構可讓多個批次以交錯方式執行，但是只能在定義良好的點上切換執行。 此外，大多數的陳述式都必須在批次內自動執行。 當資料列傳送給用戶端時，允許在完成前交錯執行傳回資料列給用戶端的陳述式 (有時也稱為「產生點」  )，例如：  
  
-   SELECT  
  
-   FETCH  
  
-   RECEIVE  
  
 當執行可以切換到其他 MARS 要求之前，當做預存程序或批次的一部分執行的其他任何陳述式都必須執行到完成為止。  
  
 批次交錯執行的確切方式會受到一些因素的影響，而且很難預測包含產生點之多個批次中將要執行命令的確切順序。 請小心避免因為這類複雜批次的交錯執行所產生之不必要的副作用。  
  
 若要避免問題的發生，請使用 API 呼叫 (而非 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式) 來管理連接狀態 (SET、USE) 和交易 (BEGIN TRAN、COMMIT、ROLLBACK)，其方式是不要將這些陳述式併入同樣包含產生點的多重陳述式批次內，以及取用或取消所有結果來序列化這類批次的執行。  
  
> [!NOTE]  
>  在啟用 MARS 時啟動手動或隱含交易的批次或預存程序必須先完成交易，然後才能結束批次。 如果不是這樣的話，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會在批次完成時回復交易所做的所有變更。 這類交易是由 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 當做批次範圍的交易來管理。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中導入了新類型的交易，好讓現有行為良好的預存程序在啟用 MARS 時可以使用。 如需批次範圍交易的詳細資訊, 請參閱[Transaction 語句&#40;transact-sql&#41;](../../../t-sql/statements/statements.md)。  
  
 如需從 ADO 使用 MARS 的範例, 請參閱搭配[使用 ado 與 OLE DB 驅動程式來進行 SQL Server](../../oledb/applications/using-ado-with-oledb-driver-for-sql-server.md)。  
  
## <a name="in-memory-oltp"></a>記憶體內部 OLTP  
 記憶體內部 OLTP 支援使用查詢和原生編譯預存程式的 MARS。 MARS 可讓您從多個查詢要求資料, 而不需要在傳送要求以從新的結果集提取資料列之前, 完全取得每個結果集。 若要成功讀取多個開啟的結果集, 您必須使用已啟用 MARS 的連接。  
  
 MARS 預設為停用, 因此您必須藉由將加入`MultipleActiveResultSets=True`至連接字串來明確加以啟用。 下列範例示範如何連接到 SQL Server 的實例, 並指定啟用 MARS:  
  
```  
Data Source=MSSQL; Initial Catalog=AdventureWorks; Integrated Security=SSPI; MultipleActiveResultSets=True  
```  
  
 具有記憶體內部 OLTP 的 MARS 基本上與其他 SQL 引擎中的 MARS 相同。 以下列出在記憶體優化資料表和原生編譯的預存程式中使用 MARS 時的差異。  
  
 **MARS 和記憶體優化資料表**  
  
 以下是使用 MARS 啟用的連接時, 磁片型和記憶體優化資料表之間的差異:  
  
-   兩個語句可以修改相同目標物件中的資料, 但如果兩者都嘗試修改相同的記錄, 則寫入寫入衝突會導致新的作業失敗。 不過, 如果這兩個作業都修改不同的記錄, 作業將會成功。  
  
-   每個語句都會在快照集隔離下執行, 因此新的作業無法看到現有語句所做的變更。 即使並行語句是在相同的交易下執行, SQL 引擎還是會針對每個彼此隔離的語句, 建立批次範圍的交易。 不過, 批次範圍的交易仍會系結在一起, 因此, 回復一個批次範圍的交易會影響相同批次中的其他交易。  
  
-   使用者交易中不允許使用 DDL 作業, 因此它們會立即失敗。  
  
 **MARS 和原生編譯的預存程序**  
  
 原生編譯的預存程式可以在已啟用 MARS 的連接中執行, 而且只有在遇到產生點時, 才會產生另一個語句的執行。 「產生點」需要 SELECT 語句, 這是原生編譯預存程式內的唯一語句, 可以產生對另一個語句的執行。 如果 SELECT 語句不存在於程式中, 就不會產生它, 而是在其他語句開始之前執行到完成。  
  
 **MARS 和記憶體內部 OLTP 交易**  
  
 語句所做的變更, 以及交錯式的不可部分完成區塊會彼此隔離。 例如, 如果一個語句或不可部分完成的區塊會進行一些變更, 然後產生另一個語句的執行, 新的語句就不會看到第一個語句所做的變更。 此外, 當第一個語句繼續執行時, 不會看到任何其他語句所做的任何變更。 語句只會在語句啟動之前, 看到已經完成和認可的變更。  
  
 使用 BEGIN TRANSACTION 語句, 可以在目前的使用者交易內啟動新的使用者交易-這只在 interop 模式中受到支援, 因此只能從 T-sql 語句呼叫 BEGIN TRANSACTION, 而不是從原生編譯的預存步. 您可以使用 SAVE TRANSACTION 或對交易的 API 呼叫, 在交易中建立儲存點。儲存 (save_point_name), 以回復至儲存點。 這項功能也只能從 T-sql 語句啟用, 而不是從原生編譯的預存程式中啟用。  
  
 **MARS 和資料行存放區索引**  
  
 SQL Server (從2016開始) 支援 MARS 搭配資料行存放區索引。 SQL Server 2014 使用 MARS 來與具有資料行存放區索引的資料表進行唯讀連線。    不過，SQL Server 2014 不支援 MARS 在具備資料行存放區索引的資料表上，進行並行資料操作語言 (DML) 作業。 發生這種情況時，SQL Server 會終止連接並中止交易。   SQL Server 2012 具有唯讀的資料行存放區索引, 而 MARS 則不適用。  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server  
 OLE DB Driver for SQL Server 可透過 SSPROP_INIT_MARSCONNECTION 資料來源初始化屬性的加入來支援 MARS，該屬性是在 DBPROPSET_SQLSERVERDBINIT 屬性集中實作。 此外，也已經加入新的連接字串關鍵字 **MarsConn**。 它接受**true**或**false**值;預設值為**false** 。  
  
 資料來源屬性 DBPROP_MULTIPLECONNECTIONS 預設為 VARIANT_TRUE。 這表示，為了支援多個並行命令和資料列集物件，此提供者將會繁衍多個連接。 當啟用 MARS 時，OLE DB Driver for SQL Server 可在單一連接上支援多個命令和資料列集物件，好讓 MULTIPLE_CONNECTIONS 預設為 VARIANT_FALSE。  
  
 如需 DBPROPSET_SQLSERVERDBINIT 屬性集之增強功能的詳細資訊, 請參閱[初始化和授權屬性](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)。  
  
### <a name="ole-db-driver-for-sql-server-example"></a>OLE DB Driver for SQL Server 範例  
 此範例中會使用 OLE DB Driver for SQL Server 建立資料來源物件，而且在建立工作階段物件之前會使用 DBPROPSET_SQLSERVERDBINIT 屬性集來啟用 MARS。  
  
```  
#include <msoledbsql.h>  
  
IDBInitialize *pIDBInitialize = NULL;  
IDBCreateSession *pIDBCreateSession = NULL;  
IDBProperties *pIDBProperties = NULL;  
  
// Create the data source object.  
hr = CoCreateInstance(CLSID_MSOLEDBSQL, NULL,  
   CLSCTX_INPROC_SERVER,  
   IID_IDBInitialize,   
    (void**)&pIDBInitialize);  
  
hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void**)&pIDBProperties);  
  
// Set the MARS property.  
DBPROP rgPropMARS;  
  
// The following is necessary since MARS is off by default.  
rgPropMARS.dwPropertyID = SSPROP_INIT_MARSCONNECTION;  
rgPropMARS.dwOptions = DBPROPOPTIONS_REQUIRED;  
rgPropMARS.dwStatus = DBPROPSTATUS_OK;  
rgPropMARS.colid = DB_NULLID;  
V_VT(&(rgPropMARS.vValue)) = VT_BOOL;  
V_BOOL(&(rgPropMARS.vValue)) = VARIANT_TRUE;  
  
// Create the structure containing the properties.  
DBPROPSET PropSet;  
PropSet.rgProperties = &rgPropMARS;  
PropSet.cProperties = 1;  
PropSet.guidPropertySet = DBPROPSET_SQLSERVERDBINIT;  
  
// Get an IDBProperties pointer and set the initialization properties.  
pIDBProperties->SetProperties(1, &PropSet);  
pIDBProperties->Release();  
  
// Initialize the data source object.  
hr = pIDBInitialize->Initialize();  
  
//Create a session object from a data source object.  
IOpenRowset * pIOpenRowset = NULL;  
hr = IDBInitialize->QueryInterface(IID_IDBCreateSession, (void**)&pIDBCreateSession));  
hr = pIDBCreateSession->CreateSession(  
   NULL,             // pUnkOuter  
   IID_IOpenRowset,  // riid  
  &pIOpenRowset ));  // ppSession  
  
// Create a rowset with a firehose mode cursor.  
IRowset *pIRowset = NULL;  
DBPROP rgRowsetProperties[2];  
  
// To get a firehose mode cursor request a   
// forward only read only rowset.  
rgRowsetProperties[0].dwPropertyID = DBPROP_IRowsetLocate;  
rgRowsetProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[0].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[0].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[0].vValue));  
rgRowsetProperties[0].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[0].vValue.boolVal = VARIANT_FALSE;  
  
rgRowsetProperties[1].dwPropertyID = DBPROP_IRowsetChange;  
rgRowsetProperties[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
rgRowsetProperties[1].dwStatus = DBPROPSTATUS_OK;  
rgRowsetProperties[1].colid = DB_NULLID;  
VariantInit(&(rgRowsetProperties[1].vValue));  
rgRowsetProperties[1].vValue.vt = VARIANT_BOOL;  
rgRowsetProperties[1].vValue.boolVal = VARIANT_FALSE;  
  
DBPROPSET rgRowsetPropSet[1];  
rgRowsetPropSet[0].rgProperties = rgRowsetProperties  
rgRowsetPropSet[0].cProperties = 2  
rgRowsetPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
  
hr = pIOpenRowset->OpenRowset (NULL,  
   &TableID,  
   NULL,  
   IID_IRowset,  
   1,  
   rgRowsetPropSet  
   (IUnknown**)&pIRowset);  
```  

  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 
  
  
