---
title: sp_changesubscription (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- changesubscription
- sp_changesubscription
- changesubscription_TSQL
- sp_changesubscription_TSQL
helpviewer_keywords:
- sp_changesubscription
ms.assetid: f9d91fe3-47cf-4915-b6bf-14c9c3d8a029
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5684d80bc63fe543e54aa4c38d9f0a516b6334ff
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770672"
---
# <a name="spchangesubscription-transact-sql"></a>sp_changesubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  變更快照集或交易式發送訂閱的屬性，或變更佇列更新異動複寫所涉及的提取訂閱的屬性。 若要變更所有其他類型之提取訂閱的屬性, 請使用[sp_change_subscription_properties &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)。 **sp_changesubscription**是在發行集資料庫的發行者端執行。  
  
> [!IMPORTANT]  
>  當利用遠端散發者來設定發行者時，提供給所有參數的值 (包括 *job_login* 和 *job_password*) 都會以純文字的方式傳給散發者。 您應該先加密「發行者」及其遠端「散發者」之間的連接，再執行這個預存程序。 如需詳細資訊，請參閱[啟用 Database Engine 的加密連接 &#40;SQL Server 組態管理員&#41;](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_changesubscription [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
        , [ @subscriber = ] 'subscriber'  
        , [ @destination_db = ] 'destination_db'  
        , [ @property = ] 'property'  
        , [ @value = ] 'value'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @publication = ] 'publication'`這是要變更的發行集名稱。 *發行*集是**sysname**, 沒有預設值  
  
`[ @article = ] 'article'`這是要變更的發行項名稱。 *文章*是**sysname**, 沒有預設值。  
  
`[ @subscriber = ] 'subscriber'`這是訂閱者的名稱。 *訂閱者*是**sysname**, 沒有預設值。  
  
`[ @destination_db = ] 'destination_db'`這是訂閱資料庫的名稱。 *destination_db*是**sysname**, 沒有預設值。  
  
`[ @property = ] 'property'`這是指定之訂用帳戶要變更的屬性。 *property*是**Nvarchar (30)** , 它可以是資料表中的其中一個值。  
  
`[ @value = ] 'value'`這是指定之*屬性*的新值。 *value*是**Nvarchar (4000)** , 它可以是資料表中的其中一個值。  
  
|屬性|值|描述|  
|--------------|-----------|-----------------|  
|**distrib_job_login**||用來執行代理程式之 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 帳戶的登入。|  
|**distrib_job_password**||用來執行代理程式之 Windows 帳戶的密碼。|  
|**subscriber_catalog**||建立 OLE DB 提供者連接時所用的目錄。 此屬性只對非[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]訂閱者有效。|  
|**subscriber_datasource**||OLE DB 提供者所了解的資料來源名稱。 *此屬性只對非*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *訂閱者有效。*|  
|**subscriber_location**||OLE DB 提供者所了解的資料庫位置。 *此屬性只對非*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *訂閱者有效。*|  
|**subscriber_login**||訂閱者的登入名稱。|  
|**subscriber_password**||提供之登入的增強式密碼。|  
|**subscriber_security_mode**|**1**|當連接到發行者時，使用 Windows 驗證。|  
||**0**|當連接到訂閱者時，使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驗證。|  
|**subscriber_provider**||非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源的 OLE DB 提供者登錄所用的唯一程式設計識別碼 (PROGID)。 *此屬性只對非*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *訂閱者有效。*|  
|**subscriber_providerstring**||OLE DB 提供者特定的連接字串，用來識別資料來源。 *此屬性只對非*[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] *訂閱者有效。*|  
|**subscriptionstreams**||這是每個散發代理程式將數批變更並行套用在訂閱者時所能使用的連接數目。 發行者[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]支援從**1**到**64**的值範圍。 對於非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]訂閱者、Oracle 發行者或點對點訂閱, 此屬性必須為**0** 。|  
|**subscriber_type**|**1**|ODBC 資料來源伺服器|  
||**3**|OLE DB 提供者|  
|**memory_optimized**|**bit**|表示訂用帳戶支援記憶體優化資料表。 *memory_optimized*是**bit**, 其中1等於 true (訂閱支援記憶體優化的資料表)。|  
  
`[ @publisher = ] 'publisher'`指定非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。 *publisher*是**sysname**, 預設值是 Null。  
  
> [!NOTE]  
>  發行者不應指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]發行者。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或**1** (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_changesubscription**用於快照式和異動複寫中。  
  
 **sp_changesubscription**只能用來修改包含在佇列更新異動複寫中的發送訂閱或提取訂閱的屬性。 若要變更所有其他類型之提取訂閱的屬性, 請使用[sp_change_subscription_properties &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)。  
  
 變更代理程式的登入或密碼之後，您必須先停止並重新啟動代理程式，變更才會生效。  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色或**db_owner**固定資料庫角色的成員, 才能夠執行**sp_changesubscription**。  
  
## <a name="see-also"></a>另請參閱  
 [sp_addsubscription &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
