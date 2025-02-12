---
title: 升級和移轉 Reporting Services | Microsoft Docs
ms.prod: reporting-services
ms.prod_service: reporting-services-native
helpviewer_keywords:
- SSRS, upgrading
- Reporting Services, upgrades
- SQL Server Reporting Services, upgrading
- upgrading Reporting Services
author: maggiesMSFT
ms.author: maggies
ms.topic: conceptual
ms.date: 08/17/2017
ms.openlocfilehash: 9d0ff28e1e9c7784da2c1206f72573ba608797a1
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68264988"
---
# <a name="upgrade-and-migrate-reporting-services"></a>Upgrade and Migrate Reporting Services

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2016](../../includes/ssrs-appliesto-2016.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)] [!INCLUDE[ssrs-appliesto-sharepoint-2013-2016i](../../includes/ssrs-appliesto-sharepoint-2013-2016.md)]

  本主題概述 SQL Server Reporting Services 的升級與移轉選項。 升級 SQL Server Reporting Services 部署的一般方式有兩種：  
 
-   **升級：** 您可以在目前安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 元件的伺服器和執行個體上升級這些元件。 這種方式通常稱為「就地」升級。 不支援從 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 伺服器的一種模式就地升級至另一種模式。 例如，您無法將原生模式報表伺服器升級至 SharePoint 模式報表伺服器。 您可以將報表項目從一個模式移轉至另一個模式。 如需詳細資訊，請參閱本文件稍後的＜原生至 SharePoint 移轉＞一節。  
  
-   **移轉**：安裝和設定新的 SharePoint 環境、將報表項目和資源複製到新環境，然後設定新環境，以使用現有的內容。 較低層級的移轉形式為複製 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 資料庫、組態檔，如果您是使用 SharePoint 模式，則還有 SharePoint 內容資料庫。  
    
> **[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式 &#124; [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式

> [!NOTE]
> SQL Server 2016 後即不再提供 Reporting Services 與 SharePoint 的整合。
   
##  <a name="bkmk_known_issues"></a> 升級的已知問題和最佳作法  
 如需可支援版本與可升級版本的詳細清單，請參閱＜ [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)＞。  
  
> [!TIP]  
>  如需有關 SQL Server 問題的最新資訊，請參閱下列主題：  
>   
>  -   [SQL Server 2016 版本資訊](https://go.microsoft.com/fwlink/?LinkID=398124)。  
  
  
##  <a name="bkmk_side_by_side"></a> 並排安裝  
 SQL Server Reporting Services 原生模式可以與 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 原生模式部署並排安裝。  
  
 不支援 SharePoint 模式的 SQL Server Reporting Services 與任何舊版 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式元件並排部署。  
  
  
##  <a name="bkmk_inplace_upgrade"></a> 就地升級  
 升級是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式完成。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式可用於升級任何或所有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件，包括 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]在內。 安裝程式會偵測現有的執行個體，並提示您進行升級。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會提供升級選項，您可以將這些選項指定為命令列引數或在安裝精靈中指定。  
  
 您在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式時，可以從下列其中一個版本選取要升級的選項，或是安裝新的 SQL Server Reporting Services 執行個體，與現有安裝並排執行：  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]  
  
-   [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]  
  
 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的詳細資訊，請參閱下列主題：  

* [升級為 SQL Server 2016](../../database-engine/install-windows/upgrade-sql-server.md)
* [使用安裝精靈升級為 SQL Server 2016 &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)
* [從命令提示字元安裝 SQL Server 2016](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)
  
  
##  <a name="bkmk_upgrade_checklist"></a> 升級前檢查清單  
 在升級到 SQL Server Reporting Services 之前，請檢閱下列各項：  
  
