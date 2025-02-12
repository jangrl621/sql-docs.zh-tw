---
title: 管理書籤 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [SQL Server Management Studio]
ms.assetid: 67cc3fd6-3238-4c58-a3ec-2d3b0438143a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 35816b3e50a49cd729ff31950bd219681dfda0fa
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265416"
---
# <a name="manage-bookmarks"></a>管理書籤
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  使用程式碼編輯器時，[書籤]  視窗可讓您建立連結至文件內之程式碼的特定行。 您可以從 [檢視]  功能表顯示這個視窗。  
  
 若要建立和巡覽整個書籤，請按一下位於 [文字編輯器]  工具列上和 [書籤]  視窗上方的按鈕。 您可加入和刪除書籤、啟動或停用書籤以及將書籤組織到資料夾中。 [書籤]  視窗的捷徑功能表中，也有一些可用的特定命令。 若要加入或移除書籤，請將插入點放在適用的編輯器行上，然後按一下 [切換書籤]  。 若要啟用書籤，請在 [書籤]  視窗中選取其核取方塊；若要停用 (而非移除) 書籤，則請清除其核取方塊。  
  
## <a name="text-editor-toolbar"></a>文字編輯器工具列  
 在編輯器中開啟文字文件時，會啟用 [文字編輯器]  工具列的下列按鈕。 在使用查詢編輯器時，若要顯示 [文字編輯器]  工具列，請在 [檢視]  功能表上指向 [工具列]  ，然後按一下 [文字編輯器]  。  
  
 **在目前的行上切換書籤**  
 在使用中的編輯器內，於文件的選取行上加入或移除書籤。 這不會改變有書籤的程式碼行。  
  
 **將插入號移動到前一個書籤**  
 請選取在 [書籤]  視窗中已啟用的上一個書籤。 當已到達第一個書籤時，將向前跳至最後一個。 視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。 捲動該文件至有書籤的行，然後將插入點加入該處。  
  
 **移動插入號到下一個書籤**  
 請選取在 [書籤]  視窗中已啟用的下一個書籤。 當已到達最後一個書籤時，將向後跳回至第一個。 視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。 捲動該文件至有書籤的行，然後將插入點加入該處。  
  
 **清除目前文件中所有的書籤**  
 顯示確認訊息，然後移除使用中文件的所有書籤。 這不會移除有書籤的程式碼行。  
  
> [!CAUTION]  
>  您無法恢復此程序。 之後，您必須使用 [在目前這一行切換書籤]  建立新書籤。 若要停用書籤但不將它們移除，請在 [書籤]  視窗中清除其核取方塊。  
  
## <a name="bookmarks-window"></a>書籤視窗  
 若要組織書籤，請在 [書籤]  視窗中建立書籤資料夾。 拖放書籤到資料夾中。 下列按鈕可以在 [書籤]  視窗的上方找到。  
  
 **在目前的行上切換書籤。**  
 在使用中的編輯器內，於文件的選取行上加入或移除書籤。 這不會改變有書籤的程式碼行。  
  
 **新增資料夾**  
 加入資料夾到 [書籤]  視窗。  
  
> [!TIP]  
>  在冗長的程式碼檔案中，將書籤組織至與工作相關的資料夾中是有幫助的。 選取資料夾，啟用 [移至資料夾中上一個書籤]  和 [移至資料夾下一個書籤]  按鈕。  
  
 **將插入號移動到前一個書籤**  
 請選取在 [書籤]  視窗中已啟用的上一個書籤。 當已到達第一個書籤時，將向前跳至最後一個。 視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。 捲動該文件至有書籤的行，然後將插入點加入該處。  
  
 **移動插入號到下一個書籤**  
 請選取在 [書籤]  視窗中已啟用的下一個書籤。 當已到達最後一個書籤時，將向後跳回至第一個。 視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。 捲動該文件至有書籤的行，然後將插入點加入該處。  
  
 **將插入號移動到目前資料夾中的前一個書籤**  
 選取在 [書籤]  視窗中，於同一資料夾內啟用的上一個書籤。 當已到達第一個書籤時，將向前跳至資料夾中的最後一個。 視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。 捲動該文件至有書籤的行，然後將插入點加入該處。  
  
 **將插入號移動到目前資料夾中的下一個書籤**  
 選取在 [書籤]  視窗中，於同一資料夾內啟用的下一個書籤。 當已到達第一個書籤時，將向後跳至資料夾中的第一個。 視需要而定，將於選取的書籤在編輯器中出現之處開啟檔案。 捲動該文件至有書籤的行，然後將插入點加入該處。  
  
 **停用/啟用所有書籤**  
 在 [書籤]  視窗中，清除或啟用所有書籤的核取方塊。 這不會移除書籤，或改變它們標示的程式碼行。  
  
 **刪除**  
 從 [書籤]  視窗以及書籤所出現的文件中，移除目前選取的書籤。 這不會移除有書籤的程式碼行。  
  
 書籤核取方塊  
 每個書籤都有自己的核取方塊。 若要啟用現有的書籤，請在 [書籤]  視窗中選取其核取方塊。 若要隱藏 (但不移除) 現有的書籤，請在 [書籤]  視窗中清除其核取方塊。  
  
## <a name="bookmarks-window-shortcut-menu"></a>書籤視窗快速鍵功能表  
 以滑鼠右鍵按一下 [書籤]  視窗中的項目時，可從捷徑功能表使用下列命令。  
  
 **刪除**  
 從 [書籤]  視窗以及書籤所出現的文件中，移除目前選取的書籤。 這不會移除有書籤的程式碼行。  
  
 **Rename**  
 允許您指派新的顯示名稱給書籤或資料夾。  
  
 **停用/啟用書籤**  
 在 [書籤]  視窗中，清除或啟用所選取書籤的核取方塊。 這不會移除書籤，或改變其標示的程式碼行。  
  
 **停用/啟用所有書籤**  
 在 [書籤]  視窗中，清除或啟用所有書籤的核取方塊。 這不會移除書籤，或改變它們標示的程式碼行。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Management Studio 鍵盤快速鍵](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)  
