---
title: 執行 T-SQL 陳述式工作 (維護計畫) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql13.swb.maint.tsql.f1
helpviewer_keywords:
- Execute T-SQL Statement Task dialog box
ms.assetid: fef3e259-0c47-4f6e-ade0-aee95e3d6c1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d27395a66cd9bddb66bd2a74bcd13492509046e9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68115804"
---
# <a name="execute-t-sql-statement-task-maintenance-plan"></a>執行 T-SQL 陳述式工作 (維護計畫)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用 [執行 T-SQL 陳述式工作]  對話方塊，即可將您選擇的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式加入此維護計畫，來自訂維護計畫。  
  
## <a name="options"></a>選項。  
 **[連接]**  
 選取執行此工作時要使用的伺服器連接。  
  
 **新增**  
 建立新的伺服器連接，以便執行此工作時使用。 下面會描述 **[新增連接]** 對話方塊。  
  
 **執行逾時**  
 在逾時之前，等候工作完成的時間 (秒數) (結束工作)。  
  
 **T-SQL 陳述式**  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 要執行的陳述式。  
  
 **檢視 T-SQL**  
 根據選取的選項，檢視此工作在伺服器上執行的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。  
  
> [!NOTE]  
>  受影響的物件數目較為大量時，會多花一些時間才會顯示。  
  
## <a name="new-connection-dialog-box"></a>新增連接對話方塊  
 **連接名稱**  
 輸入新連接的名稱。  
  
 **選取或輸入伺服器名稱**  
 選取執行此工作時要連接的伺服器。  
  
 **[重新整理]**  
 重新整理可用的伺服器清單。  
  
 **輸入要登入到伺服器的資訊**  
 指定如何對伺服器進行驗證。  
  
 **使用 Windows 整合式安全性**  
 使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 的執行個體。  
  
 **使用特定的使用者名稱和密碼**  
 使用 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 驗證，連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。 無法使用此選項。  
  
 **User name**  
 提供驗證時要使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登入。 無法使用此選項。  
  
 **密碼**  
 提供驗證時要使用的密碼。 無法使用此選項。  
  
  
