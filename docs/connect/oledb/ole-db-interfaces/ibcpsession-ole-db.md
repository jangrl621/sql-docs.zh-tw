---
title: IBCPSession (OLE DB) |Microsoft Docs
description: IBCPSession 介面 (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apitype: COM
helpviewer_keywords:
- IBCPSession interface
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 73f8fd440903c525856475200921f97a25d9b27b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015507"
---
# <a name="ibcpsession-ole-db"></a>IBCPSession (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **IBCPSession** 介面會公開以 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 檔案為基礎之大量複製作業的支援。 在 OLE DB 驅動程式中, 會針對與會話相同層級下的 SQL Server 公開**IBCPSession**介面。 在 OLE DB Driver for SQL Server 中，資料來源物件是工作階段物件的 Factory，而且大量複製作業指定於連線屬性 SSPROP_ENABLEBULKCOPY 中。 此外，SSPROP_ENABLEFASTLOAD 屬性應該要設定為 true。  
  
 然後，呼叫 **IDBCreateSession::CreateSession** 方法將會導致建立 **BulkCopySession** 物件。 所有透過 **IBCPSession** 物件公開之以檔案為基礎的大量複製方法會變成可在這個 **IBCPSession** 物件的 **IBCPSession** 介面上使用幾乎相同的簽章進行呼叫。  
  
> [!NOTE]  
>  OLE DB Driver for SQL Server 支援透過 [IRowsetFastLoad](../../oledb/ole-db-interfaces/irowsetfastload-ole-db.md) 介面進行以記憶體為基礎的大量複製作業。  
  
 如需使用 OLE DB 驅動程式進行大量複製作業 SQL Server 的詳細資訊, 請參閱[執行大量複製作業](../../oledb/features/performing-bulk-copy-operations.md)。  
  
 如需顯示如何使用**IBCPSession**介面的範例, 請參閱[IBCPSession:: BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
|方法|Description|  
|------------|-----------------|  
|[IBCPSession::BCPColFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md)|在程式變數與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料行之間建立繫結。|  
|[IBCPSession::BCPColumns &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md)|設定要繫結至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料表中之資料行的欄位數目。|  
|[IBCPSession::BCPControl &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md)|設定大量複製作業的選項。|  
|[IBCPSession::BCPDone &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpdone-ole-db.md)|認可要傳送至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的其餘資料列。|  
|[IBCPSession::BCPExec &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpexec-ole-db.md)|執行大量複製作業。|  
|[IBCPSession::BCPInit &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md)|初始化大量複製結構、執行一些錯誤檢查、確認資料和格式檔案名稱正確無誤，然後開啟這些項目。|  
|[IBCPSession::BCPReadFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md)|從格式檔案中讀取每個資料行的格式資訊。|  
|[IBCPSession::BCPWriteFmt &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-bcpwritefmt-ole-db.md)|將每個資料行的格式資訊寫入格式檔案。|  
  
## <a name="see-also"></a>另請參閱  
 [介面&#40;OLE DB&#41;](../../oledb/ole-db-interfaces/oledb-driver-for-sql-server-ole-db-interfaces.md)  
  
  
