---
title: 從安裝精靈安裝 SQL Server 2016 (安裝程式) | Microsoft Docs
ms.custom: ''
ms.date: 06/26/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, steps
- Setup [SQL Server], steps
- SQL Server, installing
ms.assetid: 6ad23de1-2bab-4933-9122-c09f5565028d
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: bdfa96839b92150fde8b6954ffd96f8f34eb7508
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67991091"
---
# <a name="install-sql-server-from-the-installation-wizard-setup"></a>從安裝精靈安裝 SQL Server 2016 (安裝程式)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本文說明如何使用安裝精靈安裝 SQL Server。 它會套用至 [!INCLUDE[SQLServer2016](../../includes/sssql15-md.md)] 和 [!INCLUDE[SQLServer2017](../../includes/sssqlv14-md.md)]。

本文提供的逐步程序，可讓您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式的安裝精靈來安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新執行個體。 安裝精靈會提供單一功能樹狀目錄以供安裝所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件，所以您不必個別安裝它們。 如需個別安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件，請參閱[安裝 SQL Server](../../database-engine/install-windows/install-sql-server.md#how-to-install-individual-components)。  

如需其他安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的方式，請參閱：  

* [從命令提示字元安裝 SQL Server](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)  
* [使用設定檔安裝 SQL Server](../../database-engine/install-windows/install-sql-server-2016-using-a-configuration-file.md)  
* [使用 SysPrep 安裝 SQL Server](../../database-engine/install-windows/install-sql-server-using-sysprep.md)  
* [建立新的 SQL Server 容錯移轉叢集 &#40;安裝程式&#41;](../../sql-server/failover-clusters/install/create-a-new-sql-server-failover-cluster-setup.md)  
* [使用安裝精靈升級 SQL Server &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)

## <a name="get-the-installation-media"></a>取得安裝媒體

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]
  
## <a name="prerequisites"></a>Prerequisites

在安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之前，請檢閱[規劃 SQL Server 安裝](../../sql-server/install/planning-a-sql-server-installation.md)。  
  
> [!NOTE]  
> 如果是本機安裝，您必須以管理員身分執行安裝程式。 如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。  

###  <a name="bkmk_ga_instalpatch"></a> 安裝修補程式需求

Microsoft 發現 Microsoft Visual C++ 2013 Runtime 二進位檔的問題，SQL Server 2016 必須安裝這些二進位檔。 已提供修正此問題的更新。 如未安裝這項 Visual C++ Runtime 二進位檔的更新，SQL Server 就可能在特定情況下遇到穩定性問題。 安裝 SQL Server 之前，請先遵循 [SQL Server 版本資訊](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)的指示，查看您的電腦是否需要 Visual C++ Runtime 二進位檔的修補程式。  
  
## <a name="to-install-includessnoversionincludesssnoversion-mdmd"></a>安裝 [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]  
  
1. 插入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體。 在根資料夾中，按兩下 **Setup.exe**。 若要從網路共用執行安裝，請找出共用上的根資料夾，然後按兩下 **Setup.exe**。  
  
2. 安裝精靈會執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝中心。 若要建立 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新安裝，請在左側導覽區域中，選取 [安裝]  ，然後選取 [新增 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 獨立安裝或將功能新增到現有安裝]  。  

3. 在 [產品金鑰]  頁面上選取選項，指出您要安裝免費的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本或具有 PID 金鑰的產品版本。 如需詳細資訊，請參閱 [SQL Server 2017 的版本及支援功能](../../sql-server/editions-and-components-of-sql-server-2017.md)。  
  
   若要繼續，請選取 [下一步]  。

<!--
The following item is for SQL Server 2019 or later
-->
  
::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

4. 在 [授權條款]  頁面上，檢閱授權合約。 如果您同意，請選取 [我接受授權條款和[隱私權聲明](https://privacy.microsoft.com/privacystatement)]  核取方塊，然後選取 [下一步]  。  

::: moniker-end

<!--
The following item is for SQL Server 2016-2017
-->

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"

4. 在 [授權條款]  頁面上，檢閱授權合約。 如果您同意，請選取 [我接受授權條款]  核取方塊，然後選取 [下一步]  。  

::: moniker-end

   >[!NOTE]
   > SQL Server 會將您的安裝經驗及其他使用方式與效能資料的相關資訊傳送給 Microsoft，以協助改進產品。 若要深入了解 SQL Server 資料處理與隱私權控制，請參閱[隱私權聲明](https://privacy.microsoft.com/privacystatement)和[設定 SQL Server 將意見反應傳送給 Microsoft](https://docs.microsoft.com/sql/sql-server/sql-server-customer-feedback?view=sql-server-2016)。

5. 在 [全域規則]  頁面中，如果沒有規則錯誤，安裝程序會自動前進到 [產品更新]  頁面。  
  
6. 如未選取 [控制台]   > [所有控制台項目]   > [Windows Update]   > [變更設定]  中的 [Microsoft Update]  核取方塊，接著即會出現 [Microsoft Update]  頁面。 選取 [Microsoft Update]  核取方塊變更電腦設定，以在掃描 Windows Updates 時包含所有 Microsoft 產品的最新更新。  

7. 最新可用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 產品更新隨即會顯示在 [產品更新]  頁面上。 如未發現任何產品更新，安裝程式不會顯示此頁面，且自動前往 [安裝安裝程式檔案]  頁面。  

8. 安裝程式會在 [安裝安裝程式檔案]  頁面上，顯示下載、擷取及安裝安裝程式檔案的進度。 如果找到安裝程式的更新，而且您指定要包含它，即會一併安裝該更新。 如果找不到任何更新，則安裝程式會自動繼續。
  
9. 在 [安裝規則]  頁面上，安裝程式會檢查執行安裝程式時可能發生的潛在問題。 如果發生故障，請選取 [狀態]  資料行中的項目以取得詳細資訊。 否則，請選取 [下一步]  。

10. 如果這是您第一次在電腦上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，安裝程式會略過 [安裝類型]  頁面，直接前往 [特徵選取]  頁面。 如果系統上已經安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，您可以使用 [安裝類型]  頁面，選取執行新安裝，或將功能新增至現有的安裝。 若要繼續，請選取 [下一步]  。
  
11. 在 [特徵選取]  頁面上，選取要安裝的元件。 例如，若要安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的新執行個體，請選取 [資料庫引擎服務]  。

    當您選取功能名稱之後，每一個元件群組的描述就會出現在 [功能描述]  窗格中。 您可以選取核取方塊的任何組合。 如需詳細資訊，請參閱 [SQL Server 2016 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2016.md)或 [SQL Server 2017 的版本和元件](../../sql-server/editions-and-components-of-sql-server-2017.md)。
  
     [選取之功能的必要元件]  窗格會顯示選取功能的必要元件。 安裝程式會在本程序稍後說明的安裝步驟期間，安裝尚未安裝的必要條件。  
  
     您也可以使用 [特徵選取]  頁面底部的欄位來指定共用元件的自訂目錄。 若要變更共用元件的安裝路徑，請在對話方塊底部的欄位中更新路徑，或選取 [瀏覽]  移至安裝目錄。 預設安裝路徑是 [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]。  
  
     > [!NOTE]
     > 共用元件的指定路徑必須是絕對路徑。 資料夾不可以為壓縮或加密資料夾。 不支援使用對應磁碟機。  
  
     SQL Server 使用兩個共用功能目錄：
  
     * 共用功能目錄  
     * 共用功能目錄 (x86)  
  
     > [!NOTE]
     > 針對上述每個選項所指定的路徑必須是不同的。  
  
12. 如果所有規則都通過，[功能規則]  頁面會自動前進。  
  
13. 在 [執行個體設定]  頁面上，請指定要安裝預設執行個體還是具名執行個體。 如需詳細資訊，請參閱[執行個體設定](../../sql-server/install/instance-configuration.md#instance-configuration-page)。  
  
     * **執行個體識別碼**：根據預設，此執行個體名稱會作為執行個體識別碼使用。 此識別碼是用來識別 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的安裝目錄和登錄機碼。 預設執行個體和具名執行個體有相同的行為。 若是預設執行個體，則執行個體名稱和執行個體識別碼是 MSSQLSERVER。 若要使用非預設的執行個體識別碼，請在 [執行個體識別碼]  文字方塊中指定其他值。  
  
       > [!NOTE]  
       > 一般的 [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)] 獨立執行個體，無論是預設還是具名執行個體，執行個體識別碼都不會使用非預設值。  
  
       所有的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Service Pack 和升級項目都會套用至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的每一個元件。  
  
     * **已安裝的執行個體**：方格內會顯示正在執行安裝程式電腦上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。 如果預設執行個體已經安裝在電腦上，您就必須安裝 [!INCLUDE[ssNoVersion](../../includes/ssNoVersion-md.md)]的具名執行個體。  
  
     其餘的安裝工作流程會因您對安裝所指定的功能而不同。 您可能不會看到所有頁面，端視您的選取項目而定。  
  
14. 使用 [伺服器設定 - 服務帳戶]  頁面指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的登入帳戶。 您在此頁面上設定的實際服務會隨您選取安裝的功能而不同。 如需組態設定的詳細資訊，請參閱[安裝精靈說明](../../sql-server/install/instance-configuration.md#serverconfig)。
  
     您可以將相同的登入帳戶指派給所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務，或個別設定每一個服務帳戶。 您也可以指定要自動啟動服務、手動啟動服務或停用服務。 我們建議您個別設定服務帳戶，為每項服務提供最低權限。 請務必授與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務完成工作所需的最低權限。 如需詳細資訊，請參閱[設定 Windows 服務帳戶與權限](../../database-engine/configure-windows/configure-windows-service-accounts-and-permissions.md)。  
  
     若要為此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中所有服務帳戶指定相同的登入帳戶，請在頁面底部的欄位中提供認證。  
  
    > [!IMPORTANT]  
    > [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  

    > [!NOTE]
    > 從 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 開始，選取 [對 SQL Server 資料庫引擎服務授與「執行磁碟區維護工作」權限]  核取方塊，允許 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 服務帳戶使用[資料庫檔案立即初始化](../../relational-databases/databases/database-instant-file-initialization.md)。
  
     使用 [伺服器設定 - 定序]  頁面，為 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 和 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 指定非預設的定序。 如需詳細資訊，請參閱[定序與 Unicode 支援](../../relational-databases/collations/collation-and-unicode-support.md)。  
  
15. 使用 [資料庫引擎設定 - 伺服器設定]  頁面指定下列選項：  
  
    * **安全性模式**：針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體選取 [Windows 驗證]  或 [混合模式驗證]  。 如果您選取 [混合模式驗證]  ，就必須為內建的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統管理員帳戶提供增強式密碼。  
  
       當裝置成功連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後，Windows 驗證和混合模式驗證的安全性機制是相同的。 如需詳細資訊，請參閱 [[資料庫引擎設定 - 伺服器設定] 頁面](../../sql-server/install/instance-configuration.md#serverconfig)。
  
    * **SQL Server 管理員**：針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，您至少必須指定一位系統管理員。 若要新增正在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式的帳戶，請選取 [新增目前的使用者]  。 若要在系統管理員清單中新增或移除帳戶，請選取 [新增]  或 [移除]  ，然後編輯有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體管理員權限的使用者、群組或電腦清單。  
  
     使用 [資料庫引擎設定 - 資料目錄]  頁面來指定非預設的安裝目錄。 若要安裝到預設目錄，請選取 [下一步]  。  
  
    > [!IMPORTANT]  
    > 如果您要指定非預設的安裝目錄，請確定安裝資料夾對此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是唯一的。 此對話方塊上的任何目錄都不應該與其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中的目錄共用。  
  
     如需詳細資訊，請參閱 [[資料庫引擎設定 - 資料目錄] 頁面](../../sql-server/install/instance-configuration.md#datadir)。

     使用 [資料庫引擎設定 - TempDB]  頁面來設定 **tempdb** 的檔案大小、檔案數目、非預設安裝目錄和檔案成長設定。 如需詳細資訊，請參閱 [[資料庫引擎設定 - TempDB] 頁面](../../sql-server/install/instance-configuration.md#tempdb)。  

     ::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions"

     使用 [[!INCLUDE[ssDE](../../includes/ssde-md.md)]設定 - MaxDOP]  索引標籤指定平行處理原則的最大程度。 此設定會決定單一陳述式在執行期間可以使用的處理器數目。 安裝期間會自動計算出建議的值。 如需詳細資訊，請參閱[平行處理原則的最大程度指導方針](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md#Guidelines)。 此選項僅自 SQL Server 2019 起提供。 

     使用 [資料庫引擎設定 - 記憶體]  索引標籤來指定此 SQL Server 執行個體在啟動後將使用的 MIN 和 MAX 記憶體值。 您可以使用預設值、使用計算出的建議值，或在選擇 [建議]  選項之後手動指定您自己的值。 此功能自 SQL Server 2019 起僅於安裝程式中提供。 

     ::: moniker-end

     使用 [資料庫引擎設定 - FILESTREAM]  頁面針對您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體啟用 FILESTREAM。 如需詳細資訊，請參閱 [[資料庫引擎設定 - FILESTREAM] 頁面](../../sql-server/install/instance-configuration.md#database-engine-configuration---filestream-page)。  
  
16. 使用 [Analysis Services 設定 - 帳戶佈建]  頁面指定伺服器模式以及擁有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員權限的使用者或帳戶。 伺服器模式會決定伺服器上使用的記憶體及儲存體子系統。 不同方案類型會在不同的伺服器模式中執行。 如果要在伺服器上執行多維度 Cube 資料庫，請選取預設的伺服器模式選項 [多維度和資料採礦]  。

    針對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]，您至少必須指定一位系統管理員：

    * 若要新增正在執行 SQL Server 安裝程式的帳戶，請選取 [新增目前的使用者]  。

    * 若要在系統管理員清單中新增或移除帳戶，請選取 [新增]  或 [移除]  ，然後編輯有 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 管理員權限的使用者、群組或電腦清單。

    如需伺服器模式及管理員權限的詳細資訊，請參閱 [[Analysis Services 設定 - 帳戶佈建] 頁面](../../sql-server/install/instance-configuration.md#analysis-services-configuration---account-provisioning-page)。

    當您完成清單的編輯之後，請選取 [確定]  。 然後，在組態對話方塊中確認管理員的清單。 清單完成後，請選取 [下一步]  。

    使用 [Analysis Services 設定 - 資料目錄]  頁面來指定非預設的安裝目錄。 若要安裝到預設目錄，請選取 [下一步]  。  

    > [!IMPORTANT]  
    > 安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，若您為 INSTANCEDIR 和 SQLUSERDBDIR 指定相同的目錄路徑，SQL Server Agent 和全文檢索搜尋會因為遺漏權限而無法啟動。  
    >  
    > 如果您要指定非預設的安裝目錄，請確定安裝資料夾對此 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體是唯一的。 此對話方塊上的任何目錄都不應該與其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體中的目錄共用。  

    如需詳細資訊，請參閱 [[Analysis Services 設定 - 資料目錄] 頁面](../../sql-server/install/instance-configuration.md#analysis-services-configuration---data-directories-page)。  

17. 使用 [Distributed Replay Controller 設定]  頁面來指定要授與 Distributed Replay Controller 服務管理權限的使用者。 擁有管理權限的使用者將可不受限制地存取 Distributed Replay Controller 服務。  
  
     * 若要將 Distributed Replay Controller 服務存取權限授與執行 SQL Server 安裝程式的使用者，請選取 [新增目前的使用者]  按鈕。

     * 若要將 Distributed Replay Controller 服務存取權限授與其他使用者，請選取 [新增]  按鈕。

     * 若要移除 Distributed Replay Controller 服務的存取權限，請選取 [移除]  按鈕。

     * 若要繼續，請選取 [下一步]  。  
  
18. 使用 [Distributed Replay Client 設定]  頁面來指定要授與 Distributed Replay Client 服務管理權限的使用者。 擁有管理權限的使用者將可不受限制地存取 Distributed Replay Client 服務。  
  
     * **控制器名稱**是選擇性的。 預設值為 \<*空白*>。 針對 Distributed Replay Client 服務，輸入用戶端電腦要與其通訊的控制器名稱：  
  
       * 如已設定控制器，請在設定每個用戶端時輸入該控制器的名稱。  
  
       * 如果尚未設定控制器，可將控制器名稱留白。 不過，您必須在 [用戶端組態]  檔中，手動輸入控制器名稱。  
  
     * 指定 Distributed Replay Client 服務的 **工作目錄** 。 預設工作目錄為 \<磁碟機代號  >:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\WorkingDir\\。  
  
     * 指定 Distributed Replay Client 服務的 **結果目錄** 。 預設工作目錄為 \<磁碟機代號  >:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\DReplayClient\ResultDir\\。  
  
     * 若要繼續，請選取 [下一步]  。  
  
19. [準備安裝]  頁面會顯示您在安裝期間指定的安裝選項樹狀檢視。 在此頁面上，安裝程式會指出**產品更新**功能為啟用或停用，以及最後的更新版本。  
  
     選取 [安裝]  繼續作業。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會先安裝選取功能所需的必要條件，再安裝所選功能。  
  
20. 在安裝期間，[安裝進度]  頁面會更新狀態，讓您可以在安裝程式進行時監視安裝進度。  
  
21. 安裝之後， **[完成]** 頁面會提供安裝和其他重要注意事項之摘要記錄檔的連結。
  
    > [!IMPORTANT]
    > 完成安裝後，請務必閱讀安裝精靈提供的訊息。 如需詳細資訊，請參閱[檢視與讀取 SQL Server 安裝程式記錄檔](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)。

    若要完成 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序，請選取 [關閉]  。  
  
22. 如果指示您重新啟動電腦，請立刻執行。

## <a name="next-steps"></a>後續步驟

[設定新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝](https://docs.microsoft.com/sql/database-engine/configure-windows/database-engine-instances-sql-server?view=sql-server-2017)。  
  
為了減少系統的可攻擊介面區， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可以選擇性地安裝和啟用主要服務和功能。 如需詳細資訊，請參閱[介面區設定](../../relational-databases/security/surface-area-configuration.md)。  
  
## <a name="see-also"></a>另請參閱
  
* [驗證 SQL Server 安裝](../../database-engine/install-windows/validate-a-sql-server-installation.md)  
* [修復失敗的 SQL Server 安裝](../../database-engine/install-windows/repair-a-failed-sql-server-installation.md)
* [檢視與讀取 SQL Server 安裝程式記錄檔](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)
* [使用安裝精靈升級至 SQL Server &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)
* [從命令提示字元安裝 SQL Server](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md) 
