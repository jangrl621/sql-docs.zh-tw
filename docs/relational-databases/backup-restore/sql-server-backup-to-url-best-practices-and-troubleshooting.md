---
title: SQL Server 備份至 URL 的最佳做法和疑難排解 | Microsoft Docs
ms.custom: ''
ms.date: 03/25/2019
ms.prod: sql
ms.prod_service: backup-restore
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: de676bea-cec7-479d-891a-39ac8b85664f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c4c93f36ca78bbd6cdeedf8d88314f7374f34a9a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68041385"
---
# <a name="sql-server-backup-to-url-best-practices-and-troubleshooting"></a>SQL Server 備份至 URL 的最佳作法和疑難排解
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  本主題包含從 SQL Server 備份及還原至 Windows Azure Blob 服務的最佳作法和疑難排解提示。  
  
 如需有關使用 Windows Azure Blob 儲存體服務進行 SQL Server 備份或還原作業的詳細資訊，請參閱：  
  
-   [使用 Microsoft Azure Blob 儲存體服務進行 SQL Server 備份及還原](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)  
  
-   [教學課程：SQL Server 備份及還原至 Windows Azure Blob 儲存體服務](../../relational-databases/tutorial-sql-server-backup-and-restore-to-azure-blob-storage-service.md)  
  
## <a name="managing-backups"></a>管理備份  
 下列清單包含管理備份的一般建議：  
  
-   建議針對每個備份使用唯一的檔案名稱，避免不小心覆寫 Blob。  
  
-   建立容器時，建議您將存取層級設定為 [私用]  ，如此只有能夠提供必要驗證資訊的使用者或帳戶才能讀取或寫入容器中的 Blob。  
  
-   如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫位於 Microsoft Azure 虛擬機器中執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上，請使用與虛擬機器位於相同地區的儲存體帳戶，避免產生不同地區之間的資料傳輸成本。 使用相同的地區也可以確保備份與還原作業達到最佳效能。  
  
-   失敗的備份活動可能會產生無效的備份檔案。 我們建議您定期識別失敗的備份並刪除 Blob 檔案。 如需詳細資訊，請參閱[刪除擁有使用中租用的備份 Blob 檔案](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)  
  
-   在備份期間使用 `WITH COMPRESSION` 選項可以將您的儲存體成本和儲存體交易成本降到最低程度。 它也可以減少完成備份程序所需的時間。  

- 遵循 [SQL Server 備份至 URL](./sql-server-backup-to-url.md) 中的建議設定 `MAXTRANSFERSIZE` 和 `BLOCKSIZE` 引數。
  
## <a name="handling-large-files"></a>處理大型檔案  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份作業會使用多個執行緒來最佳化 Windows Azure Blob 儲存體服務的資料傳輸。  不過，其效能取決於各種因素，例如 ISV 頻寬和資料庫的大小。 如果您計畫要備份內部部署 SQL Server 資料庫中的大型資料庫或檔案群組，建議您先進行一些輸送量測試。 Azure [儲存體 SLA](https://azure.microsoft.com/support/legal/sla/storage/v1_0/) 具有最大的 Blob 處理時間，您可以參考使用。  
  
