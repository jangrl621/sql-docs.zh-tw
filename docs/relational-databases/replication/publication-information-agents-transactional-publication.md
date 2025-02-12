---
title: 發行集資訊，代理程式 (交易式發行集) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.publicationinfo.downlevelagents.tran.f1
ms.assetid: 38ef2f54-53bb-4053-876d-86f8f06a4519
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 36c0233d5ba6f51f0cc7cd354bd810a08b2d3b72
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770027"
---
# <a name="publication-information-agents-transactional-publication"></a>發行集資訊，代理程式 (交易式發行集)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  **[代理程式]** 索引標籤會顯示所選取發行集之代理程式的摘要資訊。 所有的交易式發行集，都會顯示快照集代理程式與記錄讀取器代理程式的資訊。 已啟用佇列更新訂閱的交易式發行集，才會顯示佇列讀取器代理程式的資訊。  
  
## <a name="options"></a>選項。  
 如需代理程式的詳細資訊及其相關的工作，請以滑鼠右鍵按一下該代理程式的資料列，然後按一下捷徑功能表上的選項。 若要變更方格顯示資料的方式，請以滑鼠右鍵按一下方格，然後按一下下列其中一個選項：  
  
-   **排序**：在 [排序資料行]  對話方塊中排序一個或多個資料行。  
  
-   **選擇要顯示的資料行**：選取要顯示哪些資料行，以及這些資料行在 [選擇資料行]  對話方塊中的顯示順序。  
  
-   **篩選**：根據 [篩選設定]  對話方塊中的資料行值，篩選方格中的資料列。  
  
-   **清除篩選**：清除方格的所有篩選設定。  
  
 篩選設定是每個方格特有的設定。 資料行選取和排序會套用至所有相同類型的方格，例如每個發行者的發行集方格。  
  
 **狀態**  
 與發行集相關聯之每個複寫代理程式的狀態。 下列清單顯示可能的狀態值：  
  
-   錯誤  
  
-   正在重試失敗的命令  
  
-   未執行  
  
-   執行中  
  
-   已完成  
  
 **代理程式**  
 與發行集相關聯之每個複寫代理程式的名稱。 散發代理程式與這個發行集的訂閱相關聯。 如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)。  
  
 **上次啟動時間**  
 代理程式上次啟動的時間。  
  
 **有效期間**  
 代理程式已執行的時間量。 如果代理程式目前正在執行，此時間代表經過時間；如果代理程式是先前有執行過，則此時間代表總共時間。  
  
 **最後一個動作**  
 最近一次代理程式執行期間執行的最後一個動作。  
  
## <a name="see-also"></a>另請參閱  
 [啟動複寫監視器](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [監視複寫](../../relational-databases/replication/monitor/monitoring-replication.md)  
 [使用複寫監視器來檢視資訊及執行工作](../../relational-databases/replication/monitor/view-information-and-perform-tasks-replication-monitor.md)。  
  
  
