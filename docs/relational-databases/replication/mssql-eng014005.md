---
title: MSSQL_ENG014005 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014005 error
ms.assetid: f168f0d6-cb11-45d4-9781-c374d7f388ee
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 2331221ea8a15935b91a7ba8cc6691dd27cec4e3
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770504"
---
# <a name="mssqleng014005"></a>MSSQL_ENG014005
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|14005|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|無法卸除發行集。 有它的訂閱存在。|  
  
## <a name="explanation"></a>說明  
 您已嘗試卸除具有一個或多個關聯訂閱的發行集。 發行集僅在沒有關聯的訂閱時方可卸除。  
  
## <a name="user-action"></a>使用者動作  
 先卸除訂閱，然後再卸除發行集。 如果使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 卸除發行集，您可以選擇在卸除發行集之前自動卸除所有關聯的訂閱。 如果使用預存程序，則必須先明確地卸除訂閱。 如需相關資訊，請參閱 [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md) 及 [Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md)。  
  
 如果發行集不存在訂閱，或者在建立發行集時出現此錯誤，可能有之前的訂閱在移除時未完全清除。 在資料庫上執行 [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)，以移除與複寫相關的所有物件與設定。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤和事件參考 &#40;複寫&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
