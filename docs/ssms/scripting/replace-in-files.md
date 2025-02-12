---
title: 檔案中取代 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Replace in Files dialog box
ms.assetid: 51191c0a-e022-41d6-8473-5cb3c6596862
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b53a95f29495388f31ca833b992f8afe3fd9450c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265976"
---
# <a name="replace-in-files"></a>檔案中取代
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [尋找和取代] 視窗的 [檔案中取代]  索引標籤，可以讓您在指定檔案集的程式碼中搜尋字串或運算式，並變更部分或所有找到的相符結果。 找到的相符結果與採取的動作會列在 [結果選項]  所選取的 [尋找結果] 視窗中。  
  
 工具列按鈕與快速鍵也可用來開啟 **[尋找和取代]** 對話方塊。  
  
## <a name="find-what"></a>尋找目標  
 [檔案中取代]  索引標籤上的這些控制項，可以讓您指定將要比對的字串或運算式。  
  
 **尋找目標**  
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
 若要以另一個字串來取代 [尋找目標]  中所指定之字串的執行個體，請在此欄位中輸入取代字串。 若要刪除 [尋找目標]  中所指定之字串的執行個體，請將此方塊保留空白。 選取下拉式清單，即可顯示最後輸入的 20 個項目。 若要將規則運算式包含在 [取代成]  方塊裡所指定的字串中，請按一下 [使用]  核取方塊，然後按一下 [規則運算式]  選項。  
  
 **運算式產生器**  
 當您在 [尋找選項]  中選取 [使用]  核取方塊時，即可使用 [取代成]  方塊旁的三角形按鈕。 按一下此按鈕，即可顯示萬用字元或規則運算式的清單，視選取的 **[使用]** 選項而定。 按一下此清單中的任何項目，將其加入 **[取代成]** 方塊中所指定的字串。  
  
 **取代**  
 按一下此按鈕，以 [取代成]  方塊中所指定的字串，取代 [尋找目標]  中所指定之字串的目前執行個體，並於 [查詢]  中所指定的範圍內尋找下一個執行個體。  
  
 **全部取代**  
 按一下此按鈕，即可在 [查詢]  所指定之範圍內的所有檔案中，以 [取代成]  方塊中所指定的字串，取代 [尋找目標]  中所指定之字串的所有執行個體。  
  
> [!CAUTION]  
>  確認 [查詢]  已設定為僅包含您要修改的那些檔案。  
  
 顯示的提醒會包含 **[保持已修改的檔案開啟]** 選項。 若要保留 **[恢復]** 選項，您必須選取此選項。 **[恢復]** 功能僅適用於檔案在修改之後仍保持開啟可供編輯的檔案。  
  
 **略過檔案**  
 當 [查詢]  包含多個檔案時才可以使用。 如果不要搜尋或修改目前的檔案，請按一下此按鈕。 搜尋會繼續在 **[查詢]** 清單中的下一個檔案進行。  
  
## <a name="look-in"></a>查詢  
 您從 [查詢]  下拉式清單中選擇的選項，可決定 [檔案中取代]  僅搜尋目前使用中的檔案，或搜尋儲存在特定資料夾中的所有檔案。 從清單中選取搜尋範圍，鍵入資料夾路徑，或按一下 [瀏覽]  按鈕以顯示 [Custom Directory Set (自訂目錄集)]  對話方塊，然後選擇一組要搜尋的資料夾。  
  
> [!NOTE]  
>  如果所選的 [查詢]  選項導致您搜尋已從原始程式碼控制簽出的檔案，則系統僅會搜尋已下載至本機電腦的檔案版本。  
  
 **Look in**  
 從清單中選取預先定義的搜尋範圍，或使用 [Custom Directory Set (自訂目錄集)]  對話方塊來輸入您自己的目錄集。  
  
 **目前的文件**  
 當文件在編輯器中開啟時，才能使用此選項。 只在使用中文件內搜尋 [尋找目標]  中所指定的字串。  
  
 **所有開啟的文件**  
 搜尋所有目前已開啟的檔案以供編輯。  
  
 **目前的專案**  
 搜尋使用中專案的所有檔案。  
  
 **整個方案**  
 搜尋使用中方案的所有檔案。  
  
 **包含子資料夾**  
 指定也要搜尋在 [查詢]  中指定之資料夾的子資料夾。 這需要自訂目錄集。  
  
 **瀏覽 (...)**  
 按一下此按鈕即可顯示 [選擇搜尋資料夾]  對話方塊，您可以在其中組合、編輯、儲存並選取目錄的命名集，以輸入到 [查詢]  方塊中。  
  
