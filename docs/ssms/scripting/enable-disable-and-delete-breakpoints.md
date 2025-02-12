---
title: 啟用、停用以及刪除中斷點 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 357b5874-273f-43a9-8e30-83872bdea5dc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b90c950a3240d415a3792f15963ee2e3dcef35ae
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263446"
---
# <a name="enable-disable-and-delete-breakpoints"></a>啟用、停用以及刪除中斷點
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  若要檢視和管理所有已開啟的中斷點，您可以使用 **[中斷點]** 視窗。 這個視窗可用以檢視中斷點資訊，以及採取刪除、停用或啟用中斷點的這類動作。  
  
## <a name="the-breakpoints-window"></a>中斷點視窗  
 **[中斷點]** 視窗會列出一些資訊，例如中斷點所在的程式碼行。 在 **[中斷點]** 視窗中，您也可以刪除、停用和啟用中斷點。 如需有關 **[中斷點]** 視窗的詳細資訊，請參閱＜ [[中斷點] Window](../../relational-databases/scripting/transact-sql-debugger-breakpoints-window.md)＞。  
  
 停用中斷點會讓中斷點無法暫停執行，但是會將定義保留在原處，讓您可以在之後想要啟用中斷點時使用。 刪除中斷點，即會永久刪除中斷點。 您必須切換新的中斷點，以暫停陳述式的執行。  
  
## <a name="to-open-the-breakpoints-window"></a>開啟中斷點視窗  
 **To open the Breakpoints window**  
  
 您可以利用下列其中一種方式來開啟 **[中斷點]** 視窗：  
  
-   在 **[偵錯]** 功能表上，按一下 **[視窗]** ，然後按一下 **[中斷點]** 。  
  
-   在 **[偵錯]** 工具列上，按一下 **[中斷點]** 按鈕。  
  
-   按下 CTRL+ALT+B。  
  
## <a name="to-disable-a-single-breakpoint"></a>停用單一中斷點  
 **To disable a single breakpoint**  
  
 您可以使用下列其中一種方式以停用單一中斷點：  
  
-   在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [停用中斷點]  。  
  
-   在 [中斷點] 視窗中，清除中斷點左側的核取方塊。  
  
## <a name="to-disable-all-breakpoints"></a>停用所有中斷點  
 **To disable all breakpoints**  
  
 您可以使用下列其中一種方式以停用所有中斷點：  
  
-   在 **[偵錯]** 功能表上，按一下 **[停用所有中斷點]** 。  
  
-   在 **[中斷點]** 視窗的工具列上，按一下 **[停用所有中斷點]** 按鈕。  
  
## <a name="to-enable-a-single-breakpoint"></a>啟用單一中斷點  
 **To enable a single breakpoint**  
  
 您可以使用下列其中一種方式以啟用單一中斷點：  
  
-   在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [啟用中斷點]  。  
  
-   在 [中斷點] 視窗中，按一下中斷點左側的方塊。  
  
## <a name="to-enable-all-breakpoints"></a>啟用所有中斷點  
 **To enable all breakpoints**  
  
 您可以使用下列其中一種方式以啟用所有中斷點：  
  
-   在 **[偵錯]** 功能表上，按一下 **[啟用所有中斷點]** 。  
  
-   在 **[中斷點]** 視窗的工具列上，按一下 **[啟用所有中斷點]** 按鈕。  
  
## <a name="to-delete-a-single-breakpoint"></a>刪除單一中斷點  
 **To delete a single breakpoint**  
  
 您可以使用下列其中一種方式以刪除單一中斷點：  
  
-   在 [查詢編輯器] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下 [刪除中斷點]  。  
  
-   在 [中斷點] 視窗中，以滑鼠右鍵按一下中斷點，然後按一下捷徑功能表上的 [刪除]  。  
  
-   在 [中斷點] 視窗中，選取中斷點，然後按下 DELETE。  
  
## <a name="to-delete-all-breakpoints"></a>刪除所有中斷點  
 **To delete all breakpoints**  
  
 您可以使用下列其中一種方式以刪除所有中斷點：  
  
-   在 **[偵錯]** 功能表上，按一下 **[刪除所有中斷點]** 。  
  
-   在 **[中斷點]** 視窗的工具列上，按一下 **[刪除所有中斷點]** 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [切換中斷點](../../relational-databases/scripting/toggle-a-breakpoint.md)  
  
  
