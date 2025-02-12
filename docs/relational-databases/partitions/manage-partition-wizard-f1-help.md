---
title: 管理資料分割精靈 F1 說明 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
f1_keywords:
- sql13.swb.managepartition.createjob.f1
- sql13.swb.managepartition.progress.f1
- sql13.swb.managepartition.getstart.f1
- sql13.swb.managepartition.selectswitchtables.f1
- sql13.swb.managepartition.stagingtable.f1
- sql13.swb.managepartition.switchin.f1
- sql13.swb.managepartition.switchout.f1
- sql13.swb.managepartition.partitionaction.f1
- sql13.swb.managepartition.summary.f1
- sql13.swb.managepartition.selectoutput.f1
helpviewer_keywords:
- wizards [SQL Server Management Studio] See Manage Partition Wizard
ms.assetid: e2478d26-dea4-428d-98c5-aad2d2a30da8
author: julieMSFT
ms.author: jrasnick
ms.openlocfilehash: b921ed801297659b02a8f8cb2d22dcf1b498502e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68024895"
---
# <a name="manage-partition-wizard-f1-help"></a>管理資料分割精靈 F1 說明
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  使用 [管理資料分割精靈]  ，即可透過資料分割切換或滑動視窗案例的實作，管理和修改現有的資料分割資料表。 這個精靈可以讓資料分割的管理更方便，並且簡化將資料移轉入和移轉出資料表的一般作業。  
  
### <a name="to-start-the-manage-partition-wizard"></a>啟動管理資料分割精靈  
  
-   在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，選取資料庫、以滑鼠右鍵按一下您想要建立資料分割的資料表、指向 [儲存體]  ，然後按一下 [管理資料分割]  。  
  
     **注意**：如果 [管理資料分割]  無法使用，表示您可能選取了不包含資料分割的資料表。 請在 [儲存體]  子功能表中按一下 [建立資料分割]  ，然後使用 [建立資料分割精靈]  來建立資料表的資料分割。  
  
 如需資料分割和索引的一般資訊，請參閱[分割資料表與索引](../../relational-databases/partitions/partitioned-tables-and-indexes.md)。  
  
 本節提供使用 [管理資料分割精靈]  來管理、修改和實作資料分割的必要資訊。  
  
