---
title: 使用參考資料庫中的資料比較和同步處理一個或多個資料表中的資料 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 96d743b0-b69a-45bb-ae0e-62103dca76e2
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 055731473f94003440f4a78c6446ec965f1d0a2f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984672"
---
# <a name="compare-and-synchronize-data-in-one-or-more-tables-with-data-in-a-reference-database"></a>使用參考資料庫中的資料比較和同步處理一個或多個資料表中的資料
您可以比較「來源」  資料庫與「目標」  資料庫的資料，以及指定應該比較的資料表。 您可以檢閱資料並決定要同步處理哪些變更。 然後您可以更新目標來同步處理資料庫，也可以將更新指令碼匯出至 Transact\-SQL 編輯器或檔案。  
  
例如，您可以使用生產資料副本來更新開發用伺服器，同步處理資料庫。 您也可以使用其他資料庫的資料填入資料表，同步處理一個或多個資料表。 此外，在執行測試之前或之後，您可以比較資料，當做其他形式的驗證。  
  
您可以比較兩個資料庫的資料，但是無法指定比較資料庫專案檔或 .dacpac，因為它不包含資料。  
  
本節包含下列主題：  
  
-   [操作說明：比較和同步處理兩個資料庫的資料](../ssdt/how-to-compare-and-synchronize-the-data-of-two-databases.md)  
  
-   [操作說明：檢視資料差異](../ssdt/how-to-view-data-differences.md)  
  
## <a name="requirements"></a>需求  
當您比較資料表或檢視表的資料時，來源資料庫的資料表或檢視表必須與目標資料庫的資料表或檢視表共用數個屬性。 不符合下列條件的資料表和檢視不會比較，也不會出現在 [新增資料比較]  精靈的第二個頁面：  
  
-   資料表必須有相容資料型別的相符資料行名稱。  
  
    資料表、檢視表和擁有者名稱會區分大小寫。  
  
-   資料表必須有相同的主索引鍵、唯一索引或唯一的條件約束。  
  
-   檢視表必須有相同、唯一的叢集索引。  
  
-   只有在名稱相同時，才可以比較資料表與檢視表。  
  
每個物件都具有決定與其對應之其他物件的索引鍵或索引。 不過，每個資料表或檢視表可以有多個主索引鍵、唯一索引或唯一的條件約束。 因此，您可能需要指定要使用的索引鍵、索引或條件約束。  
  
## <a name="common-tasks"></a>一般工作  
在本節中，您可以找到支援此狀況的一般工作描述。  
  
**設定選項以控制比較資料的方式：** 當您比較資料時，可以安全地忽略識別欄位，停用觸發和停用外部索引鍵。 您也可以從更新指令碼卸除主索引鍵、索引和唯一的條件約束。  
  
**比較資料表中的資料並選擇性地更新目標以符合來源：** 在指定要比較的來源和目標資料庫並執行比較之後，您可以在 [資料比較]  視窗中檢視結果。 您不只可以檢視差異的詳細資料，也可以檢視用來同步處理資料的更新指令碼。 在您識別兩個資料庫之間的差異之後，可以針對每個差異指定動作。 然後您可以更新目標，也可以將更新指令碼匯出至 Transact\-SQL 編輯器或檔案。 您可以匯出此指令碼，以便您或其他人在套用變更之前可以檢閱它。  
  
## <a name="UnderstandingDataCompareResults"></a>了解比較結果  
下表描述 [資料比較]  視窗的五個資料行。  
  
|「資料行」|注意|  
|----------|---------|  
|Object|顯示資料表或檢視表的名稱，以及指示當您寫入更新或匯出更新指令碼時是否應該同步處理目標的核取方塊。 如果資料表或檢視表不包含資料，核取方塊會無法使用。|  
|不同的記錄|顯示目標中與來源的索引鍵相同但資料不同的記錄數目。 括號中的數字是當您寫入更新或匯出更新指令碼時標示要更新的記錄數目。|  
|僅限於來源|顯示來源中目標所沒有的記錄數目。 括號中的數字是當您寫入更新或匯出更新指令碼時標示要加入的記錄數目。|  
|僅限於目標|顯示目標中來源所沒有的記錄數目。 括號中的數字是當您寫入更新或匯出更新指令碼時標示要刪除的記錄數目。|  
|相同的記錄|顯示目標中與來源的索引鍵和資料相同的記錄數目。 當您寫入更新或匯出更新指令碼時，這些記錄不會更新。|  
  
### <a name="table-and-view-details"></a>資料表和檢視表詳細資料  
當您按一下 [資料比較]  視窗中的任何資料表或檢視時，詳細資料窗格會顯示該資料表或檢視包含的所有資料列。 詳細資料窗格中的每個索引標籤會顯示不同分類 ([不同的記錄]、[僅限於來源]、[僅限於目標]、[相同的記錄])。 針對每一個資料列，您可以選取或取消選取對應的核取方塊，表示是否要將該變更包含在更新指令碼中。  
  
## <a name="see-also"></a>另請參閱  
[SQL Server Data Tools](../ssdt/sql-server-data-tools.md)  
[操作說明：使用結構描述比較以比較不同的資料庫定義](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
