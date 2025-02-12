---
title: 快照集資料夾 | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 99e3910e3c97b4dcda725e80ce45d9fd928cdead
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051630"
---
# <a name="snapshot-folder"></a>快照集資料夾
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **[快照集資料夾]** 頁面會出現在設定散發精靈和新增發行集精靈中。 您為快照集資料夾指定的位置會作為此精靈中已啟用之所有發行者的預設值 (稍後使用 **[散發者屬性]** 對話方塊啟用的發行者並不會套用此預設快照集資料夾)。 針對設定散發精靈或 **[散發者屬性]** 對話方塊之 **[發行者]** 頁面上的任何發行者，您可以覆寫此預設值。  
  
 快照集資料夾只是指定為共用的目錄；讀取並寫入此資料夾的代理程式必須具有足夠的權限才能對其進行存取。 如需適當設定資料夾安全性的詳細資訊，請參閱[保護快照集資料夾](../../relational-databases/replication/security/secure-the-snapshot-folder.md)。 在實作複寫之前，請先測試確認複寫代理程式能夠連接到快照集資料夾。 在每個代理程式都會使用到的帳戶之下登入，然後嘗試存取快照集資料夾。  
  
## <a name="options"></a>選項。  
 **Snapshot folder**  
 輸入要在其中儲存快照集檔案之資料夾的路徑。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建議您使用網路共用作為快照集資料夾的位置。 其他電腦上的代理程式無法存取本機路徑 (以磁碟機代號開頭的路徑，例如 C:\\)。  
  
## <a name="see-also"></a>另請參閱  
 [修改快照集選項](../../relational-databases/replication/snapshot-options.md)   
 [[設定散發]](../../relational-databases/replication/configure-distribution.md)   
 [設定發行和散發](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [檢視及修改散發者和發行者屬性](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [使用快照集初始化訂閱](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
