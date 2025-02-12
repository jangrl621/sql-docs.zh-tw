---
title: 如何：使用結構描述比較來比較不同的資料庫定義 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.schemacompare.SchemaCompareOptionsDialog
- sql.data.tools.schemacompare.watermark.f1
- sql.data.tools.schemacompare.f1
- sql.data.tools.schemacompare.connectiondialog.f1
- sql.data.tools.schemacompare.connectiondialog.error.f1
ms.assetid: 7f0905a4-081c-46e2-bd7d-325b63e5c675
author: markingmyname
ms.author: maghan
ms.openlocfilehash: ce83808ac5953902f8f655c619f87feeffa4e8c6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68097507"
---
# <a name="how-to-use-schema-compare-to-compare-different-database-definitions"></a>如何：使用結構描述比較，比較不同的資料庫定義
SQL Server Data Tools (SSDT) 包含結構描述比較公用程式，可讓您用來比較兩項資料庫定義。  比較的來源與目標可以是下列項目的任意組合：連接的資料庫、SQL Server 資料庫專案或快照集，或是 .dacpac 檔案。  比較的結果會顯示為必須對目標採取的一組動作，以讓目標能與來源相同。  比較完成之後，您就可以直接更新目標 (若目標為專案或資料庫) 或產生具有相同效果的更新指令碼。  
  
來源與目標之間的差異會顯示在方格中以方便檢閱。  您可以由結果方格或指令碼表單中向內切入，檢閱每項差異。  接著還可選擇性地排除特定差異。  
  
您可以將個別的比較儲存成 SQL Server 資料庫專案的一部分，或儲存成單獨的檔案。  您也可以設定選項，控制比較的範圍和更新的層面。  接著透過儲存比較，您便能在日後輕鬆重複進行相同的比較，或以這次的比較做為起點來進行新的比較。  
  
下列程序將比較資料庫專案與連接的資料庫兩者的結構描述。  
  
> [!WARNING]  
> 如果指定專案做為比較目標，支援的專案最大路徑長度 (不包括磁碟機代號、冒號和前置反斜線) 為 256 個字元。 如果您的專案路徑超過 256 個字元，您仍可比較它與資料庫或其他專案的結構描述， 但是無法更新它的結構描述。  
  
> [!WARNING]  
> 下列程序利用先前在[連接的資料庫開發](../ssdt/connected-database-development.md)和[專案導向的離線資料庫開發](../ssdt/project-oriented-offline-database-development.md)小節中的程序所建立的實體。  
  
### <a name="to-compare-database-definitions"></a>若要比較資料庫定義  
  
1.  選取 [SQL]  功能表上的 [結構描述比較]  ，然後按一下 [新增結構描述比較]  。  
  
    或者，以滑鼠右鍵按一下 [方案總管]  中的 [TradeDev]  專案，再選取 [結構描述比較]  。  
  
    [結構描述比較]  視窗隨即開啟，Visual Studio 會自動為其指定 `SqlSchemaCompare1` 這類名稱。  
  
    [結構描述比較]  視窗工具列的正下方會出現兩個下拉式功能表，兩者中間有綠色箭頭。 這些功能表可讓您選取資料庫定義做為比較來源與目標。  
  
2.  在 [選取來源]  下拉式功能表中，選擇 [選取來源]  。[選取來源結構描述]  對話方塊隨即開啟。  
  
    請注意，如果您是以滑鼠右鍵按一下專案名稱來開啟 [結構描述比較]  視窗，來源結構描述便已自行填入，因此您可以繼續進行步驟 4。  
  
3.  選取 [專案]  選項按鈕，然後選取您在先前的程序中建立的 [TradeDev]  資料庫專案。  
  
4.  從 [結構描述比較]  視窗的 [選取目標]  下拉式功能表中，選擇 [選取目標]  。[選取目標結構描述]  對話方塊隨即開啟。 按一下 [結構描述]  區段中的 [資料庫]  選項按鈕，再按一下 [新增連接]  按鈕。  
  
5.  在 [連接屬性]  對話方塊中，輸入 `TradeDev` 資料庫所在的伺服器名稱，並確認提供正確的驗證認證。 接著在 [連接至資料庫]  中選取 [TradeDev]  ，然後按一下 [確定]  。  
  
    您也可以按一下 [結構描述比較]  視窗工具列上的 [選項]  按鈕，指定要比較的物件、要忽略的差異類型和其他設定。  
  
6.  按一下 [結構描述比較]  視窗工具列上的 [比較]  按鈕，開始進行比較程序。  
  
    當比較完成時，視窗上半部的 [結果]  窗格會顯示專案與資料庫之間的結構差異。 根據預設，比較結果會依動作 (例如 [刪除]、[變更] 或 [加入]) 將所有差異分組。 [結果]  窗格會為每個有不同資料庫定義的資料庫物件各顯示一列。 每一列將指出位於來源或目標結構描述 (或兩者) 中的物件，以及要讓目標物件與來源物件相同而即將對目標結構描述採取的動作。  如果某物件已重構並已重新命名或移至新的結構描述，其來源和目標名稱便有所不同，且來源名稱將顯示為粗體字型以醒目提示差異。  
  
    結果清單預設會隱藏在兩方結構描述中都相同的物件或是不支援更新的物件 (例如內建物件)。  您可以按一下工具列上適當的篩選按鈕來顯示這些物件。  
  
    若要變更群組偏好設定，請按一下工具列上的 [群組結果]  下拉式清單。  選取 [類型]  以依據物件類型 (例如，依資料表、檢視或預存程序) 將結果分組。  
  
