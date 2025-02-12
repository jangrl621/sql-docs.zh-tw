---
title: 備份資料庫工作 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.backupdatabasetask.f1
helpviewer_keywords:
- database backups [Integration Services]
- Back Up Database task [Integration Services]
- backing up databases [Integration Services]
- transaction log backups [Integration Services]
- backing up transaction logs [Integration Services]
ms.assetid: b8839d71-13b7-41f2-a434-cb95020e79d7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d610b40e38832e2dc82b02edf276475d2b27d74c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67947181"
---
# <a name="back-up-database-task"></a>備份資料庫工作

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  「備份資料庫」工作會執行不同類型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫備份作業。 如需詳細資訊，請參閱 [Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)。  
  
 使用「備份資料庫」工作，封裝即可備份單一資料庫或多個資料庫。 如果工作僅備份單一資料庫，您可以選擇備份元件：資料庫，或其檔案和檔案群組。  
  
## <a name="supported-recover-models-and-backup-types"></a>支援的復原模型和備份類型  
 下表列出「備份資料庫」工作支援的復原模式和備份類型。  
  
|復原模式|[資料庫]|資料庫差異|交易記錄|檔案或檔案差異|  
|--------------------|--------------|---------------------------|---------------------|-------------------------------|  
|Simple|必要項|選擇性|不支援|不支援|  
|完整|必要項|選擇性|必要項|選擇性|  
|大量記錄|必要項|選擇性|必要項|選擇性|  
  
 「備份資料庫」工作會封裝 Transact-SQL BACKUP 陳述式。 如需詳細資訊，請參閱 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)。  
  
## <a name="configuration-of-the-back-up-database-task"></a>備份資料庫工作的組態  
 您可以透過「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」設定屬性 這項工作位於「 **設計師」中** [工具箱] **的** [維護計畫工作] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 區段。  
  
 如需有關可在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之屬性的詳細資訊，請按下列主題：  
  
-   [備份資料庫工作 &#40;維護計畫&#41;](../../relational-databases/maintenance-plans/options-in-the-back-up-database-task-for-maintenance-plan.md)  
  
 如需有關如何在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：  
  
-   [設定工作或容器的屬性](https://msdn.microsoft.com/library/52d47ca4-fb8c-493d-8b2b-48bb269f859b)  
  
  
