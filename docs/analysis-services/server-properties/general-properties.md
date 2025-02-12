---
title: Analysis Services 一般屬性 |Microsoft Docs
ms.date: 07/24/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d0d2a1fd8a83c4b181dfc182f5fb5630e29c9efb
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419516"
---
# <a name="general-properties"></a>一般屬性
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援下表列出的伺服器屬性。 本主題記載 msmdsrv.ini 檔案中，不包含在特定章節中的伺服器屬性，例如 Security、Network 或 ThreadPool。 如需其他伺服器屬性以及如何設定伺服器屬性的詳細資訊，請參閱 [Analysis Services 中的伺服器屬性](../../analysis-services/server-properties/server-properties-in-analysis-services.md)。  
  
 除非另有說明, 否則這些屬性適用于多維度和表格式伺服器模式。  
  
## <a name="non-specific-category"></a>非特定類別目錄  
 **AdminTimeout**  
 此為帶正負號的 32 位元整數屬性，定義管理員逾時 (以秒為單位)。 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 此屬性的預設值為零 (0)，表示沒有逾時。  
  
 **AllowedBrowsingFolders**  
 字串屬性，以分隔清單指定在 Analysis Services 對話方塊中可儲存、開啟和尋找檔案時可瀏覽的資料夾。 Analysis Services 服務帳戶對您加入至清單中的所有資料夾，必須有讀取和寫入權限。  
  
 **BackupDir**  
 字串屬性, 識別預設儲存備份檔案的目錄名稱, 在此事件中, 不會將路徑指定為 Backup 命令的一部分。  
 
**ClientCacheRefreshPolicy**針對 SSAS 和 Azure Analysis Services 中的表格式模型, 此屬性會覆寫所有 Power BI 資料集的**排程**快取重新整理設定。 所有 Live Connect 報表都會觀察伺服器層級的設定, 不論資料集層級設定或其所在的工作區。

