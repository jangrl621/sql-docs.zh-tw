---
title: 選項 (環境 - 字型和色彩頁面) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea3aa222-538d-485f-99dc-01eb02cdcfea
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 7270a67f9f040f986b58ee0bb9d0d5366fe05169
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265947"
---
# <a name="options-environment---fonts-and-colors-page"></a>選項 (環境 - 字型和色彩頁面)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[選項]  對話方塊讓您能夠針對 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的各種使用者介面元素，來建立自訂的字型和色彩配置。 在 [工具]  功能表上按一下 [選項]  、展開 [環境]  資料夾，然後選取 [字型和色彩]  。  
  
在對色彩配置進行變更的工作階段中，色彩配置的變更並不會生效。 您可以開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的其他執行個體，並產生您希望套用變更的條件，來評估色彩變更。  
  
## <a name="uielement-list"></a>UIElement 清單  
**顯示設定**  
列出您可以變更字型和色彩配置的所有使用者介面元素。 從此清單中選取了項目之後，您可以自訂 [顯示項目]  中所選之項目的色彩設定。  
  
|詞彙|定義|  
|--------|--------------|  
|文字編輯器|變更文字編輯器的字型樣式、大小，以及色彩顯示設定，會影響預設文字編輯器裡文字的外觀。 這些設定並不會影響文字編輯器在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的外部所開啟的文件。|  
|印表機|變更印表機的字型樣式、大小，以及色彩顯示設定，會影響列印文件裡文字的外觀。<br /><br />注意：您可以針對列印目的選取不同於文字編輯器所顯示字型的預設字型。 當列印同時包含單一位元組和雙位元組字元的程式碼時，這就非常有用。|  
|[所有文字工具視窗] |變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中有輸出窗格之工具視窗裡文字的外觀。 例如，[輸出] 視窗、[文字結果] 視窗等等。<br /><br />注意:對 [所有文字工具視窗] 項目的文字所做的變更，在您進行變更的工作階段中並不會生效。 您可以開啟 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的其他執行個體，來評估這些變更。|  
|尋找結果視窗|變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [尋找結果] 視窗裡文字的外觀。|  
|輸出視窗|變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [輸出] 視窗裡文字的外觀。|  
|方格結果|變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [查詢] 視窗的 [方格結果]  區域裡文字的外觀。|  
|執行計畫|變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 查詢之執行計畫裡文字的外觀。|  
|文字結果|變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [查詢] 視窗之 [文字結果]  區域裡文字的外觀。|  
|商業智慧設計師|變更此項目的字型樣式、大小，以及色彩顯示設定，會影響 [商務智慧設計師] 視窗裡文字的外觀。|  
  
**使用預設值**  
[使用預設值]  按鈕會重設預設字型的值，以及從 [顯示設定]  清單中選取之清單項目的色彩值。  
  
**字型 (粗體字表示固定寬度的字型)**  
列出系統上安裝的所有字型。 在第一次開啟此下拉式清單時，會選取您從 [顯示設定]  清單中選擇之元素的目前字型。 固定字型 (在編輯器中較易於對齊) 以粗體顯示。  
  
**大小**  
列出選取之字型的可用大小。 變更字型的大小會影響 [顯示設定]  選取項目的所有 [顯示項目]  項目。  
  
**顯示項目**  
列出您可以修改前景和背景色彩的項目。  
  
> [!NOTE]  
>  預設的顯示項目是文字。 如此一來，指派給其他顯示項目的屬性就會覆寫指派給文字的屬性。 例如，如果您指派藍色給 **文字** ，且指派綠色給識別碼，則所有識別碼都會以綠色顯示。 在此範例中，識別碼屬性會覆寫文字屬性。  
  
某些顯示項目包含：  
  
-   指示區邊界：位於程式碼編輯器的左邊，顯示中斷點和書籤圖示的邊界。  
  
-   可摺疊的文字：在程式碼編輯器內，可以切換顯示與否的文字或程式碼區塊 (僅限 XML)。  
  
**項目前景**  
列出您可以選擇作為 [顯示項目]  中所選取項目之前景的可用色彩。 因為有些項目相關，所以應維護一致的顯示配置；例如，變更文字的前景色彩也會變更如 String 等元素的前景色彩。  
  
**Custom**  
顯示 [色彩]  對話方塊，您可以在此為 [顯示項目]  清單中所選取的項目，設定自訂色彩。  
  
> [!NOTE]  
> 電腦顯示器的色彩設定可能會限制您定義自訂色彩的能力。 例如，如果電腦設定為顯示 256 色，且您從 [色彩]  對話方塊中選取自訂色彩，則 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會選擇 [基本色彩]  中最接近可用的值作為預設值，並在 [色彩]  對話方塊中顯示黑色。  
  
**項目背景**  
提供了色彩調色盤，而您可以從中選擇 [顯示項目]  中所選取項目的背景色彩。 因為有些項目相關，所以應維護一致的顯示配置；例如，變更文字的背景色彩也會變更如 SQL String 等元素的背景色彩。  
  
**Custom**  
顯示 [色彩]  對話方塊，您可以在此為 [顯示項目]  清單中所選取的項目，設定自訂色彩。  
  
**粗體字**  
選取此核取方塊，即可以粗體字型來顯示選取之 [顯示項目] 的文字。 在編輯器中粗體文字較易於識別。  
  
**範例**  
針對 [顯示設定]  和 [顯示項目]  中的選取值，顯示字型樣式、大小，以及色彩配置的範例。 嘗試使用不同的格式化選項時，您可以使用此文字方塊來預覽結果。  
  
## <a name="see-also"></a>另請參閱  
[程式碼編輯器中的色彩編碼](../../relational-databases/scripting/color-coding-in-query-editors.md)  
[選項 (文字編輯器/編輯器索引標籤和狀態列頁面)](https://msdn.microsoft.com/e4815678-7885-4631-878f-c6a2b857ee05)  
  
