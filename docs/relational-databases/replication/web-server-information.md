---
title: Web 伺服器資訊 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.webserverinformation.f1
ms.assetid: 86d72275-45c7-459f-98cf-f5a366ed279c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a267600824313e55f49a175aee89891d7aad3dc0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68137030"
---
# <a name="web-server-information"></a>Web 伺服器資訊
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用合併式複寫的 Web 同步處理選項時，需要有 Web 伺服器資訊。 如需設定 Web 同步處理的資訊，請參閱[設定 Web 同步處理](../../relational-databases/replication/configure-web-synchronization.md)。  
  
## <a name="options"></a>選項。  
 **Web 伺服器位址**  
 如果您在 [發行集屬性]  對話方塊的 [FTP 快照集和網際網路]  頁面中，指定了 Web 伺服器位址，該位址就會在此文字方塊中顯示為預設值。 接受預設值，或輸入同步處理此訂閱的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services (IIS) 伺服器之完整 Web 伺服器位址。  
  
 **每一個訂閱者如何連接到 Web 伺服器？**  
 指定用於連接到 Web 伺服器的驗證類型。 針對 IIS 伺服器連接，建議使用基本驗證搭配安全通訊端層 (SSL)。 如果您選取基本驗證，請輸入從訂閱者連接到 IIS 伺服器時所使用的登入名稱和密碼。  
  
## <a name="see-also"></a>另請參閱  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [檢視及修改提取訂閱屬性](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [非 SQL Server 訂閱者](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [合併式複寫的 Web 同步處理](../../relational-databases/replication/web-synchronization-for-merge-replication.md)  
  
  