此屬性的預設值為-1, 允許在資料集的 [排程快取重新整理] 設定中指定所有背景快取重新整理。 若要防止所有背景快取重新整理, 請指定零 (0)。

  
 **CollationName**  
 此為識別伺服器定序的字串屬性。 如需詳細資訊，請參閱[語言和定序 &#40;Analysis Services&#41;](../../analysis-services/languages-and-collations-analysis-services.md)。  
  
 **CommitTimeout**  
 整數屬性，指定伺服器為了認可交易而將等候取得寫入鎖定的時間 (以毫秒為單位)。 通常需要等候期間，因為伺服器必須等候其他鎖定釋放，然後才能取得認可交易的寫入鎖定。  
  
 此屬性的預設值為零 (0)，表示伺服器會無限期等候。 如需有關鎖定相關屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](http://go.microsoft.com/fwlink/?LinkID=225539)。  
  
 **CoordinatorBuildMaxThreads**  
 此為帶正負號的 32 位元整數屬性，定義配置給建立資料分割索引的最大執行緒數目。 增加此值就能加速資料分割索引，但要耗用較多記憶體。 如需有關此屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](http://go.microsoft.com/fwlink/?LinkID=225539)。  
  
 **CoordinatorCancelCount**  
 此為帶正負號的 32 位元整數屬性，定義伺服器應檢查取消事件是否發生的頻率 (依據內部反覆運算計數)。 降低此數字就能以更高的頻率檢查取消事件，但要耗用一般效能。 表格式伺服器模式會忽略這個屬性。  
  
 **CoordinatorExecutionMode**  
 此為帶正負號的 32 位元整數屬性，定義伺服器會嘗試的最大平行作業數目，包含處理和查詢作業。 零 (0) 表示伺服器會依據內部演算法決定。 正數表示總計的最大作業數目。 具有反轉符號的負數，表示每個處理器的最大作業數目。  

 此屬性的預設值為 -4，表示伺服器限制為每個處理器 4 個平行作業。 如需有關此屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](http://go.microsoft.com/fwlink/?LinkID=225539)。  
  
 **CoordinatorQueryMaxThreads**  
 此為帶正負號的 32 位元整數屬性，定義查詢解析期間每個資料分割區段的最大執行緒數目。 並行使用者的數目愈少此值就愈高，但要耗用較多記憶體。 相對地，如果有大量的並行使用者，就可能需要降低此值。  
  
 **CoordinatorShutdownMode**  
 此為布林值屬性，定義協調器關機模式。 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **DataDir**  
 此為字串屬性，可識別儲存資料的目錄名稱。  
  
 **DeploymentMode**  
 判斷 Analysis Services 伺服器執行個體的運作內容。 在對話方塊、訊息和檔中, 此屬性稱為「伺服器模式」。 根據您在安裝 Analysis Services 時所選取的伺服器模式，此屬性是由 SQL Server 安裝程式所設定。 此屬性應該僅被視為內部屬性，永遠使用安裝程式所指定的值。  
  
 這個屬性的有效值包括：  
  
|值|描述|  
|-----------|-----------------|  
|0|這是預設值。 它指定多維度模式，用於服務使用 MOLAP、HOLAP 和 ROLAP 儲存以及資料採礦模型的多維度資料庫。|  
|1|指定要與 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 部署一起安裝的 Analysis Services 執行個體。 請不要變更 Analysis Services 執行個體的部署模式屬性，因為它是屬於 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for SharePoint 安裝的一部分。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 如果您變更模式，資料將不再於伺服器上執行。|  
|2|指定用於裝載使用記憶體中儲存或 DirectQuery 儲存之表格式模型資料庫的表格式模式。|  
  
 每個模式彼此之間是獨佔的。 設定為表格式模式的伺服器無法執行包含 Cube 和維度的 Analysis Services 資料庫。 如果基礎電腦硬體可以支援它，您就可以在相同的電腦上安裝多個 Analysis Services 執行個體，並將每個執行個體設定為使用不同的部署模式。 請記住，Analysis Services 是非常耗用資源的應用程式。 建議在相同的系統上，僅針對高階伺服器部署多個執行個體。  
  
 **EnableFast1033Locale**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **ExternalCommandTimeout**  
 整數屬性，定義命令發出到外部伺服器的逾時 (以秒為單位)，包含關聯式資料來源和外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。  
  
 此屬性的預設值為 3600 (秒)。  
  
 **ExternalConnectionTimeout**  
 整數屬性，定義建立連接到外部伺服器的逾時 (以秒為單位)，包含關聯式資料來源和外部 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器。 如果在連接字串中指定了連接逾時，則會忽略此屬性。  
  
 此屬性的預設值為 60 (秒)。  
  
 **ForceCommitTimeout**  
 整數屬性，指定在取消目前命令前面的其他命令 (包括進行中的查詢) 之前，寫入認可作業應等候的時間 (以毫秒為單位)。 這允許認可交易透過取消較低優先順序的作業 (例如查詢) 來繼續。  
  
 此屬性的預設值為 30 秒 (30000 毫秒)，表示在認可交易等候 30 秒之前，不會強制其他命令逾時。  
  
> [!NOTE]  
>  這個事件所取消的查詢和處理序將報告下列錯誤訊息："`Server: The operation has been cancelled`"  
  
 如需有關此屬性的詳細資訊，請參閱 [SQL Server 2008 R2 Analysis Services 操作指南](http://go.microsoft.com/fwlink/?LinkID=225539)。  
  
> [!IMPORTANT]  
>  **ForceCommitTimeout** 適用於 Cube 處理命令和回寫作業。  
  
 **IdleConnectionTimeout**  
 整數屬性，指定處於非使用狀態之連接的逾時 (以秒為單位)。  
  
 此屬性的預設值為零 (0)，表示閒置連接不會逾時。  
  
 **IdleOrphanSessionTimeout**  
 整數屬性，定義被遺棄的工作階段要在伺服器記憶體中保留多久 (以秒為單位)。 被遺棄的工作階段是不再具有相關聯連接的工作階段。 預設值是 120 秒。  
  
 **InstanceVisible**  
 此為布林屬性，表示是否可以看見伺服器執行個體，以探索來自 SQL Server Browser 服務的執行個體要求。 預設值為 True。 如果將屬性設定為 false，則執行個體對 SQL Server Browser 為不可見。  
  
 **語言**  
 此為定義語言的字串屬性，包含錯誤訊息和數字格式。 此屬性會覆寫 CollationName 屬性。  
  
 此屬性的預設值是空白，表示 CollationName 屬性會定義語言。  
  
 **LogDir**  
 此為字串屬性，識別包含伺服器記錄檔的目錄名稱。 這個屬性只適用於當記錄會儲存到磁碟檔案，而非資料庫資料表時 (預設行為)。  
  
 **MaxIdleSessionTimeout**  
 整數屬性，定義最長閒置工作階段逾時 (以秒為單位)。 預設值為零 (0)，表示工作階段永遠不會逾時。但是，如果伺服器受到資源的條件約束，閒置工作階段仍然會被移除。  
  
 **MinIdleSessionTimeout**  
 整數屬性，定義最短閒置工作階段逾時 (以秒為單位)。 預設值是 2700 秒。 此時間過期之後，就允許伺服器結束閒置工作階段，但只有需要記憶體時才會如此做。  
  
 **通訊埠**  
 整數屬性，定義伺服器接聽用戶端連接的通訊埠編號。 如果沒有設定，伺服器會動態地找到第一個未使用的通訊埠。  
  
 此屬性的預設值為零 (0)，因而會預設為通訊埠 2383。 如需通訊埠組態的詳細資訊，請參閱＜ [設定 Windows 防火牆以允許 Analysis Services 存取](../../analysis-services/instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)＞。  
  
 **ServerTimeout**  
 整數，定義查詢的逾時 (以秒為單位)。 預設值為 3600 秒 (或 60 分鐘)。 零 (0) 指定任何查詢都不會逾時。  
  
 **TempDir**  
 此為字串屬性，指定儲存暫存檔的位置，在處理、還原以及其他作業期間使用這些暫存檔。 此屬性的預設值是由安裝程式所決定的。 如果未指定，則預設值為 Data 目錄。  
  
## <a name="requestprioritization-category"></a>RequestPrioritization 類別目錄  
 **已啟用**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **StatisticsStoreSize**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 中的伺服器屬性](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [判斷 Analysis Services 執行個體的伺服器模式](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
