---
title: XEvent 概觀 - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/28/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: overview
helpviewer_keywords:
- extended events [SQL Server]
- xe
ms.assetid: bf3b98a6-51ed-4f2d-9c26-92f07f1fa947
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: abdb5eae1bb24bcedd2095a607895ffa671b7d53
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68021840"
---
# <a name="extended-events-overview"></a>擴充事件概觀

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充事件具有可高度擴充及可高度設定的基礎結構，可以讓使用者視需要收集許多或部分的資訊來排除或識別效能問題。  

您可以在下列位置找到延伸事件的詳細資訊：[快速入門：SQL Server 中的延伸事件](../../relational-databases/extended-events/quick-start-extended-events-in-sql-server.md)。


## <a name="benefits-of-includessnoversionincludesssnoversion-mdmd-extended-events"></a>[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充事件的優點  
 「擴充事件」是一種使用極少量效能資源的一種輕量型效能監視系統。 擴充事件提供了兩個圖形化使用者介面 ([新增工作階段精靈]  和 [新增工作階段]  )，用以建立、修改、顯示及分析您的工作階段資料。  
  
## <a name="extended-events-concepts"></a>擴充事件概念  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 擴充事件是以現有的概念為建置基礎 (例如事件或事件取用者)、使用 Windows 事件追蹤的概念，並引進新的概念。  
  
 下表描述擴充事件的概念。  
  