7.  在 `Products` 群組中找到 `Tables` 資料表。 按一下該列，並注意此資料表顯示在 [物件定義]  窗格中的來源和目標定義已醒目提示差異。 您也可以展開 [結果]  窗格中的 `Products` 資料表所在當列，檢查此資料表有差異的特定元素。  
  
8.  根據預設，所有差異都會包括在 [更新目標] 動作的範圍內。 您可以排除任何不想要同步處理的差異。 若要這麼做，請取消選取每一列中央 [動作]  欄內的方塊。 或者，以滑鼠右鍵按一下 [結構描述] 窗格中的任一列，然後選取 [排除]  。 請注意，該列隨即呈現灰色。到了更新目標資料庫的時候，這一列的任何暫止變更都不會列入考慮。  
  
    您也能以滑鼠右鍵按一下某個群組列，再選取 [全部排除]  或 [全部包含]  ，這相當於取消選取或選取隸屬該群組的所有差異。 當您是依結構描述將結果分組時，即可利用此快捷方法包含或排除對特定結構描述所做的一切變更。  
  
    > [!WARNING]  
    > 如果排除的列有任何相依物件 (例如，[檢視]  列所參考的 [資料表]  列)，將會停用該排除的列，但不會清除其核取方塊。 只有取消選取相依於該列的所有各列後，才會取消選取該列。 此外，如果某一列已重構 (重新命名或移至其他結構描述)，則會停用該列及其所有相依子列的核取方塊。  
    >   
    > 請注意，如果您重新整理比較結果，那些您已選擇略過的差異將被忽略。  
  
更新目標的結構描述時可有兩種選擇。 您可以直接從 [結構描述比較]  視窗更新目標 (若目標為資料庫或專案)，或者產生更新指令碼 (若目標為資料庫或資料庫檔案)。  產生的指令碼會出現在 Transact\-SQL 編輯器中，可讓您加以檢查並對資料庫執行該指令碼。 下列程序將進一步說明這些選項。  
  
> [!WARNING]  
> 由於變更的層面涉及將某個資料行從 NOT NULL 變更為 NULL 會造成資料遺失，更新動作將失敗。 若您想要繼續執行更新，請按一下 [結構描述比較] 工具列上的 [選項]  按鈕 (左邊算起第五個按鈕)，並取消選取 [如果遺失資料，即封鎖累加部署]  選項。  
  
### <a name="to-update-directly-in-the-schema-compare-window"></a>若要直接在結構描述比較視窗中更新  
  
1.  按一下 [結構描述比較] 視窗工具列上的 [更新]  按鈕。  
  
2.  檢查產生的變更指令碼。 您可以使用 [檔案]/[新增] 功能表來儲存指令碼。 這對未獲授權無法更新生產資料庫的情況有用，在這個情況下，您可以將指令碼交給 DBA 供以後部署使用。  
  
3.  如果您有更新資料庫的必要權限，請按一下編輯窗格工具列上的 [執行查詢]  按鈕執行指令碼。  
  
### <a name="to-update-by-script"></a>若要使用指令碼更新  
  
1.  按一下 [結構描述比較] 視窗工具列上的 [產生指令碼]  按鈕 (左邊數來第四個按鈕)。  
  
    產生的指令碼會出現在新的 Transact\-SQL 編輯器視窗中  
  
    > [!WARNING]  
    > 只有由 SSDT 快照集處理序產生的 .dacpac 檔案支援此行為。  目前，由 SQL 資料層應用程式 (DAC) 工具或架構所產生的 .dacpac 檔案不能做為更新對象。  
  
2.  檢查產生的變更指令碼。 您可以使用 [檔案/儲存]  或 [檔案/另存新檔] 功能表命令來儲存指令碼。  
  
    儲存指令碼對於未獲授權無法更新生產資料庫的情況很有用。 在這個情況下，您可以將指令碼交給 DBA 供以後部署使用。  
  
    或者，您也可以將 Transact\-SQL 編輯器連接至適當的伺服器，然後再直接執行指令碼。 您必須已有建立或更新資料庫的必要權限，才能夠執行此程序。 如果您有更新資料庫的必要權限，請按一下編輯窗格工具列上的 [執行查詢]  按鈕執行指令碼。  
  
3.  按一下 [連接]  按鈕。 這個動作會將您連接至目前的伺服器，或提示您在 [連接至伺服器] 對話方塊中輸入或選取伺服器。  請注意，資料庫名稱在指令碼中定義為命令變數。  
  
4.  檢查指令碼，並視需要針對定義目標資料庫名稱和關聯的前置詞與檔案路徑的命令變數進行任何變更。  
  
5.  按一下編輯窗格工具列上的 [執行]  按鈕執行指令碼。  
  
