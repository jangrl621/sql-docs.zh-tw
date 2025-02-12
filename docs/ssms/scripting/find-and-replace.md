---
title: 尋找和取代 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Find and Replace dialog box
ms.assetid: 09297893-d80b-4c88-86b4-52bfb639e521
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f8ddfadb13d2c1882b0c489f8e0567ea26dd2165
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265514"
---
# <a name="find-and-replace"></a>尋找和取代
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  使用 **[尋找和取代]** 對話方塊尋找檔案內的文字，並選擇性地取代。 **[尋找和取代]** 對話方塊的版本不同，選項也會有些微差異，視對話方塊以何種方式開啟而定。 在 **[編輯]** 功能表上，指向 **[尋找和取代]** ，然後按一下 **[快速尋找]** 以開啟有尋找選項，但沒有取代選項的對話方塊。 在 **[編輯]** 功能表上，指向 **[尋找和取代]** ，然後按一下 **[快速取代]** 以開啟同時具有尋找和取代選項的對話方塊。  
  
 工具列按鈕與快速鍵也可用來開啟 **[尋找和取代]** 對話方塊。  
  
## <a name="find-what"></a>尋找目標  
 這些控制項可以讓您指定符合的字串或運算式。  
  
 **Find what**  
 鍵入要搜尋的文字。 對話方塊會使用在開啟對話方塊之前，資料指標所選取的文字、鄰近的文字，或先前搜尋過的文字，嘗試填入可能要搜尋的文字。 您可以重複使用最後 20 個搜尋字串的其中之一，方法是從此下拉式清單中選取。  
  
 **[具有萬用字元的字串]**  
 如果您要在搜尋字串中，使用如星號 (`*`) 和問號 (`?`) 等的萬用字元，請選取 [尋找選項]  下的 [使用]  核取方塊，然後按一下 [萬用字元]  。  
  
 **[規則運算式]**  
 若要讓搜尋引擎將搜尋字串解譯為規則運算式，請選取 [尋找選項]  下的 [使用]  核取方塊，然後按一下 [規則運算式]  。  
  
 **運算式產生器**  
 當您在 [尋找選項]  中選取 [使用]  核取方塊時，即可使用 [尋找目標]  方塊旁的三角形按鈕。 按一下此按鈕，即可顯示萬用字元或規則運算式的清單，視選取的 **[使用]** 選項而定。 在此清單中選擇任何項目，會加入 **[尋找目標]** 方塊中所指定的字串。  
  
## <a name="replace-with"></a>取代成  
 這些控制項可以讓您指定要插入的字串，以取代相符的字串或運算式。  
  
 **Replace with**  
 若要以另一個字串來取代 [尋找目標]  中所指定之字串的執行個體，請在此欄位中輸入取代字串。 若要刪除 **[尋找目標]** 中所指定之文字的執行個體，請保留此欄位空白。 選取下拉式清單，即可顯示最後輸入的 20 個項目。 若要將規則運算式包含在 **[取代成]** 方塊裡所指定的字串中，請按一下 **[使用]** 核取方塊，然後按一下 **[規則運算式]** 。 只有透過按一下 **[快速取代]** 的方式開啟此對話方塊，才會出現此方塊。  
  
 **Replace with**  
 若要以另一個字串來取代 [尋找目標]  方塊中所指定之字串的執行個體，請在此欄位中輸入取代字串。 若要刪除 **[尋找目標]** 方塊中所指定之字串的執行個體，請保留此欄位空白。 選取下拉式清單，即可顯示最後輸入的 20 個項目。 若要將規則運算式包含在 **[取代成]** 方塊裡所指定的字串中，請按一下 **[使用]** 核取方塊，然後按一下 **[規則運算式]** 。  
  
 **運算式產生器**  
 當您在 [尋找選項]  中選取 [使用]  核取方塊時，即可使用 [取代成]  方塊旁的三角形按鈕。 按一下此按鈕，即可顯示萬用字元或規則運算式的清單，視選取的 **[使用]** 選項而定。 按一下此清單中的任何項目，將其加入 **[取代成]** 方塊中所指定的字串。  
  
 **取代**  
 按一下此按鈕，以 [取代成]  方塊中所指定的字串，取代 [尋找目標]  方塊中所指定之字串的目前執行個體，並於 [查詢]  中所指定的範圍內尋找下一個執行個體。  
  
 **全部取代**  
 按一下此按鈕，即可在 [查詢]  方塊中所指定之範圍內的所有檔案中，以 [取代成]  方塊中所指定的字串，取代 [尋找目標]  方塊中所指定之字串的所有執行個體。  
  
