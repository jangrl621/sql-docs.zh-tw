---
title: 安裝 SQL Server 資料庫引擎 | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 968cf923f1defcf724b3a3c8a968a20c54f3e30b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67991109"
---
# <a name="install-sql-server-database-engine"></a>安裝 SQL Server Database Engine

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

## <a name="overview"></a>概觀
[!INCLUDE[ssDE](../../includes/ssde-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件是用來儲存、處理及維護資料安全的核心服務。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 提供控制存取和快速交易處理，以符合企業中最需要的資料耗用應用程式的需求。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在單一電腦上最多支援 50 個 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。 若要建立一般的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝，請參閱[從安裝精靈安裝 SQL Server &#40;安裝程式&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md)。  
  
>[!IMPORTANT]
>如果是本機安裝，您必須以管理員身分執行安裝程式。 如果您是從遠端共用位置安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，則必須使用對遠端共用位置具有讀取和執行權限的網域帳戶。  

## <a name="features"></a>功能
當您在 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝精靈] 的 [要安裝的元件] 頁面上選取 [[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Database Engine]  時，會安裝下列功能：  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   [SQL Server 複寫](../../relational-databases/replication/sql-server-replication.md) - 這是選擇性元件  

-   [機器學習服務 (資料庫內) 含 R 與 Python](../../advanced-analytics/install/sql-machine-learning-services-windows-install.md) - 是選擇性元件

-   全文檢索搜尋 (選擇性元件)  
  
-   Data Quality Services (選擇性元件)  
  
    > [!NOTE]  
    >  在這版的安裝程式中選取 [Data Quality Services]  核取方塊，並不會安裝 Data Quality Services (DQS) 伺服器。 您必須執行額外的安裝後步驟，才能安裝 DQS 伺服器。 如需詳細資訊，請參閱 [安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)。  
    
- [外部資料的 PolyBase 查詢服務](../../relational-databases/polybase/polybase-guide.md) - 為選擇性元件。 自 SQL Server 2019 起，也提供適用於 HDFS 資料來源的 Java 連接器。

  
 下列其他功能是許多典型使用者案例的選項：  
  
-   Data Quality Client
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]
-   連接元件
-   程式設計模型
-   管理工具
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]
-   文件集元件  
  

> [!NOTE]  
>  根據預設， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝程序中不會安裝範例資料庫和範例程式碼。 若要安裝範例資料庫和範例程式碼，請參閱 [Microsoft SQL Server 範例](../../sample/microsoft-sql-server-samples.md)。 請參閱 [CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843) 上的較舊範例。  

  
## <a name="see-also"></a>另請參閱  
 [SQL Server 2017 的版本與支援功能](~/sql-server/editions-and-components-of-sql-server-2017.md)   
 [規劃 SQL Server 安裝](../../sql-server/install/planning-a-sql-server-installation.md)   
 [高可用性解決方案 &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [使用安裝精靈升級 SQL Server &#40;安裝程式&#41;](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
