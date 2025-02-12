---
title: 狀態列 (Database Engine 查詢編輯器) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 736b16b01a2a0bbba98233400fdad82a08990c58
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262842"
---
# <a name="status-bar-database-engine-query-editor"></a>狀態列 (Database Engine 查詢編輯器)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗的狀態列可能利用彩色編碼，以便表示每個視窗所連接的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體。  
  
1.  **開始之前：** [狀態列色彩](#StatusBarColors)  
  
2.  **在以下項目中設定伺服器狀態色彩：** [物件總管](#SetOEServerColor)、[已註冊的伺服器](#SetRegServerColor)  
  
3.  **使用狀態色彩：** [使用伺服器色彩開啟查詢編輯器](#OpenServerColor)、[指定狀態色彩並開啟查詢編輯器](#OpenSpecColor)  
  
##  <a name="StatusBarColors"></a> 狀態列色彩  
 您可在 **[物件總管]** 或 **[已註冊的伺服器]** 中讓狀態列色彩與特定伺服器節點產生關聯。 您僅能指定連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的伺服器節點之色彩，而不能指定其他 SQL Server 技術的伺服器節點色彩。 每當您將新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗連接至 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體時，便可自訂狀態列色彩。 接著您可以使用為伺服器節點所定義的狀態色彩，開啟查詢編輯器視窗；或為該編輯器視窗指定獨特的色彩。  
  
 為 [物件總管] 中伺服器節點設定自訂狀態列色彩的作業，必須在進行連接時完成。 若要變更現有伺服器節點的色彩，您必須中斷連接後重新連接，然後再指定新的色彩。  
  
##  <a name="SetOEServerColor"></a> 為 [物件總管] 中的伺服器設定狀態色彩  
 **設定 [物件總管] 中的伺服器狀態色彩**  
  
1.  在 [物件總管]  中，選取 [連接]  按鈕，然後選取 [資料庫引擎…]  。  
  
2.  在 [連接到伺服器]  對話方塊中選取 [選項 >>]  。  
  
3.  選取 **[使用自訂色彩]** 核取方塊。  
  
4.  選取 [選取...]  按鈕，可選取色彩。  
  
5.  選取基本色彩或自訂色彩，然後選取 [確定]。  
  
6.  填入其餘的連接資訊，然後選取 **[連接]** 按鈕。  
  
##  <a name="SetRegServerColor"></a> 為已註冊的伺服器設定狀態色彩  
 **為已註冊的伺服器設定伺服器色彩**  
  
1.  在 [已註冊的伺服器]  中，以滑鼠右鍵按一下伺服器節點，然後選取 [屬性…]  。  
  
2.  在 **[編輯伺服器註冊屬性]** 對話方塊上，選取 **[連接屬性]** 索引標籤。  
  
3.  選取 **[使用自訂色彩]** 核取方塊。  
  
4.  選取 [選取...]  按鈕，可選取色彩。  
  
5.  選取基本色彩或自訂色彩，然後選取 [確定]。  
  
6.  選取 **[編輯伺服器註冊屬性]** 對話方塊上的 **[儲存]** 按鈕。  
  
##  <a name="OpenServerColor"></a> 使用伺服器色彩開啟編輯器  
 **使用伺服器色彩開啟編輯器視窗**  
  
-   在 [物件總管]  或 [已註冊的伺服器]  中，以滑鼠右鍵按一下伺服器節點，然後選取 [新增查詢]  。  
  
-   或者，反白顯示伺服器節點，然後選取 **[新增查詢]** 工具列按鈕。  
  
-   編輯器視窗中的狀態列將會使用為相對應之伺服器定義的色彩。  
  
##  <a name="OpenSpecColor"></a> 開啟指定狀態色彩的編輯器  
 **開啟指定狀態色彩的編輯器視窗**  
  
-   在 **[檔案]** 功能表上，選取 **[開新檔案]** ，再選取 **[Database Engine 查詢]** 。  
  
-   在 [連接到伺服器]  對話方塊中選取 [選項 >>]  。  
  
-   選取 **[使用自訂色彩]** 核取方塊。  
  
-   選取 [選取...]  按鈕，可選取色彩。  
  
-   選取基本色彩或自訂色彩，然後選取 [確定]。  
  
-   填入其餘的連接資訊，然後選取 **[連接]** 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [查詢與文字編輯器 &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
