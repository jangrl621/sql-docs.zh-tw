---
title: 驗證對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.ssis.ssms.isprojectvalidate.f1
- sql13.ssis.ssms.ispackagevalidate.f1
ms.assetid: 134e14ce-4f8d-4a20-889a-918014c841d8
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 999b409025cce7ec209f527841d8ecb9fc416af9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070514"
---
# <a name="validate-dialog-box"></a>驗證對話方塊

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  使用 **[驗證]** 對話方塊檢查 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案或封裝中的常見問題。  
  
 如果有問題，就會在對話方塊上方顯示一個訊息。 否則，「就緒」這個詞會顯示在上方。  
  
 **您想要做什麼事？**  
  
-   [開啟 [驗證] 對話方塊](#open_dialog)  
  
-   [設定 [一般] 頁面上的選項](#general)  
  
##  <a name="open_dialog"></a> 開啟 [驗證] 對話方塊  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，連接至 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 伺服器。  
  
     您正在連線到裝載 SSISDB 資料庫的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體。  
  
2.  在 [物件總管] 中，展開樹狀目錄以顯示 **[Integration Services 目錄]** 節點。  
  
3.  展開 **[SSISDB]** 節點。  
  
4.  展開包含您要驗證之專案或封裝的資料夾。  
  
5.  以滑鼠右鍵按一下封裝，然後按一下 [驗證]  。  
  
##  <a name="general"></a> 設定 [一般] 頁面上的選項  
 **環境**  
 選取您要用來驗證專案或封裝的環境。  
  
 **32 位元執行階段**  
 選擇使用 32 位元執行階段執行封裝。  
  
 **[參數]** 索引標籤會列出您用來驗證專案或封裝的參數值。 以下是在 [參數] 索引標籤上的選項。  
  
 **容器**  
 列出包含參數的物件。  
  
 **參數**  
 列出參數的名稱  
  
 **ReplTest1**  
 列出參數值。  
  
 **[連接管理員]** 索引標籤會列出您用來驗證專案或封裝的連接管理員屬性值。  
  
 以下是在 **[連接管理員]** 索引標籤上的選項。  
  
 **容器**  
 列出包含連接管理員的物件。  
  
 **名稱**  
 列出連接管理員名稱。  
  
 **屬性名稱**  
 列出連接管理員屬性的名稱。  
  
 **ReplTest1**  
 列出指派給連接管理員屬性的值。  
  
  
