---
title: 瞭解累加式產生 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 71355cfe5341af74083e21cb786b441c71c48c80
ms.sourcegitcommit: 495913aff230b504acd7477a1a07488338e779c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68811306"
---
# <a name="understanding-incremental-generation"></a>了解累加式產生
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  在初始結構描述產生之後，您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]來變更 Cube 和維度定義，然後重新執行 [結構描述產生精靈]。 此精靈會更新主題領域資料庫和相關資料來源檢視中的結構描述，以便能夠反映變更，同時盡量保留目前存在於要重新產生之資料表中的資料。 如果您在初始產生之後變更了資料表，結構描述產生精靈會使用下列規則，盡量保留那些變更：  
  
-   如果資料表是由精靈先前產生的，則會覆寫該資料表。 您可以將資料來源檢視中之資料表的 **AllowChangesDuringGeneration** 屬性變更為 **false**，以防止精靈產生的資料表遭到覆寫。 當您控制資料表時，資料表被視為任何其他使用者自訂資料表來處理，而且在重新產生時不受影響。 從產生移除資料表之後，稍後您可以將資料來源檢視中之資料表的 **AllowChangesDuringGeneration** 屬性變更為 **true** ，並重新開啟資料表供精靈變更。 如需詳細資訊，請參閱[變更資料來源檢視的屬性 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)。  
  
-   如果資料表已透過此精靈以外的方式加入到資料來源檢視或基礎資料庫中，則不會覆寫該資料表。  
  
 當結構描述產生精靈重新產生在先前主題領域資料庫中產生的資料表時，您可以選擇由精靈保留那些資料表中的現有資料。  
  
## <a name="supporting-data-preservation"></a>支援資料保留  
 一般而言，結構描述產生精靈會保留儲存在所產生之資料表中的資料。 此外，如果您將資料行加入至精靈已產生的資料表中，精靈也會保留該資料。 您可以使用此功能來加入或修改維度和 Cube，然後重新產生基礎物件，而不必重新載入基礎資料表中所儲存的資料。  
  
> [!NOTE]  
>  如果您是從分隔的文字檔載入資料，則也可以選擇結構描述產生精靈在重新產生期間，是否覆寫這些檔案和它們所包含的資料。 文字檔不是完全覆寫，就是完全不覆寫。 結構描述產生精靈不會局部覆寫這些檔案。 依預設，不會覆寫這些檔案。  
  
### <a name="partial-preservation"></a>局部保留  
 結構描述產生精靈在某些情況下無法保留現有的資料。 下表提供的範例是一些狀況，其中精靈無法在重新產生期間，保留基礎資料表中所有現有的資料。  
  
|資料變更類型|處理方式|  
|-------------------------|---------------|  
|不相容資料類型的變更|結構描述產生精靈使用標準 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型轉換，盡可能將現有的資料轉換成不同的資料類型。 不過，當您將屬性的資料類型變更為與現有資料不相容的類型時，精靈會卸除受影響資料行的資料。|  
|參考完整性錯誤|如果您變更包含資料的維度或 Cube，且該變更在重新產生期間造成參考完整性錯誤，結構描述產生精靈會卸除外部索引鍵資料表中的所有資料。 卸除的資料不限於造成外部索引鍵條件約束違規的資料行，或含有參考完整性錯誤的資料列。 比方說，如果您將維度索引鍵變更為含有非唯一或 Null 資料的屬性，則會卸除外部索引鍵資料表中的所有現有資料。 此外，卸除一個資料表的所有資料會產生一連串的效果，而可能造成其他參考完整性違規。|  
|刪除屬性或維度|如果您從維度刪除屬性，結構描述產生精靈會刪除對應到已刪除之屬性的資料行。 如果您刪除維度，精靈會刪除對應到已刪除之維度的資料表。 在這些情況下，精靈會卸除已刪除之資料行或資料表中所包含的資料。|  
  
 結構描述產生精靈在卸除任何資料之前會發出警告，讓您可以取消精靈，而不會失去任何資料。 不過，結構描述產生精靈無法區分預期的資料流失，和非預期的資料流失。 當您執行精靈時，對話方塊會列出包含要卸除之資料的資料表和資料行。 您可以讓精靈繼續並卸除資料，或取消精靈，以修訂您對資料表和資料行所做的變更。  
  