##  <a name="Top"></a> 本節內容  
 下列章節提供有關 [管理資料分割精靈]  頁面的說明。  
  
 [管理資料分割精靈 (選取資料分割動作頁面)](#SelectPartitionAction)  
  
 [管理資料分割精靈 (切換移入頁面)](#SwitchIn)  
  
 [管理資料分割精靈 (切換移出頁面)](#SwitchOut)  
  
 [管理資料分割精靈 (選取臨時資料表選項頁面)](#StagingTableOptions)  
  
 [管理資料分割精靈 (選取輸出選項頁面)](#OutputOption)  
  
 [管理資料分割精靈 (新增作業排程頁面)](#NewJob)  
  
 [管理資料分割精靈 (摘要頁面)](#Summary)  
  
 [管理資料分割精靈 (進度頁面)](#Progress)  
  
##  <a name="SelectPartitionAction"></a> 選取資料分割動作頁面  
 使用 [選取資料分割動作]  頁面，即可選擇您想要針對資料分割執行的動作。  
  
### <a name="create-a-staging-table"></a>建立臨時資料表  
 如果您擁有一份定期移轉入或移轉出資料的資料分割資料表，資料分割切換就是常見的資料分割工作。例如，您擁有一份儲存每季最新資料的資料分割資料表，而且您必須在每季結束時移入新資料並封存舊資料。  
  
 此精靈會使用相同的分割資料行、資料表與資料行結構和索引來設計臨時資料表，並且將新的資料表儲存在來源資料分割所在的檔案群組中。  
  
 若要建立切換移入或切換移出資料分割資料的臨時資料表，請選取 [建立用於切換資料分割的暫存資料表]  。  
  
### <a name="sliding-window-scenario"></a>滑動視窗案例  
 若要以滑動視窗案例管理資料分割，請選取 [以滑動視窗案例管理分割資料]  。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **建立用於切換資料分割的臨時資料表**  
 針對您要切換移入或切換移出現有資料分割資料表的資料建立臨時資料表。  
  
 **切換移出資料分割**  
 提供從資料表中移除資料分割時的選項。  
  
 **切換移入資料分割**  
 提供在資料表中加入資料分割時的選項。  
  
 **以滑動視窗案例管理分割資料**  
 將空白的資料分割附加至可用於切換移入資料的現有資料表。 此精靈目前支援切換移入最後一個資料分割以及切換移出第一個資料分割。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="SwitchIn"></a> 選取資料分割切換移入選項頁面  
 使用 [選取資料分割切換移入選項]  頁面，選取您想要切換移入資料分割資料表的暫存資料表。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **顯示所有資料分割**  
 選取此選項可顯示所有資料分割，包括目前在資料分割資料表中的資料分割。  
  
 **資料分割方格**  
 顯示您所選取之資料分割的資料分割名稱、[左界限]  、[右界限]  、[檔案群組]  和 [資料列計數]  。  
  
 **切換移入資料表**  
 選取包含了您想要加入至資料分割資料表之資料分割的臨時資料表。 您必須先建立此暫存資料表，然後才能使用 [管理資料分割精靈]  來切換移入資料分割。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="SwitchOut"></a> 選取資料分割切換移出選項頁面  
 使用 [選取資料分割切換移出選項]  頁面，選取資料分割和暫存資料表來保存您想要切換移出資料分割資料表的分割資料。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **資料分割方格**  
 顯示您所選取之資料分割的資料分割名稱、[左界限]  、[右界限]  、[檔案群組]  和 [資料列計數]  。  
  
 **切換移出資料表**  
 選擇要將資料切換移出到其中的新資料表或是現有資料表。  
  
 **新增**  
 針對您想要用來讓資料分割切換移出目前來源資料表的臨時資料表輸入新的名稱。  
  
 **現有的**  
 選取您想要用來讓資料分割切換移出目前來源資料表的現有臨時資料表。 如果現有的資料表含有資料，您切換移出的資料就會覆寫這項資料。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="StagingTableOptions"></a> 選取暫存資料表選項頁面  
 使用 [選取暫存資料表選項]  頁面，即可建立您想要用來切換分割資料的暫存資料表。  
  
 臨時資料表必須與來源資料表所在的選取資料分割位於相同的檔案群組中。 臨時資料表必須鏡像來源資料表和目的地資料表的設計。  
  
 您也可以在臨時資料表中建立存在來源資料分割內的相同索引。 臨時資料表會自動包含以來源資料分割元素為基礎的條件約束。 這個條件約束通常是根據來源資料分割的界限值產生。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **臨時資料表名稱**  
 為臨時資料表建立名稱，或接受顯示在編輯方塊中的預設名稱。  
  
 **切換資料分割**  
 選取您想要切換移出目前資料表的來源資料分割。  
  
 **新界限值**  
 選取或輸入您想要用於臨時資料表之資料分割的界限值。  
  
 **檔案群組**  
 為新的資料表選取檔案群組。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="OutputOption"></a> 選取輸出選項頁面  
 使用 [選取輸出選項]  頁面，指定要如何完成資料分割修改。  
  
### <a name="create-script"></a>建立指令碼  
 當精靈完成時，它會在查詢編輯器中建立指令碼，以便修改資料表中的資料分割。 如果您想要檢閱此指令碼，然後手動執行指令碼，請選取 [建立指令碼]  。  
  
 **編寫指令碼至檔案**  
 產生指令碼至 .sql 檔案。 指定 [Unicode]  或 [ANSI 文字]  。 若要指定檔案的名稱和位置，請按一下 [瀏覽]  。  
  
 **編寫指令碼至剪貼簿**  
 將指令碼儲存至剪貼簿。  
  
 **編寫指令碼至新增查詢視窗**  
 產生指令碼至 [查詢編輯器] 視窗。 如果未開啟編輯器視窗，就會開啟新編輯器視窗做為指令碼的目標。  
  
### <a name="run-immediately"></a>立即執行  
 **Run immediately**  
 當您按 [下一步]  或 [完成]  時，讓精靈完成對資料分割所做的修改。  
  
### <a name="schedule"></a>[排程]  
 選取此選項即可在排程的日期和時間修改資料表資料分割。  
  
 **變更排程**  
 開啟 [新增作業排程]  對話方塊，以便選取、變更或檢視排程作業的屬性。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="NewJob"></a> 新增作業排程頁面  
 使用 [新增作業排程]  頁面，即可檢視和變更排程的屬性。  
  
### <a name="options"></a>選項。  
 選取您想要用於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業的排程類型。  
  
 **名稱**  
 輸入排程的新名稱。  
  
 **排程中的作業**  
 檢視使用此排程的現有作業。  
  
 **排程類型**  
 選取排程類型。  
  
 **已啟用**  
 啟用或停用排程。  
  
### <a name="recurring-schedule-types-options"></a>重複執行排程類型選項  
 選取排程作業的頻率。  
  
 **發生於**  
 選取排程重複執行的間隔。  
  
 **重複頻率**  
 選取排程重複執行間隔的日數或週數。 每月排程無法使用這個選項。  
  
 **星期一**  
 設定作業於星期一發生。 只有每週排程可以使用。  
  
 **星期二**  
 設定作業於星期二發生。 只有每週排程可以使用。  
  
 **星期三**  
 設定作業於星期三發生。 只有每週排程可以使用。  
  
 **星期四**  
 設定作業於星期四發生。 只有每週排程可以使用。  
  
 **星期五**  
 設定作業於星期五發生。 只有每週排程可以使用。  
  
 **星期六**  
 設定作業於星期六發生。 只有每週排程可以使用。  
  
 **星期日**  
 設定作業於星期日發生。 只有每週排程可以使用。  
  
 **Day**  
 請選取排程每月在哪一日發生。 只有每月排程可以使用。  
  
 **重複間隔**  
 請選取排程出現間隔的月數。 只有每月排程可以使用。  
  
 **星期**  
 指定排程，選擇月份中特定週數的特定星期幾。 只有每月排程可以使用。  
  
 **執行一次於**  
 請設定作業每日發生的時間。  
  
 **發生間隔**  
 設定每隔幾個小時或幾分鐘發生一次。  
  
 **開始日期**  
 請設定這個排程開始有效的日期。  
  
 **結束日期**  
 請設定排程將不再有效的日期。  
  
 **沒有結束日期**  
 請指定排程將無限期地保持有效。  
  
### <a name="one-time-schedule-types-options"></a>僅執行一次的排程類型選項  
 如果您將作業排程為僅執行一次，就必須選取未來的日期和時間。  
  
 **日期**  
 選取作業要執行的日期。  
  
 **Time**  
 選取作業要執行的時間。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="Summary"></a> 摘要頁面  
 使用 [摘要]  頁面，即可檢閱您在先前頁面中選取的選項。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **檢閱您的選取項目**  
 針對精靈的每一頁，顯示您所選取的項目。 按一下節點即可展開並檢視您先前選取的選項。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
##  <a name="Progress"></a> 進度頁面  
 使用 [進度]  頁面，即可監視有關 [管理資料分割精靈]  動作的狀態資訊。 根據您在精靈中選取的選項，[進度]  頁面可能會包含一或多個動作。 頂端的方塊會顯示精靈的整體狀態以及精靈已接收的狀態、錯誤和警告訊息數。  
  
### <a name="options"></a>選項。  
 **詳細資料**  
 提供從精靈所採取的動作傳回的動作、狀態和任何訊息。  
  
 **動作**  
 指定每個動作的類型和名稱。  
  
 **狀態**  
 指出整個精靈動作傳回 [成功]  或 [失敗]  的值。  
  
 **訊息**  
 提供從程序所傳回的任何錯誤或警告訊息。  
  
 **停止**  
 停止精靈的動作。  
  
 **報表**  
 建立包含 [管理資料分割精靈]  結果的報表。 選項包括：  
  
-   **檢視報表**  
  
-   **將報表儲存到檔案**  
  
-   **複製報表到剪貼簿**  
  
-   **以電子郵件傳送報表**  
  
 **檢視報表**  
 開啟 [檢視報表]  對話方塊。 這個對話方塊包含 [管理資料分割精靈]  進度的文字報表。  
  
 **關閉**  
 關閉精靈。  
  
 ![搭配 [回到頁首] 連結使用的箭號圖示](../../analysis-services/instances/media/uparrow16x16.gif "搭配 [回到頁首] 連結使用的箭號圖示") [本節內容](#Top)  
  
## <a name="see-also"></a>另請參閱  
 [分割資料表與索引](../../relational-databases/partitions/partitioned-tables-and-indexes.md)  
  
  
