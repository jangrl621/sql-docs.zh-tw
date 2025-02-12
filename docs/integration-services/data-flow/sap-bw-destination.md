---
title: SAP BW 目的地 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: a612ed91-b89b-4173-a0b1-0bce381e1e28
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 688ef80602783a3e9e362d58f74a73bbf4f6085b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68034170"
---
# <a name="sap-bw-destination"></a>SAP BW 目的地

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  SAP BW 目的地是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的目的地元件。 因此，SAP BW 目的地會將 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝中資料流程的資料載入 SAP Netweaver BW 版本 7 系統中。  
  
 這個目的地具有一個輸入和一個錯誤輸出。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。 如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。  
  
 若要使用 SAP BW 目的地，您必須執行下列工作：  
  
-   [準備 SAP Netweaver BW 物件](#bkmk_Prepare_Objects)  
  
-   [連接到 SAP Netweaver BW 系統](#bkmk_Connect_Database)  
  
-   [設定 SAP BW 目的地](#bkmk_Configure_Destination)  
  
##  <a name="bkmk_Prepare_Objects"></a> 準備目的地所需的 SAP Netweaver BW 物件  
 SAP BW 目的地要求特定物件必須存在 SAP Netweaver BW 系統中，然後目的地才能運作。 如果這些物件原本不存在，您就必須遵循下列步驟，在 SAP Netweaver BW 系統中建立並設定這些物件。  
  
> [!NOTE]  
>  如需有關這些物件和這些組態設定步驟的其他詳細資料，請參閱 SAP Netweaver BW 文件集。  
  
1.  建立新的來源系統：  
  
    1.  選取 [協力廠商/暫存 BAPI]  類型。  
  
    2.  針對 [目標系統的通訊類型]  ，選取 [非 Unicode (非使用中 MDMP 設定)]  。  
  
    3.  指派適當的程式識別碼。  
  
2.  將來源系統指派給 InfoSource。  
  
3.  建立 InfoPackage。  
  
     InfoPackage 是 SAP BW 目的地所需的最重要物件。  
  
 您也可以建立其他支援將資料載入 SAP Netweaver BW 系統所需的 InfoObject、InfoCube、InfoSource 和 InfoPackage。  
  
##  <a name="bkmk_Connect_Database"></a> 連接到 SAP Netweaver BW 系統  
 為了連接到 SAP Netweaver BW 版本 7 系統，SAP BW 目的地會使用屬於 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 封裝一部分的 SAP BW 連接管理員。 SAP BW 連接管理員是 SAP BW 目的地可以使用的唯一 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 連接管理員。  
  
 如需有關 SAP BW 連接管理員的詳細資訊，請參閱＜ [SAP BW Connection Manager](../../integration-services/connection-manager/sap-bw-connection-manager.md)＞。  
  
##  <a name="bkmk_Configure_Destination"></a> 設定 SAP BW 目的地  
 您可以利用下列方式設定 SAP BW 目的地：  
  
-   查閱並選取要用來載入資料的 InfoPackage。  
  
-   將資料流程中的每個資料行對應至 InfoPackage 中的適當 InfoObject。  
  
-   透過設定 **PackageSize** 屬性，指定一次會傳輸多少個資料列。  
  
-   選擇要等候直到 SAP Netweaver BW 系統完成資料載入為止。  
  
-   選擇不要觸發 InfoPackage，而是等候 SAP Netweaver BW 系統已開始載入資料的通知。  
  
-   (選擇性) 在資料載入完成之後觸發另一個處理序鏈結。  
  
-   (選擇性) 建立目的地所需的 SAP Netweaver BW 物件。 這包括建立 InfoObject、InfoCube、InfoSource 和 InfoPackage。  
  
-   使用您已選取的選項來測試資料的載入。  
  
 您也可以針對目的地的 RFC 函數呼叫啟用記錄 (這項記錄與您針對 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝啟用的選擇性記錄是分開的)。您可以在設定目的地將使用的 SAP BW 連接管理員時啟用 RFC 函數呼叫的記錄。 如需有關如何設定 SAP BW 連接管理員的詳細資訊，請參閱＜ [SAP BW Connection Manager](../../integration-services/connection-manager/sap-bw-connection-manager.md)＞。  
  
 如果您不知道設定目的地的所有必要值，可能必須詢問 SAP 系統管理員。  
  
 如需示範如何設定及使用 SAP BW 連接管理員、來源和目的地的逐步解說，請參閱＜ [搭配 SAP BI 7.0 使用 SQL Server 2008 Integration Services](https://go.microsoft.com/fwlink/?LinkID=137090)＞技術白皮書。 這份技術白皮書也會示範如何設定 SAP BW 中的必要物件。  
  
### <a name="using-the-ssis-designer-to-configure-the-destination"></a>使用 SSIS 設計師設定目的地  
 如需有關可以在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定之 SAP BW 目的地屬性的詳細資訊，請按下列其中一個主題：  
  
-   [SAP BW 目的地編輯器 &#40;連線管理員頁面&#41;](../../integration-services/data-flow/sap-bw-destination-editor-connection-manager-page.md)  
  
-   [SAP BW 目的地編輯器 &#40;對應頁面&#41;](../../integration-services/data-flow/sap-bw-destination-editor-mappings-page.md)  
  
-   [SAP BW 目的地編輯器 &#40;錯誤輸出頁面&#41;](../../integration-services/data-flow/sap-bw-destination-editor-error-output-page.md)  
  
-   [SAP BW 目的地編輯器 &#40;進階頁面&#41;](../../integration-services/data-flow/sap-bw-destination-editor-advanced-page.md)  
  
 設定 SAP BW 目的地時，您也可以使用各種對話方塊來查閱或建立 SAP Netweaver BW 物件。 如需有關這些對話方塊的詳細資訊，請按下列其中一個主題：  
  
-   [查閱 InfoPackage](../../integration-services/data-flow/look-up-infopackage.md)  
  
-   [建立新的 InfoObject](../../integration-services/data-flow/create-new-infoobject.md)  
  
-   [建立交易資料的 InfoCube](../../integration-services/data-flow/create-infocube-for-transaction-data.md)  
  
-   [查詢 InfoObject](../../integration-services/data-flow/look-up-infoobject.md)  
  
-   [建立 InfoSource](../../integration-services/data-flow/create-infosource.md)  
  
-   [建立交易資料的 InfoSource](../../integration-services/data-flow/create-infosource-for-transaction-data.md)  
  
-   [建立主要資料的 InfoSource](../../integration-services/data-flow/create-infosource-for-master-data.md)  
  
-   [建立 InfoPackage](../../integration-services/data-flow/create-infopackage.md)  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft Connector for SAP BW 元件](../../integration-services/microsoft-connector-for-sap-bw-components.md)  
  
  
