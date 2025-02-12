---
title: 資料庫鏡像監視器 (狀態頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.dbmmonitor.status.f1
ms.assetid: 4f64b4e1-89e9-4827-98fa-b92c3dc73b48
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 449633953c0561191471733fa3a3dcba0fb24b83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006400"
---
# <a name="database-mirroring-monitor-status-page"></a>資料庫鏡像監視器 (狀態頁面)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  這個唯讀頁面會針對目前在導覽樹狀目錄中選取的資料庫，顯示其主體和鏡像伺服器執行個體的最新鏡像狀態。 如果有關某個執行個體的資訊目前無法使用，則 [狀態]  方格中與該執行個體對應的某些資料格就會呈現灰色並顯示 [未知]  。  
  
 **若要使用 SQL Server Management Studio 監視資料庫鏡像**  
  
-   [啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)  
  
## <a name="options"></a>選項。  
 **狀態**  
 顯示包含了各個主體和鏡像伺服器執行個體之最新高層級鏡像狀態的方格。 [狀態]  方格中的資料列順序如下：  
  
-   主體伺服器執行個體  
  
-   鏡像伺服器執行個體  
  
 資料行如下：  
  
|資料行名稱|Description|  
|-----------------|-----------------|  
|**伺服器執行個體**|其狀態顯示在 **[狀態]** 資料列中的伺服器執行個體名稱。|  
|**目前的角色**|伺服器執行個體目前的角色，可為 [主體]  或 [鏡像]  。|  
|**鏡像狀態**|伺服器執行個體所報告的鏡像狀態，並以圖示指出狀態的嚴重性。 可能的狀態及其相關聯的圖示如下所示：<br /><br /> 圖示：-，狀態為 [未知]  。 監視器未連接到任何一個夥伴。 唯一的可用資訊就是監視器所快取的內容。<br /><br /> 圖示：警告圖示，狀態為 [正在同步處理]  。 鏡像資料庫的內容落後於主體資料庫的內容。 主體伺服器執行個體正在將記錄傳送到鏡像伺服器執行個體，這時會將變更套用至鏡像資料庫，以便向前復原。 在資料庫鏡像工作階段開始時，鏡像資料庫和主體資料庫都是處於這個狀態。<br /><br /> 圖示：標準資料庫圓柱，狀態為 [已同步處理]  。 當鏡像伺服器足以追趕上主體伺服器時，資料庫狀態就會變成 [已同步處理]  。 只要主體伺服器繼續將變更傳送到鏡像伺服器，而鏡像伺服器也繼續將變更套用到鏡像資料庫，資料庫便會一直保持在這個狀態。  在高安全性模式中，可以進行自動容錯移轉和手動容錯移轉，不會遺失任何資料。  在高效能模式中，永遠都有可能遺失部分資料，即使是在 [已同步處理]  狀態也是如此。<br /><br /> 圖示：警告圖示，狀態為 [已暫停]  。 <br />                            主體資料庫可供使用，但是不會將任何記錄傳送到鏡像伺服器。<br /><br /> 圖示：錯誤圖示，狀態為 [已中斷連接]  。 伺服器執行個體無法連接到其夥伴。|  
|**見證連接**|見證的連接狀態，前面會有一個狀態圖示，可為 [未知]  、[已連接]  或 [已中斷連接]  。|  
|**記錄**|按一下即可顯示伺服器執行個體上的鏡像記錄。 這時會開啟 [資料庫鏡像記錄]  對話方塊，顯示特定伺服器執行個體上某個鏡像資料庫的鏡像狀態記錄和統計資料。<br /><br /> 如果監視器未連接到伺服器執行個體，則 [記錄]  按鈕會呈暗灰色。|  
  
 **主體記錄 (** *\<時間>* **)**  
 主體伺服器執行個體上的記錄狀態，以伺服器執行個體的本地時間為準，此時間是以 \<時間>  來表示。 會顯示下列參數：  
  
 **未傳送的記錄**  
 在傳送佇列中等待的記錄量 (以 KB 為單位)。  
  
 **最舊尚未傳送的交易**  
 傳送佇列中最舊尚未傳送之交易的存在時間。 這項交易的存在時間會指出尚未傳送到鏡像伺服器執行個體的交易分鐘數。 這個值有助於從時間方面來測量資料遺失的可能性。  
  
 **傳送記錄的時間 (估計)**  
 主體伺服器執行個體將目前在傳送佇列中的記錄傳送到鏡像伺服器執行個體所需的大約時間量 ( *傳送速率*)。 由於內送交易的速率可能會有極大的差異，因此傳送記錄的時間只是估計值。 但是，傳送速率對於粗略估計手動容錯移轉所需的時間可能會很有用。  
  
 **目前的傳送速率**  
 將交易傳送到鏡像伺服器執行個體的速率 (以每秒 KB 數為單位)。  
  
 **新交易的目前速率**  
 將內送交易輸入到主體記錄中的速率 (以每秒 KB 數為單位)。 若要判斷鏡像是落後、超前，還是趕上進度，請將這個值與 **[傳送記錄的時間 (估計)]** 值加以比較。  
  
 **鏡像記錄 (** \<時間>  **)**  
 鏡像伺服器執行個體上的記錄狀態，以伺服器執行個體的本地時間為準，此時間是以 \<時間>  來表示。 會顯示下列參數：  
  
 **未還原的記錄**  
 在重做佇列中等待的記錄量 (以 KB 為單位)。  
  
 **還原記錄的時間 (估計)**  
 將目前在重做佇列中的記錄套用至鏡像資料庫所需的大約分鐘數。  
  
 **目前的還原速率**  
 將交易還原到鏡像資料庫中的速率 (以每秒 KB 數為單位)。  
  
 **鏡像認可負擔**  
 在主體伺服器上產生警告之前所容許之每項交易的平均延遲毫秒數。 這項延遲是當主體伺服器執行個體等待鏡像伺服器執行個體將交易記錄寫入重做佇列中時所產生的負擔量。 只有在高安全性模式中才會顯出這個值的重要性。  
  
 **傳送與還原所有目前記錄的時間 (估計)**  
 傳送與還原到目前時間為止已在主體伺服器上認可之所有記錄所需的時間。 由於傳送與還原可以平行操作，因此這個時間值可能會小於 [傳送記錄的時間 (估計)]  和 [還原記錄的時間 (估計)]  欄位值的總和。 不過，這個估計值確實可以預測在處理傳送佇列中的積存記錄時，如果要傳送與還原在主體伺服器上所認可之新交易所需的時間。  
  
 **見證位址**  
 見證伺服器執行個體的網路位址。 如需此位址格式的資訊，請參閱[指定伺服器網路位址 &#40;資料庫鏡像&#41;](../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)。  
  
 **作業模式**  
 資料庫鏡像工作階段的作業模式：  
  
-   **高效能 (非同步)**  
  
-   **不具有自動容錯移轉的高安全性 (同步)**  
  
-   **具有自動容錯移轉的高安全性 (同步)**  
  
## <a name="remarks"></a>Remarks  
 **dbm_monitor** 固定資料庫角色的成員可以使用「資料庫鏡像監視器」或 **sp_dbmmonitorresults** 預存程序，檢視現有的鏡像狀態。 但是這些使用者無法更新狀態資料表。 它們必須透過 [資料庫鏡像監視器作業]  來定期更新狀態資料表。 若要了解顯示狀態的時間，使用者可以查看 [主體記錄 (\<時間>)]  和 [鏡像記錄 (\<時間>)]  標籤中的時間。  
  
 如果這項作業不存在，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 已停止，則狀態將會越來越過時，因此可能再也無法反映鏡像工作階段的組態。 例如，在容錯移轉之後，夥伴可能看起來像是共用相同的角色 (主體或鏡像)，或者目前的主體伺服器可能會顯示為鏡像，而目前的鏡像伺服器則顯示為主體。  
  
## <a name="see-also"></a>另請參閱  
 [啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [監視資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/monitoring-database-mirroring-sql-server.md)   
 [啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
  
