---
title: 代理程式安全性 (新增發行集精靈) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.agentsecurity.articles.f1
ms.assetid: 05ae44df-8e9f-46ea-95f6-972ad109c6c0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: db3e9b71b5e19e4dec55d64f9e0dde75a38947f5
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770782"
---
# <a name="agent-security-new-publication-wizard"></a>代理程式安全性 (新增發行集精靈)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  **[代理程式安全性]** 頁面可讓您指定執行下列代理程式的帳戶，並與複寫拓撲中的電腦建立連接。  
  
-   所有發行集的快照集代理程式。  
  
-   所有交易式發行集的記錄讀取器代理程式。  
  
-   允許可更新訂閱的交易式發行集之佇列讀取器代理程式。 如果您在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job for this agent is created if you specified **Transactional publication with updatable subscriptions** on the **Publication Type** page, regardless of the type of updatable subscriptions you use. 如需有關可更新訂閱的詳細資訊，請參閱[異動複寫的可更新訂閱](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)。  
  
 如需有關代理程式所需權限和複寫安全性的最佳做法的詳細資訊，請參閱＜ [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md) ＞和＜ [Replication Security Best Practices](../../relational-databases/replication/security/replication-security-best-practices.md)＞。  
  
## <a name="options"></a>選項。  
 **快照集代理程式**  
 所有發行集都會顯示。 按一下 **[安全性設定]** ，即可在 **[快照集代理程式安全性]** 對話方塊中指定安全性設定。  
  
 如需有關快照集代理程式所使用帳戶需要之權限的詳細資訊，請在 **[快照集代理程式安全性]** 對話方塊中按一下 **[說明]** 。  
  
 **記錄讀取器代理程式**  
 所有交易式發行集都會顯示。 按一下 **[安全性設定]** ，即可在 **[記錄讀取器代理程式安全性]** 對話方塊中指定安全性設定。  
  
 如需有關記錄讀取器代理程式所使用帳戶需要之權限的詳細資訊，請在 **[記錄讀取器代理程式安全性]** 對話方塊中按一下 **[說明]** 。  
  
> [!NOTE]  
>  每一個使用異動複寫發行的資料庫都有一個記錄讀取器代理程式。 如果交易式發行集已存在資料庫中，則安全性設定是唯讀的。 您可以在 **[發行集屬性]** 對話方塊中變更設定，但變更會影響資料庫中的所有交易式發行集。  
  
 **佇列讀取器代理程式**  
 允許可更新訂閱的交易式發行集都會顯示。 按一下 **[安全性設定]** ，即可在 **[佇列讀取器代理程式安全性]** 對話方塊中指定安全性設定。 此精靈完成時就會建立佇列讀取器代理程式作業；與您是否建立任何佇列更新訂閱無關。 如果您不要建立任何佇列更新訂閱，就可以停用此作業。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 [作業]  資料夾中，以滑鼠右鍵按一下作業 (命名格式：\<發行者>.\<整數>  )，然後按一下 [停用]  。  
  
 如需有關佇列讀取器代理程式所使用的帳戶所需之權限的詳細資訊，請在 **[佇列讀取器代理程式安全性]** 對話方塊上按一下 **[說明]** 。  
  
> [!NOTE]  
>  針對每個散發資料庫 (及其服務的所有發行者) 都有一個佇列讀取器代理程式。 在使用給定散發資料庫的任何發行者上，如果已存在允許佇列更新訂閱的交易式發行集，則安全性設定是唯讀的。 您可以在 **[散發者屬性]** 對話方塊中，變更用於執行佇列讀取器代理程式和建立連接的帳戶，但變更會影響使用散發資料庫之所有發行者的發行集。  
  
## <a name="see-also"></a>另請參閱  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Create an Updatable Subscription to a Transactional Publication](publish/create-an-updatable-subscription-to-a-transactional-publication.md)   
 [檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [檢視及修改發行集屬性](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [用於複寫的身分識別和存取控制](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [發行資料和資料庫物件](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [複寫代理程式概觀](../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
