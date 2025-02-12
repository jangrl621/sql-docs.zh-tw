---
title: 安裝 SQL Server 的硬體與軟體需求 | Microsoft Docs
ms.custom: sqlfreshmay19
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Setup [SQL Server], software
- software [SQL Server]
- installing SQL Server, software
- operating systems [SQL Server], SQL Server requirements
- Setup [SQL Server], cross-language support
- operating systems [SQL Server], cross-language support
- network connections [SQL Server], requirements
- disk space [SQL Server], SQL Server installations
- WOW [SQL Server]
- Setup [SQL Server], hardware
- dependencies [SQL Server], SQL Server installations
- cluster hardware requirements [SQL Server]
- endpoints [SQL Server], SQL Server installations
- Internet [SQL Server], SQL Server installations
- hardware [SQL Server]
- Windows on Windows [SQL Server]
- installing SQL Server, hardware
- Setup Configuration Checker
- SCC [SQL Server]
- operating systems [SQL Server]
- space [SQL Server], SQL Server installations
- system configuration checker
- installing SQL Server, cross-language support
- Internet [SQL Server]
- space [SQL Server]
- extended system support [SQL Server]
- 64-bit edition [SQL Server]
- failover clustering [SQL Server]
- failover clustering [SQL Server], hardware requirements
- 32-bit edition [SQL Server]
- locales [SQL Server], SQL Server installations
- cross-language support
- disk space [SQL Server]
- localized SQL Server versions
ms.assetid: 09bcf20b-0a40-4131-907f-b61479d5e4d8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54f2bdb3d844a8e5aab947f19f7905173b2cb04f
ms.sourcegitcommit: 1f222ef903e6aa0bd1b14d3df031eb04ce775154
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/23/2019
ms.locfileid: "68419566"
---
# <a name="hardware-and-software-requirements-for-installing-sql-server"></a>安裝 SQL Server 2008 R2 的硬體和軟體需求
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

本文章列出在 Windows 作業系統上安裝和執行 [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] 的最低軟硬體需求。 

