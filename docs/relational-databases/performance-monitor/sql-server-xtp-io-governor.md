---
title: SQL Server XTP IO 管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 91e176fe-c838-44e9-b4fc-2814a0551ca3
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: 975dca6fe0151b5bd1fc1d72b9d14e47a57413d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67915217"
---
# <a name="sql-server-xtp-io-governor"></a>SQL Server XTP IO 管理員
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server XTP IO 管理員效能物件包含與記憶體內部 OLTP IO 速率管理員相關的計數器。

本表說明 **SQL Server XTP IO 管理員** 計數器。

|計數器|Description|  
|-------------|-----------------|  
|**Insufficient Credits Waits/sec**|因為速率物件額度不足 (每秒) 所產生的等候次數。|
|**Io Issued/sec**|清除執行緒每秒發出的 Io 數目。|
|**Log Blocks/sec**|控制站每秒處理的記錄區塊數目。|
|**Missed Credit Slots**|因為等候速率物件的信用額度而遺漏的信用插槽數目。|
|**Stale Rate Object Waits/sec**|因為速率物件過時 (每秒) 而產生的等候次數。|
|**Total Rate Objects Published**|發佈的速率物件總數。|
 

## <a name="see-also"></a>另請參閱  
[SQL Server XTP &#40;記憶體內部 OLTP&#41; 效能計數器](../../relational-databases/performance-monitor/sql-server-xtp-in-memory-oltp-performance-counters.md)
