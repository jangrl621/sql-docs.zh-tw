---
title: 索引屬性 F1 說明 | Microsoft Docs
ms.custom: ''
ms.date: 02/17/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: reference
f1_keywords:
- sql13.swb.indexproperties.filter.f1
- sql13.swb.indexproperties.partitions.f1
- sql13.swb.indexproperties.general.f1
- sql13.swb.indexproperties.storage.f1
- sql13.swb.indexproperties.columns.f1
- sql13.swb.indexproperties.options.f1
- sql13.swb.indexproperties.spatial.f1
ms.assetid: 45efd81a-3796-4b04-b0cc-f3deec94c733
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: c6d84af2893cc535717c2785d35875ca2b0d5550
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68476294"
---
# <a name="index-properties-f1-help"></a>索引屬性 F1 說明
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  本主題中的章節參考使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 對話方塊提供的各種不同索引屬性。  
  
 **本主題內容：**  
  
 [索引屬性一般頁面](#General)  
  
 [選取 (索引) 資料行對話方塊](#Columns)  
  
 [索引屬性儲存頁面](#Storage)  
  
 [索引屬性空間頁面](#Spatial)  
  
 [索引屬性篩選頁面](#Filter)  
  
##  <a name="General"></a> 索引屬性一般頁面  
 使用 [一般] 頁面可檢視或修改所選取資料表或檢視的索引屬性。 每一個頁面的選項可能會因為選取的索引類型而不同。  
  
 **資料表名稱**  
 顯示建立索引的資料表名稱或檢視名稱。 此欄位是唯讀的。 若要選取不同的資料表，請關閉 [索引屬性] 頁面，選取正確的資料表，然後再次開啟 [索引屬性] 頁面。  
  
 不能在索引檢視表上指定空間索引。 空間索引只能定義在具有主索引鍵的資料表上。 資料表上主索引鍵資料行的最大數目是 15。 主索引鍵資料行的每列合併大小上限是 895 個位元組。  
  
 **索引名稱**  
 顯示索引的名稱。 這個檔案對現有的索引而言是唯讀的。 建立新的索引時，請輸入索引的名稱。  
  
 **索引類型**  
 表示索引的類型。 如果是新的索引，則表示開啟此對話方塊時所選取的索引類型。 索引可以是：[叢集]  、[非叢集]  、[主要 XML]  、[次要 XML]  、[空間]  、[叢集資料行存放區]  或 [非叢集資料行存放區]  。  
  
 **注意** ：每個資料表只允許有一個叢集索引。 每個資料表只允許有一個 xVelocity 記憶體最佳化的資料行存放區索引。  
  
 **唯一**  
 選取此核取方塊使索引成為唯一的。 任何兩個資料列都不允許有相同索引值。 依預設，不會勾選此核取方塊。 修改現有的索引時，如果兩個資料列有相同的值，索引建立將會失敗。 針對允許 NULL 的資料行，唯一索引允許一個 NULL 值。  
  
 如果您在 **[索引類型]** 欄位中選取 **[空間]** ， **[唯一]** 核取方塊會呈暗灰色。  
  
 **索引鍵資料行**  
 將想要的資料行加入 **[索引鍵資料行]** 方格。 加入多個資料行時，必須以想要的順序列出資料行。 索引中的資料行順序對索引效能有很大的影響。  
  
 單一複合索引中參與的資料行不能超過 16 個。 如果超過 16 個資料行，請參閱本主題結尾的＜包含的資料行＞。  
  
 空間索引只能定義在包含空間資料類型的單一資料行上 ( *「空間資料行」* (Spatial Column))。  
  
 **名稱**  
 顯示參與索引鍵的資料行名稱。  
  
 **排序次序**  
 指定所選取索引資料行的排序方向為 **[遞增]** 或 **[遞減]** 。  
  
> [!NOTE]  
>  如果索引類型為 **[主要 XML]** 或 **[空間]** ，此資料行不會出現在資料表中。  
  
 **資料類型**  
 顯示資料類型資訊。  
  
> [!NOTE]  
>  如果資料表資料行是計算資料行， **[資料類型]** 就會顯示「計算資料行」。  
  
 **大小**  
 顯示儲存資料行資料類型所需的最大位元組數。 針對空間或 XML 資料行顯示零 (0)。  
  
 **識別**  
 顯示參與索引鍵的資料行是否為識別欄位。  
  
 **允許 NULL**  
 顯示參與索引鍵的資料行是否允許在資料表或檢視資料行中儲存 NULL 值。  
  
 **[加入]**  
 將資料行加入索引鍵。 請從您按一下 [新增]  時所出現的 [從 *\<資料表名稱>* 選取資料行]  對話方塊中，選取資料表資料行。 如果是空間索引，在您選取一個資料行之後，此按鈕會呈暗灰色。  
  
 **移除**  
 從索引鍵中的參與裡移除選取的資料行。  
  
 **上移**  
 在索引鍵方格中將選取的資料行向上移動。  
  
 **下移**  
 在索引鍵方格中將選取的資料行向下移動。  
  
 **資料行存放區資料行**  
 按一下 [加入]  ，選取資料行存放區索引的資料行。 如需資料行存放區索引的限制，請參閱 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md)。  
  
 **包含的資料行**  
 在非叢集索引中包含非索引鍵資料行。 此選項可藉由在非叢集索引的分葉層級中加入資料行當做非索引鍵資料行，以略過索引鍵大小總計的目前索引限制，以及參與索引鍵的最大資料行數目。 如需詳細資訊，請參閱 [建立內含資料行的索引](../../relational-databases/indexes/create-indexes-with-included-columns.md)  
  
##  <a name="Columns"></a> 選取 (索引) 資料行對話方塊  
 建立或修改索引時，請使用此頁面來將資料行加入 **[索引屬性一般]** 頁面。  
  
 **核取方塊**  
 選取以加入資料行。  
  
 **名稱**  
 資料行的名稱。  
  
 **資料類型**  
 資料行的資料類型。  
  
 **Bytes**  
 資料行的大小 (以位元組為單位)。  
  
 **識別**  
 針對識別欄位顯示 **[是]** ，若資料行不是識別欄位，就顯示 **[否]** 。  
  
 **允許 Null**  
 如果資料表定義對於資料行允許 Null 值，就會顯示 **[是]** 。 如果資料表定義對於資料行不允許 Null 值，就會顯示 **[否]** 。  

##  <a name="Options"></a> 選項頁面選項
 使用此頁面來檢視或修改各種索引選項。

### <a name="general-options"></a>一般選項
**自動重新計算統計資料**<br>
指定是否要自動重新計算散發統計資料。 預設為 **True**，相當於將 STATISTICS_NORECOMPUTE 設定為 OFF。 將此項目設定為 **False** 會將 STATISTICS_NORECOMPUTE 設定為 ON。

**忽略重複的值** <br>
指定當插入作業嘗試將重複的索引鍵值插入唯一索引時所產生的錯誤回應。

True<br>
當重複的索引鍵值插入唯一索引時，就會出現警告訊息。 只有違反唯一性條件約束的資料列才會失敗。

False<br>
當重複的索引鍵值插入唯一索引時，就會出現錯誤訊息。 整個 INSERT 作業將會回復。

### <a name="locks-options"></a>鎖定選項

**允許資料列鎖定**<br>
指定是否允許資料列鎖定。

**允許頁面鎖定**<br>
指定是否允許頁面鎖定。

### <a name="operation-options"></a>作業選項

 **允許線上 DML 處理**  
 允許使用者在索引作業期間存取基礎資料表或叢集索引資料，以及與非叢集索引相關聯的任何項目，例如 CREATE 或 ALTER。 如需詳細資訊，請參閱 [Perform Index Operations Online](../../relational-databases/indexes/perform-index-operations-online.md)。  
  
> [!NOTE]  
>  此選項不適用於 XML 索引，或索引為已停用的叢集索引時亦不適用。  
  
 **平行處理原則的最大程度**  
 限制平行計畫執行期間要使用的處理器數目。 預設值 (0) 會使用實際可用的 CPU 數目。 將值設定為 1 會抑制平行計畫的產生；將值設定為大於 1 的數字則會限制單一查詢執行所使用的處理器最大數目。 此選項僅會在對話方塊處於 **[重建]** 或 **[重新建立]** 狀態時可用。 如需詳細資訊，請參閱 [設定平行處理原則的最大程度選項來取得最佳效能](../../relational-databases/policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md)。  
  
> [!NOTE]  
>  如果指定的數值大於可用的 CPU 數目，就會使用可用 CPU 的實際數目。  


**針對循序索引鍵優化**<br>
指定是否要最佳化最後一頁的插入競爭。 如需詳細資訊，請參閱[循序索引鍵](../../t-sql/statements/create-index-transact-sql.md#sequential-keys)。

### <a name="storage-options"></a>儲存選項

**在 tempdb 中排序**<br>
指定是否要將暫時排序結果儲存在 tempdb 中。

True<br>
用來建立索引的中繼排序結果會儲存在 tempdb 中。 如果 tempdb 位於使用者資料庫以外的另一組磁碟上，這種儲存方式可以減少建立索引所需的時間。 不過，這會增加建立索引時所使用的磁碟空間量。

False<br>
中繼排序結果會儲存在與用來儲存索引相同的資料庫中。 如需詳細資訊，請參閱[索引的 SORT_IN_TEMPDB 選項](./sort-in-tempdb-option-for-indexes.md)。

**填滿因數**<br>
指定百分比，以表示 Database Engine 在索引建立或重建期間應該將每個索引頁面的分葉層級填滿的程度。 fillfactor 必須是 1 到 100 之間的整數值。 如果 fillfactor 是 100，資料庫引擎會利用已填滿容量的分葉頁面來建立索引。
只有在建立或重建索引時才會套用 FILLFACTOR 設定。 資料庫引擎不會動態保留頁面中空白空間的指定百分比。

如需詳細資訊，請參閱 [指定索引的填滿因素](./specify-fill-factor-for-an-index.md)。

**索引頁預留空間**<br>
指定索引填補。

True<br>
fillfactor 指定的可用空間百分比會套用到索引的中繼層級頁面上。

False 或未指定 fillfactor<br>
中繼層級頁面會幾乎填滿整個容量，但會考量中繼頁面上的索引鍵集，而保留至少可供索引所能擁有之大小上限的一個資料列使用的足夠空間。


##  <a name="Storage"></a> 儲存頁面選項  
 使用此頁面來檢視或修改選取之索引的檔案群組或資料分割結構描述屬性。 僅顯示與索引類型相關的選項。  
  
 **檔案群組**  
 在指定的檔案群組中儲存索引。 清單僅顯示標準 (資料列) 檔案群組。 預設清單選取項目為資料庫的 PRIMARY 檔案群組。 如需相關資訊，請參閱 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)。  
  
 **檔案資料流檔案群組**  
 為 FILESTREAM 資料指定檔案群組。 此清單只會顯示 FILESTREAM 檔案群組。 預設清單選取項目為資料庫的 PRIMARY FILESTREAM 檔案群組。 如需詳細資訊，請參閱 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)。  
  
 **分割區配置**  
 在資料分割結構描述中儲存索引。 按一下 **[資料分割配置]** 以啟用下列方格。 預設清單選取項目是用來儲存資料表資料的資料分割配置。 當您在清單中選取不同的資料分割配置時，會更新方格中的資訊。 如需相關資訊，請參閱 [Partitioned Tables and Indexes](../../relational-databases/partitions/partitioned-tables-and-indexes.md)。  
  
 如果資料庫中沒有資料分割結構描述，則無法使用資料分割結構描述選項。  
  
 **檔案資料流資料分割配置**  
 指定資料分割配置的 FILESTREAM 資料。 資料分割配置必須對稱於在 **[資料分割配置]** 選項中所指定的配置。  
  
 如果資料表不是資料分割，則此欄位空白。  
  
 **資料分割結構描述參數**  
 顯示參與資料分割結構描述的資料行名稱。  
  
 **資料表資料行**  
 選取資料表或檢視以對應至資料分割結構描述。  
  
 **資料行資料類型**  
 顯示有關資料行的資料類型資訊。  
  
> [!NOTE]  
>  如果資料表資料行是計算資料行， **[資料行資料類型]** 就會顯示「計算資料行」。  
  
##  <a name="Spatial"></a> 空間頁面索引選項  
 使用 **[空間]** 頁面可檢視或指定空間屬性的值。 如需詳細資訊，請參閱[空間資料 &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)。  
  
### <a name="bounding-box"></a>週框方塊  
 *「週框方塊」* (Bounding Box) 是幾何平面最上層方格的周邊。 週框方塊參數只存在於幾何方格鑲嵌內。 如果 **[鑲嵌式配置]** 為 **[地理方格]** ，就無法使用這些參數。  
  
 此面板會顯示週框方塊的 **(** _X-min_ **,** _Y-min_ **)** 和 **(** _X-max_ **,** _Y-max_ **)** 座標。 沒有預設座標值。 因此，當您在 **geometry** 類型資料行上建立新的空間索引時，您必須指定座標值。  
  
 **X-min**  
 週框方塊左下角的 X 座標。  
  
 **Y-min**  
 週框方塊左下角的 Y 座標。  
  
 **X-max**  
 週框方塊右上角的 X 座標。  
  
 **Y-max**  
 週框方塊右上角的 Y 座標。  
  
### <a name="general"></a>一般  
 **[鑲嵌式配置]**  
 表示索引的鑲嵌式配置。 支援的鑲嵌式配置如下所示。  
  
 **幾何方格**  
 指定幾何方格鑲嵌式配置，這會套用到 **geometry** 資料類型的資料行。  
  
 **幾何自動方格**  
 當資料庫相容性層級設定為 110 或更高時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會啟用這個選項。  
  
 **[地理方格]**  
 指定地理方格鑲嵌式配置，這會套用到 **geography** 資料類型的資料行。  
  
 **地理自動方格**  
 當資料庫相容性層級設定為 110 或更高時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會啟用這個選項。  
  
 如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何實作鑲嵌的資訊，請參閱[空間資料 &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)。  
  
 **每一物件的資料格**  
 指示可用於索引內單一空間物件的鑲嵌式每一物件的資料格數目。 這個數目可以是 1 和 8192 之間 (含) 的任何整數。 當資料庫相容性層級設定為 110 或更高時，舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的預設值為 16 和 8。  
  
 在最上層，如果物件涵蓋的資料格數目要比 *n*指定的數目還要多，則索引會盡量使用所需的資料格數目來提供完整的最上層鑲嵌。 在這類情況下，物件可能會收到比指定之資料格數目還要多的資料格。 在此情況下，最大數目就是最上層方格產生的資料格數目，該數目取決於 **[層級 1]** 密度。  
  
### <a name="grids"></a>方格  
 此面板會顯示鑲嵌式配置之每一個層級上的方格密度。 密度會指定為 **[低]** 、 **[中]** 或 **[高]** 。 預設值是 **[中]** 。 **[低]** 代表 4x4 個方格 (16 個方格)、 **[中]** 代表 8x8 個方格 (64 個方格)，而 **[高]** 則代表 16x16 個方格 (256 個方格)。 當選擇了 **[幾何自動方格]** 或 **[地理自動方格]** 鑲嵌選項時，就無法使用這些選項。  
  
 **層級 1**  
 第一層 (上層) 方格的密度。  
  
 **層級 2**  
 第二層方格的密度。  
  
 **層級 3**  
 第三層方格的密度。  
  
 **層級 4**  
 第四層方格的密度。  
  
##  <a name="Filter"></a> 篩選頁面  
 使用此頁可輸入篩選索引的篩選述詞。 如需詳細資訊，請參閱 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)。  
  
 **篩選運算式**  
 定義要在篩選索引中包含什麼資料列。 例如， `StartDate > '20000101' AND EndDate IS NOT NULL'.`  
  
## <a name="see-also"></a>另請參閱  
 [設定索引選項](../../relational-databases/indexes/set-index-options.md)   
 [INDEXPROPERTY &#40;Transact-SQL&#41;](../../t-sql/functions/indexproperty-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)  
  
  
