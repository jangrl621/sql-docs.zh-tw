---
title: SQL Server Agent 屬性 (連接頁面) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 115099a4bc177320be367e3c397444322383df2c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265282"
---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server Agent 屬性 (連接頁面)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此頁面檢視及修改 [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之間的連線設定。  
  
## <a name="options"></a>選項。  
**別名本機主機伺服器**  
指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]之本機執行個體的別名。 如果您無法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的預設連接選項，請為執行個體定義別名，並在此處指定該別名。  
  
**使用 Windows 驗證**  
將 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 驗證設定為連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的驗證方法。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 會以 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務執行身分帳戶連線。  
  
**[使用 SQL Server 驗證]**  
設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證為連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的驗證方法。  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供驗證的目的在提供回溯相容性。 為了提升安全性，如果可能的話請使用 Windows 驗證。  
  
**登入**  
指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的登入名稱。  
  
**密碼**  
指定用來連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的密碼。  
  
