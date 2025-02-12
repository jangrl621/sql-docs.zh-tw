---
title: sp_copysubscription (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_copysubscription
- sp_copysubscription_TSQL
helpviewer_keywords:
- sp_copysubscription
ms.assetid: 3c56cd62-2966-4e87-a986-44cb3fd0b760
author: stevestein
ms.author: sstein
ms.openlocfilehash: d1a093364192e3bab32a2fa0234c7198d8e0f3ff
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771427"
---
# <a name="spcopysubscription-transact-sql"></a>sp_copysubscription (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  可附加訂閱功能已被取代，未來的版本將會移除它。 這項功能不應該使用在新的開發工作中。 對於使用參數化篩選來進行資料分割的合併式發行集，我們建議您使用資料分割快照集的新功能，這些功能可以簡化大量訂閱的初始化。 如需詳細資訊，請參閱 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)。 對於未進行資料分割的發行集，您可以用備份來初始化訂閱。 如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。  
  
 複製有提取訂閱但沒有發送訂閱的訂閱資料庫。 只能複製單一檔案資料庫。 這個預存程序執行於訂閱資料庫的訂閱者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_copysubscription [ @filename = ] 'file_name'  
    [ , [ @temp_dir = ] 'temp_dir' ]  
    [ , [ @overwrite_existing_file = ] overwrite_existing_file]  
```  
  
## <a name="arguments"></a>引數  
`[ @filename = ] 'file_name'`這是指定儲存資料檔案 (.mdf) 複本的完整路徑 (包括檔案名) 的字串。 [*檔案名*] 是**Nvarchar (260)** , 沒有預設值。  
  
`[ @temp_dir = ] 'temp_dir'`這是包含暫存檔案的目錄名稱。 *temp_dir*是**Nvarchar (260)** , 預設值是 Null。 如果是 Null, [!INCLUDE[msCoName](../../includes/msconame-md.md)]則[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]會使用預設資料目錄。 目錄應該有足夠的空間來存放組合了所有訂閱者資料庫檔案的檔案大小。  
  
`[ @overwrite_existing_file = ] 'overwrite_existing_file'`這是一個選擇性的布林值旗標, 它會指定是否要覆寫中 **@filename** 所指定之相同名稱的現有檔案。 *overwrite_existing_file*是**bit**, 預設值是**0**。 如果是**1**, 則會覆寫所 **@filename** 指定的檔案 (如果存在的話)。 如果是**0**, 如果檔案存在, 則預存程式會失敗, 而且不會覆寫檔案。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** (成功) 或**1** (失敗)  
  
## <a name="remarks"></a>備註  
 **sp_copysubscription**用於所有類型的複寫中, 將訂閱資料庫複製到檔案, 做為在訂閱者端套用快照集的替代方法。 資料庫必須設定成只支援提取訂閱。 有適當權限的使用者可以建立訂閱資料庫的副本，再複製、傳輸或利用電子郵件來傳送訂閱檔 (.msf) 到另一個訂閱者，之後，便能在此將它附加成一項訂閱。  
  
 所複製的訂閱資料庫大小必須小於 2 GB。  
  
 只有具有用戶端訂閱的資料庫才支援**sp_copysubscription** , 而且當資料庫具有伺服器訂閱時無法執行。  
  
## <a name="permissions"></a>Permissions  
 只有**系統管理員 (sysadmin** ) 固定伺服器角色的成員, 才能夠執行**sp_copysubscription**。  
  
## <a name="see-also"></a>另請參閱  
 [替代快照集資料夾位置](../../relational-databases/replication/snapshot-options.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
