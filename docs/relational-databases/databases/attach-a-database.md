---
title: 附加資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql13.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
ms.openlocfilehash: ca1ff898841b946c0823b71b065f360a59e69696
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071698"
---
# <a name="attach-a-database"></a>附加資料庫
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中附加資料庫。 您可以使用此功能來複製、移動或升級 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。  
  
##  <a name="Prerequisites"></a> 必要條件  
  
-   資料庫必須先卸離。 嘗試附加未卸離的資料庫會傳回錯誤。 如需詳細資訊，請參閱 [卸離資料庫](../../relational-databases/databases/detach-a-database.md)。  
  
-   當您附加資料庫時，所有的資料檔案 (MDF 和 LDF 檔案) 都必須可供使用。 如果資料檔案的路徑與資料庫第一次建立或最後一次附加時的路徑不同，您必須指定檔案的目前路徑。  
  
-   在您附加資料庫時，如果 MDF 和 LDF 檔案位於不同的目錄，而且其中一個路徑包括 \\\\?\GlobalRoot，作業將會失敗。  
  
###  <a name="Recommendations"></a> 附加是否為最佳選擇？  
在相同的執行個體中移動資料庫檔案時，建議您使用 `ALTER DATABASE` 規劃的重新配置程序來移動資料庫，而不要使用卸離和附加。 如需詳細資訊，請參閱 [移動使用者資料庫](../../relational-databases/databases/move-user-databases.md)。 
 
不建議使用卸離和附加進行備份和復原。 這種做法不會有交易記錄檔備份，且可能會不小心刪除檔案。
  
###  <a name="Security"></a> 安全性  
檔案存取權限是在數個資料庫作業期間設定，包括卸離或附加資料庫。 如需有關卸離和附加資料庫時所設定之檔案權限的詳細資訊，請參閱《 [線上叢書》中的](https://technet.microsoft.com/library/ms189128.aspx) 保護資料和記錄檔 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] (仍然值得閱讀！) 
  
建議您不要附加或還原來源不明或來源不受信任的資料庫。 這種資料庫可能包含惡意程式碼，因此可能執行非預期的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，或是修改結構描述或實體資料庫結構而造成錯誤。 使用來源不明或來源不受信任的資料庫之前，請先在非實際執行伺服器的資料庫上執行 [DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md) ，同時檢查資料庫中的程式碼，例如預存程序或其他使用者定義程式碼。 如需附加資料庫的詳細資訊，以及附加資料庫時，對中繼資料所做變更的相關資訊，請參閱 [資料庫卸離與附加 (SQL Server)](../../relational-databases/databases/database-detach-and-attach-sql-server.md)。  
  
####  <a name="Permissions"></a> 權限  
需要 `CREATE DATABASE`、`CREATE ANY DATABASE` 或 `ALTER ANY DATABASE` 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  

### <a name="to-attach-a-database"></a>附加資料庫  
  
1.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [物件總管]中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，然後按一下以在 SSMS 中展開該執行個體檢視。  
  
2.  以滑鼠右鍵按一下 **[資料庫]** ，然後按一下 **[附加]** 。  
  
3.  在 **[附加資料庫]** 對話方塊中，若要指定要附加的資料庫，請按一下 **[加入]** ；在 **[尋找資料庫檔案]** 對話方塊中，選取資料庫所在的磁碟機、展開目錄樹狀結構，尋找並選取資料庫的 .mdf 檔案；例如：  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > Trying to select a database that is already attached generates an error.  
  
     **Databases to attach**  
     Displays information about the selected databases.  
  
     \<no column header>  
     Displays an icon indicating the status of the attach operation. The possible icons are described in the **Status** description, below).  
  
     **MDF File Location**  
     Displays the path and file name of the selected MDF file.  
  
     **Database Name**  
     Displays the name of the database.  
  
     **Attach As**  
     Optionally, specifies a different name for the database to attach as.  
  
     **Owner**  
     Provides a drop-down list of possible database owners from which you can optionally select a different owner.  
  
     **Status**  
     Displays the status of the database according to the following table.  
  
    |圖示|狀態文字|Description|  
    |----------|-----------------|-----------------|  
    |(無圖示)|(沒有文字)|附加作業尚未啟動或是針對此物件進行暫止。 當對話方塊開啟時，這是預設的動作。|  
    |綠色、指向右方的三角形|進行中|附加作業已啟動，但尚未完成。|  
    |綠色的核取記號|成功|已順利附加物件。|  
    |包含白色十字的紅色圓圈|錯誤|附加作業發生錯誤，且未順利完成。|  
    |包含兩個黑色的象限 (在左方和右方) 以及兩個白色的象限 (在上方和下方)|Stopped|附加作業未順利完成，因為使用者已停止作業。|  
    |包含指向逆時針方向之彎曲箭頭的圓圈|已回復|附加作業已順利完成，但是因為在附加其他物件的期間發生了錯誤，所以已將其回復。|  
  
     **Message**  
     Displays either a blank message or a "File not found" hyperlink.  
  
     **Add**  
     Find the necessary main database files. When the user selects an .mdf file, applicable information is automatically filled in the respective fields of the **Databases to attach** grid.  
  
     **Remove**  
     Removes the selected file from the **Databases to attach** grid.  
  
     **"** *<database_name>* **" database details**  
     Displays the names of the files to be attached. To verify or change the pathname of a file, click the **Browse** button (**...**).  
  
    > [!NOTE]  
    > If a file does not exist, the **Message** column displays "Not found." If a log file is not found, it exists in another directory or has been deleted. You need to either update the file path in the **database details** grid to point to the correct location or remove the log file from the grid. If an .ndf data file is not found, you need to update its path in the grid to point to the correct location.  
  
     **Original File Name**  
     Displays the name of the attached file belonging to the database.  
  
     **File Type**  
     Indicates the type of file, **Data** or **Log**.  
  
     **Current File Path**  
     Displays the path to the selected database file. The path can be edited manually.  
  
     **Message**  
     Displays either a blank message or a "**File not found**" hyperlink.  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
