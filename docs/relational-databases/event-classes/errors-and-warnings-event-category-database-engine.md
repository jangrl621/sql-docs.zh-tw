---
title: Errors and Warnings 事件類別目錄 (Database Engine) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
- SQL Server event classes, Errors and Warnings event category
- event classes [SQL Server], Errors and Warnings event category
ms.assetid: 249c19b5-af68-4433-80f6-337395176641
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1fd2ee391b2223c7c2db0d086d561594ebec1125
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68089550"
---
# <a name="errors-and-warnings-event-category-database-engine"></a>Errors and Warnings 事件類別目錄 (Database Engine)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **Errors and Warnings** 事件類別目錄包含一般的錯誤與警告事件。  
  
## <a name="in-this-section"></a>本節內容  
  
|主題|Description|  
|-----------|-----------------|  
|[Attention 事件類別](../../relational-databases/event-classes/attention-event-class.md)|指出發生 **Attention** 事件。|  
|[Background Job Error 事件類別](../../relational-databases/event-classes/background-job-error-event-class.md)|指出背景作業已異常結束。|  
|[點陣圖警告事件類別](../../relational-databases/event-classes/bitmap-warning-event-class.md)|指出查詢中已經停用點陣圖篩選。|  
|[Blocked Process Report 事件類別](../../relational-databases/event-classes/blocked-process-report-event-class.md)|指出封鎖工作已超出指定的時間量。|  
|[CPU Threshold Exceeded 事件類別](../../relational-databases/event-classes/cpu-threshold-exceeded-event-class.md)|指出資源管理員偵測到超出指定之 CPU 臨界值的查詢。|  
|[ErrorLog 事件類別](../../relational-databases/event-classes/errorlog-event-class.md)|指出錯誤事件已記錄在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔中。|  
|[EventLog 事件類別](../../relational-databases/event-classes/eventlog-event-class.md)|指出事件已記錄在 Windows 事件記錄檔中。|  
|[Exception 事件類別](../../relational-databases/event-classes/exception-event-class.md)|指出 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發生例外狀況。|  
|[Exchange Spill 事件類別](../../relational-databases/event-classes/exchange-spill-event-class.md)|指出平行查詢計畫中的通訊緩衝區已寫入 tempdb 資料庫。|  
|[Execution Warnings 事件類別](../../relational-databases/event-classes/execution-warnings-event-class.md)|指出在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 陳述式或預存程序期間所發生的記憶體授權警告。|  
|[Hash Warning 事件類別](../../relational-databases/event-classes/hash-warning-event-class.md)|指出雜湊作業期間發生了雜湊遞迴或 Hash Bailout。|  
|[Missing Column Statistics 事件類別](../../relational-databases/event-classes/missing-column-statistics-event-class.md)|指出無法取得最佳化工具可能用到的資料行統計資料。|  
|[遺失聯結述詞事件類別](../../relational-databases/event-classes/missing-join-predicate-event-class.md)|指出正在執行沒有聯結述詞的查詢。|  
|[Sort Warnings 事件類別](../../relational-databases/event-classes/sort-warnings-event-class.md)|指出不適合在記憶體中的排序作業。|  
|[User Error Message 事件類別](../../relational-databases/event-classes/user-error-message-event-class.md)|顯示使用者看到的錯誤訊息。|  
  
## <a name="see-also"></a>另請參閱  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