-   備份大型檔案時，務必遵循[管理備份](##managing-backups)一節中的建議使用 `WITH COMPRESSION` 選項。  
  
## <a name="troubleshooting-backup-to-or-restore-from-url"></a>疑難排解備份至 URL 或從中還原  
 以下是一些快速疑難排解備份至 Windows Azure Blob 儲存體服務或從中還原時發生之錯誤的方法。  
  
 若要避免由於不支援的選項或限制而發生的錯誤，請在 [使用 Microsoft Azure Blob 儲存體服務進行 SQL Server 備份及還原](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md) 文章中檢閱限制的清單，以及支援 BACKUP 和 RESTORE 命令的資訊。  
  
 **驗證錯誤：**  
  
-   `WITH CREDENTIAL` 是新的選項，而且必須在備份至 Microsoft Azure Blob 儲存體服務或從中還原時使用。 與認證有關的失敗可能包括：  
  
     **BACKUP** 或 **RESTORE** 命令中指定的認證不存在。 若要避免此問題，您可以在 Backup 陳述式中加入 T-SQL 陳述式來建立認證 (如果認證不存在的話)。 以下是您可以使用的範例：  
  
    ```sql  
    IF NOT EXISTS  
    (SELECT * FROM sys.credentials   
    WHERE credential_identity = 'mycredential')  
    CREATE CREDENTIAL <credential name> WITH IDENTITY = 'mystorageaccount'  
    ,SECRET = '<storage access key> ;  
    ```  
  
-   認證存在，但是用來執行 Backup 命令的登入帳戶沒有存取認證的權限。 請使用具備 **更改任何認證** 權限的 ***db_backupoperator*** 角色登入帳戶。  
  
-   確認儲存體帳戶名稱與金鑰值。 儲存在認證中的資訊必須符合您在備份和還原作業中使用之 Windows Azure 儲存體帳戶的屬性值。  
  
 **備份錯誤/失敗：**  
  
-   相同 Blob 的平行備份會導致其中一個備份失敗並出現 [初始化失敗]  錯誤。  
  
-   使用下列錯誤記錄來協助疑難排解備份錯誤：  
  
    -   您可以使用下列格式來設定追蹤旗標 3051，以便記錄至特定錯誤記錄：  
  
        `BackupToUrl-\<instname>-\<dbname>-action-\<PID>.log`，其中 `\<action>` 是下列其中之一：  
  
        -   **DB**  
        -   **FILELISTONLY**  
        -   **LABELONLY**  
        -   **HEADERONLY**  
        -   **VERIFYONLY**  
  
    -   您也可以透過檢閱 Windows 事件記錄檔 (在名為 `SQLBackupToUrl` 的應用程式記錄底下)，尋找相關資訊。  

    -   備份大型資料庫時，請考慮 COMPRESSION、MAXTRANSFERSIZE、BLOCKSIZE 和多個 URL 引數。  請參閱[將 VLDB 備份至 Azure Blob 儲存體](https://blogs.msdn.microsoft.com/sqlcat/2017/03/10/backing-up-a-vldb-to-azure-blob-storage/)
  
        ```
        Msg 3202, Level 16, State 1, Line 1
        Write on "https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak" failed: 1117(The request could not be performed because of an I/O device error.)
        Msg 3013, Level 16, State 1, Line 1
        BACKUP DATABASE is terminating abnormally.
        ```

        ```sql  
        BACKUP DATABASE TestDb
        TO URL = 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak',
        URL = 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_1.bak',
        URL = 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_2.bak'
        WITH COMPRESSION, MAXTRANSFERSIZE = 4194304, BLOCKSIZE = 65536;  
        ```  

-   從壓縮備份還原時，您可能會看見下列錯誤：  
  
    -   `SqlException 3284 occurred. Severity: 16 State: 5  
        Message Filemark on device 'https://mystorage.blob.core.windows.net/mycontainer/TestDbBackupSetNumber2_0.bak' is not aligned.           Reissue the Restore statement with the same block size used to create the backupset: '65536' looks like a possible value.`  
  
        若要解決此錯誤，請重新發出 **RESTORE** 陳述式並搭配指定 **BLOCKSIZE = 65536**。  
  
-   含有使用中租用的 Blob 導致備份期間發生錯誤：失敗的備份活動可能會產生含有使用中租用的 Blob。  
  
     如果重新嘗試執行 Backup 陳述式，備份作業可能會失敗並出現類似以下的錯誤：  
  
     `Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (412) There is currently a lease on the blob and no lease ID was specified in the request.`  
  
     如果針對擁有使用中租用的備份 Blob 檔案執行 Restore 陳述式，還原作業會失敗並出現類似以下的錯誤：  
  
     `Exception Message: The remote server returned an error: (409) Conflict..`  
  
     發生這類錯誤時，您必須刪除 Blob 檔案。 如需有關此案例以及如何更正這個問題的詳細資訊，請參閱 [刪除擁有使用中租用的備份 Blob 檔案](../../relational-databases/backup-restore/deleting-backup-blob-files-with-active-leases.md)  
  
## <a name="proxy-errors"></a>Proxy 錯誤  
 如果您使用 Proxy 伺服器存取網際網路，可能會看見下列問題：  
  
 **Proxy 伺服器連線節流：**  
  
 Proxy 伺服器可能有限制每分鐘連接數目的設定。 備份至 URL 處理序是一個多執行緒處理序，因此可能會超出此限制。 如果發生這種情況，Proxy 伺服器會清除該連接。 若要解決這個問題，請變更 Proxy 設定，讓 SQL Server 不使用 Proxy。 以下是您可能在錯誤記錄檔中看到的類型或錯誤訊息的部分範例：  
  
```
Write on "https://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak" failed: Backup to URL received an exception from the remote endpoint. Exception Message: Unable to read data from the transport connection: The connection was closed.
```  
  
```
A nonrecoverable I/O error occurred on file "https://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Error could not be gathered from Remote Endpoint.  
  
Msg 3013, Level 16, State 1, Line 2  
  
BACKUP DATABASE is terminating abnormally.  
```

```
BackupIoRequest::ReportIoError: write failure on backup device https://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak'. Operating system error Backup to URL received an exception from the remote endpoint. Exception Message: Unable to read data from the transport connection: The connection was closed.
```  
  
如果您使用追蹤旗標 3051 開啟詳細資訊記錄，可能也會在記錄檔中看到下列資訊：  
  
`HTTP status code 502, HTTP Status Message Proxy Error (The number of HTTP requests per minute exceeded the configured limit. Contact your ISA Server administrator.)` 
  
 **預設 Proxy 設定未收取：**  
  
有時預設設定未收取會導致 Proxy 驗證錯誤，如下所示：
 
 `A nonrecoverable I/O error occurred on file "https://storageaccount.blob.core.windows.net/container/BackupAzurefile.bak:" Backup to URL received an exception from the remote endpoint. Exception Message: The remote server returned an error: (407)* **Proxy Authentication Required.`  
  
若要解決這個問題，使用下列步驟建立組態檔，讓備份至 URL 處理序可以使用預設 Proxy 設定：  
  
1.  建立具有下列 XML 內容的設定檔，名稱為 `BackuptoURL.exe.config`：  
  
    ```xml  
    <?xml version ="1.0"?>  
    <configuration>   
                    <system.net>   
                                    <defaultProxy enabled="true" useDefaultCredentials="true">   
                                                    <proxy usesystemdefault="true" />   
                                    </defaultProxy>   
                    </system.net>  
    </configuration>  
    ```  
  
2.  將設定檔放在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 Binn 資料夾。 例如，如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安裝在電腦的 C 磁碟機上，請將設定檔放在 `C:\Program Files\Microsoft SQL Server\MSSQL13.\<InstanceName>\MSSQL\Binn` 中。  
  
## <a name="see-also"></a>另請參閱  
 [從儲存在 Microsoft Azure 的備份還原](../../relational-databases/backup-restore/restoring-from-backups-stored-in-microsoft-azure.md)  
[BACKUP (Transact-SQL)](../../t-sql/statements/backup-transact-sql.md)  
[RESTORE (Transact-SQL)](../../t-sql/statements/restore-statements-transact-sql.md)
  
