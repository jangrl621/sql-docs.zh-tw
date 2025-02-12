---
title: sys.databases (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 05/30/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_stats_TSQL
- dm_exec_query_stats
- sys.dm_exec_query_stats
- sys.dm_exec_query_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_stats dynamic management view
ms.assetid: eb7b58b8-3508-4114-97c2-d877bcb12964
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: e05f71b7b602e702f8c7c5862b31458205ddfab5
ms.sourcegitcommit: c5e2aa3e4c3f7fd51140727277243cd05e249f78
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2019
ms.locfileid: "68742924"
---
# <a name="sysdmexecquerystats-transact-sql"></a>sys.dm_exec_query_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中之快取查詢計劃的彙總效能統計資料。 在此檢視中，快取計畫內的每個查詢陳述式各包含一個資料列，而資料列的存留期取決於計畫本身。 從快取移除計畫時，對應的資料列也會從這個檢視中刪除。  
  
> [!NOTE]
> - 由於資料只會反映完成的查詢, 而不是一次仍在進行中的查詢, 因此, **sys.databases**的變換結果可能會隨每個執行而有所不同。
> - 若要從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼叫此, 請使用名稱 **_pdw_nodes_exec_query_stats**。    

  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**sql_handle**|**varbinary(64)**  |這是一個標記, 可唯一識別查詢所屬的批次或預存程式。<br /><br /> **sql_handle**(搭配**statement_start_offset**和**statement_end_offset**) 可用來藉由呼叫**sys.databases _exec_sql_text**動態管理函數來抓取查詢的 sql 文字。|  
|**statement_start_offset**|**int**|表示資料列於其批次或保存物件的文字中所描述之查詢的起始位置 (由 0 開始並以位元組為單位)。|  
|**statement_end_offset**|**int**|表示資料列於其批次或保存物件的文字中所描述之查詢的結束位置 (由 0 開始並以位元組為單位)。 在之前[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]的版本中,-1 的值表示批次的結尾。 已不再包含尾端批註。|  
|**plan_generation_num**|**bigint**|可用於重新編譯之後區分計畫執行個體的序號。|  
|**plan_handle**|**varbinary(64)**|這是一個標記, 可唯一識別已執行之批次的查詢執行計畫, 且其計畫位於計畫快取中, 或目前正在執行。 此值可以傳遞至[_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)動態管理函數, 以取得查詢計劃。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0x000。|  
|**creation_time**|**datetime**|計畫的編譯時間。|  
|**last_execution_time**|**datetime**|上次開始執行計畫的時間。|  
|**execution_count**|**bigint**|計畫從上次編譯以來被執行的次數。|  
|**total_worker_time**|**bigint**|這個計畫從編譯以來執行所耗用的 CPU 時間總量 (以毫秒為單位來報告，但是精確度只到毫秒)。<br /><br /> 如果原生編譯預存程序執行數次的時間都少於 1 毫秒， **total_worker_time** 可能就不準確。|  
|**last_worker_time**|**bigint**|計畫上次執行所耗用的 CPU 時間 (以毫秒為單位來報告，但是精確度只到毫秒)。 <sup>1</sup>|  
|**min_worker_time**|**bigint**|這個計畫在單次執行期間曾經耗用的最少 CPU 時間 (以毫秒為單位來報告，但是精確度只到毫秒)。 <sup>1</sup>|  
|**max_worker_time**|**bigint**|這個計畫在單次執行期間曾經耗用的最多 CPU 時間 (以毫秒為單位來報告，但是精確度只到毫秒)。 <sup>1</sup>|  
|**total_physical_reads**|**bigint**|這個計畫在編譯以來執行所執行的實體讀取總數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**last_physical_reads**|**bigint**|計畫上次執行所執行的實體讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**min_physical_reads**|**bigint**|這個計畫在單次期間曾執行的最小實體讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**max_physical_reads**|**bigint**|這個計畫在單次執行期間曾執行的最大實體讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**total_logical_writes**|**bigint**|這個計畫在編譯以來執行所執行的邏輯寫入總數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**last_logical_writes**|**bigint**|最近一次完成計畫執行期間變動的緩衝集區頁面數。<br /><br />讀取頁面之後, 頁面只有在第一次修改時才會變成中途。 當頁面變得中途時, 這個數位就會遞增。 後續修改已中途分頁並不會影響此數位。<br /><br />查詢記憶體優化資料表時, 這個數位一律為0。|  
|**min_logical_writes**|**bigint**|這個計畫在單次執行期間曾執行的最小邏輯寫入數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**max_logical_writes**|**bigint**|這個計畫在單次執行期間曾執行的最大邏輯寫入數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**total_logical_reads**|**bigint**|這個計畫在編譯以來執行所執行的邏輯讀取總數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**last_logical_reads**|**bigint**|計畫上次執行所執行的邏輯讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**min_logical_reads**|**bigint**|這個計畫在單次執行期間曾執行的最小邏輯讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**max_logical_reads**|**bigint**|這個計畫在單次執行期間曾經執行的最大邏輯讀取數。<br /><br /> 查詢記憶體最佳化的資料表時一律為 0。|  
|**total_clr_time**|**bigint**|在[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR) 物件中的時間 (以毫秒為[!INCLUDE[msCoName](../../includes/msconame-md.md)]單位來報告, 但是精確度只到毫秒), 這是在編譯後執行此計畫的方式。 CLR 物件可以是預存程序、函數、觸發程序、類型和彙總。|  
|**last_clr_time**|**bigint**|這個計畫上一次執行期間，在 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 物件內部執行所耗用的時間 (以毫秒為單位來報告，但是精確度只到毫秒)。 CLR 物件可以是預存程序、函數、觸發程序、類型和彙總。|  
|**min_clr_time**|**bigint**|這個計畫在單次執行期間於 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 物件內部曾經耗用的最少時間 (以毫秒為單位來報告，但是精確度只到毫秒)。 CLR 物件可以是預存程序、函數、觸發程序、類型和彙總。|  
|**max_clr_time**|**bigint**|這個計畫在單次執行期間於 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR 物件內部曾經耗用的最多時間 (以毫秒為單位來報告，但是精確度只到毫秒)。 CLR 物件可以是預存程序、函數、觸發程序、類型和彙總。|  
|**total_elapsed_time**|**bigint**|這個計畫完成執行經歷的總時間 (以毫秒為單位來報告，但是精確度只到毫秒)。|  
|**last_elapsed_time**|**bigint**|這個計畫最近完成所經歷的時間 (以毫秒為單位來報告，但是精確度只到毫秒)。|  
|**min_elapsed_time**|**bigint**|這個計畫的任何一次完成執行所經歷的最少時間 (以毫秒為單位來報告，但是精確度只到毫秒)。|  
|**max_elapsed_time**|**bigint**|這個計畫的任何一次完成執行所經歷的最多時間 (以毫秒為單位來報告，但是精確度只到毫秒)。|  
|**query_hash**|**Binary(8)**|針對查詢所計算的二進位雜湊值，可用來識別含有類似邏輯的查詢。 您可以使用查詢雜湊判別只有常值不同之查詢的彙總資源使用狀況。|  
|**query_plan_hash**|**binary(8)**|從查詢執行計畫計算所得的二進位雜湊值將用於識別類似的查詢執行計畫。 您可以使用查詢計劃雜湊尋找具有類似執行計畫之查詢的累計成本。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0x000。|  
|**total_rows**|**bigint**|查詢傳回的資料列總數。 不可為 null。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0。|  
|**last_rows**|**bigint**|上次執行查詢時所傳回的資料列數目。 不可為 null。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0。|  
|**min_rows**|**bigint**|在一次執行期間, 查詢所傳回的最小資料列數目。 不可為 null。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0。|  
|**max_rows**|**bigint**|在一次執行期間, 查詢所傳回的最大資料列數目。 不可為 null。<br /><br /> 當原生編譯的預存程序查詢記憶體最佳化的資料表時，一律為 0。|  
|**statement_sql_handle**|**varbinary(64)**|**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 只有在開啟查詢存放區, 並收集該特定查詢的統計資料時, 才會填入非 Null 值。|  
|**statement_context_id**|**bigint**|**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 只有在開啟查詢存放區, 並收集該特定查詢的統計資料時, 才會填入非 Null 值。|  
|**total_dop**|**bigint**|此計畫自編譯以來所使用的平行處理原則程度總計總和。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**last_dop**|**bigint**|此計畫上一次執行時的平行處理原則程度。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**min_dop**|**bigint**|這個計畫在一次執行期間所使用的平行處理原則最小程度。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**max_dop**|**bigint**|這個計畫在一次執行期間使用的平行處理原則最大程度。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**total_grant_kb**|**bigint**|此計畫自編譯後所收到的保留記憶體授與總數 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**last_grant_kb**|**bigint**|當此計畫上次執行時, 保留的記憶體授與的數量 (KB)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**min_grant_kb**|**bigint**|在一次執行期間, 此計畫收到的保留記憶體授與的最小數量 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**max_grant_kb**|**bigint**|在一次執行期間, 此計畫收到的保留記憶體授與的最大數量 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**total_used_grant_kb**|**bigint**|此計畫自編譯後所用的保留記憶體的總數量 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**last_used_grant_kb**|**bigint**|當此計畫上次執行時, 已使用的記憶體授與的數量 (KB)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**min_used_grant_kb**|**bigint**|這個計畫在一次執行期間所使用的最小記憶體授與量 (KB)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**max_used_grant_kb**|**bigint**|這個計畫在一次執行期間所使用的記憶體授與數量上限 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**total_ideal_grant_kb**|**bigint**|此計畫在編譯以來估計的理想記憶體授與的總數量 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**last_ideal_grant_kb**|**bigint**|當此計畫上次執行時, 理想的記憶體授與量 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**min_ideal_grant_kb**|**bigint**|這項計畫在一次執行期間預估的最小記憶體授與量 (以 KB 為單位)。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**max_ideal_grant_kb**|**bigint**|理想記憶體授與的最大數量 (以 KB 為單位), 在一次執行期間估計此計畫。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**total_reserved_threads**|**bigint**|此計畫自編譯以來曾使用的保留平行線程總總和。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**last_reserved_threads**|**bigint**|此計畫上次執行時的保留平行線程數目。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**min_reserved_threads**|**bigint**|這個計畫在一次執行期間所使用的保留平行線程數目下限。  查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**max_reserved_threads**|**bigint**|這個計畫在一次執行期間使用的保留平行線程數目上限。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**total_used_threads**|**bigint**|這個計畫自編譯以來曾使用過的已使用平行線程總總和。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**last_used_threads**|**bigint**|此計畫上次執行時所使用的平行線程數目。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**min_used_threads**|**bigint**|這個計畫在一次執行期間使用的最小平行線程數目。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**max_used_threads**|**bigint**|這個計畫在一次執行期間使用的最大平行線程數目。 查詢記憶體優化資料表時, 一律為0。<br /><br /> **適用於**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。|  
|**total_columnstore_segment_reads**|**bigint**|查詢讀取的資料行存放區區段總計總和。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**last_columnstore_segment_reads**|**bigint**|上次執行查詢時所讀取的資料行存放區區段數目。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**min_columnstore_segment_reads**|**bigint**|查詢在一次執行期間所讀取的資料行存放區區段最小數目。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**max_columnstore_segment_reads**|**bigint**|查詢在一次執行期間所讀取的資料行存放區區段數目上限。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**total_columnstore_segment_skips**|**bigint**|查詢略過的資料行存放區區段總計總和。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**last_columnstore_segment_skips**|**bigint**|上次執行查詢時略過的資料行存放區區段數目。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**min_columnstore_segment_skips**|**bigint**|查詢在一次執行期間曾略過的資料行存放區區段數目下限。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|    
|**max_columnstore_segment_skips**|**bigint**|查詢在一次執行期間曾略過的資料行存放區區段數目上限。 不可為 null。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|
|**total_spills**|**bigint**|自編譯以來執行此查詢所溢出的總頁數。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|**last_spills**|**bigint**|上次執行查詢時所溢出的頁面數目。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|**min_spills**|**bigint**|在單次執行期間, 此查詢已溢出的最小頁面數目。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|**max_spills**|**bigint**|在單次執行期間, 此查詢已溢出的最大頁面數目。<br /><br /> **適用於**：從 SP2 和[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3開始 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|  
|**pdw_node_id**|**int**|此散發所在節點的識別碼。<br /><br /> **適用**于: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]| 
|**total_page_server_reads**|**bigint**|這個計畫在編譯以來執行所執行的遠端頁面伺服器讀取總數。<br /><br /> **適用於：** Azure SQL DB 超大規模資料庫 |  
|**last_page_server_reads**|**bigint**|上次執行計畫時所執行的遠端頁面伺服器讀取數目。<br /><br /> **適用物件:** Azure SQL DB 超大規模資料庫 |  
|**min_page_server_reads**|**bigint**|這個計畫在單次執行期間曾執行的最小遠端頁面伺服器讀取數。<br /><br /> **適用物件:** Azure SQL DB 超大規模資料庫 |  
|**max_page_server_reads**|**bigint**|這個計畫在單次執行期間曾執行的最大遠端頁面伺服器讀取數。<br /><br /> **適用物件:** Azure SQL DB 超大規模資料庫 |  
> [!NOTE]
> <sup>1</sup>在啟用統計資料收集時, 原生編譯預存程式會收集工作者時間 (以毫秒為單位)。 如果查詢在不到一毫秒的時間內執行, 此值會是0。  
  
## <a name="permissions"></a>Permissions  

在[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]上, `VIEW SERVER STATE`需要許可權。   
在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]高階層級上, `VIEW DATABASE STATE`需要資料庫的許可權。 在[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] [標準] 和 [基本] 層上, 需要**伺服器管理員**或**Azure Active Directory 系統管理員**帳戶。   
   