> [!CAUTION]  
>  確定 [查詢]  已設定為僅包含您要修改的那些檔案。  
  
 顯示的提醒會包含 **[保持已修改的檔案開啟]** 選項。 若要保留 **[恢復]** 選項，您必須選取此選項。 **[恢復]** 功能僅適用於檔案在修改之後仍保持開啟可供編輯的檔案。  
  
 **略過檔案**  
 當 [查詢]  所指定的值包含多個檔案時，即可使用。 如果不要搜尋或修改目前的檔案，請按一下此按鈕。 搜尋會繼續在 **[查詢]** 清單中的下一個檔案進行。  
  
## <a name="look-in"></a>查詢  
 **Look in**  
 選取位置以尋找 [尋找目標]  中指定的文字。 選項包括 **[目前的文件]** ，這會搜尋開啟對話方塊時的焦點文件視窗；以及 **[所有開啟的文件]** ，就會搜尋目前在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中開啟的所有文件視窗。  
  
## <a name="find-options"></a>[使用]  
 您可以展開或摺疊 **[尋找選項]** 區段。 您可以選取或清除下列選項。  
  
 **大小寫須相符**  
 如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示內容和大小寫均與 [尋找目標]  中所指定之字串相符的執行個體。 例如，選取 **[大小寫須相符]** 核取方塊來搜尋「 **MyObject** 」，將會傳回「MyObject」，但不會傳回「myobject」或「MYOBJECT」。  
  
 **全字拼寫須相符**  
 如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示整個字串與 [尋找目標]  中所指定之字串相符的執行個體。 例如，搜尋 **MyObject** ，將會傳回「MyObject」，但不會傳回「CMyObject」或「MyObjectC」。  
  
 **向上搜尋**  
 從游標位置朝文件開始處進行搜尋。  
  
 **搜尋隱藏文字**  
 找出隱藏和摺疊文字的執行個體。  
  
 **[使用]**  
 指出如何解譯在 [尋找目標]  或 [取代成]  文字方塊中所輸入的特殊字元。 選項包含 **[萬用字元]** 和 **[規則運算式]** 。  
  
 **[規則運算式]**  
 定義要比對之文字模式的特殊標記法。 如需清單，請參閱 [使用規則運算式搜尋文字](../../relational-databases/scripting/search-text-with-regular-expressions.md)。  
  
 **[萬用字元]**  
 例如星號 (`*`) 和問號 (`?`) 等特殊字元，代表一或多個字元。 如需清單，請參閱 [使用萬用字元搜尋文字](../../relational-databases/scripting/search-text-with-wildcards.md)。  
  
 **找下一個**  
 開始在 [尋找目標]  方塊中搜尋文字。  
  
 **取代**  
 按一下此按鈕，以 [取代成]  中所指定的字串，取代 [尋找目標]  中所指定之字串的目前執行個體，並於 [查詢]  中所指定的範圍內尋找下一個執行個體。  
  
 **Replace All**  
 選擇此按鈕，即可在 [查詢]  中所指定之範圍內的所有檔案中，以 [取代成]  中所指定的字串，取代 [尋找目標]  中所指定之字串的所有執行個體。  
  
> [!CAUTION]  
>  確定 [查詢]  已設定為僅包含您要修改的那些檔案。  
  
## <a name="find-and-replace-views"></a>尋找和取代檢視  
 [尋找和檢視] 視窗上方的索引標籤包含 **[檢視]** 功能表。 這些功能表可以讓您選擇要在使用中窗格裡顯示的一組欄位。 您可以讓 **[尋找和取代]** 視窗停駐在方便存取的位置，然後在各索引標籤之間和各檢視之間進行變更，以執行任何類型的尋找或取代作業。  
  
 **[快速尋找]**  
 此工具列索引標籤會將對話方塊變更為 [快速尋找]  對話方塊。  
  
 **檔案中尋找**  
 此工具列索引標籤會將對話方塊變更為 [檔案中尋找]  對話方塊。  
  
 **[快速取代]**  
 此工具列索引標籤會將對話方塊變更為 [快速取代]  對話方塊  
  
 **檔案中取代**  
 此工具列索引標籤會將對話方塊變更為 [檔案中取代]  對話方塊  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Management Studio 鍵盤快速鍵](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)  
