---
title: 服務帳戶 (設定資料庫鏡像安全性精靈) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9c0fb67d173ed0f4ade469c5233a7fdff59dd1a7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68025252"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>服務帳戶 (設定資料庫鏡像安全性精靈)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在使用 Windows 驗證時，如果伺服器執行個體使用不同的帳戶，請指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的服務帳戶。 這些服務帳戶必須全都是網域帳戶 (在同一或受信任的網域中)。  
  
 如果所有伺服器執行個體都使用相同的網域帳戶，或是使用以憑證為基礎的驗證，則請將欄位保留空白。 只要按一下 **[完成]** ，精靈就會根據目前精靈的帳戶自動設定帳戶。  
  
> [!IMPORTANT]  
>  如果伺服器執行個體的資料庫鏡像端點設定為使用憑證，則服務帳戶欄位必須保留空白。  
  
 **若要使用 SQL Server Management Studio 設定資料庫鏡像**  
  
-   [使用 Windows 驗證建立資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish-database-mirroring-session-windows-authentication.md)  
  
-   [啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>選項。  
 **主體**  
 指定主體伺服器執行個體的服務帳戶。 以大寫輸入網域名稱：  
  
 *DOMAINNAME*\\*username*  
  
 **鏡像**  
 指定鏡像伺服器執行個體的服務帳戶。 以大寫輸入網域名稱：  
  
 *DOMAINNAME*\\*username*  
  
 **Witness**  
 指定見證伺服器執行個體的服務帳戶。 以大寫輸入網域名稱：  
  
 *DOMAINNAME*\\*username*  
  
## <a name="see-also"></a>另請參閱  
 [資料庫屬性 &#40;鏡像頁面&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)   
 [設定資料庫鏡像或 AlwaysOn 可用性群組的登入帳戶 &#40;SQL Server&#41;](../../database-engine/database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
