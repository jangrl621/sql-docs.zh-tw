---
title: 第 1 課：準備建立部署配套 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: b6fe283c-9856-4ba1-a497-e3912424fd18
author: janinezhang
ms.author: janinez
ms.openlocfilehash: fee38d51257ad21822d39700b549b2388eed1714
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68112210"
---
# <a name="lesson-1-preparing-to-create-the-deployment-bundle"></a>第 1 課：準備建立部署套件組合

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


在這一課中，您會建立支援教學課程的工作資料夾和環境變數、建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案、在專案中加入數個封裝及其支援檔案，以及在封裝中實作組態。  
  
[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 會依照個別專案部署套件，因此，在建立部署配套的第一個步驟中，您必須將所有的套件和套件相依性全部收集到一個 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中。 在部署的封裝中納入其他資訊，通常會很有用，例如，您也可以在專案中加入讀我檔案，以提供此封裝群組的基本文件集。  
  
在加入封裝和檔案之後，您還會在尚未使用組態的封裝中加入組態。 組態會在執行階段更新封裝和封裝物件的屬性。 在稍後的課程中，您將會在封裝部署期間修改這些組態的值，以便在部署的目標環境中支援封裝。  
  
在加入組態之後，您應該在 [ [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] (用來建立 ETL 封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 圖形化工具) 中開啟封裝，並且檢查封裝和封裝元素的屬性以及封裝組態，以便能更加了解部署所需解決的問題。 例如，由於其中一個封裝會從文字檔擷取資料，因此您必須先更新資料檔的位置，部署的封裝才能順利執行。  
  
**完成本課程的估計時間：** 1 小時  
  
## <a name="lesson-tasks"></a>課程工作  
這一課包含下列工作：  
  
-   [步驟 1：建立工作資料夾和環境變數](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
-   [步驟 2：建立部署專案](../integration-services/lesson-1-2-creating-the-deployment-project.md)  
  
-   [步驟 3：新增套件和其他檔案](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
-   [步驟 4：新增套件設定](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
-   [步驟 5：測試更新的套件](../integration-services/lesson-1-5-testing-the-updated-packages.md)  
  
## <a name="start-the-lesson"></a>開始課程  
[步驟 1：建立工作資料夾和環境變數](../integration-services/lesson-1-1-creating-working-folders-and-environment-variables.md)  
  
  
  