## <a name="remarks"></a>備註  
 完成查詢時，會更新檢視中的統計資料。  
  
## <a name="examples"></a>範例  
  
### <a name="a-finding-the-top-n-queries"></a>A. 尋找 TOP N 查詢  
 下列範例會傳回平均 CPU 時間之前五項查詢的相關資訊。 這個範例會根據查詢雜湊彙總查詢，以便依據累計資源耗用量分組邏輯對等查詢。  
  
```sql  
SELECT TOP 5 query_stats.query_hash AS "Query Hash",   
    SUM(query_stats.total_worker_time) / SUM(query_stats.execution_count) AS "Avg CPU Time",  
    MIN(query_stats.statement_text) AS "Statement Text"  
FROM   
    (SELECT QS.*,   
    SUBSTRING(ST.text, (QS.statement_start_offset/2) + 1,  
    ((CASE statement_end_offset   
        WHEN -1 THEN DATALENGTH(ST.text)  
        ELSE QS.statement_end_offset END   
            - QS.statement_start_offset)/2) + 1) AS statement_text  
     FROM sys.dm_exec_query_stats AS QS  
     CROSS APPLY sys.dm_exec_sql_text(QS.sql_handle) as ST) as query_stats  
GROUP BY query_stats.query_hash  
ORDER BY 2 DESC;  
```  
  
