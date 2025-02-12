---
title: 啟用和停用異動資料擷取 (SQL Server) | Microsoft Docs
ms.date: 01/02/2019
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], enabling tables
- change data capture [SQL Server], enabling databases
- change data capture [SQL Server], disabling databases
- change data capture [SQL Server], disabling tables
ms.assetid: b741894f-d267-4b10-adfe-cbc14aa6caeb
author: rothja
ms.author: jroth
ms.openlocfilehash: dcd857c9a493528b5759d83dd3b89924a2c22f74
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68058090"
---
# <a name="enable-and-disable-change-data-capture-sql-server"></a>啟用和停用異動資料擷取 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]
  此主題描述如何針對資料庫和資料表啟用及停用異動資料擷取。  
  
## <a name="enable-change-data-capture-for-a-database"></a>針對資料庫啟用異動資料擷取  
 針對個別資料表建立擷取執行個體之前， **sysadmin** 固定伺服器角色的成員必須先啟用異動資料擷取的資料庫。 這項步驟可透過在資料庫內容中執行 [sys.sp_cdc_enable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-enable-db-transact-sql.md) 預存程序完成。 若要判斷資料庫是否已啟用，請查詢 **sys.databases** 目錄檢視中的 **is_cdc_enabled** 資料行。  
  
 啟用異動資料擷取的資料庫時，也會針對資料庫建立 **cdc** 結構描述、 **cdc** 使用者、中繼資料表，以及其他系統物件。 **cdc** 結構描述包含異動資料擷取中繼資料表，以及啟用異動資料擷取的來源資料表後，當做變更資料儲存機制使用的個別變更資料表。 **cdc** 結構描述也包含用來查詢變更資料的相關聯系統函數。  
  
 異動資料擷取需要獨佔使用 **cdc** 結構描述與 **cdc** 使用者。 如果名稱為 *cdc* 的結構描述或資料庫使用者目前存在於資料庫中，就無法啟用異動資料擷取的資料庫，直到卸除或重新命名結構描述和 (或) 使用者為止。  
  
 如需啟用資料庫的範例，請參閱「啟用異動資料擷取的資料庫」範本。  
  
> [!IMPORTANT]  
>  若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中找出範本，請移至 **[檢視]** 、按一下 **[範本總管]** ，然後選取 **[SQL Server 範本]** 。 **[異動資料擷取]** 是子資料夾。 在這個資料夾底下，您將會找到這個主題所參考的所有範本。 **工具列上也有一個** [範本總管] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 圖示。  
  
```sql  
-- ====  
-- Enable Database for CDC template   
-- ====  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_db  
GO  
```  
  
## <a name="disable-change-data-capture-for-a-database"></a>針對資料庫停用異動資料擷取  
 **系統管理員**固定伺服器角色的成員可以在資料庫內容中執行 [sys.sp_cdc_disable_db &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-cdc-disable-db-transact-sql.md) 預存程序，以便停用資料庫異動資料擷取。 在您停用資料庫之前，不需要停用個別資料表。 停用資料庫就會移除所有相關聯的異動資料擷取中繼資料，包括 **cdc** 使用者和結構描述以及異動資料擷取作業。 不過，系統不會自動移除異動資料擷取所建立的任何控制角色，而且您必須明確刪除這些角色。 若要判斷資料庫是否已啟用，請查詢 sys.databases 目錄檢視中的 **is_cdc_enabled** 資料行。  
  
 如果啟用異動資料擷取的資料庫已卸除，系統就會自動移除異動資料擷取作業。  
  
 如需停用資料庫的範例，請參閱「停用異動資料擷取的資料庫」範本。  
  
> [!IMPORTANT]  
>  若要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中找出範本，請移至 **[檢視]** 、按一下 **[範本總管]** ，然後按一下 **[SQL Server 範本]** 。 **[異動資料擷取]** 是子資料夾，而且您將會在其中找到這個主題所參考的所有範本。 **工具列上也有一個** [範本總管] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 圖示。  
  
```sql  
-- =======  
-- Disable Database for Change Data Capture template   
-- =======  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_db  
GO  
```  
  
## <a name="enable-change-data-capture-for-a-table"></a>針對資料表啟用異動資料擷取  
 啟用異動資料擷取的資料庫之後， **db_owner** 固定資料庫角色的成員就可以使用 **sys.sp_cdc_enable_table**預存程序，針對個別的來源資料表建立擷取執行個體。 若要判斷是否已經啟用異動資料擷取的來源資料表，請檢查 **sys.tables** 目錄檢視中的 is_tracked_by_cdc 資料行。  
  
 您可以在建立擷取執行個體時指定下列選項：  
  
 **來源資料表中要擷取的資料行**。  
  
 根據預設，系統會將來源資料表中的所有資料行識別為擷取資料行。 如果只需要追蹤資料行的子集 (例如，基於隱私或效能的原因)，請使用 *@captured_column_list* 參數來指定資料行的子集。  
  
 **要包含變更資料表的檔案群組。**  
  
 根據預設，變更資料表位於資料庫的預設檔案群組中。 想要控制個別變更資料表位置的資料庫擁有者可以使用 *@filegroup_name* 參數，指定與擷取執行個體相關聯之變更資料表的特定檔案群組。 此指定的檔案群組必須已存在。 一般而言，我們建議您將變更資料表放在與來源資料表不同的檔案群組中。 如需示範 *@filegroup_name* 參數用法的範例，請參閱**啟用指定檔案群組選項的資料表**範本。  
  
