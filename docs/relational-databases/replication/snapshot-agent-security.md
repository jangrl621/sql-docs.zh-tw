---
title: 快照集代理程式安全性 | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.security.SSA.f1
helpviewer_keywords:
- Snapshot Agent Security dialog box
ms.assetid: 64e84c67-acc6-4906-98d4-3451767363fe
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: ab40ebb4935616ff8960c3348756e36d45203c03
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769552"
---
# <a name="snapshot-agent-security"></a>快照集代理程式安全性
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  **[快照集代理程式安全性]** 對話方塊可讓您指定：  
  
-   在散發者端執行快照集代理程式的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶。 Windows 帳戶也稱為 *處理帳戶*，因為代理程式處理是在這個帳戶下執行。  
  
-   快照集代理程式用於連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發行者的內容。 可以模擬 Windows 帳戶進行連接，或者在您指定之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶的內容下進行連接。  
  
    > [!NOTE]  
    >  即使發行者和散發者不在同一部電腦上，快照集代理程式也會連接到發行者。 快照集代理程式也會連接到散發者；這些連接一律會藉由模擬執行代理程式的 Windows 帳戶來進行。  
  
     針對 Oracle 發行者，請在 **[發行者屬性]** 對話方塊 (可從 **[散發者屬性]** 對話方塊中取得) 中指定快照集代理程式連接到發行者的內容。 如需詳細資訊，請參閱 [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)。  
  
 所有帳戶都必須有效，並且每個帳戶皆有指定正確的密碼。 等到代理程式執行時，才會驗證帳戶與密碼。  
  
## <a name="options"></a>選項。  
 **Process account**  
 輸入在散發者端執行快照集代理程式的 Windows 帳戶。 您指定的 Windows 帳戶必須：  
  
-   至少是散發資料庫中 **db_owner** 固定資料庫角色的成員。  
  
-   擁有快照集共用上的寫入權限。  
  
 **密碼** 與 **確認密碼**  
 輸入 Windows 帳戶的密碼。  
  
 **連接到發行者**  
 選取快照集代理程式是藉由模擬 **[處理帳戶]** 文字方塊中指定的帳戶、或藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，來連接到發行者。 如果您選取使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶，請輸入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入和密碼。  
  
> [!NOTE]  
>  建議您選取模擬 Windows 帳戶，而不要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶。  
  
 用於連接的 Windows 帳戶或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 帳戶至少必須是發行集資料庫內 **db_owner** 固定資料庫角色的成員。  
  
## <a name="see-also"></a>另請參閱  
 [用於複寫的身分識別和存取控制](../../relational-databases/replication/security/identity-and-access-control-replication.md)   
 [複寫代理程式安全性模型](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [複寫代理程式概觀](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [複寫安全性最佳作法](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