### <a name="to-attach-a-database"></a>若要附加資料庫  
  
1.  連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在標準列中，按一下 **[新增查詢]** 。  
  
3.  搭配 `FOR ATTACH` 子句使用 [CREATE DATABASE](../../t-sql/statements/create-database-sql-server-transact-sql.md) 陳述式。  
  
     複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。 這個範例會附加 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 資料庫的檔案，並將資料庫重新命名為 `MyAdventureWorks`。  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > 或者，您可以使用 [sp_attach_db](../../relational-databases/system-stored-procedures/sp-attach-db-transact-sql.md) 或 [sp_attach_single_file_db](../../relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql.md) 預存程序。 但是，Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的未來版本將移除這些程序。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 我們建議您改用 `CREATE DATABASE ... FOR ATTACH` 。  
  
##  <a name="FollowUp"></a> 後續操作：升級 SQL Server 資料庫之後  
當您使用附加方法升級資料庫之後，該資料庫會立即可用並自動升級。 如果資料庫具有全文檢索索引，升級程序就會根據 **[全文檢索目錄升級選項]** 伺服器屬性的設定，匯入、重設或重建這些索引。 如果升級選項設定為 **[匯入]** 或 **[重建]** ，則全文檢索索引在升級期間將無法使用。 根據進行索引的資料數量而定，匯入可能需要數個小時，而重建可能需要十倍以上的時間。 此外，請注意，當升級選項設定為 **[匯入]** 時，如果全文檢索目錄無法使用，系統就會重建相關聯的全文檢索索引。  
  
如果使用者資料庫的相容性層級在升級前為 100 或更高層級，則在升級後仍會保持相同。 如果升級前的相容性層級為 90，則在升級後的資料庫中，相容性層級會設定為 100 (這是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 所支援的最低相容性層級)。 如需詳細資訊，請參閱 [ALTER DATABASE 相容性層級 &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)。  
  
> [!NOTE]
> 如果您是從執行已啟用異動資料擷取 (CDC) 之 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 或以下版本的執行個體附加資料庫，則也必須執行下列命令來升級異動資料擷取 (CDC) 中繼資料。
  
```sql
USE <database name>
EXEC sys.sp_cdc_vupgrade  
``` 
 
## <a name="see-also"></a>另請參閱  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md) 
 <br>[管理在另一部伺服器上提供資料庫時所需的中繼資料](manage-metadata-when-making-a-database-available-on-another-server.md)  
 [卸離資料庫](../../relational-databases/databases/detach-a-database.md)  
  
  
