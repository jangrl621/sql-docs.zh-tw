---
title: 未同步處理某些同步複本 | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp5synchronized.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: e58ed56e-4c30-42e6-a9fc-a8c401620e02
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d091cb3151daf161818124d6b4473637355a3674
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68014035"
---
# <a name="some-synchronous-replicas-are-not-synchronized"></a>未同步處理某些同步複本
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>簡介  
  
|||  
|-|-|  
|**原則名稱**|同步複本的資料同步處理狀態|  
|**問題**|某些同步複本並未同步處理。|  
|**類別目錄**|**警告**|  
|**Facet**|可用性群組|  
  
## <a name="description"></a>Description  
 這項原則會積存所有可用性複本的資料同步處理狀態，並檢查是否有任何可用性複本未處於預期的同步處理狀態。 當任何非同步複本不是處於 SYNCHRONIZING 狀態，而且任何同步複本不是處於 SYNCHRONIZED 狀態時，原則為狀況不良。 否則原則狀態良好。  
  
> [!NOTE]  
>  在此版本 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中，可能原因和解決方案的資訊位於 TechNet Wiki 上的 [未同步處理某些同步複本](https://go.microsoft.com/fwlink/p/?LinkId=220853) 。  
  
## <a name="possible-causes"></a>可能的原因  
 在這個可用性群組中，至少有一個可用性複本目前並未同步處理。 複本同步處理狀態可能是 SYNCHRONIZING 或 NOT SYNCHRONIZING。  
  
## <a name="possible-solution"></a>可能的解決方案  
 使用可用性複本原則狀態，尋找同步處理狀態不正確的可用性複本，然後解決可用性複本上的問題。  
  
## <a name="see-also"></a>另請參閱  
 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
