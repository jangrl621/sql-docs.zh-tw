---
title: 設定 SQL Server Agent Mail 使用 Database Mail | Microsoft Docs
ms.custom: ''
ms.date: 08/05/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], SQL Server Agent Mail
- SQL Server Agent Mail
ms.assetid: 4b8b61bd-4bd1-43cd-b6e5-c6ed2e101dce
author: stevestein
ms.author: sstein
ms.openlocfilehash: 81dbaedcb67b7e641e00c37ebb27e35fb2fceca5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134567"
---
# <a name="configure-sql-server-agent-mail-to-use-database-mail"></a>設定 SQL Server Agent Mail 使用 Database Mail
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主題描述如何使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中將 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]Agent 設定為使用 Database Mail 來傳送通知和警示。  如需如何啟用及設定 Database Mail 的相關資訊，請參閱 [設定 Database Mail](../../relational-databases/database-mail/configure-database-mail.md)。  如需使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]的範例，請參閱 [建立 Database Mail 設定檔](../../relational-databases/database-mail/create-a-database-mail-profile.md)。
  
-   **開始之前：**  
  
-   [必要條件](#Prerequisites)  
  
-   [安全性](#Security)  
  
-   [使用 SQL Server Management Studio 將 SQL Server Agent 設定為使用 Database Mail](#SSMSProcedure)  
  
-   [後續工作](#Follow_Up)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Prerequisites"></a> 必要條件  
  
-   [啟用 Database Mail](../../relational-databases/database-mail/configure-database-mail.md)。  
  
-    對[Agent 服務帳戶](../../relational-databases/database-mail/create-a-database-mail-account.md) 建立要使用的 Database Mail 帳戶 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。  
  
-   [建立 Database Mail 設定檔](../../relational-databases/database-mail/create-a-database-mail-profile.md) ，供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務帳戶使用並將使用者新增至 **msdb** 資料庫中的 **DatabaseMailUserRole** 。  
  
-   將設定檔設為 **msdb** 資料庫的預設設定檔。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 建立設定檔帳戶以及執行預存程序的使用者，應該是系統管理員 (sysadmin) 固定伺服器角色的成員。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **設定 SQL Server Agent 使用 Database Mail**  
  
-   在 [物件總管] 中，展開 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。  
  
-   以滑鼠右鍵按一下 [SQL Server Agent]  ，然後按一下 [屬性]  。  
  
-   按一下 **[警示系統]** 。  
  
-   選取 **[啟用郵件設定檔]** 。  
  
-   在 **[郵件系統]** 清單中，選取 **[Database Mail]** 。  
  
-   在 **[郵件設定檔]** 清單中，選取 Database Mail 的郵件設定檔。  
  
-   重新啟動 SQL Server Agent。  
  
##  <a name="Follow_Up"></a> 後續工作  
 需要進行下列工作，才能完成將 Agent 設定為傳送警示和通知的作業。  
  
-   [警示](../../ssms/agent/alerts.md)  
  
     將警示設定為在發生特定資料庫事件或作業系統狀況時通知操作員。  
  
-   [運算子](../../ssms/agent/operators.md)  
  
     操作員是可接收電子通知之人員或群組使用的別名  
  
  