### <a name="b-returning-row-count-aggregates-for-a-query"></a>B. 傳回查詢的資料列計數彙總  
 下列範例會傳回查詢的資料列計數彙總資訊 (資料列總數、最小資料列數目、最大資料列數目及上次傳回的資料列數目)。  
  
```sql  
SELECT qs.execution_count,  
    SUBSTRING(qt.text,qs.statement_start_offset/2 +1,   
                 (CASE WHEN qs.statement_end_offset = -1   
                       THEN LEN(CONVERT(nvarchar(max), qt.text)) * 2   
                       ELSE qs.statement_end_offset end -  
                            qs.statement_start_offset  
                 )/2  
             ) AS query_text,   
     qt.dbid, dbname= DB_NAME (qt.dbid), qt.objectid,   
     qs.total_rows, qs.last_rows, qs.min_rows, qs.max_rows  
FROM sys.dm_exec_query_stats AS qs   
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS qt   
WHERE qt.text like '%SELECT%'   
ORDER BY qs.execution_count DESC;  
```  
  
## <a name="see-also"></a>另請參閱  
[執行相關的動態管理檢視和&#40;函數 transact-sql&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)    
[sys.dm_exec_sql_text &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)    
[sys.dm_exec_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)    
[sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)     
[sys.databases _exec_trigger_stats &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)     
[sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)    
  


