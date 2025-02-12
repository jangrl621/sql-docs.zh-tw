---
title: 如何檢視 CDC 執行個體屬性 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 4bce9b82-7bbd-41df-b3f4-4b40b8bad474
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 548ca5fcbe851d84f884857acb72cb200e3420fd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101708"
---
# <a name="how-to-view-the-cdc-instance-properties"></a>如何檢視 CDC 執行個體屬性

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  這個程序描述如何使用 CDC 設計工具主控台來檢視有關執行個體的資訊，您建立這些資訊是為了管理執行個體的操作。  
  
### <a name="to-view-information-about-a-specific-instance"></a>若要檢視有關特定執行個體的資訊  
  
1.  從 **[開始]** 功能表選取 **[CDC 設計工具主控台]** 。  
  
2.  在左窗格中展開 **[異動資料擷取]** ，然後展開包含您要檢視之執行個體的服務。  
  
3.  選取您要使用的執行個體名稱。  
  
     有關執行個體的資訊會顯示在 CDC 設計工具主控台的中央。 它分為四個索引標籤。 所有索引標籤都是唯讀的。  
  
     **狀態**  
     這個索引標籤會顯示有關此執行個體之目前異動資料擷取狀態的資訊。 如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ **Manage a CDC Instance** ＞中的 [[檢視器索引標籤]](../../integration-services/change-data-capture/manage-a-cdc-instance.md)一節。  
  
     **Oracle**  
     此索引標籤會顯示有關 CDC 執行個體和 Oracle 來源資料庫的一般資訊。 如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ [Edit the Oracle Database Properties](../../integration-services/change-data-capture/edit-the-oracle-database-properties.md)＞。  
  
     **資料表**  
     這個索引標籤會顯示有關異動資料擷取中所包含之資料表的資訊。 也會列出擷取的資料行。 如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ [Edit Tables](../../integration-services/change-data-capture/edit-tables.md)＞。  
  
     **進階**  
     此索引標籤會顯示您在屬性編輯器中所定義的進階屬性清單。 如需有關此索引標籤顯示之內容的詳細資訊，請參閱＜ [Edit the Advanced Properties](../../integration-services/change-data-capture/edit-the-advanced-properties.md)＞。  
  
  
