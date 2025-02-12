---
title: sp_replicationdboption (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac51409db23f4b8eefb3616d5daf5ca43b3ab0f6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771247"
---
# <a name="spreplicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  設定指定資料庫的複寫資料庫選項。 這個預存程序執行於任何資料庫的發行者端或訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>引數  
 [ **@dbname=** ] **'***dbname***'**  
 這是要設定複寫資料庫選項的資料庫。 *db_name*是**sysname**, 沒有預設值。  
  
 [ **@optname=** ] **'***optname***'**  
 這是要啟用或停用的複寫資料庫選項。 *optname*是**sysname**, 它可以是下列其中一個值。  
  
|值|描述|  
|-----------|-----------------|  
|**合併發行**|可用於合併式發行集的資料庫。|  
|**publish**|資料庫可用於其他類型的發行集。|  
|**subscribe**|資料庫是訂閱資料庫。|  
|**與備份同步**|啟用資料庫的協調備份。 如需詳細資訊, 請參閱[啟用異動複寫&#40;複寫 transact-sql 程式設計&#41;的協調備份](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md)。|  
  
`[ @value = ] 'value'`這是指是否要啟用或停用給定的複寫資料庫選項。 *值*為**sysname**, 而且可以是**true**或**false**。 當此值為**false**且*optname*為**merge publish**時, 也會卸載合併發行資料庫的訂閱。  
  
`[ @ignore_distributor = ] ignore_distributor`指出是否在未連接到散發者的情況下執行此預存程式。 *ignore_distributor*是**bit**, 預設值是**0**, 表示散發者應該連接到發行資料庫的新狀態並加以更新。 只有在無法存取散發者, 而且**sp_replicationdboption**正用來停用發行時, 才應該指定值**1** 。  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或**1** (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_replicationdboption**用於快照式複寫、異動複寫和合併式複寫中。  
  
 隨著給定的選項而不同，這個程序會建立或卸除特定複寫系統資料表、安全性帳戶等。 在**sysdatabases**系統資料表中設定對應的分類位, 並建立必要的系統資料表。  
  
 若要停用發行，發行集資料庫必須在線上。 如果發行集資料庫的資料庫快照集存在，您必須先卸除它，才能停用發行。 資料庫快照集是資料庫的唯讀離線複本，與複寫快照集無關。 如需詳細資訊，請參閱[資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)。  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色的成員, 才能夠執行**sp_replicationdboption**。  
  
## <a name="see-also"></a>另請參閱  
 [設定發行和散發](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [刪除發行集](../../relational-databases/replication/publish/delete-a-publication.md)   
 [停用發行和散發](../../relational-databases/replication/disable-publishing-and-distribution.md)   
 [sysdatabases &#40;transact-sql&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
