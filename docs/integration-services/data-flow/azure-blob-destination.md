---
title: Azure Blob 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 07/25/2016
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpblobdest.f1
- sql14.dts.designer.afpblobdest.f1
ms.assetid: 820a1e7a-7182-4c7b-ab56-5b4097a7e042
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 3194e2dbb6563b5260fcc390e84e73a17e09542c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68045466"
---
# <a name="azure-blob-destination"></a>Azure Blob 目的地

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


 [Azure Blob 目的地]  元件可讓 SSIS 封裝將資料寫入 Azure Blob。 支援的檔案格式：CSV 和 AVRO。 
   
 將 [Azure Blob 目的地]  拖放到資料流程設計師，然後在上面按兩下以查看編輯器)。  
  
 **Azure Blob 目的地**是 [SQL Server Integration Services (SSIS) Feature Pack for Azure](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) 的元件。  
  
1.  針對 [Azure 儲存體連線管理員]  欄位，請指定現有的 Azure 儲存體連線管理員，或建立參考 Azure 儲存體帳戶的新連線管理員。  
  
2.  針對 [Blob 容器名稱]  欄位，請指定包含原始程式檔的 Blob 容器名稱。  
  
3.  針對 [Blob 名稱]  欄位，請指定 Blob 的路徑。  
  
4.  針對 [Blob 檔案格式]  欄位，請指定要使用的 Blob 格式。  
  
5.  若檔案格式為 CSV，則您必須指定 [資料行分隔符號字元]  值。 若檔案中第一個資料列包含資料行名稱，請選取 [第一個資料列的資料行名稱]  。  
  
6.  指定連接資訊後，請切換至 [資料行]  頁面，將來源資料行對應至 SSIS 資料流程的目的地資料行。  
  
  
