---
title: 將檔案還原到新位置 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring files [SQL Server], how-to topics
- restoring databases [SQL Server], moving
- restoring files [SQL Server], steps
- file restores [SQL Server], how-to topics
- filegroups [SQL Server], restoring
- restoring filegroups [SQL Server]
ms.assetid: b4f4791d-646e-4632-9980-baae9cb1aade
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 5d3d3ddc6d14414344e847249cb337e9f6a0d5c2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041526"
---
# <a name="restore-files-to-a-new-location-sql-server"></a>將檔案還原到新位置 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中將檔案還原到新位置。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [安全性](#Security)  
  
-   **若要使用下列項目將檔案還原到新位置：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   負責還原檔案的系統管理員，必須是目前唯一正在使用即將還原之資料庫的人。  
  
-   在明確或隱含的交易中，不允許使用 RESTORE。  
  
-   在完整或大量記錄復原模式下，您必須先備份使用中的交易記錄 (也稱為記錄的結尾)，才能還原檔案。 如需詳細資訊，請參閱 [備份交易記錄 &#40;SQL Server&#41;](../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)中還原檔案與檔案群組。  
  
-   若要還原加密的資料庫，您必須能夠存取之前用來加密資料庫的憑證或非對稱金鑰。 如果沒有該憑證或非對稱金鑰，就無法還原資料庫。 因此，只要需要備份，就必須保留用來加密資料庫加密金鑰的憑證。 如需詳細資訊，請參閱 [SQL Server Certificates and Asymmetric Keys](../../relational-databases/security/sql-server-certificates-and-asymmetric-keys.md)。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。 如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。  
  
 RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。 由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-restore-files-to-a-new-location"></a>若要將檔案還原到新位置  
  
1.  在 [物件總管]  中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]的執行個體，展開該執行個體，然後展開 [資料庫]  。  
  
2.  以滑鼠右鍵按一下所要的資料庫，依序指向 [工作]  與 [還原]  ，然後按一下 [檔案與檔案群組]  。  
  
3.  在 **[一般]** 頁面上的 **[目的地資料庫]** 清單方塊，輸入要還原的資料庫。 您可以輸入新的資料庫，或者從下拉式清單中選擇現有的資料庫。 清單包含伺服器上的所有資料庫，排除系統資料庫 **master** 和 **tempdb**。  
  
4.  若要指定要還原之備份組的來源與位置，請按一下下列任一個選項：  
  
    -   **來源資料庫**  
  
         在清單方塊中輸入資料庫名稱。 此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。  
  
    -   **來源裝置**  
  
         按一下 [瀏覽] 按鈕。 在 **[指定備份裝置]** 對話方塊中，選取 **[備份媒體類型]** 清單方塊上列出的其中一個裝置類型。 若要選取 **[備份媒體]** 清單方塊的一個或多個裝置，請按一下 **[加入]** 。  
  
         將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。  
  
5.  在 **[選取要還原的備份組]** 方格中，選取要還原的備份。 這個方格會顯示指定位置可用的備份。 依預設，會建議一個復原計畫。 若要覆寫建議的復原計畫，您可以變更方格中的選取項目。 任何相依於已取消選取備份的備份，會自動被取消選取。  
  
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
  
6.  在 **[選取頁面]** 窗格中，按一下 **[選項]** 頁面。  
  
7.  在 **[將資料庫檔案還原為]** 方格中，為要移動的檔案指定新位置。  
  
    |資料行標頭|值|  
    |-----------------|------------|  
    |**原始檔案名稱**|來源備份檔案的完整路徑。|  
    |**檔案類型**|指定備份中的資料類型：[資料]  、[記錄]  或 [Filestream 資料]  。 資料表中所包含的資料位於 **[資料]** 檔案中。 交易記錄資料位於 **[記錄檔]** 中。 儲存在檔案系統上的二進位大型物件 (BLOB) 資料位於 [Filestream 資料]  檔案中。|  
    |**還原成**|還原資料庫檔案的完整路徑。 若要指定新的還原檔案，請按一下文字方塊並編輯建議的路徑與檔案名稱。 變更 **[還原成]** 資料行中的路徑或檔案名稱相當於使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] RESTORE 陳述式中的 MOVE 選項。|  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-restore-files-to-a-new-location"></a>若要將檔案還原到新位置  
  
1.  選擇性執行 RESTORE FILELISTONLY 陳述式，以決定完整資料庫備份中之檔案的數目和名稱。  
  
2.  執行 RESTORE DATABASE 陳述式以還原完整資料庫備份，請指定：  
  
    -   所要還原的資料庫名稱。  
  
    -   將要還原完整資料庫備份的來源備份裝置。  
  
    -   替要還原的每個檔案指定 MOVE 子句，將其還原到新位置上。  
  
    -   NORECOVERY 子句。  
  
3.  如果檔案在備份建立之後做過修改，則請執行 RESTORE LOG 陳述式以套用交易記錄備份，並指定下列項目：  
  
    -   交易記錄檔要套用的資料庫名稱。  
  
    -   用於還原交易記錄備份的備份裝置。  
  
    -   倘若在目前的交易記錄備份之後還有另一個交易記錄備份要套用，請指定 NORECOVERY 子句，否則請指定 RECOVERY 子句。  
  
         您所套用的交易記錄備份必須涵蓋檔案和檔案群組備份的時間。  
  
###  <a name="TsqlExample"></a> 範例 &#40;Transact-SQL&#41;  
 此範例會將原本位於磁碟機 C 的兩個 `MyNwind` 資料庫的檔案還原到磁碟機 D 上的新位置。此外，也會套用兩個交易記錄檔，以將資料庫還原到目前的時間。 `RESTORE FILELISTONLY` 陳述式是用來決定資料庫中所要還原的檔案數目及其邏輯與實體名稱。  
  
```sql  
USE master;  
GO  
-- First determine the number and names of the files in the backup.  
RESTORE FILELISTONLY  
   FROM MyNwind_1;  
-- Restore the files for MyNwind.  
RESTORE DATABASE MyNwind  
   FROM MyNwind_1  
   WITH NORECOVERY,  
   MOVE 'MyNwind_data_1' TO 'D:\MyData\MyNwind_data_1.mdf',   
   MOVE 'MyNwind_data_2' TO 'D:\MyData\MyNwind_data_2.ndf';  
GO  
-- Apply the first transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log1  
   WITH NORECOVERY;  
GO  
-- Apply the last transaction log backup.  
RESTORE LOG MyNwind  
   FROM MyNwind_log2  
   WITH RECOVERY;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [Restore a Database Backup Using SSMS](../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)   
 [RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)   
 [使用備份與還原複製資料庫](../../relational-databases/databases/copy-databases-with-backup-and-restore.md)   
 [還原檔案和檔案群組 &#40;SQL Server&#41;](../../relational-databases/backup-restore/restore-files-and-filegroups-sql-server.md)  
  
  
