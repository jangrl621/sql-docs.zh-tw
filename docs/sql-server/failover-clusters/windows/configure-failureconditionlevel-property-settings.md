---
title: 設定 FailureConditionLevel 屬性設定 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 513dd179-9a46-46da-9fdd-7632cf6d0816
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6cbffb92f81ec8eb4485be6672de5ed037546997
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68063735"
---
# <a name="configure-failureconditionlevel-property-settings"></a>設定 FailureConditionLeve 屬性設定
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用 FailureConditionLevel 屬性，即可將 AlwaysOn 容錯移轉叢集執行個體 (FCI) 的條件設定為容錯移轉或重新啟動。 對這個屬性的變更會立即套用，而不需要重新啟動 Windows Server 容錯移轉叢集 (WSFC) 服務或 FCI 資源。  
  
-   **開始之前：** [FailureConditionLevel 屬性設定](#Restrictions)[安全性](#Security)  
  
-   **To configure the FailureConditionLevel property settings using,** [PowerShell](#PowerShellProcedure), [Failover Cluster Manager](#WSFC), [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> FailureConditionLevel 屬性設定  
 失敗狀況會設定為遞增等級。 對於等級 1-5，每個等級都包含來自上一個等級的所有狀況，並加上自身的狀況。 這表示，每個等級都具有更高的容錯移轉或重新啟動可能性。  如需詳細資訊，請參閱＜ [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md) ＞主題中的＜判斷失敗＞一節。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 需要 ALTER SETTINGS 及 VIEW SERVER STATE 權限。  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
  
##### <a name="to-configure-failureconditionlevel-settings"></a>設定 FailureConditionLevel 設定  
  
1.  透過 **[以系統管理員身分執行]** 來啟動更高權限的 Windows PowerShell。  
  
2.  匯入 **FailoverClusters** 模組來啟用叢集指令程式。  
  
3.  使用 **Get-ClusterResource** Cmdlet 尋找 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源，然後使用 **Set-ClusterParameter** Cmdlet 設定容錯移轉叢集執行個體的 **FailureConditionLevel** 屬性。  
  
> [!TIP]  
>  每次開啟新的 PowerShell 視窗時，都需要匯入 **FailoverClusters** 模組。  
  
### <a name="example-powershell"></a>範例 (PowerShell)  
 下列範例會將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源 "`SQL Server (INST1)`" 上的 FailureConditionLevel 設定變更為在發生嚴重伺服器錯誤時容錯移轉或重新啟動。  
  
```powershell  
Import-Module FailoverClusters  
  
$fci = "SQL Server (INST1)"  
Get-ClusterResource $fci | Set-ClusterParameter FailureConditionLevel 3  
  
```  
  
### <a name="related-content-powershell"></a>相關內容 (PowerShell)  
  
-   [Clustering and High-Availability](https://blogs.msdn.com/b/clustering/archive/2009/05/23/9636665.aspx) (叢集和高可用性 - 容錯移轉叢集和網路負載平衡團隊部落格)  
  
-   [在容錯移轉叢集上開始使用 Windows PowerShell](https://technet.microsoft.com/library/ee619762\(WS.10\).aspx)  
  
-   [叢集資源命令和對等的 Windows PowerShell 指令程式](https://msdn.microsoft.com/library/ee619744.aspx#BKMK_resource)  
  
##  <a name="WSFC"></a> 使用容錯移轉叢集管理員嵌入式管理單元  
 **設定 FailureConditionLeve 屬性設定：**  
  
1.  開啟 [容錯移轉叢集管理員] 嵌入式管理單元。  
  
2.  展開 **[服務及應用程式]** 並選取 FCI。  
  
3.  以滑鼠右鍵按一下 [其他資源]  下方的 [SQL Server 資源]  ，然後從功能表中選取 [屬性]  。 SQL Server 資源的 **[屬性]** 對話方塊隨即開啟。  
  
4.  選取 **[屬性]** 索引標籤，為 **[FaliureConditionLevel]** 屬性輸入所要的值，然後再按一下 **[確定]** 以套用變更。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **設定 FailureConditionLeve 屬性設定：**  
  
 使用 [ALTER SERVER CONFIGURATION](../../../t-sql/statements/alter-server-configuration-transact-sql.md)[!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，可以指定 FailureConditionLevel 屬性值。  
  
###  <a name="TsqlExample"></a> 範例 &#40;Transact-SQL&#41;  
 下列範例會將 FailureConditionLevel 屬性設定為 0，指出任何失敗狀況都不會自動觸發容錯移轉或重新啟動。  
  
```  
ALTER SERVER CONFIGURATION SET FAILOVER CLUSTER PROPERTY FailureConditionLevel = 0;  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_server_diagnostics &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)   
 [Failover Policy for Failover Cluster Instances](../../../sql-server/failover-clusters/windows/failover-policy-for-failover-cluster-instances.md)  
  
  
