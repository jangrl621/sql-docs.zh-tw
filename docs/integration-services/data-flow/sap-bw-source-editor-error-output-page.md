---
title: SAP BW 來源編輯器 (錯誤輸出頁面) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.sapbwsource.erroroutput.f1
ms.assetid: b6e23b0c-949a-46d1-8424-4dc3d9035e79
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2d823b1155a07f7bb3dc44f84f852d747692ae58
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002368"
---
# <a name="sap-bw-source-editor-error-output-page"></a>SAP BW 來源編輯器 (錯誤輸出頁面)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  使用 **[SAP BW 來源編輯器]** 的 **[錯誤輸出]** 頁面可以選取錯誤處理選項，並設定錯誤輸出資料行的屬性。  
  
 若要深入了解 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Connector 1.1 for SAP BW 的 SAP BW 來源元件，請參閱 [SAP BW 來源](../../integration-services/data-flow/sap-bw-source.md)。  
  
> [!IMPORTANT]  
>  Microsoft Connector 1.1 for SAP BW 的文件集是假設使用者已熟悉 SAP Netweaver BW 環境。 如需有關 SAP Netweaver BW 的詳細資訊，或有關如何設定 SAP Netweaver BW 物件與處理序的詳細資訊，請參閱 SAP 文件集。  
  
> [!IMPORTANT]  
>  擷取 SAP Netweaver BW 中的資料需要額外的 SAP 授權。 請洽詢 SAP 以確認這些需求。  
  
 **開啟錯誤輸出頁面**  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含 SAP BW 來源的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝。  
  
2.  在 [資料流程]  索引標籤上，按兩下 SAP BW 來源。  
  
3.  在 **[SAP BW 來源編輯器]** 中，按一下 **[錯誤輸出]** 開啟編輯器的 **[錯誤輸出]** 頁面。  
  
## <a name="options"></a>選項。  
  
> [!NOTE]  
>  如果您不知道設定來源的所有必要值，可能必須詢問 SAP 系統管理員。  
  
 **輸入或輸出**  
 檢視資料來源的名稱。  
  
 **資料行**  
 檢視您在 [SAP BW 來源編輯器]  對話方塊之 [資料行]  頁面上所選取的外部 (來源) 資料行。 如需此對話方塊的詳細資訊，請參閱 [SAP BW 來源編輯器 &#40;資料行頁面&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)。  
  
 **錯誤**  
 指定 SAP BW 來源元件應該在發生錯誤時採取的動作：忽略失敗、重新導向資料列，或使元件失效。  
  
 **截斷**  
 指定 SAP BW 來源元件應該在發生截斷時採取的動作：忽略失敗、重新導向資料列，或使元件失效。  
  
 **說明**  
 檢視錯誤的描述。  
  
 **將這個值設定到選取的資料格**  
 指定 SAP BW 來源元件應該在發生錯誤或截斷時對所有選取之資料格採取的動作：忽略失敗、重新導向資料列，或使元件失效。  
  
 **套用**  
 將錯誤處理選項套用至選取的資料格。  
  
## <a name="see-also"></a>另請參閱  
 [SAP BW 來源編輯器 &#40;連線管理員頁面&#41;](../../integration-services/data-flow/sap-bw-source-editor-connection-manager-page.md)   
 [SAP BW 來源編輯器 &#40;資料行頁面&#41;](../../integration-services/data-flow/sap-bw-source-editor-columns-page.md)   
 [SAP BW 來源編輯器 &#40;進階頁面&#41;](../../integration-services/data-flow/sap-bw-source-editor-advanced-page.md)   
 [Microsoft Connector for SAP BW F1 說明](../../integration-services/microsoft-connector-for-sap-bw-f1-help.md)  
  
  
