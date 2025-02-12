---
title: 新增作業排程 - 作業排程屬性 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.scheduleproperties.f1
- sql13.swb.maint.editrecurringjobsched.f1
ms.assetid: 5c0b1bc9-dd87-49cc-b0dd-75d0d922b177
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4e7500e61be6167271388f688428b6c1530e8d58
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263000"
---
# <a name="new-job-schedule---job-schedule-properties"></a>新增作業排程 - 作業排程屬性
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此頁面來檢視和變更排程的屬性。  
  
## <a name="options"></a>選項。  
**名稱**  
輸入排程的新名稱。  
  
**排程中的作業**  
檢視使用排程的作業。  
  
**排程類型**  
選取排程類型。  
  
**已啟用**  
核取以啟用或停用排程。  
  
## <a name="recurring-schedule-types-options"></a>重複執行排程類型選項  
**發生於**  
選取排程重複執行的間隔。  
  
**重複頻率**  
選取排程重複執行間隔的日數或週數。 每月重複執行的排程無法使用這個選項。  
  
**星期一**  
設定作業於星期一發生。 只有每週重複執行的排程可以使用。  
  
**星期二**  
設定作業於星期二發生。 只有每週重複執行的排程可以使用。  
  
**星期三**  
設定作業於星期三發生。 只有每週重複執行的排程可以使用。  
  
**星期四**  
設定作業於星期四發生。 只有每週重複執行的排程可以使用。  
  
**星期五**  
設定作業於星期五發生。 只有每週重複執行的排程可以使用。  
  
**星期六**  
設定作業於星期六發生。 只有每週重複執行的排程可以使用。  
  
**星期日**  
設定作業於星期日發生。 只有每週重複執行的排程可以使用。  
  
**Day**  
請選取排程每月在哪一日發生。 只有每月重複執行的排程可以使用。  
  
**重複間隔**  
請選取排程出現間隔的月數。 只有每月重複執行的排程可以使用。  
  
**星期**  
指定排程，選擇月份中特定週數的特定星期幾。 只有每月重複執行的排程可以使用。  
  
**執行一次於**  
請設定作業每日發生的時間。  
  
**發生間隔**  
設定每隔幾個小時、幾分鐘或幾秒發生一次。  
  
**開始日期**  
請設定這個排程開始有效的日期。  
  
**結束日期**  
請設定排程將不再有效的日期。  
  
**沒有結束日期**  
請指定排程將無限期地保持有效。  
  
## <a name="one-time-schedule-types-options"></a>僅執行一次的排程類型選項  
**日期**  
選取作業要執行的日期。  
  
**Time**  
選取作業要執行的時間。  
  
## <a name="see-also"></a>另請參閱  
[建立及附加排程至作業](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[排程作業](../../ssms/agent/schedule-a-job.md)  
  
