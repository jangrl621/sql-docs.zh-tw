---
title: sp_helparticle (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helparticle_TSQL
- sp_helparticle
helpviewer_keywords:
- sp_helparticle
ms.assetid: 9c4a1a88-56f1-45a0-890c-941b8e0f0799
author: stevestein
ms.author: sstein
ms.openlocfilehash: e1e71d3795b233ec335cf01848fa3b226a6ebde0
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771104"
---
# <a name="sphelparticle-transact-sql"></a>sp_helparticle (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  顯示發行項的相關資訊。 這個預存程序執行於發行集資料庫的發行者端。 如果是 Oracle 發行者，這個預存程序執行於任何資料庫中的散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_helparticle [ @publication = ] 'publication'   
    [ , [ @article = ] 'article' ]  
    [ , [ @returnfilter = ] returnfilter ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @found = ] found OUTPUT ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'`這是發行集的名稱。 *發行*集是**sysname**, 沒有預設值。  
  
`[ @article = ] 'article'`這是發行集中的發行項名稱。 發行項 **%** 是 sysname, 預設值是。 如果未提供發行項, 則會傳回指定之發行集的所有文章相關資訊。  
  
`[ @returnfilter = ] returnfilter`指定是否應該傳回篩選子句。 *returnfilter*是**bit**, 預設值是**1**, 會傳回篩選子句。  
  
`[ @publisher = ] 'publisher'`指定非[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。 *publisher*是**sysname**, 預設值是 Null。  
  
> [!NOTE]  
>  要求[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者發行之發行項的資訊時, 不應指定發行者。  
  
`[ @found = ] found OUTPUT`僅供內部使用。  
  
## <a name="result-sets"></a>結果集  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**發行項識別碼**|**int**|發行項的識別碼。|  
|**發行項名稱**|**sysname**|發行項的名稱。|  
|**基底物件**|**nvarchar(257)**|發行項或預存程序所代表之基礎資料表的名稱。|  
|**目的地物件**|**sysname**|目的地 (訂閱) 資料表的名稱。|  
|**同步處理物件**|**nvarchar(257)**|定義已發行的發行項之檢視的名稱。|  
|**type**|**smallint**|發行項的類型：<br /><br /> **1** = 以記錄為基礎。<br /><br /> **3** = 以手動篩選進行記錄式。<br /><br /> **5** = 以手動視圖進行記錄式。<br /><br /> **7** = 以手動篩選和手動視圖進行記錄式。<br /><br /> **8** = 預存程式執行。<br /><br /> **24** = 可序列化預存程式執行。<br /><br /> **32** = 預存程式 (僅限架構)。<br /><br /> **64** = View (僅限架構)。<br /><br /> **96** = 彙總函式 (僅限架構)。<br /><br /> **128** = 函數 (僅限架構)。<br /><br /> **257** = 以記錄為基礎的索引視圖。<br /><br /> **259** = 具有手動篩選的以記錄為基礎的索引視圖。<br /><br /> **261** = 具有手動視圖之以記錄為基礎的索引視圖。<br /><br /> **263** = 具有手動篩選和手動視圖的記錄式索引視圖。<br /><br /> **320** = 索引視圖 (僅限架構)。<br /><br />|  
|**status**|**tinyint**|可以是一或多個或這些發行項屬性的[& (位 and)](../../t-sql/language-elements/bitwise-and-transact-sql.md)結果:<br /><br /> **0x00** = [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]<br /><br /> **0x01** = 發行項在使用中。<br /><br /> **0x08** = 在 insert 語句中包含資料行名稱。<br /><br /> **0x16** = 使用參數化語句。<br /><br /> **0x32** = 使用參數化語句, 並在 insert 語句中包含資料行名稱。|  
|**filter**|**nvarchar(257)**|用來水平篩選資料表的預存程序。 必須已利用 FOR REPLICATION 子句來建立這個預存程序。|  
|**description**|**nvarchar(255)**|發行項的描述項目。|  
|**insert_command**|**nvarchar(255)**|當隨著資料表發行項而複寫插入時，所用的複寫命令類型。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。|  
|**update_command**|**nvarchar(255)**|當隨著資料表發行項而複寫更新時，所用的複寫命令類型。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。|  
|**delete_command**|**nvarchar(255)**|當隨著資料表發行項而複寫刪除時，所用的複寫命令類型。 如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../../relational-databases/replication/transactional/transactional-articles-specify-how-changes-are-propagated.md)。|  
|**建立腳本路徑**|**nvarchar(255)**|用來建立目標資料表之發行項結構描述指令碼的路徑和名稱。|  
|**垂直資料分割**|**bit**|這是指是否啟用發行項的垂直資料分割;**1**的值表示已啟用垂直資料分割。|  
|**pre_creation_cmd**|**tinyint**|DROP TABLE、DELETE TABLE 或 TRUNCATE 的預先建立命令：|  
|**filter_clause**|**ntext**|指定水平篩選的 WHERE 子句。|  
|**schema_option**|**binary(8)**|給定發行項的結構描述產生選項點陣圖。 如需**schema_option**值的完整清單, 請[參閱&#40;sp_addarticle transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)。|  
|**dest_owner**|**sysname**|目的地物件的擁有者名稱。|  
|**source_owner**|**sysname**|來源物件的擁有者。|  
|**unqua_source_object**|**sysname**|來源物件的名稱，不含擁有者名稱。|  
|**sync_object_owner**|**sysname**|定義已發行的發行項之檢視的擁有者。 .|  
|**unqualified_sync_object**|**sysname**|定義已發行的發行項之檢視的名稱，不含擁有者名稱。|  
|**filter_owner**|**sysname**|篩選的擁有者。|  
|**unqua_filter**|**sysname**|篩選的名稱，不含擁有者名稱。|  
|**auto_identity_range**|**int**|這是一個旗標，指出在前次建立發行集時，開啟了自動識別範圍處理。 **1**表示已啟用自動識別範圍;**0**表示已停用。|  
|**publisher_identity_range**|**int**|如果發行項的*identityrangemanagementoption*設為**auto**或**auto_identity_range**設為**true**, 則為發行者端識別範圍的範圍大小。|  
|**identity_range**|**bigint**|如果發行項的*identityrangemanagementoption*設為**auto**或**auto_identity_range**設為**true**, 則為訂閱者端之識別範圍的範圍大小。|  
|**threshold**|**bigint**|這是一個百分比值，指出散發代理程式指派新識別範圍的時機。|  
|**identityrangemanagementoption**|**int**|指出處理發行項的識別範圍管理。|  
|**fire_triggers_on_snapshot**|**bit**|這是指在套用初始快照集時，是否執行複寫的使用者觸發程序。<br /><br /> **1** = 執行使用者觸發程式。<br /><br /> **0** = 不執行使用者觸發程式。|  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或**1** (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_helparticle**用於快照式複寫和異動複寫中。  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色、 **db_owner**固定資料庫角色, 或目前發行集之發行集存取清單的成員, 才能夠執行**sp_helparticle**。  
  
## <a name="example"></a>範例  
 [!code-sql[HowTo#sp_helptranarticle](../../relational-databases/replication/codesnippet/tsql/sp-helparticle-transact-_1.sql)]  
  
## <a name="see-also"></a>另請參閱  
 [查看和修改發行項屬性](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addarticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlecolumn &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)   
 [sp_changearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [複寫預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
