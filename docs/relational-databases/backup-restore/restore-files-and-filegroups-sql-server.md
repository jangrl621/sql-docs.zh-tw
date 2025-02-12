---
title: 還原檔案和檔案群組 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.restorefilesandfilegrps.general.f1
- sql13.swb.bselectfilegrpsfiles.f1
- sql13.swb.restorefilesandfilegrps.options.f1
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], restoring files and filegroups
- restoring [SQL Server], files
ms.assetid: 72603b21-3065-4b56-8b01-11b707911b05
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 81a832b4372dc2b35893c329d0b7ca909224fb9f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041515"
---
# <a name="restore-files-and-filegroups-sql-server"></a>還原檔案和檔案群組 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中還原檔案與檔案群組。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
-   [安全性](#Security)  
  
-   **若要使用下列項目還原檔案和檔案群組：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   負責還原檔案與檔案群組備份的系統管理員，必須是目前唯一正在使用即將還原之資料庫的人。  
  
-   在明確或隱含的交易中，不允許使用 RESTORE。  
  
-   在簡單復原模式之下，檔案必須屬於唯讀檔案群組。  
  
-   在完整或大量記錄復原模式下，您必須先備份使用中的交易記錄 (也稱為記錄的結尾)，才能還原檔案。 如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)中還原檔案與檔案群組。  
  
-   若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。 如果沒有該憑證或非對稱金鑰，就無法還原資料庫。 因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。 如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。 如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。  
  
 RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。 由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-restore-files-and-filegroups"></a>還原檔案和檔案群組  
  
1.  連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。  
  
2.   展開 [資料庫]。 視資料庫而定，選取使用者資料庫，或者展開 [系統資料庫]  ，再選取系統資料庫。  
  
3.  以滑鼠右鍵按一下資料庫，指向 [工作]  ，然後按一下 [還原]  。  
  
4.  按一下 **[檔案和檔案群組]** ，開啟 **[還原檔案和檔案群組]** 對話方塊。  
  
5.  在 **[一般]** 頁面上的 **[目的地資料庫]** 清單方塊，輸入要還原的資料庫。 您可以輸入新的資料庫，或者從下拉式清單中選擇現有的資料庫。 清單包含伺服器上的所有資料庫，排除系統資料庫 **master** 和 **tempdb**。  
  
6.  若要指定要還原之備份組的來源與位置，請按一下下列任一個選項：  
  
    -   **來源資料庫**  
  
         在清單方塊中輸入資料庫名稱。 此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。  
  
    -   **來源裝置**  
  
         按一下 [瀏覽] 按鈕。 在 **[指定備份裝置]** 對話方塊中，選取 **[備份媒體類型]** 清單方塊上列出的其中一個裝置類型。 若要選取 **[備份媒體]** 清單方塊的一個或多個裝置，請按一下 **[加入]** 。  
  
         將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。  
  
7.  在 **[選取要還原的備份組]** 方格中，選取要還原的備份。 這個方格會顯示指定位置可用的備份。 依預設，會建議一個復原計畫。 若要覆寫建議的復原計畫，您可以變更方格中的選取項目。 任何相依於已取消選取備份的備份，會自動被取消選取。  
  
    |資料行標頭|值|  
    |-----------------|------------|  
    |**Restore**|選取的核取方塊會指出要還原的備份組。|  
    |**名稱**|備份組的名稱。|  
    |**檔案類型**|指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。 資料表中所包含的資料位於 **[資料]** 檔案中。 交易記錄資料位於 **[記錄檔]** 中。 儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。|  
    |**型別**|執行的備份類型：[完整]  、[差異]  或 [交易記錄]  。|  
    |**Server**|執行備份作業的 Database Engine 執行個體名稱。|  
    |**檔案邏輯名稱**|檔案的邏輯名稱。|  
    |**[資料庫備份]**|備份作業中所含的資料庫名稱。|  
    |**開始日期**|備份作業開始時的日期和時間，會出現在用戶端的地區設定中。|  
    |**完成日期**|備份作業完成時的日期和時間，會出現在用戶端的地區設定中。|  
    |**大小**|備份組的大小 (以位元組為單位)。|  
    |**使用者名稱**|執行備份作業的使用者名稱。|  
  
8.  若要檢視或選取進階選項，請按一下 **[選取頁面]** 窗格中的 **[選項]** 。  
  
