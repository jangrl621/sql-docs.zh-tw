---
title: MSSQLSERVER_9002 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9002 (Database Engine error)
ms.assetid: 2e50841f-2b99-45f4-aec5-aa4add70cbeb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3397d8fc1fbf271ab3bd8032ae14c7d9b61b6020
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118355"
---
# <a name="mssqlserver9002"></a>MSSQLSERVER_9002
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|9002|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|LOG_IS_FULL|  
|訊息文字|資料庫 '%.*ls' 的交易記錄已滿。 如果要了解為何無法重複使用記錄中的空間，請參閱 sys.databases 中的 log_reuse_wait_desc 資料行。|  
  
## <a name="explanation"></a>說明  
資料庫記錄檔空間不足。 **sys.databases** 中的 **log_reuse_wait_desc** 資料行描述為何無法重複使用記錄檔中的空間。  
  
## <a name="user-action"></a>使用者動作  
使用 **sys.databases** 確定記錄已滿的原因，然後更正該狀況。 如需詳細資訊，請參閱《SQL Server 線上叢書》中的＜寫滿交易記錄疑難排解 (錯誤 9002)＞。  
  
## <a name="see-also"></a>另請參閱  
[為寫滿交易記錄進行疑難排解 &#40;SQL Server 錯誤 9002&#41;](~/relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
[sys.databases &#40;Transact-SQL&#41;](~/relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