[!INCLUDE[sscurrent](../../includes/sssqlv14-md.md)] 引進了 Linux 上的 [!INCLUDE[ssNoVer](../../includes/ssnoversion-md.md)] 支援。 如需資訊，請參閱[ Linux 上 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的硬體與軟體需求](../../linux/sql-server-linux-setup.md#system)。 

  
**現在就試試看：**  
  
-   從[**評估中心**](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)下載 SQL Server。 
  
-   啟動已安裝 [**SQL Server 2017**](https://azure.microsoft.com/services/virtual-machines/sql-server/?wt.mc_id=sqL16_vm) 的虛擬機器。  
  
**下列考量適用於所有版本：**  
  
-   建議您在使用 NTFS 或 ReFS 檔案格式的電腦上執行 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 。 雖然支援在使用 FAT32 檔案系統的電腦上安裝 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] ，但並不建議這種做法，因為其安全性低於 NTFS 或 ReFS 檔案系統。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式將會封鎖在唯讀、對應或是壓縮的磁碟機上進行的安裝。  
  
-   如果您透過遠端桌面連線使用 RDC 用戶端本機資源的媒體來啟動安裝程式，則安裝會失敗。 必須在實體或虛擬機器的網路共用或本機從遠端安裝媒體。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝媒體可能位於網路共用、對應磁碟機、本機磁碟機，或顯示為虛擬機器的 ISO。  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 安裝的必要條件是安裝 .NET 4.6.1。 安裝程式會在選取 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 時自動安裝 .NET 4.6.1。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式會安裝該產品所需的下列軟體元件：  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式支援檔案  
  
-   如需在 [!INCLUDE[win8srv](../../includes/win8srv-md.md)] 或 [!INCLUDE[win8](../../includes/win8-md.md)] 上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的最低版本需求，請參閱[在 Windows Server 2012 或 Windows 8 上安裝 SQL Server](https://support.microsoft.com/kb/2681562) \(機器翻譯\)。  
  
##  <a name="hwswr"></a> 硬體及軟體需求  
下列需求適用於所有安裝：  
  
|元件|需求|  
|---------------|-----------------|  
|.NET Framework|[!INCLUDE[sql2016](../../includes/sssql15-md.md)] RC1 和更新版本需要 Database Engine、Master Data Services 或複寫的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6。 SQL Server 安裝程式會自動安裝 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]。 您也可以從 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Microsoft .NET Framework 4.6 (Web Installer) for Windows [(適用於 Windows 的 Microsoft .NET Framework 4.6 (Web 安裝程式)) 手動安裝](https://support.microsoft.com/kb/3045560)。<br/><br/>[!INCLUDE[sql2019](../../includes/sssqlv15-md.md)] 需要 .NET Framework 4.6.2。 可從[下載中心](https://www.microsoft.com/download/details.aspx?id=53344)取得<br/><br/> 如需 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 4.6 的詳細資訊、建議和指引，請參閱 [.NET Framework 開發人員部署手冊](https://msdn.microsoft.com/library/ee942965\(v=vs.110\).aspx)。<br/><br/>[!INCLUDE[winblue_client_2](../../includes/winblue-client-2-md.md)]，而安裝 [!INCLUDE[winblue_server_2](../../includes/winblue-server-2-md.md)] 4.6 之前， [需要](https://support.microsoft.com/kb/2919355) KB2919355 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 。|  
|網路軟體|[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 支援的作業系統有內建的網路軟體。 獨立安裝的具名和預設執行個體均支援下列網路通訊協定：共用記憶體、具名管道、TCP/IP 和 VIA。<br/><br/> **注意：** 容錯移轉叢集不支援 VIA 通訊協定。 和 SQL Server 在相同容錯移轉叢集節點上執行的用戶端或應用程式，可以使用其本機管道位址以共用記憶體通訊協定連線到 SQL Server。 不過，此類型的連線不是叢集感知，且會在執行個體容錯移轉之後中斷。 因此不建議使用此連線，且只應該在非常特定的案例中使用。<br/><br/> **重要：** VIA 通訊協定已被取代。 [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]<br/><br/> 如需有關網路通訊協定和網路程式庫的詳細資訊，請參閱＜ [Network Protocols and Network Libraries](../../sql-server/install/network-protocols-and-network-libraries.md)＞。|  
|硬碟|[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 需要至少 6 GB 的可用硬碟空間。<br/><br/> 磁碟空間需求會因為您安裝的 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 元件而有所不同。 如需詳細資訊，請參閱本文章稍後的[硬碟空間需求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#HardDiskSpace)。 如需支援之資料檔案儲存類型的資訊，請參閱 [資料檔案的儲存類型](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md#StorageTypes)。|  
|光碟機|若要從光碟片安裝，則需要 DVD 光碟機。|  
|監視器|[!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 需要 Super-VGA (800x600) 或更高解析度的監視器。|  
|網際網路|網際網路功能需要網際網路存取 (可能會另行收費)。|  
  
> [!NOTE]
> 由於虛擬化的負擔所致，因此在虛擬機器上執行 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 的速度會比原生方式執行的速度慢。  
  
> [!IMPORTANT]
> PolyBase 功能有其他的硬體和軟體需求。 如需詳細資訊，請參閱 [開始使用 PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)。  
  
##  <a name="pmosr"></a> 處理器、記憶體和作業系統需求  
 下列記憶體和處理器需求適用於所有版本的 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]：  
  
|元件|需求|  
|---------------|-----------------|  
|記憶體 \*|**最小值：**<br/><br/> Express 版本：512 MB<br/><br/> 所有其他版本：1 GB<br/><br/> **建議使用：**<br/><br/> Express 版本：1 GB<br/><br/> 所有其他版本：至少 4 GB，並應隨著資料庫大小增加以確保最佳效能。|  
|處理器速度|**最小值：** x64 處理器：1.4 GHz<br/><br/> **建議使用：** 2.0 GHz 或更快|  
|處理器類型|x64 處理器：AMD Opteron、AMD Athlon 64、具有 Intel EM64T 支援的 Intel Xeon、具有 EM64T 支援的 Intel Pentium IV|  
  
> [!NOTE]  
> 只有 x64 處理器支援安裝 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 。 x86 處理器不再支援其安裝。  
  
 \*在 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 中安裝 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 元件所需的最小記憶體為 2 GB RAM，這與 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 的最小記憶體需求不同。 如需有關安裝 DQS 的詳細資訊，請參閱＜ [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)＞。  
  
 **WOW64 支援：**  
  
 WOW64 (Windows 64 位元上的 Windows 32 位元) 是 Windows 64 位元版本的一項功能，可讓 32 位元應用程式在 32 位元模式中以原生方式執行。 即使基礎作業系統是 64 位元的作業系統，應用程式仍可在 32 位元模式下運作。 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 安裝不支援 WOW64。 不過，WOW64 支援管理工具。  


**Server Core 支援：**

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions" 

下列 Windows Server 版本支援在 Server Core 模式中安裝 SQL Server 2019：

|                              |                                |
| :------------------------    | :------------------------------|
| Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| Windows Server 2016 Standard | Windows Server 2016 Datacenter |
   | &nbsp; | &nbsp; |

::: moniker-end

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"

下列 Windows Server 版本支援在 Server Core 模式中安裝 SQL Server 2016 和 2017：

|                              |                                |
| :------------------------    | :------------------------------|
| Windows Server 2019 Standard | Windows Server 2019 Datacenter |
| Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| Windows Server 2012 R2 Standard | Windows Server 2012 R2  Datacenter|
| Windows Server 2012 Standard | Windows Server 2012 Datacenter |
| Windows Server 2008 R2 SP1 Standard | Windows Server 2008 R2 SP1 Datacenter |
| Windows Server 2008 R2 SP1 Enterprise | Windows Server 2008 R2 SP1 Web|
   | &nbsp; | &nbsp; |
::: moniker-end

如需在 Server Core 上安裝 SQL Server 的詳細資訊，請參閱[在 Server Core 上安裝 SQL Server](../../database-engine/install-windows/install-sql-server-on-server-core.md)。  

  
### <a name="features-supported-on-32-bit-client-operating-systems"></a>32 位元用戶端作業系統支援的功能  
 Windows 用戶端作業系統，例如 Windows 10 和 Windows 8.1 都有 32 位元或 64 位元架構。   64 位元用戶端作業系統支援所有的 SQL Server 功能。 在支援的 32 位元用戶端作業系統上，Microsoft 支援下列功能︰  
  
-   Data Quality Client
-   用戶端工具連接性
-   Integration Services
-   用戶端工具回溯相容性
-   用戶端工具 SDK
-   文件集元件
-   Distributed Replay 元件
-   Distributed Replay Controller
-   Distributed Replay Client
-   SQL 用戶端連接性 SDK
  
 [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] 和更新版本的伺服器作業系統沒有 32 位元架構。 所有支援的伺服器作業系統只有 64 位元。 64 位元伺服器作業系統支援所有的功能。  
  
###  <a name="TOP_Principal"></a> OS 相容性   

::: moniker range=">=sql-server-ver15||=sqlallproducts-allversions" 
下表顯示 SQL Server 2019 哪些版本可與 Windows 的哪些版本相容：  
  

| SQL Server 版本：               | Enterprise | Developer | Standard | Web | Express |  
| :------------------------         | :--------- | :-------- | :------- | :-- | :------ | 
| Windows Server 2019 Datacenter    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2019 Standard      |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2019 Essentials    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2016 Datacenter    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2016 Standard      |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2016 Essentials    |    是     |    是    |    是   | 是 |   是   |
| &nbsp; | &nbsp; |
::: moniker-end

::: moniker range=">=sql-server-2016 <=sql-server-2017||=sqlallproducts-allversions"

下表顯示 SQL Server 2016 哪些版本或 2017 可與 Windows 的哪些版本相容：  
  
| SQL Server 版本：               | Enterprise | Developer | Standard | Web | Express |  
| :------------------------         | :--------- | :-------- | :------- | :-- | :------ | 
| Windows Server 2019 Datacenter    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2019 Standard      |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2019 Essentials    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2016 Datacenter    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2016 Standard      |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2016 Essentials    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 R2 Datacenter |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 R2 Standard   |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 R2 Essentials |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 R2 Foundation |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 Datacenter    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 Standard      |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 Essentials    |    是     |    是    |    是   | 是 |   是   |
| Windows Server 2012 Foundation    |    是     |    是    |    是   | 是 |   是   |
| Windows 10 IoT 企業版         |    否      |    是    |    是   | 否  |   是   |
| Windows 10 Enterprise             |    否      |    是    |    是   | 否  |   是   |
| Windows 10 Professional           |    否      |    是    |    是   | 否  |   是   |
| Windows 10 Home                   |    否      |    是    |    是   | 否  |   是   |
| Windows 8.1 Enterprise            |    否      |    是    |    是   | 否  |   是   |
| Windows 8.1 專業版                   |    否      |    是    |    是   | 否  |   是   |
| Windows 8.1 Enterprise            |    否      |    是    |    是   | 否  |   是   |
| Windows 8 專業版                     |    否      |    是    |    是   | 否  |   是   |
| Windows 8                         |    否      |    是    |    是   | 否  |   是   | 

> [!NOTE]  
> 本節所述的作業系統支援的例外狀況，是下列 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 和更早版本的商業智慧功能，可以安裝在 Windows Server 2008 R2 SP1 或更新版本上︰  
>  
>-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] - SharePoint  
>-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用於 SharePoint 產品的增益集  
::: moniker-end


  
##  <a name="CrossLanguageSupport"></a> 跨語言支援  
 如需跨語言支援及使用當地語系化語言安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之考量的詳細資訊，請參閱 [SQL Server 中的地區語言版本](../../sql-server/install/local-language-versions-in-sql-server.md)。  
  
##  <a name="HardDiskSpace"></a> 硬碟空間需求  
 安裝 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]期間，Windows Installer 會在系統磁碟機上建立暫存檔。 在執行安裝程式來安裝或升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之前，請確認系統磁碟機上至少有 6.0 GB 的可用磁碟空間可供這些檔案使用。 即使您將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件安裝到非預設磁碟機，這項需求也適用。  
  
 實際硬碟空間需求需視系統組態和您決定要安裝的功能而定。 下表提供 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 元件的磁碟空間需求。  
  
|**功能**|**磁碟空間需求**|  
|-----------------|--------------------------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] 和資料檔案、複寫、全文檢索搜尋和 Data Quality Services|1480 MB|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (如上) 與 R Services (資料庫內)|2744 MB|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] (如上) 與外部資料的 PolyBase 查詢服務|4194 MB|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 和資料檔案|698 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|967 MB|  
|[!INCLUDE[rsql_platform](../../includes/rsql-platform-md.md)] (獨立式)|280 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] - SharePoint|1203 MB|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 適用於 SharePoint 產品的增益集|325 MB|  
|[!INCLUDE[ssDQSClient](../../includes/ssdqsclient-md.md)]|121 MB|  
|用戶端工具連接性|328 MB|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|306 MB|  
|用戶端元件 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書元件和 Integration Services 工具除外)|445 MB|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|280 MB|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書元件，可用來檢視並管理說明內容*|27 MB|  
|所有功能|8030 MB|  
  
 *下載線上叢書內容的磁碟空間需求為 200 MB。  
  