-   檢閱需求，以判斷您的軟硬體是否可以支援 [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)]。 如需詳細資訊，請參閱 [安裝 SQL Server 2016 的硬體與軟體需求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。  
  
-   使用 System Configuration Checker (SCC) 來掃描報表伺服器電腦，找出任何可能阻礙 SQL Server Reporting Services 成功安裝的狀況。 如需詳細資訊，請參閱 [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)。  
  
-   檢閱 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的安全性最佳做法和指南。 如需詳細資訊，請參閱＜ [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)＞。  
  
-   備份對稱金鑰。 如需詳細資訊，請參閱 [備份與還原 Reporting Services 加密金鑰](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)。  
  
-   備份報表伺服器資料庫和組態檔。 如需詳細資訊，請參閱＜ [Backup and Restore Operations for Reporting Services](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md)＞。  
  
-   備份在 IIS 中對現有 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 虛擬目錄所進行的任何自訂。  
  
-   移除無效的 SSL 憑證。  這包括已過期而且您不打算要在升級 Reporting Services 之前更新的憑證。  無效的憑證會導致升級失敗，並且會在 Reporting Services 記錄檔中寫入類似下列的錯誤訊息︰ **Microsoft.ReportingServices.WmiProvider.WMIProviderException︰網站上未設定安全通訊端層 (SSL) 憑證**。  
  
 在升級實際執行環境之前，請務必在與實際執行環境具有相同組態的實際執行前環境中執行測試升級。  
  
  
## <a name="overview-of-migration-scenarios"></a>移轉案例概觀  
 如果您要從受支援的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 版本升級到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，通常可以執行 [ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈] 來升級報表伺服器程式檔案、資料庫和所有應用程式資料。  
  
 但是，如果您遇到下列任何狀況，則需要手動 **移轉** 報表伺服器安裝：  
  
-   您想要變更部署中使用的報表伺服器類型。 例如，您無法將原生模式報表伺服器升級或轉換為 SharePoint 模式。 如需詳細資訊，請參閱[原生至 SharePoint 移轉 &#40;SSRS&#41;](../../reporting-services/install-windows/native-to-sharepoint-migration-ssrs.md)。  
  
-   您想要在升級過程中，將報表伺服器離線的時間縮到最短。 當您將內容資料複製到新的報表伺服器執行個體並測試安裝時，目前的安裝會保持上線狀態，而不會變更現有報表伺服器安裝的狀態。  
  
-   您想要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 的 SharePoint 2010 部署移轉到 SharePoint 2013/2016。 SharePoint 2013/2016 不支援從 SharePoint 2010 就地升級。 如需詳細資訊，請參閱[移轉 Reporting Services 安裝 &#40;SharePoint 模式&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)。  
  
  
##  <a name="bkmk_native_scenarios"></a> 原生模式升級和移轉狀況  
 **升級：** 原生模式的就地升級對於每個稍早在本主題中列出的支援版本而言，是相同的程序。 執行 SQL Server 安裝精靈或命令列安裝。 在安裝之後，報表伺服器資料庫將自動升級至新的報表伺服器資料庫結構描述。 如需詳細資訊，請參閱本主題中的 [就地升級](#bkmk_inplace_upgrade) 一節。  
  
 當您選取要升級的現有報表伺服器執行個體時，升級程序就會開始。  
  
1.  如果報表伺服器資料庫在遠端電腦上，而且您沒有更新該資料庫的權限，安裝程式會提示您提供用於更新遠端報表伺服器資料庫的認證。 請務必提供具有 **sysadmin** 或資料庫更新權限的認證。  
  
2.  安裝程式會檢查是否有防止升級的條件或設定，並讀取組態設定。 範例包括部署在報表伺服器上的自訂延伸模組。 如果升級受到封鎖，您必須修改您的安裝，好讓升級不再被封鎖，或是移轉到新的 SQL Server Reporting Services 執行個體。 如需詳細資訊，請參閱 Upgrade Advisor 文件集。  
  
3.  如果升級可以繼續，安裝程式會提示您繼續進行升級程序。  
  
4.  安裝程式會針對 SQL Server Reporting Services 程式檔建立新的資料夾。 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝的程式資料夾包括 MSRS13.\<執行個體名稱  >。  
  
5.  安裝程式會新增 SQL Server Reporting Services 報表伺服器程式檔、設定工具，以及屬於報表伺服器功能之一部分的命令列公用程式。  
  
    1.  舊版中的程式檔會遭到移除。  
  
    2.  升級到新版本的報表伺服器組態工具和公用程式包括原生模式 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具、命令列公用程式 (例如 RS.exe) 和報表產生器。  
  
    3.  其他用戶端工具，如 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，要另行下載且需要個別升級。 如需詳細資訊，請參閱 [Download SQL Server Management Studio (SSMS)](https://msdn.microsoft.com/library/mt238290.aspx)(下載 SQL Server Management Studio (SSMS))。
  
    4.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 是不同的下載。 如需詳細資訊，請參閱 [SQL Server Data Tools in Visual Studio 2015](https://msdn.microsoft.com/mt186501)(Visual Studio 中的 SQL Server Data Tools)。  
  
6.  安裝程式會在服務控制管理員中重複使用 SQL Server Reporting Services 報表伺服器服務的服務項目。 這個服務項目包含 Report Server Windows 服務帳戶。  
  
7.  安裝程式會根據 IIS 中的現有虛擬目錄設定來保留新的 URL。 安裝程式可能不會移除 IIS 中的虛擬目錄，所以在升級完成之後，請務必手動移除這些目錄。  
  
8.  安裝程式會合併組態檔中的設定。 使用目前安裝中的組態檔當做基礎，加入新的項目。 已過時的項目不會移除，但是報表伺服器在升級完成之後不會再讀取這些項目。 升級將不會刪除舊的記錄檔、過時的 RSWebApplication.config 檔，或是 IIS 中的虛擬目錄設定。 升級也不會移除舊版報表設計師、Management Studio 或其他用戶端工具。 如果您不再需要這些項目，請務必在升級完成之後移除這些檔案和工具。  
  
 **移轉：** 將舊版的原生模式安裝移轉至 SQL Server Reporting Services 對於所有稍早在本主題中列出的支援版本而言是相同的步驟。 如需詳細資訊，請參閱[移轉 Reporting Services 安裝 &#40;原生模式&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-native-mode.md)  
  
  
##  <a name="bkmk_native_scaleout"></a> 升級 Reporting Services 原生模式向外延展部署  
 以下為如何升級向外延展至多部報表伺服器之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 原生模式部署的摘要。 此程序需要 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 部署的停機時間：  
  
1.  備份報表伺服器資料庫和加密金鑰。 如需詳細資訊，請參閱 [Reporting Services 的備份與還原作業](../../reporting-services/install-windows/backup-and-restore-operations-for-reporting-services.md)和[新增和移除向外延展部署的加密金鑰 &#40;SSRS 設定管理員&#41;](../../reporting-services/install-windows/add-and-remove-encryption-keys-for-scale-out-deployment.md)。  
  
2.  使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，將向外延展部署中的所有報表伺服器移除。 如需詳細資訊，請參閱[設定原生模式報表伺服器向外延展部署 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)。  
  
3.  將其中一部報表伺服器升級至 SQL Server Reporting Services。  
  
4.  使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態管理員，將該報表伺服器加回向外延展部署中。 如需詳細資訊，請參閱[設定原生模式報表伺服器向外延展部署 &#40;SSRS 組態管理員&#41;](../../reporting-services/install-windows/configure-a-native-mode-report-server-scale-out-deployment.md)。  
  
     針對每部伺服器，重複升級和向外延展步驟。  
  
##  <a name="bkmk_sharePoint_scenarios"></a> SharePoint 模式升級和移轉狀況  
 下列章節描述從指定版本的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式升級或移轉至 SQL Server Reporting Services [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的問題及所需的基本步驟。  
  
 有兩個安裝元件要升級 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式部署。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共用服務。  
  
    > [!TIP]  
    >  使用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 指令程式 `Get-SPRSServiceApplicationServers` 判斷 SharePoint 伺服器陣列中目前執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 共用服務，因此也需要升級的伺服器。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用於 SharePoint 產品的增益集。 如需詳細資訊，請參閱 [安裝或解除安裝 SharePoint 的 Reporting Services 增益集](../../reporting-services/install-windows/install-or-uninstall-the-reporting-services-add-in-for-sharepoint.md)。  
  
 如需移轉 SharePoint 模式安裝的詳細步驟，請參閱[遷移 Reporting Services 安裝 &#40;SharePoint 模式&#41;](../../reporting-services/install-windows/migrate-a-reporting-services-installation-sharepoint-mode.md)。  
  
> [!IMPORTANT]  
>  下列某些狀況因為升級所需的技術不同，而需要將 SharePoint 環境停機。 如果您的情況不允許停機，將需要完成移轉，而非就地升級。  
  
### <a name="includesssql14includessssql14-mdmd-to-sql-server-reporting-services"></a>[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 SQL Server Reporting Services  
 **起始環境：** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 或 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP1、SharePoint 2010 或 SharePoint 2013。  
  
 **結束環境：** SQL Server Reporting Services、SharePoint 2013 或 SharePoint 2016。   
  
-   **SharePoint 2013/2016：** SharePoint 2013/2016 不支援從 SharePoint 2010 就地升級。 不過，支援 **資料庫附加升級**  的程序。
  
     如果您擁有與 SharePoint 2010 整合的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝，就無法就地升級 SharePoint 伺服器。 不過，您可以將內容資料庫和伺服器應用程式資料庫從 SharePoint 2010 伺服器陣列移轉至 SharePoint 2013/2016 伺服器陣列。  
  
### <a name="includesssql11includessssql11-mdmd-to-sql-server-reporting-services"></a>[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 SQL Server Reporting Services  
 **起始環境：** [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)]、SharePoint 2010。  
  
 **結束環境：** SQL Server Reporting Services、SharePoint 2013 或 SharePoint 2016。   
  
-   **SharePoint 2013/2016：** SharePoint 2013/2016 不支援從 SharePoint 2010 就地升級。 不過，支援 **資料庫附加升級**  的程序。
  
     如果您擁有與 SharePoint 2010 整合的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 安裝，就無法就地升級 SharePoint 伺服器。 不過，您可以將內容資料庫和伺服器應用程式資料庫從 SharePoint 2010 伺服器陣列移轉至 SharePoint 2013/2016 伺服器陣列。  
  
### <a name="includesskilimanjaroincludessskilimanjaro-mdmd-to-sql-server-reporting-services"></a>[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 至 SQL Server Reporting Services  
 **起始環境：** [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、SharePoint 2010。  
  
 **結束環境：** SQL Server Reporting Services、SharePoint 2013 或 SharePoint 2016。  
 
-   **SharePoint 2013/2016：** SharePoint 2013/2016 不支援從 SharePoint 2010 就地升級。 不過，支援 **資料庫附加升級**  的程序。

    SharePoint 必須先移轉，Reporting Services 才能升級。
  
-   在伺服器陣列的每個 Web 前端上，安裝適用於 SharePoint 之 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 增益集的 SQL Server Reporting Services 版本。 您可以使用 SQL Server Reporting Services 安裝精靈或下載增益集來安裝此增益集。  
  
-   執行 SQL Server Reporting Services 安裝以升級每部「報表伺服器」的 SharePoint 模式。 SQL Server 安裝精靈會安裝 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務，並建立新的服務應用程式。 
  
  
##  <a name="bkmk_migration_considerations"></a> 移轉的考量  
 當您移動應用程式資料時，應該注意下列考量和限制：  
  
-   加密金鑰的保護包括了併入電腦識別的雜湊。  
  
-   報表伺服器資料庫名稱是固定的，不能在新的電腦上重新命名。  
  
### <a name="encryption-key-considerations"></a>加密金鑰考量  
 在您將報表伺服器資料庫移到新的電腦之前，一定要先備份加密金鑰。  
  
 將報表伺服器安裝移到另一部電腦時，將會讓用來保護加密金鑰的雜湊失效，這些加密金鑰是用來確保報表伺服器資料庫中所儲存之敏感性資料的安全。 使用此資料庫的每一個報表伺服器執行個體都有各自的加密金鑰複本，該複本是使用目前電腦上定義之服務帳戶的識別來加密。 如果您變更電腦，該服務就無法再存取它的金鑰，即使您在新的電腦上使用相同的帳戶名稱也是一樣。  
  
 若要在新的報表伺服器電腦上重新建立可回復的加密，您必須還原之前所備份的金鑰。 儲存在報表伺服器資料庫中的完整金鑰集合是由對稱金鑰值所組成，再加上用來限制此金鑰之存取的服務識別資訊，如此一來，只有儲存此金鑰的報表伺服器執行個體才可以使用此金鑰。 在金鑰還原期間，報表伺服器將會以新的版本取代現有的金鑰複本。 新的版本包括目前電腦上所定義的電腦和服務識別的值。 如需詳細資訊，請參閱下列主題：  
  
-   SharePoint 模式：請參閱[管理 Reporting Services SharePoint 服務應用程式](../../reporting-services/report-server-sharepoint/manage-a-reporting-services-sharepoint-service-application.md)的＜金鑰管理＞一節  
  
-   原生模式：請參閱 [備份與還原 Reporting Services 加密金鑰](../../reporting-services/install-windows/ssrs-encryption-keys-back-up-and-restore-encryption-keys.md)  
  
  
### <a name="fixed-database-name"></a>固定資料庫名稱  
 您無法重新命名報表伺服器資料庫。 資料庫的識別會在建立資料庫時，記錄於報表伺服器預存程序中。 重新命名報表伺服器的主要或暫存資料庫將會在程序執行時造成錯誤發生，使得報表伺服器安裝失效。  
  
 如果現有安裝的資料庫名稱不適用於新的安裝，您應該考慮使用您所偏好的名稱建立新的資料庫，然後使用以下清單中的技術，載入現有的應用程式資料：  
  
-   撰寫呼叫報表伺服器 Web 服務 SOAP 方法的 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 指令碼，以便在資料庫之間複製資料。 您可以使用 RS.exe 公用程式執行此指令碼。 如需這種方法的詳細資訊，請參閱 [指令碼與 PowerShell 搭配 Reporting Services](../../reporting-services/tools/scripting-and-powershell-with-reporting-services.md)。  
  
-   撰寫可呼叫 WMI 提供者的程式碼，以便在資料庫之間複製資料。 如需這種方法的詳細資訊，請參閱 [存取 Reporting Services WMI 提供者](../../reporting-services/tools/access-the-reporting-services-wmi-provider.md)。  
  
-   如果您只有少量的項目，就可以從報表設計師、模型設計師和報表產生器來將報表和共用資料來源重新發行到新的報表伺服器。 您必須重新建立角色指派、訂閱、共用排程、報表快照集排程、您在報表或其他項目上設定的自訂屬性、模型項目安全性，以及您在報表伺服器上設定的屬性。 您將會遺失報表記錄和報表執行記錄資料。  
  
  
##  <a name="bkmk_additional_resources"></a> 其他資源  
  
> [!NOTE]  
>  如需有關 SharePoint 資料庫附加升級的詳細資訊，請參閱下列主題：  
  
-   [升級到 SharePoint 2016 的程序概觀](https://technet.microsoft.com/library/cc262483\(v=office.16\))。

-   [升級到 SharePoint 2013 的程序概觀](https://go.microsoft.com/fwlink/p/?LinkId=256688)。
  
-   [升級到 SharePoint 2013 之前的清除準備工作](https://go.microsoft.com/fwlink/p/?LinkId=256689)。  
  
-   [將資料庫從 SharePoint 2013 升級到 SharePoint 2016](https://technet.microsoft.com/library/cc303436\(v=office.16\))。

-   [將資料庫從 SharePoint 2010 升級到 SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=256690)。  

## <a name="next-steps"></a>後續步驟

[升級報表](../../reporting-services/install-windows/upgrade-reports.md)   
[使用安裝精靈升級為 SQL Server 2016 &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](https://go.microsoft.com/fwlink/?LinkId=620231)