```sql  
-- =========  
-- Enable a Table Specifying Filegroup Option Template  
-- =========  
USE MyDB  
GO  
  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@filegroup_name = N'MyDB_CT',  
@supports_net_changes = 1  
GO  
```  
  
 **用於控制變更資料表存取權的角色。**  
  
 指定角色的目的是要控制變更資料的存取權。 指定的角色可以是現有的固定伺服器角色或資料庫角色。 如果指定的角色不存在，則會自動建立該名稱的資料庫角色。 **系統管理員** 或 **db_owner** 角色的成員對於變更資料表中的資料擁有完整存取權。 其他所有使用者對於來源資料表的所有擷取資料行必須具備 SELECT 權限。 此外，指定角色時，不屬於 **系統管理員** 或 **db_owner** 角色之成員的使用者也必須是指定角色的成員。  
  
 如果您不想要使用控制角色，請將 *@role_name* 參數明確設定為 NULL。 如需在不使用控制角色的情況下啟用資料表的範例，請參閱 **在不使用控制角色的情況下啟用資料表** 範本。  
  
```sql  
-- =========  
-- Enable a Table Without Using a Gating Role template   
-- =========  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = NULL,  
@supports_net_changes = 1  
GO  
  
```  
  
 **用以查詢變更淨值的函數。**  
  
 擷取執行個體一定會包含資料表值函式，以便傳回在定義間隔內發生的所有變更資料表項目。 這個函數的命名方式是將擷取執行個體名稱附加至 "cdc.fn_cdc_get_all_changes_"。 如需詳細資訊，請參閱 [cdc.fn_cdc_get_all_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-all-changes-capture-instance-transact-sql.md)。  
  
 如果 *@supports_net_changes* 參數設為 1，擷取執行個體也會產生淨變更函數。 此函數僅會針對在呼叫中指定之間隔內變更的每個不同資料列，傳回一個變更。 如需詳細資訊，請參閱 [cdc.fn_cdc_get_net_changes_&#60;capture_instance&#62; &#40;Transact-SQL&#41;](../../relational-databases/system-functions/cdc-fn-cdc-get-net-changes-capture-instance-transact-sql.md)。  
  
 若要支援淨變更查詢，來源資料表必須具有主索引鍵或唯一的索引才能唯一識別資料列。 如果使用了唯一的索引，就必須使用 *@index_name* 參數來指定該索引的名稱。 在主索引鍵或唯一索引中定義的資料行必須包含在要擷取之來源資料行的清單中。  
  
 如需示範建立含有兩個查詢函數之擷取執行個體的範例，請參閱 **針對所有和淨變更查詢啟用資料表** 範本。  
  
```sql  
-- =============  
-- Enable a Table for All and Net Changes Queries template   
-- =============  
USE MyDB  
GO  
EXEC sys.sp_cdc_enable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@role_name     = N'MyRole',  
@supports_net_changes = 1  
GO  
```  
  
> [!NOTE]
>  如果在含有現有主索引鍵的資料表上啟用 [異動資料擷取]，而且並未使用 *@index_name* 參數來識別替代的唯一索引鍵，異動資料擷取功能就會使用此主索引鍵。 如果沒有先針對資料表停用異動資料擷取，系統就不允許對主索引鍵進行後續變更。 不論設定異動資料擷取時是否要求淨變更查詢的支援，都是如此。 如果啟用異動資料擷取時，資料表沒有任何主索引鍵，則異動資料擷取就會忽略後續加入主索引鍵的作業。 由於異動資料擷取不會使用啟用資料表之後所建立的主索引鍵，因此您可以移除此索引鍵和索引鍵資料行，而且沒有任何限制。  
  
## <a name="disable-change-data-capture-for-a-table"></a>針對資料表停用異動資料擷取  
 **db_owner** 固定資料庫角色的成員可以使用 **sys.sp_cdc_disable_table**預存程序，針對個別的來源資料表移除擷取執行個體。 若要判斷是否已經啟用異動資料擷取的來源資料表，請檢查 **sys.tables** 目錄檢視中的 **is_tracked_by_cdc** 資料行。 如果進行停用之後，資料庫中沒有任何資料表啟用，系統也會移除異動資料擷取作業。  
  
 如果啟用異動資料擷取的資料表已卸除，系統就會自動移除與此資料表相關聯的異動資料擷取中繼資料。  
  
 如需停用資料表的範例，請參閱「停用資料表的擷取執行個體」範本。  
  
```sql  
-- =====  
-- Disable a Capture Instance for a Table template   
-- =====  
USE MyDB  
GO  
EXEC sys.sp_cdc_disable_table  
@source_schema = N'dbo',  
@source_name   = N'MyTable',  
@capture_instance = N'dbo_MyTable'  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [追蹤資料變更 &#40;SQL Server&#41;](../../relational-databases/track-changes/track-data-changes-sql-server.md)   
 [關於異動資料擷取 &#40;SQL Server&#41;](../../relational-databases/track-changes/about-change-data-capture-sql-server.md)   
 [使用變更資料 &#40;SQL Server&#41;](../../relational-databases/track-changes/work-with-change-data-sql-server.md)   
 [管理和監視異動資料擷取 &#40;SQL Server&#41;](../../relational-databases/track-changes/administer-and-monitor-change-data-capture-sql-server.md)  
  
  