##  <a name="StorageTypes"></a> 資料檔案的儲存類型  
 支援的資料檔案儲存類型包括：  
  
-   本機磁碟 
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 目前支援具有標準原生磁區大小 512 位元組及 4 KB 的磁碟機。  磁區大小大於 4 KB 的硬碟可能會在嘗試於其上儲存 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料檔案時產生錯誤。  請參閱 [SQL Server 中的硬碟磁區大小支援界限](https://support.microsoft.com/kb/926930) \(機器翻譯\)，以取得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中硬碟磁區大小支援的詳細資訊。 
    - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集安裝只有在安裝 tempdb 檔時支援本機磁碟。 務必確定在所有叢集節點上為 tempdb 資料和記錄檔指定的路徑都是有效的。 在容錯移轉期間，如果容錯移轉目標節點上的 tempdb 目錄無法使用，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源將無法上線。
-   共用儲存  
-   [儲存空間直接存取 \(S2D\)](https://technet.microsoft.com/windows-server-docs/storage/storage-spaces/storage-spaces-direct-overview)  
-   SMB 檔案共用  
    - 獨立或叢集安裝的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料檔案不支援 SMB 儲存體。 請改用直接連結存放裝置、存放區域網路或 S2D。 
    - SMB 儲存體可由 Windows 檔案伺服器或第三方 SMB 存放裝置所裝載。 如果使用了 Windows File Server，則 Windows File Server 版本應為 2008 或更新版本。 如需有關使用 SMB 檔案共用安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 做為儲存體選項的詳細資訊，請參閱＜ [將 SQL Server 與 SMB Fileshare 當做儲存選項一起安裝](../../database-engine/install-windows/install-sql-server-with-smb-fileshare-as-a-storage-option.md)的最低軟硬體需求。  
  
  
  
##  <a name="DC_support"></a> 在網域控制站上安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
 基於安全性理由，不建議您在網域控制站上安裝 [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] 。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式將不會封鎖當做網域控制站之電腦上的安裝，但適用以下限制：  
  
-   您無法以本機服務帳戶在網域控制站上執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務。    
-   當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝到電腦上以後，您無法將電腦從網域成員變成網域控制站。 在您將主機電腦變更為網域控制站之前，必須先解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。    
-   當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝到電腦上以後，您無法將電腦從網域控制站變成網域成員。 在您將主機電腦變更為網域成員之前，必須先解除安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。   
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。   
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不受唯讀網域控制站的支援。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程式無法在唯讀的網域控制站上建立安全性群組或提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶。 在此狀況中，安裝程式將會失敗。 
- 只能存取唯讀網域控制站的環境不支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體。 
  
## <a name="see-also"></a>另請參閱  
 [規劃 SQL Server 安裝](../../sql-server/install/planning-a-sql-server-installation.md)   
 [SQL Server 安裝的安全性考量](../../sql-server/install/security-considerations-for-a-sql-server-installation.md)   

