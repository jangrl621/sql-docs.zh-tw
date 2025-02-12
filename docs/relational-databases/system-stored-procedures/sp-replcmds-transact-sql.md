---
title: sp_replcmds (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replcmds_TSQL
- sp_replcmds
helpviewer_keywords:
- sp_replcmds
ms.assetid: 7e932f80-cc6e-4109-8db4-2b7c8828df73
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3d60de0f459ec1224f6023e8ee848227fdc17ece
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771012"
---
# <a name="spreplcmds-transact-sql"></a>sp_replcmds (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  傳回含複寫標示之交易的命令。 這個預存程序執行於發行集資料庫的發行者端。  
  
> [!IMPORTANT]  
>  **Sp_replcmds**程式應該只執行以疑難排解複寫的問題。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_replcmds [ @maxtrans = ] maxtrans  
```  
  
## <a name="arguments"></a>引數  
`[ @maxtrans = ] maxtrans`這是要傳回相關資訊的交易數目。 *maxtrans*是**int**, 預設值是**1**, 指定下一個等待散發的交易。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**發行項識別碼**|**int**|發行項的識別碼。|  
|**partial_command**|**bit**|指出這是否為部分命令。|  
|**command**|**varbinary(1024)**|命令值。|  
|**xactid**|**binary(10)**|交易識別碼。|  
|**xact_seqno**|**varbinary(16)**|交易序號。|  
|**publication_id**|**int**|發行集的識別碼。|  
|**command_id**|**int**|[MSrepl_commands](../../relational-databases/system-tables/msrepl-commands-transact-sql.md)中的命令識別碼。|  
|**command_type**|**int**|命令的類型。|  
|**originator_srvname**|**sysname**|引發交易的伺服器。|  
|**originator_db**|**sysname**|引發交易的資料庫。|  
|**pkHash**|**int**|僅供內部使用。|  
|**originator_publication_id**|**int**|引發交易的發行集識別碼。|  
|**originator_db_version**|**int**|引發交易的資料庫版本。|  
|**originator_lsn**|**varbinary(16)**|識別命令在原始發行集中的記錄序號 (LSN)。|  
  
## <a name="remarks"></a>備註  
 **sp_replcmds**是由異動複寫中的記錄讀取器進程所使用。  
  
 複寫會將在給定資料庫內執行**sp_replcmds**的第一個用戶端, 視為記錄讀取器。  
  
 這個程序可以產生以擁有者來限定之資料表的命令，或不限定資料表名稱 (預設值)。 加入限定的資料表名稱，可讓您將某資料庫中特定使用者所擁有之資料表的資料，複寫到另一個資料庫中相同使用者所擁有的資料表。  
  
> [!NOTE]  
>  由於來源資料庫中的資料表名稱是以擁有者名稱來限定的，因此，目標資料庫中之資料表的擁有者必須是相同的擁有者名稱。  
  
 嘗試在相同資料庫內執行**sp_replcmds**的用戶端會收到錯誤 18752, 直到第一個用戶端中斷連線為止。 第一個用戶端中斷連線之後, 另一個用戶端可以執行**sp_replcmds**, 並成為新的記錄讀取器。  
  
 如果**sp_replcmds**無法複寫文字命令, 則會在[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]錯誤記錄檔和[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 應用程式記錄檔中加入警告訊息編號 18759, 因為不會在相同的中抓取文字指標事務.  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色或**db_owner**固定資料庫角色的成員, 才能夠執行**sp_replcmds**。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤訊息](../../relational-databases/native-client-odbc-error-messages/error-messages.md)   
 [sp_repldone &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repldone-transact-sql.md)   
 [sp_replflush &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replflush-transact-sql.md)   
 [sp_repltrans &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-repltrans-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
