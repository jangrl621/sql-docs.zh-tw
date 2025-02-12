---
title: Azure 訂用帳戶連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.designer.afpsubscrconn.f1
- sql14.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 1e958acea51f9664323a6f5662bed6b8d78c0444
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968129"
---
# <a name="azure-subscription-connection-manager"></a>Azure 訂用帳戶連線管理員

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  **Azure 訂用帳戶連線管理員**可讓 SSIS 套件使用您指定的屬性值連接到 Azure 訂用帳戶︰Azure 訂用帳戶識別碼及管理憑證。  
  
 **Azure 訂用帳戶連線管理員**是 [Azure SQL Server Integration Services (SSIS) Feature Pack](../../integration-services/azure-feature-pack-for-integration-services-ssis.md) 的元件。
  
1.  在上方顯示的 [加入 SSIS 連線管理員]  對話方塊中，選取 [Azure 訂用帳戶]  ，然後按一下 [加入]  。  [Azure Subscription Connection Manager Editor (Azure 訂用帳戶連線管理員編輯器)]  對話方塊應會隨即出現。  
  
    ![SSIS-AzureSubscriptionConnectionManager](../../integration-services/connection-manager/media/ssis-azuresubscriptionconnectionmanager.png)
  
2.  在 [Azure 訂用帳戶識別碼]  輸入可唯一識別 Azure 訂用帳戶的 Azure 訂用帳戶識別碼。  可以在 [設定]  頁面下的 [Azure 管理入口網站](https://manage.windowsazure.com)找到此值：  
  
    ![SSIS-AzureSettings-SubscriptionID](../../integration-services/connection-manager/media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  從下拉式清單中選擇 [Management certificate store location (管理憑證存放區位置)]  和 [Management certificate store name (管理憑證存放區名稱)]  。  
  
4.  輸入 [管理憑證指紋]  ，或按一下 [瀏覽...]  可從選取的存放區選擇憑證。 憑證必須上傳為訂用帳戶的管理憑證。 若要這樣做，請按一下 Azure 入口網站下一個頁面上的 [上傳]  (如需詳細資訊，請參閱此 [MSDN 文章](https://msdn.microsoft.com/library/azure/gg551722.aspx))。  
  
     ![SSIS-AzureSettings-ManagementCertificate](../../integration-services/connection-manager/media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  按一下 [測試連接]  來測試連接。  
  
6.  按一下 **[確定]** ，關閉對話方塊。  
  
  
