---
title: 將記錄傳送轉換成可用性群組的必要條件
description: 描述將記錄傳送轉換成 Always On 可用性群組的必要條件。
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73cd348f9cb1f22eca30c28cee97ce8e81a20b16
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014512"
---
# <a name="prerequisites-to-convert-log-shipping-to-always-on-availability-groups"></a>將記錄傳送轉換成 Always On 可用性群組的必要條件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  本主題描述將記錄傳送主要資料庫與其一或多個次要資料庫轉換成 AlwaysOn 主要資料庫和次要資料庫的必要條件。  
  
> [!NOTE]  
>  您可以將可用性群組中的任何主要或次要資料庫 (可能是可讀取) 設定為記錄傳送主要資料庫。  
  
  
##  <a name="AGPrereqsRealAddress"></a> 可用性群組必要條件  
 若要允許備份作業在可用性群組的主要複本上執行，請使用下列 AlwaysOn 可用性群組備份設定：  
  
|屬性|設定|  
|--------------|-------------|  
|可用性群組的自動備份喜好設定|只在主要複本上|  
|主要複本的備份優先權。|>0|  
  
 **如需詳細資訊：＜＞**  
  
 [檢視可用性群組屬性 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
 [設定可用性複本的備份 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="LogShipPrereqs"></a> 記錄傳送必要條件  
  
-   記錄傳送主要資料庫必須位於主控可用性群組之初始/目前主要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上。  
  
-   為了將指定的記錄傳送次要資料庫轉換成 AlwaysOn 次要資料庫，它必須：  
  
    -   使用與主要資料庫相同的名稱。  
  
    -   位於主控可用性群組之次要複本的伺服器執行個體上。  
  
 備份作業在主要資料庫上執行之後，請停用備份作業；還原作業在指定的次要資料庫上執行之後，請停用還原作業。  
  
 為可用性群組建立所有次要資料庫之後，如果您想要在次要複本上執行備份，則需要重新設定可用性群組的自動備份喜好設定。  
  
 **如需詳細資訊：＜＞**  
  
 [Converting a log shipping configuration to Availability Group](https://blogs.msdn.microsoft.com/sqlalwayson/2012/01/09/converting-a-logshipping-configuration-to-availability-group/) (將記錄傳送設定轉換成可用性群組) (SQL Server 部落格)  
  
##  <a name="RelatedTasks"></a> 相關工作  
 **記錄傳送**  
  
-   [將記錄傳送升級至 SQL Server 2016 &#40;Transact-SQL&#41;](../../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [移除記錄傳送 &#40;SQL Server&#41;](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
 **AlwaysOn 可用性群組**  
  
-   [使用可用性群組精靈 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [建立可用性群組 &#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [建立可用性群組 &#40;SQL Server PowerShell&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [設定可用性複本的備份 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="RelatedContent"></a> 相關內容  
  
-   **部落格：**  
  
     [Converting a logshipping configuration to Availability Group](https://blogs.msdn.microsoft.com/sqlalwayson/2012/01/09/converting-a-logshipping-configuration-to-availability-group/)  
  
     [將記錄傳送主要資料庫和次要資料庫加入至現有的可用性群組](https://blogs.msdn.microsoft.com/sqlalwayson/2012/02/01/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group/)  
  
     [SQL Server Always On 小組部落格：官方 SQL Server Always On 小組部落格](https://blogs.msdn.microsoft.com/sqlalwayson/)  
  
     [CSS SQL Server 工程師部落格](https://blogs.msdn.com/b/psssql/)  
  
-   **白皮書：**  
  
     [Migration Guide:Migrating to Always On Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping](https://msdn.microsoft.com/library/jj635217) (移轉指南：從結合資料庫鏡像與記錄傳送的先前部署移轉至 Always On 可用性群組)  
  
     [Microsoft 的 SQL Server 2012 白皮書](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server 客戶諮詢團隊白皮書](https://techcommunity.microsoft.com/t5/DataCAT/bg-p/DataCAT/)  
  
## <a name="see-also"></a>另請參閱  
 [關於記錄傳送 &#40;SQL Server&#41;](../../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [監視可用性群組 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  
