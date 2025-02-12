---
title: 步驟 3：加入套件和其他檔案 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: tutorial
ms.assetid: a7e6ec9c-d31d-4613-9525-8947a7b358f7
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 418b113429e31fdd0c6ad75bbc1707ef3a417b1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67902660"
---
# <a name="lesson-1-3---adding-packages-and-other-files"></a>課程 1-3 - 加入封裝和其他檔案

[!INCLUDE[ssis-appliesto](../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


在這項工作中，您會將現有的封裝、支援個別封裝的輔助檔案以及讀我檔案，加入至前一項工作所建立的「部署教學課程」專案中。 例如，您將會加入包含封裝資料的 XML 資料檔，還會加入一個文字檔，以提供有關專案中所有封裝的讀我資訊。  
  
當您將封裝部署到測試或實際執行環境時，通常不會將資料檔包含在部署中，而是利用組態來更新資料來源的路徑，以存取資料檔或資料庫的測試版本或實際執行版本。 為了教學上的目的，這個教學課程會將資料檔包含在封裝部署中。  
  
當您安裝 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 範例時，會一併安裝封裝和封裝所使用的範例資料。 您將會在「部署教學課程」專案中加入下列封裝：  
  
-   **DataTransfer：** 這是基本套件，它會從一般檔案中擷取資料、評估資料行的值以便有條件地保留資料集中的資料列，以及將資料載入至 AdventureWorks 資料庫中的資料表。  
  
-   **LoadXMLData：** 這是資料傳輸套件，它會從 XML 資料檔中擷取資料、評估和彙總資料行的值，以及將資料載入至 AdventureWorks 資料庫中的資料表。  
  
若要支援這些封裝的部署，您需要將下列輔助檔案加入至「部署教學課程」專案中：  
  
|封裝|檔案|  
|-----------|--------|  
|DataTransfer|NewCustomers.txt|  
|LoadXMLData|orders.xml 和 orders.xsd|  
  
您還需要加入讀我檔案，這是一個文字檔，會提供有關「部署教學課程」專案的資訊。  
  
下列程序中所使用的路徑是假設 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 範例已安裝在預設位置 [!INCLUDE[ssSampPathIS](../includes/sssamppathis-md.md)]。 如果您將範例安裝在不同的位置，則請在程序中改用該位置。  
  
在下一項工作中，您會將組態加入至 DataTransfer 和 LoadXMLData 封裝中。 所有組態都是儲存在 XML 檔案中，您必須使用系統環境變數來指定檔案的位置。 在您建立組態檔之後，請將檔案加入至專案中。  
  
### <a name="to-add-packages-to-the-deployment-tutorial-project"></a>若要將封裝加入至部署教學課程專案中  
  
1.  如果 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 尚未開啟，請按一下 [開始]  ，依序指向 [所有程式]  和 [Microsoft SQL Server]  ，然後按一下 [SQL Server Data Tools]  。  
  
2.  在 [檔案]  功能表上，依序按一下 [開啟]  、[專案/方案]  和 [部署教學課程]  資料夾，然後按一下 [開啟]  ，再按兩下 [Deployment Tutorial.sln]  。  
  
3.  在方案總管中，以滑鼠右鍵按一下 [部署教學課程]，按一下 [加入]  ，然後按一下 [現有的封裝]  。  
  
4.  在 [加入現有封裝的複本]  對話方塊的 [封裝位置]  中，選取 [檔案系統]  。  
  
5.  按一下瀏覽 **(…)** 按鈕，巡覽至 C:\Program Files\Microsoft SQL Server\100\Samples\Integration ServicesTutorial\Deploying Packages\Completed Packages，選取 [DataTransfer.dtsx]  ，然後按一下 [開啟]  。  
  
6.  按一下 [確定]  。  
  
7.  重複步驟 3 到 6，這次請加入 LoadXMLData.dtsx，您可以在 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages 中找到此檔案。  
  
### <a name="to-add-ancillary-files-to-the-deployment-tutorial-project"></a>若要將輔助檔案加入至部署教學課程專案中  
  
1.  在方案總管中，以滑鼠右鍵按一下 [部署教學課程]，按一下 [加入]  ，然後按一下 [現有項目]  。  
  
2.  在 [加入現有項目 - 部署教學課程]  對話方塊中，巡覽至 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\Sample Data，選取 orders.xml、orders.xsd 和 NewCustomers.txt，然後按一下 [加入]  。  
  
3.  在 [加入現有項目 - 部署教學課程]  對話方塊中，巡覽至 C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deployment Packages\\，選取 Readme.txt，然後按一下 [加入]  。  
  
4.  按一下 [檔案] 功能表上的 [全部儲存]  。  
  
## <a name="next-task-in-lesson"></a>本課程的下一項工作  
[步驟 4：新增套件設定](../integration-services/lesson-1-4-adding-package-configurations.md)  
  
  
  