|主題|Description|  
|-----------|-----------------|  
|[SQL Server 擴充的事件套件](../../relational-databases/extended-events/sql-server-extended-events-packages.md)|描述擴充事件封裝，其中包含執行擴充事件工作階段時，用來取得及處理資料的物件。|  
|[SQL Server 擴充的事件目標](https://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)|描述事件工作階段期間可以接收資料的事件取用者。|  
|[SQL Server 擴充的事件引擎](../../relational-databases/extended-events/sql-server-extended-events-engine.md)|描述可實作和管理擴充事件工作階段的引擎。|  
|[SQL Server 擴充的事件工作階段](../../relational-databases/extended-events/sql-server-extended-events-sessions.md)|描述擴充事件工作階段。|  
  
## <a name="extended-events-architecture"></a>擴充事件架構  
 「擴充事件」是一種適用於伺服器系統的一般事件處理系統。 擴充的事件基礎結構可支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中資料的相互關聯，而在某些條件下，則可支援作業系統和資料庫應用程式中資料的相互關聯。 在後者的情況下，「擴充事件」輸出必須導向 Windows 事件追蹤 (ETW)，才能讓此事件資料與作業系統或應用程式事件資料相互關聯。  
  
 所有應用程式都有執行點，這些執行點在應用程式內部和外部都很實用。 在應用程式內，可以使用工作最初執行期間所收集的資訊將非同步處理加入佇列。 在應用程式外，執行點會將有關受監視之應用程式的行為和效能特性資訊提供給監視公用程式。  
  
 擴充的事件可支援在處理序外使用事件資料。 這些資料通常是由以下項目所使用：  
  
-   追蹤工具，例如 SQL 追蹤和系統監視器。  
  
-   記錄工具，例如 Windows 事件記錄檔或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔。  
  
-   管理產品或是開發產品上之應用程式的使用者。  
  
 「擴充事件」具有下列重要的設計層面：  
  
-   「擴充事件」引擎無法得知事件。 如此可讓此引擎將任何事件繫結至任何目標，因為此引擎不受到事件內容的限制。 如需有關擴充的事件引擎的詳細資訊，請參閱＜ [SQL Server Extended Events Engine](../../relational-databases/extended-events/sql-server-extended-events-engine.md)＞。  
  
-   事件會與事件取用者區隔，後者在擴充的事件中稱為 *「目標」* 。 這表示，任何目標都可以接收任何事件。 此外，目標可以自動耗用任何引發的事件，這樣可以記錄或提供其他事件內容。 如需詳細資訊，請參閱＜ [SQL Server Extended Events Targets](https://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)＞。  
  
-   事件與事件發生時所要採取的動作不同。 因此，任何動作都可以與任何事件產生關聯。  
  
-   述詞可以動態篩選何時應該擷取事件資料。 這樣會增加「擴充事件」基礎結構的彈性。 如需詳細資訊，請參閱＜ [SQL Server Extended Events Packages](../../relational-databases/extended-events/sql-server-extended-events-packages.md)＞。  
  
 擴充的事件可以同步產生事件資料 (以及非同步處理該資料)，這樣可為事件處理提供彈性的方案。 此外，擴充的事件還提供下列功能：  
  
-   在伺服器系統上處理事件的統一方式，同時也可讓使用者隔離特定的事件來進行疑難排解。  
  
-   與現有的 ETW 工具整合並支援這些工具。  
  
-   可根據 [!INCLUDE[tsql](../../includes/tsql-md.md)]完整設定的事件處理機制。  
  
-   能夠動態監視使用中處理序，同時對這些處理序有最少的影響。  
  
-   執行的預設系統健康工作階段，而不會有任何顯著的效能影響。 此工作階段會收集系統資料，讓您能夠用來協助排除效能問題。 如需詳細資訊，請參閱 [使用 system_health 工作階段](../../relational-databases/extended-events/use-the-system-health-session.md)。  
  
## <a name="extended-events-tasks"></a>擴充事件工作  

使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料定義語言 (DDL) 陳述式、動態管理檢視和函數或目錄檢視時，您可以針對您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境建立簡單或複雜 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「擴充事件」疑難排解方案。  
  
|工作描述|主題|  
|----------------------|-----------|  
|使用 **[物件總管]** 管理事件工作階段。|[在物件總管中管理事件工作階段](../../relational-databases/extended-events/manage-event-sessions-in-the-object-explorer.md)|  
|描述如何建立擴充事件工作階段。|[建立擴充事件工作階段](https://msdn.microsoft.com/library/34b1e95a-a80e-4aca-9201-abde47f2ca74)|  
|描述如何檢視及重新整理目標資料。| [進階檢視 SQL Server 中擴充事件的目標資料](../../relational-databases/extended-events/advanced-viewing-of-target-data-from-extended-events-in-sql-server.md)|  
|描述如何使用擴充事件工具來建立和管理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 「擴充事件」工作階段。|[擴充事件工具](../../relational-databases/extended-events/extended-events-tools.md)|  
|描述如何改變擴充事件工作階段。|[更改擴充事件工作階段](../../relational-databases/extended-events/alter-an-extended-events-session.md)|  
|描述如何取得與事件有關之欄位的資訊。|[取得所有事件的欄位](https://msdn.microsoft.com/library/4e4ee03f-5bca-42ed-a37c-db1c82e3aad2)|  
|描述如何在註冊的封裝中查明哪些事件可用。|[檢視已註冊之套件的事件](https://msdn.microsoft.com/library/9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f)|  
|描述如何判斷哪些擴充事件目標可在註冊的封裝中使用。|[檢視已註冊之套件的擴充事件目標](https://msdn.microsoft.com/library/4985aa5f-ac99-49f6-852c-9d25916549e9)|  
|描述如何檢視同等於每一個 SQL 追蹤事件及其關聯資料行的「擴充事件」事件和動作。|[檢視同等於 SQL 追蹤事件類別的擴充事件](../../relational-databases/extended-events/view-the-extended-events-equivalents-to-sql-trace-event-classes.md)|  
|描述當您在 CREATE EVENT SESSION 或 ALTER EVENT SESSION 中使用 ADD TARGET 引數時，如何尋找可以設定的參數。|[取得 ADD TARGET 引數的可設定參數](https://msdn.microsoft.com/library/08454543-c5c8-4ca3-9af9-f1d82264471c)|  
|描述如何將現有的 SQL 追蹤指令碼轉換為擴充事件工作階段。|[將現有的 SQL 追蹤指令碼轉換為擴充事件工作階段](../../relational-databases/extended-events/convert-an-existing-sql-trace-script-to-an-extended-events-session.md)|  
|描述如何判斷哪些查詢持有鎖定、查詢的計畫，以及取得鎖定時的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 堆疊。|[判斷哪些查詢持有鎖定](../../relational-databases/extended-events/determine-which-queries-are-holding-locks.md)|  
|描述如何識別阻礙資料庫效能的鎖定來源。|[尋找持有最多鎖定的物件](../../relational-databases/extended-events/find-the-objects-that-have-the-most-locks-taken-on-them.md)|  
|描述如何搭配 Windows 事件追蹤來使用擴充事件，以監視系統活動。|[使用擴充事件監視系統活動](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)|  
| 使用擴充事件的目錄檢視和動態管理檢視 (DMV) | [SQL Server 擴充事件系統檢視表中的 SELECT 和 JOIN](../../relational-databases/extended-events/selects-and-joins-from-system-views-for-extended-events-in-sql-server.md) |

## <a name="code-examples-can-differ-for-azure-sql-database"></a>適用於 Azure SQL Database 的程式碼範例可能有所不同

[!INCLUDE[sql-on-premises-vs-azure-similar-sys-views-include.](../../includes/paragraph-content/sql-on-premises-vs-azure-similar-sys-views-include.md)]

## <a name="see-also"></a>另請參閱  
 [資料層應用程式](../../relational-databases/data-tier-applications/data-tier-applications.md)   
 [SQL Server 物件與版本的 DAC 支援](../../relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions.md)   
 [部署資料層應用程式](../../relational-databases/data-tier-applications/deploy-a-data-tier-application.md)   
 [監視資料層應用程式](../../relational-databases/data-tier-applications/monitor-data-tier-applications.md)   
 [擴充的事件動態管理檢視](../../relational-databases/system-dynamic-management-views/extended-events-dynamic-management-views.md)   
 [擴充的事件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)  
 [XELite：跨平台程式庫，用來讀取 XEL 檔案或即時 SQL 串流中的 XEvent](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite/)，於 2019 年 5 月發行。   
 [Read-SQLXEvent PowerShell Cmdlet](https://www.powershellgallery.com/packages/SqlServer.XEvent)，發行日期 2019 年 6 月。