## <a name="find-options"></a>尋找選項  
 您可以展開或摺疊 **[尋找選項]** 區段。 您可以選取或清除下列選項。  
  
 **大小寫須相符**  
 如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示內容和大小寫均與 [尋找目標]  中所指定之字串相符的執行個體。 例如，選取 [大小寫須相符]  核取方塊來搜尋 **MyObject** 時，將會傳回 "MyObject"，但不會傳回 "myobject" 或 "MYOBJECT"。  
  
 **全字拼寫須相符**  
 如果選取此核取方塊，則 [尋找結果] 視窗僅會顯示整個字串與 [尋找目標]  中所指定之字串相符的執行個體。 例如，搜尋 **MyObject** ，將會傳回「MyObject」，但不會傳回「CMyObject」或「MyObjectC」。  
  
 **[使用]**  
 指出如何解譯在 [尋找目標]  或 [取代成]  文字方塊中所輸入的特殊字元。 選項包含 **[萬用字元]** 和 **[規則運算式]** 。  
  
 **[規則運算式]**  
 定義要比對之文字模式的特殊標記法。 如需清單，請參閱 [使用規則運算式搜尋文字](../../relational-databases/scripting/search-text-with-regular-expressions.md)。  
  
 **[萬用字元]**  
 例如星號 (`*`) 和問號 (`?`) 等特殊字元，代表一或多個字元。 如需清單，請參閱 [使用萬用字元搜尋文字](../../relational-databases/scripting/search-text-with-wildcards.md)。  
  
 **尋找下列檔案類型**  
 此清單指出要在 [查詢]  所指定之目錄中搜尋的檔案類型。 如果此方塊保留空白，則會搜尋 [查詢]  所指定之目錄中的所有檔案。  
  
```  
*.[ext]; *.[ext] (manual)  
```  
  
 若要尋找特定類型的檔案，請輸入星號萬用字元 (`*`) 作為檔案名稱，接著輸入半形句點 (`.`)，然後輸入副檔名。 若要尋找一個以上的檔案類型，請輸入多重搜尋字串，並以分號 (`;`) 分隔。  
  
```  
*.[ext]; *.[ext] (from list)  
```  
  
 選取清單中的任何項目，即可輸入預先設定的搜尋字串，來尋找特定類型的檔案。  
  
## <a name="result-options"></a>結果選項  
 您可以展開或摺疊 **結果選項** 區段。 您可以選取或清除下列選項。  
  
 **尋找結果 1 視窗**  
 如果選取此核取方塊，目前搜尋的結果將會附加至 [尋找結果 1] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請按一下 [檢視]  功能表上的 [其他視窗]  ，然後按一下 [尋找結果 1]  。  
  
 **尋找結果 2 視窗**  
 如果選取此核取方塊，目前搜尋的結果將會附加至 [尋找結果 2] 視窗的內容。 此視窗會自動開啟，以顯示您的搜尋結果。 若要手動開啟此視窗，請按一下 [檢視]  功能表上的 [其他視窗]  ，然後按一下 [尋找結果 2]  。  
  
 **僅顯示檔案名稱**  
 在 [尋找結果 1] 或 [尋找結果 2] 視窗中，以檔案為單位顯示包含符合搜尋條件之項目，而非顯示每一個符合搜尋條件的項目。 此選項在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中無法使用。  
  
 **全部取代後保持已修改檔案為開啟狀態**  
 如果選取，就會將有進行取代作業的所有檔案保持開啟，以便您恢復或儲存變更。 記憶體的容量可能會限制進行取代作業之後，能夠保持開啟的檔案數目。  
  
> [!CAUTION]  
>  您僅能針對仍然保持開啟以供編輯的檔案執行 [恢復]  動作。 如果沒有選取此選項，沒有開啟以供編輯的檔案將會保持關閉狀態，且該些檔案就無法使用 [恢復]  選項。  
  
## <a name="find-and-replace-views"></a>尋找和取代檢視  
 [尋找和取代] 視窗上方的索引標籤包含 [檢視]  功能表。 這些功能表可以讓您選擇要在使用中窗格裡顯示的一組欄位。 您可以讓 [尋找和取代] 視窗停駐在方便存取的位置，然後在各索引標籤之間和各檢視之間變更，以執行任何類型的尋找或取代作業。  
  
 **切換至快速尋找**  
 此工具列索引標籤會將對話方塊變更為 [快速尋找]  對話方塊。  
  
 **切換至檔案中尋找**  
 此工具列索引標籤會將對話方塊變更為 [檔案中尋找]  對話方塊。  
  
 **切換至尋找符號**  
 此工具列索引標籤會將對話方塊變更為 [Find in Symbols (符號中尋找)]  對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Management Studio 鍵盤快速鍵](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)  
