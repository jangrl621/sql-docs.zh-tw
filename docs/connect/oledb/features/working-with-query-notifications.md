---
title: 使用查詢通知 |Microsoft Docs
description: 在適用于 SQL Server 的 OLE DB 驅動程式中使用查詢通知
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], query notifications
- rowsets [SQL Server], notifications
- OLE DB Driver for SQL Server, query notifications
- notifications [OLE DB Driver for SQL Server]
- query notifications [SQL Server], OLE DB Driver for SQL Server
- canceling rowset changes
- IRowsetNotify interface
- MSOLEDBSQL, query notifications
- OLE DB Driver for SQL Server, query notifications
- consumer notification for rowset changes [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 29aaab523b3a754c65b1b7a0312ceb5ea122f2d3
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419314"
---
# <a name="working-with-query-notifications"></a>使用查詢通知

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

查詢通知是在中[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]引進, 而 OLE DB 驅動程式用於 SQL Server。 查詢通知是根據 SQL Server 2005 (9.x) 中引進的 SQL Service Broker 基礎結構而建置，可讓應用程式在資料變更時收到通知。 此功能對於從資料庫中提供資訊快取的應用程式 (如 Web 應用程式)，及需要在來源資料變更時收到通知的應用程式來說非常有用。

藉由使用查詢通知, 您可以在查詢的基礎資料變更時, 于指定的超時時間內要求通知。 要求會指定通知選項，其中包含服務名稱、訊息文字和伺服器的逾時值。 通知會透過 Service Broker 佇列傳遞，應用程式會輪詢此佇列以查看是否有可用的通知。

查詢通知選項字串的語法為：

`service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`

 例如：

`service=mySSBService;local database=mydb`

通知訂閱會 outlive 起始它們的進程。 這是因為應用程式可以建立通知訂閱, 然後終止。 訂閱仍會保持有效，而如果資料在建立訂閱時所指定的逾時期間內變更，就會發生通知。 通知是由執行的查詢、通知選項和郵件內文所識別。 您可以將其 timeout 值設定為零來取消它。

通知只會傳送一次。 若要持續收到資料變更的通知, 請在處理每個通知之後重新執行查詢, 以建立新的訂用帳戶。

SQL Server 應用程式的 OLE DB 驅動程式通常[!INCLUDE[tsql](../../../includes/tsql-md.md)] [會使用 RECEIVE](../../../t-sql/statements/receive-transact-sql.md)命令來接收通知。 它會使用此命令, 從與通知選項中指定之服務相關聯的佇列讀取通知。

> [!NOTE]
> 您必須在需要通知的查詢中限定資料表名稱。 例如， `dbo.myTable`。 資料表名稱必須使用兩部分的名稱來加以限定。 如果使用三或四部份的名稱，則訂閱無效。

通知基礎結構是依照 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引進的佇列功能而建立。 一般而言，在伺服器所產生的通知會透過這些佇列傳送，以供稍後處理。

若要使用查詢通知，伺服器上必須有佇列和服務。 您可以使用[!INCLUDE[tsql](../../../includes/tsql-md.md)]命令來建立這些, 如下所示:

```sql
CREATE QUEUE myQueue
CREATE SERVICE myService ON QUEUE myQueue
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])
```

> [!NOTE]
> 服務必須使用預先定義的合約，如上所示。

## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server

SQL Server 的 OLE DB 驅動程式支援在資料列集修改時使用取用者通知。 使用者會在資料列集修改的每個階段以及嘗試進行任何變更時收到通知。

> [!NOTE]
> 使用 **ICommand::Execute** 將通知查詢傳遞至伺服器，是使用 OLE DB Driver for SQL Server 訂閱查詢通知的唯一有效方法。

### <a name="dbpropsetsqlserverrowset-property-set"></a>DBPROPSET_SQLSERVERROWSET 屬性集

為了透過 OLE DB 支援查詢通知，OLE DB Driver for SQL Server 會將下列屬性新增至 `DBPROPSET_SQLSERVERROWSET` 屬性集。

|[屬性]|類型|Description|
|----------|----------|-----------------|
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|查詢通知要維持使用中的秒數。<br /><br /> 預設值為 432,000 秒 (5 天)。 最小值為 1 秒，最大值為 2^31-1 秒。|
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|通知的訊息文字。 這是使用者定義的文字，而且沒有預先定義的格式。<br /><br /> 根據預設，字串是空的。 請使用1到2000個字元來指定訊息。|
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|查詢通知選項。 這些是使用 *name*=*value* 語法在字串中指定。 使用者負責建立此服務以及從佇列讀取通知。<br /><br /> 預設為空字串。|

通知訂閱一律會進行認可。 不論語句是在使用者交易中執行, 還是在自動認可中執行, 或是語句執行的交易是由哪一個或一個復原而成, 都會發生這種情況。 伺服器通知會在發生下列任何無效通知條件時觸發：基礎資料或結構描述變更，或達到逾時期限 (視何者為先)。 

通知註冊會在引發之後立刻刪除。 因此在接到通知後，應用程式必須再次訂閱，才能取得進一步的更新。

其他的連接或執行緒可以檢查目的地佇列是否有通知。 例如：

```sql
WAITFOR (RECEIVE * FROM MyQueue); -- Where MyQueue is the queue name.
```

> [!NOTE]
> `SELECT *`不會從佇列中刪除專案。 不過, `RECEIVE * FROM`會執行。 如果佇列是空的，這麼做會使伺服器延滯。 如果呼叫時有佇列專案, 則會立即傳回。 否則, 呼叫會等到佇列專案建立為止。

```sql
RECEIVE * FROM MyQueue
```

如果佇列是空的, 此語句會立即傳回空的結果集。 否則, 它會傳回所有佇列通知。

如果`SSPROP_QP_NOTIFICATION_MSGTEXT` 和`SSPROP_QP_NOTIFICATION_OPTIONS`為非 null 且非空白, 則會將包含上述三個屬性的查詢通知 TDS 標頭傳送至伺服器。 每次執行命令時, 就會發生這種情況。 如果其中一個為 null (或空白), 則不會傳送標頭`DB_E_ERRORSOCCURRED`並引發`DB_S_ERRORSOCCURRED` (如果屬性同時標示為選擇性, 則會引發)。 然後, 狀態值會設定為`DBPROPSTATUS_BADVALUE`。 執行和準備時, 會進行驗證。 同樣地，當針對 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 之前的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本連線設定查詢通知屬性時，會引發 `DB_S_ERRORSOCCURED`。 在此情況下, status 值`DBPROPSTATUS_NOTSUPPORTED`為。

初始化訂閱並不保證後續的訊息能成功傳遞。 此外，系統也不會檢查所指定服務名稱的有效性。

> [!NOTE]
> 準備語句永遠不會啟動訂閱。 只有語句執行才會完成起始。 查詢通知不會因為使用 OLE DB 核心服務而受到影響。

如需屬性集的`DBPROPSET_SQLSERVERROWSET`詳細資訊, 請參閱資料列[集屬性和行為](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)。

## <a name="see-also"></a>另請參閱

[OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)