9. 在 **[還原選項]** 面板中，您可以選擇下列任何選項 (如果情況適用)。  
  
     **還原成檔案群組**  
     指出正在還原整個檔案群組。  
  
     **覆寫現有的資料庫**  
     指定還原作業應該覆寫任何現有的資料庫及其相關檔案，即使已經有另一個資料庫或檔案具有相同名稱也一樣。  
  
     選取此選項相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式的 REPLACE 選項。  
  
     **還原每個備份之前先提示**  
     在將每個備份組還原之前，會要求您確認。  
  
     您必須為不同的媒體集交換磁帶時，這個選項特別有用，例如當伺服器只有一個磁帶機時。  
  
     **限制對還原資料庫的存取**  
     僅有 **db_owner**、 **dbcreator**或 **系統管理員**的成員可以使用還原資料庫。  
  
     選取此選項相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式的 RESTRICTED_USER 選項。  
  
10. 另外，您也可以在 **[將資料庫檔案還原為]** 方格中為每個檔案指定新的還原目的地，以將資料庫還原到新的位置。  
  
    |資料行標頭|值|  
    |-----------------|------------|  
    |**原始檔案名稱**|來源備份檔案的完整路徑。|  
    |**檔案類型**|指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。 資料表中所包含的資料位於 **[資料]** 檔案中。 交易記錄資料位於 **[記錄檔]** 中。 儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。|  
    |**還原成**|還原資料庫檔案的完整路徑。 若要指定新的還原檔案，請按一下文字方塊並編輯建議的路徑與檔案名稱。 變更 **[還原成]** 資料行中的路徑或檔案名稱相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中的 MOVE 選項。|  
  
11. **[復原狀態]** 面板可決定資料庫在還原作業之後的狀態。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     **Leave the database ready for use by rolling back the uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**  
     Recovers the database. This is the default behavior. Choose this option only if you are restoring all of the necessary backups now. This option is equivalent to specifying WITH RECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.  
  
     **Leave the database non-operational, and don't roll back the uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**  
     Leaves the database in the restoring state. To recover the database, you will need to perform another restore using the preceding RESTORE WITH RECOVERY option (see above). This option is equivalent to specifying WITH NORECOVERY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.  
  
     If you select this option, the **Preserve replication settings** option is unavailable.  
  
     **Leave the database in read-only mode. Roll back the uncommitted transactions, but save the rollback operation in a file so the recovery effects can be undone. (RESTORE WITH STANDBY)**  
     Leaves the database in a standby state. This option is equivalent to specifying WITH STANDBY in a [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE statement.  
  
     Choosing this option requires that you specify a standby file.  
  
     **Rollback undo file**  
     Specify a standby file name in the **Rollback undo file** text box. This option is required if you leave the database in read-only mode (RESTORE WITH STANDBY).  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-restore-files-and-filegroups"></a>還原檔案和檔案群組  
  
1.  執行 RESTORE DATABASE 陳述式以還原檔案及檔案群組備份，並指定以下項目：  
  
    -   所要還原的資料庫名稱。  
  
    -   將要還原完整資料庫備份的來源備份裝置。  
  
    -   替要還原的每個檔案指定 FILE 子句。  
  
    -   替要還原的每個檔案群組指定 FILEGROUP 子句。  
  
    -   NORECOVERY 子句。 如果檔案在備份建立之後沒有做過任何修改，請指定 RECOVERY 子句。  
  
2.  如果檔案在備份建立之後做過修改，則請執行 RESTORE LOG 陳述式以套用交易記錄備份，並指定下列項目：  
  
    -   交易記錄檔要套用的資料庫名稱。  
  
    -   用於還原交易記錄備份的備份裝置。  
  
    -   倘若在目前的交易記錄備份之後還有另一個交易記錄備份要套用，請指定 NORECOVERY 子句，否則請指定 RECOVERY 子句。  
  
         如果套用交易記錄備份，則交易記錄備份必須涵蓋備份檔案與檔案群組直到記錄結束的時間 (除非還原「所有的」資料庫檔案)。  
  
###  <a name="TsqlExample"></a> 範例 &#40;Transact-SQL&#41;  
 這個範例會還原 `MyDatabase` 資料庫的檔案和檔案群組。 為了將資料庫還原到目前的時間，還套用了兩份交易記錄。  
  
```sql  
USE master;  
GO  
-- Restore the files and filesgroups for MyDatabase.  
RESTORE DATABASE MyDatabase  
   FILE = 'MyDatabase_data_1',  
   FILEGROUP = 'new_customers',  
   FILE = 'MyDatabase_data_2',  
   FILEGROUP = 'first_qtr_sales'  
   FROM MyDatabase_1  
   WITH NORECOVERY;  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyDatabase  
   FROM MyDatabase_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [備份檔案和檔案群組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-files-and-filegroups-sql-server.md)   
 [建立完整資料庫備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)   
 [備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)   
 [還原交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)  
  
  
