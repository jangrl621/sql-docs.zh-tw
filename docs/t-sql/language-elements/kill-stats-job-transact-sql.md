---
title: KILL STATS JOB (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/27/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- KILL STATS JOB
- KILL_STATS_JOB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ending statistics update jobs [SQL Server]
- stopping statistics update jobs
- terminating statistics update jobs
- asynchronous statistics updates [SQL Server]
- KILL STATS JOB statement
- statistics update jobs [SQL Server]
ms.assetid: 55a8f9f1-3259-45c0-8ab9-60b9c088b4b4
author: rothja
ms.author: jroth
ms.openlocfilehash: b0dd587240a56dcdfab4d618255ee838491054af
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122293"
---
# <a name="kill-stats-job-transact-sql"></a>KILL STATS JOB (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  終止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中非同步的統計資料更新作業。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
KILL STATS JOB job_id   
```  
  
## <a name="arguments"></a>引數  
 *job_id*  
 這是由作業的 sys.dm_exec_background_job_queue 動態管理檢視傳回的 job_id 欄位。  
  
## <a name="remarks"></a>Remarks  
 job_id 與 session_id 或其他格式的 KILL 陳述式所用的工作單位沒有關聯。  
  
## <a name="permissions"></a>權限  
 使用者必須具備 VIEW SERVER STATE 權限，才能存取來自 sys.dm_exec_background_job_queue 動態管理檢視的資訊。  
  
 KILL STATS JOB 權限預設會授與系統管理員 (sysadmin) 和處理序管理員 (processadmin) 固定資料庫角色的成員，無法轉輸。  
  
## <a name="examples"></a>範例  
 下列範例示範如何結束與作業相關聯的統計資料更新，其中 *job_id* = `53`。  
  
```  
KILL STATS JOB 53;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [KILL &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-transact-sql.md)   
 [KILL QUERY NOTIFICATION SUBSCRIPTION &#40;Transact-SQL&#41;](../../t-sql/language-elements/kill-query-notification-subscription-transact-sql.md)   
 [sys.dm_exec_background_job_queue &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-background-job-queue-transact-sql.md)   
 [統計資料](../../relational-databases/statistics/statistics.md)  
  
  
