---
title: 開發自訂連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- packages [Integration Services], connections
- custom connection managers [Integration Services], about custom connection managers
- connection managers [Integration Services], custom
- Integration Services packages, connection managers
- SSIS packages, connection managers
- SQL Server Integration Services packages, connection managers
- custom connection managers [Integration Services]
ms.assetid: bda0b29e-57f5-4879-b04d-1396dc56daa8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b650963db2dbfe07eaafdc879da39ff62d8e57c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896380"
---
# <a name="developing-a-custom-connection-manager"></a>開發自訂連接管理員

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 會使用連接管理員封裝連接至外部資料來源所需的資訊。 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含各種連接管理員，可以連接到最常使用的資料來源，包括企業資料庫、文字檔案與 Excel 工作表等。 如果 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 支援的連接管理員和外部資料來源無法完全符合您的需求，可以建立自訂連接管理員。  
  
 若要建立自訂連接管理員，您必須建立繼承自 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase> 基底類別的類別、將 <xref:Microsoft.SqlServer.Dts.Runtime.DtsConnectionAttribute> 屬性 (Attribute) 套用至新類別，以及覆寫基底類別的重要方法與屬性 (Property)，包括 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.ConnectionString%2A> 屬性 (Property) 與 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManagerBase.AcquireConnection%2A> 方法。  
  
> [!IMPORTANT]  
>  已經建置到 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中的大多數工作、來源和目的地只能搭配特定類型的內建連接管理員一起使用。 在開發自訂連接管理員以搭配內建工作與元件使用時，請檢查這些元件是否將可用的連接管理員清單限制在特定類型的連接管理員。 如果您的解決方案需要自訂連接管理員，您可能也必須開發自訂工作或是自訂來源或目的地，以供連接管理員使用。  
  
## <a name="in-this-section"></a>本節內容  
 本章節描述如何建立和設定自訂連接管理員及其選用自訂使用者介面，以及如何撰寫它們的程式碼。 在本章節中所顯示的程式碼片段是取自 SQL Server 自訂連接管理員範例。  
  
 [建立自訂連線管理員](../../../integration-services/extending-packages-custom-objects/connection-manager/creating-a-custom-connection-manager.md)  
 描述如何為自訂連接管理員專案建立類別。  
  
 [撰寫自訂連線管理員的程式碼](../../../integration-services/extending-packages-custom-objects/connection-manager/coding-a-custom-connection-manager.md)  
 描述如何透過覆寫基底類別的方法與屬性，來實作自訂連接管理員。  
  
 [開發自訂連線管理員的使用者介面](../../../integration-services/extending-packages-custom-objects/connection-manager/developing-a-user-interface-for-a-custom-connection-manager.md)  
 描述如何實作使用者介面類別以及用以設定自訂連接管理員的表單。  
  
## <a name="related-sections"></a>相關章節  
  
### <a name="information-common-to-all-custom-objects"></a>自訂物件的共通資訊  
 如需有關 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之所有類型自訂物件適用的共通資訊，請參閱下列主題：  
  
 [開發 Integration Services 的自訂物件](../../../integration-services/extending-packages-custom-objects/developing-custom-objects-for-integration-services.md)  
 描述為 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 實作所有類型的自訂物件之基本步驟。  
  
 [保存自訂物件](../../../integration-services/extending-packages-custom-objects/persisting-custom-objects.md)  
 描述自訂的持續性並解釋必須實作它的時機。  
  
 [自訂物件的建立、部署和偵錯](../../../integration-services/extending-packages-custom-objects/building-deploying-and-debugging-custom-objects.md)  
 描述建立、簽署、部署和偵錯自訂物件的技術。  
  
### <a name="information-about-other-custom-objects"></a>其他自訂物件的相關資訊  
 如需有關在 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 中可以建立之其他類型自訂物件的詳細資訊，請參閱下列主題：  
  
 [開發自訂工作](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)  
 討論如何進行自訂工作的程式設計。  
  
 [開發自訂記錄提供者](../../../integration-services/extending-packages-custom-objects/log-provider/developing-a-custom-log-provider.md)  
 討論如何進行自訂記錄提供者的程式設計。  
  
 [開發自訂 Foreach 列舉程式](../../../integration-services/extending-packages-custom-objects/foreach-enumerator/developing-a-custom-foreach-enumerator.md)  
 討論如何進行自訂列舉值的程式設計。  
  
 [開發自訂資料流程元件](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)  
 討論如何進行自訂資料流程來源、轉換和目的地的程式設計。  
  