## <a name="supporting-cube-and-dimension-changes"></a>支援 Cube 和維度變更  
 當您變更維度和 Cube 的屬性時，結構描述產生精靈會在基礎主題領域資料表中，以及相關資料來源檢視中重新產生適當的物件，如下表所述。  
  
 刪除物件，例如維度、Cube 或屬性。  
 結構描述產生精靈會刪除已刪除之物件所對應的基礎物件。 如果您將資料行加入至精靈所產生的資料表中，新資料行不會防止該資料表被刪除。 刪除物件會造成基礎物件所儲存的資料被卸除，如果發生參考完整性錯誤，則也會造成其他資料被卸除。  
  
 重新命名物件，例如維度、Cube 或屬性。  
 結構描述產生精靈會將已重新命名之物件所對應的基礎物件重新命名。 精靈也會重新命名所有受影響的物件，例如主索引鍵。 儲存在基礎物件中的現有資料會保留下來。  
  
 修改物件，例如變更它的資料類型。  
 結構描述產生精靈會修改已變更之物件所對應的基礎物件。 除非新的資料類型與現有的資料不相容，否則，儲存在資料庫中基礎物件內的現有資料會保留下來。  
  
 加入新物件，例如維度、Cube 或屬性。  
 結構描述產生精靈會加入新物件所對應的基礎物件。  
  
 如果 [結構描述產生精靈] 因為主題領域資料庫中出現使用者物件，而無法進行必要的變更 (因為 Database Engine 會傳回錯誤)，則 [結構描述產生精靈] 會失敗，並顯示 Database Engine 所傳回的錯誤。 例如, 如果您在嚮導產生資料表之後, 在資料表上建立 primary key 條件約束或非叢集索引, 則「架構產生嚮導」不會卸載該資料表, 因為它並未建立條件約束或索引。  
  
## <a name="supporting-schema-changes"></a>支援結構描述變更  
 當您在主題領域資料庫，或在相關聯資料來源檢視中變更資料表或資料行的屬性時，結構描述產生精靈會如下表所述來處理變更。  
  
 刪除結構描述產生精靈所產生的資料表或資料行。  
 如果您刪除結構描述產生精靈所產生的資料表或資料行，精靈會重新產生已刪除之資料表。 對於將重新產生已刪除之資料表或資料行，精靈並不提出警告。  
  
 變更結構描述產生精靈所產生之資料表或資料行的屬性。  
 如果您修改結構描述產生精靈所產生之資料表或資料行的屬性，精靈會重新產生已變更之資料表，但其中不含變更。 比方說，如果變更結構描述產生精靈所產生之資料行的資料類型或 Null 屬性，或資料表的檔案群組，則重新產生之後變更就會失效。 對於重新產生已變更之物件且不含變更，精靈並不提出警告。  
  
 將資料行加入至結構描述產生精靈所產生的資料表，或將資料表加入至主題領域資料庫或臨時區域資料庫中。  
 如果您將資料行加入至結構描述產生精靈所產生的資料表中，在重新產生期間，精靈會保留其他資料行，以及它所儲存的任何資料。 不過，如果您將資料表加入至主題領域資料庫或臨時區域資料庫，結構描述產生精靈不會併入新資料表。 加入的資料行或加入的資料表，不會反映在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫、DTS 封裝、資料來源檢視，或所產生之結構描述中的任何其他地方。  
  
## <a name="supporting-data-source-and-data-source-view-changes"></a>支援資料來源和資料來源檢視變更  
 當結構描述產生精靈重新執行時，會重新使用它在原始產生所使用的相同資料來源和資料來源檢視。 如果您加入資料來源或資料來源檢視，精靈不會使用它。 如果您在初始產生之後刪除原始資料來源或資料來源檢視，您必須從頭開始執行精靈。 精靈中所有先前的設定也會被刪除。 下次您執行結構描述產生精靈時，對於基礎資料庫中任何繫結到已刪除之資料來源或資料來源檢視的現有物件，將視同使用者建立的物件來處理。  
  
 如果在產生時資料來源檢視不反映基礎資料庫的實際狀態，當結構描述產生精靈產生主題領域資料庫和臨時區域資料庫的結構描述時，會發生錯誤。 比方說，如果資料來源檢視指定資料行的資料類型設為 **int**，但該資料行的資料類型實際上是設為 **string**，則結構描述產生精靈會將外部索引鍵的資料類型設為 **int** ，以符合資料來源檢視，但當它建立關聯性時會失敗，因為實際資料類型是 **string**。  
  
 相反地，如果您將資料來源連接字串，變更為與前一次產生不同的資料庫，則不會產生錯誤。 這時會使用新資料庫，且先前的資料庫不會產生任何變更。  
  
## <a name="see-also"></a>另請參閱  
 [管理對資料來源檢視及資料來源所做的變更](../../analysis-services/multidimensional-models/manage-changes-to-data-source-views-and-data-sources.md)   
 [結構描述產生精靈 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/schema-generation-wizard-analysis-services.md)  
  
  
