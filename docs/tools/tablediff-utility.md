---
title: tablediff 公用程式 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- comparing data
- tablediff utility
- tables [SQL Server replication]
- table comparisons [SQL Server]
- command prompt utilities [SQL Server], tablediff
- troubleshooting [SQL Server replication], non-convergence
- non-convergence [SQL Server]
ms.assetid: 3c3cb865-7a4d-4d66-98f2-5935e28929fc
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017'
ms.openlocfilehash: 48fc2d25bc65e76156da80c6b6117a62fa39e2a3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67986042"
---
# <a name="tablediff-utility"></a>tablediff 公用程式
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  **tablediff** 公用程式用來比較兩份資料表之資料的非聚合狀況，當進行複寫拓撲中之非聚合狀況的疑難排解時，它尤其有用。 您可以在命令提示字元之下，或在批次檔中，利用這個公用程式來執行下列工作：  
  
-   在扮演複寫簽發者之 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的來源資料表，與扮演複製訂閱者的一或多個 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的目的地資料表之間，每個資料列做比較。  
  
-   執行快速比較，只比較資料列計數和結構描述。  
  
-   進行資料行層級的比較。  
  
-   產生 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼來修正目的地伺服器不一致的情形，以便聚合來源和目的地資料表。  
  
-   將結果記錄在輸出檔中，或記錄在目的地資料庫的資料表中。  
  
## <a name="syntax"></a>語法  
  
```  
  
tablediff   
[ -? ] |   
{  
        -sourceserver source_server_name[\instance_name]  
        -sourcedatabase source_database  
        -sourcetable source_table_name   
    [ -sourceschema source_schema_name ]  
    [ -sourcepassword source_password ]  
    [ -sourceuser source_login ]  
    [ -sourcelocked ]  
        -destinationserver destination_server_name[\instance_name]  
        -destinationdatabase subscription_database   
        -destinationtable destination_table   
    [ -destinationschema destination_schema_name ]  
    [ -destinationpassword destination_password ]  
    [ -destinationuser destination_login ]  
    [ -destinationlocked ]  
    [ -b large_object_bytes ]   
    [ -bf number_of_statements ]   
    [ -c ]   
    [ -dt ]   
    [ -et table_name ]   
    [ -f [ file_name ] ]   
    [ -o output_file_name ]   
    [ -q ]   
    [ -rc number_of_retries ]   
    [ -ri retry_interval ]   
    [ -strict ]  
    [ -t connection_timeouts ]   
}  
```  
  
## <a name="arguments"></a>引數  
 [ **-?** ]  
 傳回支援的參數清單。  
  
 **-sourceserver** _source_server_name_[ **\\** _instance\_name_]  
 這是來源伺服器的名稱。 指定 *預設執行個體的* source_server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 指定 _具名執行個體的_ **\\** _source_server_name_ instance_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。  
  
 **-sourcedatabase** _source_database_  
 這是來源資料庫的名稱。  
  
 **-sourcetable** _source_table_name_  
 這是所檢查的來源資料表的名稱。  
  
 **-sourceschema** _source_schema_name_  
 來源資料表的結構描述擁有者。 依預設，資料表擁有者假設為 dbo。  
  
 **-sourcepassword** _source_password_  
 這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之來源伺服器的登入密碼。  
  
