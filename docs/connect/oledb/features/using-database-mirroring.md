---
title: 使用資料庫鏡像 |Microsoft Docs
description: 針對 SQL Server 使用具有 OLE DB 驅動程式的資料庫鏡像
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- OLE DB Driver for SQL Server, database mirroring
- data access [OLE DB Driver for SQL Server], database mirroring
- database mirroring [SQL Server], connecting clients to
- MSOLEDBSQL, database mirroring
- OLE DB Driver for SQL Server, database mirroring
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 9d61dfe1441029cfa1b742e3b56021e55764d4eb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67988874"
---
# <a name="using-database-mirroring"></a>使用資料庫鏡像
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)] 請改用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。  
  
 在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中導入的資料庫鏡像是一套增加資料庫可用性與資料冗餘的方案。 OLE DB Driver for SQL Server 會提供對資料庫鏡像的隱含支援，因此在將其針對資料庫設定後，開發人員就不需要撰寫任何程式碼或採取其他任何動作。  
  
 資料庫鏡像是根據每一個資料庫來實作，它會在待命伺服器上保留 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 生產資料庫的複本。 此伺服器為熱或暖待命伺服器，端視資料庫鏡像工作階段的組態和狀態而定。 熱待命伺服器支援不會遺失任何已認可交易的快速容錯移轉，而暖待命伺服器支援強制服務 (資料可能會遺失)。  
  
 生產資料庫稱為「主體資料庫」  ，而待命副本則稱為「鏡像資料庫」  。 主體資料庫和鏡像資料庫必須位於個別的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體 (伺服器執行個體) 上，如有可能，也應該位於個別的電腦上。  
  
 稱為「主體伺服器」  的實際執行伺服器執行個體會與稱為「鏡像伺服器」  的待命伺服器執行個體進行通訊。 主體伺服器和鏡像伺服器會在資料庫鏡像「工作階段」  內當做夥伴運作。 如果主體伺服器失敗，則鏡像伺服器可以透過稱為「容錯移轉」  的處理序，使鏡像伺服器的資料庫成為主體資料庫。 例如，Partner_A 與 Partner_B 是兩個夥伴伺服器，其中主體資料庫一開始位於 Partner_A 上做為主體伺服器，而鏡像資料庫位於 Partner_B 上做為鏡像伺服器。 如果 Partner_A 離線，Partner_B 上的資料庫可以容錯移轉，變成目前的主體資料庫。 當 Partner_A 重新加入鏡像工作階段時，它會變成鏡像伺服器而其資料庫會變成鏡像資料庫。  
  
 替代的資料庫鏡像組態提供不同層次的效能及資料安全，並支援不同形式的容錯移轉。 如需詳細資訊，請參閱[資料庫鏡像 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)。  
  
 指定鏡像資料庫名稱時，可以使用別名。  
  
> [!NOTE]  
>  如需有關初始連接嘗試和鏡像資料庫之重新連接嘗試的詳細資訊, 請參閱[將用戶端&#40;連接&#41;到資料庫鏡像會話 SQL Server](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)。  
  
## <a name="programming-considerations"></a>程式設計考量  
 當主體資料庫伺服器失敗時，用戶端應用程式會在回應 API 呼叫時收到錯誤，這表示與資料庫的連接已經中斷。 發生這個情況時，對於資料庫的任何未認可變更都會遺失，而且目前的交易會回復。 如果發生這個情況，應用程式應該關閉連接 (或釋出資料來源物件) 然後再重新開啟它。 此連接會以透明的方式重新導向鏡像資料庫，現在當做主體伺服器使用。  
  
 建立連接時，主體伺服器會將其容錯移轉夥伴的識別傳送到容錯移轉發生時所使用的用戶端。 在應用程式嘗試在主體伺服器失敗後建立連接的情況下，用戶端不會知道容錯移轉夥伴的識別。 為了讓用戶端有機會處理此狀況，初始化屬性和相關聯的連接字串關鍵字可讓用戶端自行指定容錯移轉夥伴的識別。 只有在有可用的主體伺服器，但未使用時，才會在此狀況中使用用戶端屬性。 如果用戶端提供的容錯移轉夥伴伺服器指的不是當做容錯移轉夥伴的伺服器，伺服器就會拒絕連接。 若要讓應用程式符合組態變更，實際容錯移轉夥伴的識別可以透過檢查建立連接後的屬性來判斷。 如果第一次建立連接的嘗試失敗，您應該考慮快取處理夥伴資訊來更新連接字串或想出重試策略。  
  
> [!NOTE]  
>  如果您要在 DSN、連接字串或連接屬性 (Property)/屬性 (Attribute) 中使用此功能，您必須明確指定連接所使用的資料庫。 SQL Server 的 OLE DB 驅動程式不會嘗試容錯移轉到夥伴資料庫 (如果未這麼做)。  
>   
>  鏡像是資料庫的一個功能。 使用多個資料庫的應用程式可能無法使用此功能。  
>   
>  此外，伺服器名稱不區分大小寫，但是資料庫名稱會區分大小寫。 因此，您應該確認您在 DSN 和連接字串中使用相同的大小寫。  
  
## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server  
 OLE DB Driver for SQL Server 透過連接和連接字串屬性支援資料庫鏡像。 SSPROP_INIT_FAILOVERPARTNER 屬性已加入到 DBPROPSET_SQLSERVERDBINIT 屬性集，而 **FailoverPartner** 關鍵字是 DBPROP_INIT_PROVIDERSTRING 的新連接字串屬性。 如需詳細資訊, 請參閱[使用連接字串關鍵字搭配適用于 SQL Server 的 OLE DB 驅動程式](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。  
  
 只要載入提供者，就可以維持容錯移轉快取，直到呼叫 **CoUninitialize** 為止，或只要應用程式擁有 OLE DB Driver for SQL Server 所管理之特定物件的參考即可，例如資料來源物件。  
  
 如需資料庫鏡像之 SQL Server 支援 OLE DB 驅動程式的詳細資訊, 請參閱[初始化和授權屬性](../../oledb/ole-db-data-source-objects/initialization-and-authorization-properties.md)。  
 
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)   
 [將用戶端連接至資料庫鏡像工作階段 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)   
 [資料庫鏡像 &#40;SQL Server&#41;](../../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
