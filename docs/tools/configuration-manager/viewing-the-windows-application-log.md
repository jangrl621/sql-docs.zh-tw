---
title: 檢視 Windows 應用程式記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- application logs [SQL Server]
- Windows application logs [SQL Server]
- viewing Windows application logs
- errors [SQL Server], logs
- system logs [SQL Server]
- security logs [SQL Server]
- displaying Windows application logs
- logs [SQL Server], Windows application logs
ms.assetid: f9853b74-7db7-47cc-b957-e49ed5bc0a1a
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 7c6d652545fcdc44ea46fbc417b1f0de7956cd83
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68106063"
---
# <a name="viewing-the-windows-application-log"></a>檢視 Windows 應用程式記錄
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 設成使用 Microsoft Windows 應用程式記錄檔時，每個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工作階段都會將新事件寫入該記錄檔。 您每次啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體時，並不會建立新的應用程式記錄檔，這和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤記錄檔不同。  
  
 使用「Windows 事件檢視器」或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的記錄檢視器，可以檢視和管理 Windows 應用程式記錄檔。  
  
 使用「事件檢視器」可以檢視三個記錄檔。  
  
|Windows 記錄類型|Description|  
|----------------------|-----------------|  
|系統記錄檔|記錄由 Windows 作業系統元件所記錄的事件。 例如，啟動時無法載入驅動程式或其他系統元件，就會記錄於系統記錄檔內。|  
|安全性記錄檔|記錄安全性事件，例如失敗的登入嘗試。 這有助於追蹤安全性系統的變更，並找出可能破壞安全性的漏洞。 例如，您可設定使用者管理員中的稽核選項，將嘗試登入至系統的事件記錄於安全性記錄檔內。<br /><br /> 只有 **系統管理員 (sysadmin)** 固定伺服器角色的成員可以檢視安全性記錄檔。|  
|應用程式記錄檔|記錄應用程式所記錄的事件。 例如，資料庫應用程式可能會將檔案錯誤記錄於應用程式記錄檔內。|  
  
 如需有關使用「事件檢視器」、管理應用程式記錄檔，以及了解它所呈現的資訊，請參閱 Windows 文件。  
  
 **若要檢視 Windows 應用程式記錄檔**  
  
 [檢視 Windows 應用程式記錄檔 &#40;Windows&#41;](../../relational-databases/performance/view-the-windows-application-log-windows-10.md)  
  
  