> [!IMPORTANT]  
>  可能的話，請在執行階段提供安全性認證。 如果您必須將認證儲存在指令碼檔案中，您應該維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
 **-sourceuser** _source_login_  
 這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之來源伺服器的登入。 如果未提供 *source_login* ，在連接到來源伺服器時，會使用 Windows 驗證。 [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-sourcelocked**  
 在比較期間，來源資料表以 TABLOCK 和 HOLDLOCK 資料表提示鎖定。  
  
 **-destinationserver** _destination_server_name_[ **\\** _instance_name_]  
 這是目的地伺服器的名稱。 指定 *預設執行個體的* destination_server_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 指定 _具名執行個體的_ **\\** _destination_server_name_ instance_name [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。  
  
 **-destinationdatabase** _subscription_database_  
 這是目的地資料庫的名稱。  
  
 **-destinationtable** _destination_table_  
 這是目的地資料表的名稱。  
  
 **-destinationschema** _destination_schema_name_  
 目的地資料表的結構描述擁有者。 依預設，資料表擁有者假設為 dbo。  
  
 **-destinationpassword** _destination_password_  
 這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之目的地伺服器的登入密碼。  
  
> [!IMPORTANT]  
>  可能的話，請在執行階段提供安全性認證。 如果您必須將認證儲存在指令碼檔案中，您應該維護這個檔案的安全性，使他人無法在未獲授權的情況下擅自存取。  
  
 **-destinationuser** _destination_login_  
 這是用來連接使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證之目的地伺服器的登入。 如果未提供 *destination_login* ，在連接到伺服器時，會使用 Windows 驗證。 [!INCLUDE[ssNoteWinAuthentication](../includes/ssnotewinauthentication-md.md)]  
  
 **-destinationlocked**  
 在比較期間，目的地資料表以 TABLOCK 和 HOLDLOCK 資料表提示鎖定。  
  
 **-b** _large_object_bytes_  
 是大型物件資料類型資料行要比較的位元組數，包括︰ **text**、 **ntext**、 **image**、 **varchar(max)** 、 **nvarchar(max)** 和 **varbinary(max)** 。 *large_object_bytes* 預設為資料行的大小。 不比較任何超出 *large_object_bytes* 的資料。  
  
 **-bf**  _number_of_statements_  
 這是使用 [!INCLUDE[tsql](../includes/tsql-md.md)] -f [!INCLUDE[tsql](../includes/tsql-md.md)] 選項時要寫入目前 **指令碼檔案中的** 陳述式數目。 當 [!INCLUDE[tsql](../includes/tsql-md.md)] 陳述式數目超出 *number_of_statements*時，會建立新的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼檔案。  
  
 **-c**  
 比較資料行層級的差異。  
  
 **-dt**  
 卸除 *table_name*指定的結果資料表 (如果該資料表已存在的話)。  
  
 **-et** _table_name_  
 指定要建立的結果資料表名稱。 如果這份資料表已經存在，就必須使用 **-DT** ，否則作業會失敗。  
  
 **-f** [ *file_name* ]  
 產生一份 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼來聚合目的地伺服器的資料表與來源伺服器的資料表。 您可以選擇性地為所產生的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼檔案指定名稱和路徑。 如果未指定 *file_name* ， [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼檔案會產生在執行公用程式的目錄中。  
  
 **-o** _output_file_name_  
 這是輸出檔的完整名稱和路徑。  
  
 **-q**  
 執行快速比較，只比較資料列計數和結構描述。  
  
 **-rc** _number_of_retries_  
 公用程式重試失敗作業的次數。  
  
 **-ri**  _retry_interval_  
 兩次重試之間等待的間隔秒數。  
  
 **-strict**  
 嚴格比較來源和目的地結構描述。  
  
 **-t** _connection_timeouts_  
 設定通往來源伺服器和目的地伺服器之連接的連接逾時期限 (以秒為單位)。  
  
## <a name="return-value"></a>傳回值  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**0**|成功|  
|**1**|嚴重錯誤|  
|**2**|資料表差異|  
  
## <a name="remarks"></a>Remarks  
 **tablediff** 公用程式不能與非 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 伺服器搭配使用。  
  
 不支援具有 **sql_variant** 資料類型資料行的資料表。  
  
 根據預設， **tablediff** 公用程式支援來源和目的地資料行之間的下列資料類型對應。  
  
|來源資料類型|目的地資料類型|  
|----------------------|---------------------------|  
|**tinyint**|**smallint**、 **int**或 **bigint**|  
|**smallint**|**int** 或 **bigint**|  
|**int**|**bigint**|  
|**timestamp**|**varbinary**|  
|**varchar(max)**|**text**|  
|**nvarchar(max)**|**ntext**|  
|**varbinary(max)**|**image**|  
|**text**|**varchar(max)**|  
|**ntext**|**nvarchar(max)**|  
|**image**|**varbinary(max)**|  
  
 使用 **-strict** 選項可禁止這些對應並執行嚴格驗證。  
  
 比較中的來源資料表必須至少包含一個主索引鍵、身分識別或 ROWGUID 資料行。 當您使用 **-strict** 選項時，目的地資料表也必須有主索引鍵、識別或 ROWGUID 資料行。  
  
 為了使目的地資料表達到聚合而產生的 [!INCLUDE[tsql](../includes/tsql-md.md)] 指令碼不包括下列資料類型：  
  
-   **varchar(max)**  
  
-   **nvarchar(max)**  
  
-   **varbinary(max)**  
  
-   **timestamp**  
  
-   **xml**  
  
-   **text**  
  
-   **ntext**  
  
-   **image**  
  
## <a name="permissions"></a>權限  
 若要比較資料表，您必須具有所比較之資料表物件的 SELECT ALL 權限。  
  
 若要使用 **-et** 選項，您必須是 db_owner 固定資料庫角色的成員，或至少具有訂閱資料庫中的 CREATE TABLE 權限，或目的地伺服器之目的地擁有者結構描述的 ALTER 權限。  
  
 若要使用 **-dt** 選項，您必須是 db_owner 固定資料庫角色的成員，或至少具有目的地伺服器之目的地擁有者結構描述的 ALTER 權限。  
  
 若要使用 **-o** 或 **-f** 選項，您必須具有指定檔案目錄位置的寫入權限。  
  
## <a name="see-also"></a>另請參閱  
 [比較複寫資料表的差異 &#40;複寫程式設計&#41;](../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md)  
  
  
