---
title: 最佳化 SQL 追蹤 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- time [SQL Server], traces
- SQL Trace, performance
- traces [SQL Server], performance
- performance [SQL Server], trace
ms.assetid: 50944218-925f-4576-aec8-4379846d7681
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 59b1a599a38e31abeee677059d5a99842e76d807
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033224"
---
# <a name="optimize-sql-trace"></a>最佳化 SQL 追蹤
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  因為執行 SQL 追蹤會使用系統資源來收集資料，所以會產生效能成本，但是有許多方式可以使成本降至最少。 若要使追蹤導致的效能成本降至最少，請試試下列方法：  
  
-   考慮使用命令提示字元來執行追蹤。 使用圖形化使用者介面會妨礙效能。 如需詳細資訊，請參閱 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)。  
  
-   避免納入經常發生的事件。 如果可能，利用特定事件類別和篩選來縮小追蹤。 若收集的追蹤事件越少，支援追蹤所需的系統資源也會跟著減少。  
  
-   將追蹤集中在只收集可提供相關資料的事件， 例如，如果追蹤是為了要識別死結，則請納入 **Lock:Deadlock** 事件類別，而不要納入 **Lock:Acquired** 事件類別。 如果您同時納入這兩個事件類別，則追蹤必須回應所取得的每一個鎖定，執行成本就會加倍。  
  
-   避免收集重複的資料。 例如，如果您要收集 **SQL:BatchStarted** 和 **SQL:BatchCompleted**，您可以只收集 **SQL:BatchStarted** 事件類別的文字資料，使結果集的大小縮至最小。  
  
-   在追蹤定義中使用篩選。 例如，如果您知道某個使用者回報在隨選查詢期間的效能緩慢，則可建立 **LoginName**的篩選， 將篩選設為只納入 **LoginName** 符合使用者名稱的事件。  
  
 如果您需要執行的事件追蹤會對效能造成重大影響，請考慮使用下列其中一個方法，來限制此追蹤對伺服器效能的影響：  
  
-   使執行追蹤的時間變短。 您可以啟用停止時間，來控制追蹤執行的時間長度。 尤其當您無法限制事件類別或篩選事件時，這麼做特別重要。 啟用停止時間可以確定所造成的效能問題，不會無限期地持續下去。  
  
-   限制追蹤結果的大小。 您可以將追蹤結果的大小限制為檔案大小上限。 此策略可確保在達到檔案大小上限時，效能成本會立即停止 (如果未啟用檔案換用的話)。  
  
-   限制傳回的事件數目。 利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ，您可以將追蹤儲存至資料表並設定最大資料列數，來限制傳回的事件數目。 在達到最大資料列數之後，追蹤結果仍會傳回至 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 畫面，但可省去將結果記錄到資料表的成本。  
  
## <a name="see-also"></a>另請參閱  
 [篩選追蹤](../../relational-databases/sql-trace/filter-a-trace.md)  
  
  
