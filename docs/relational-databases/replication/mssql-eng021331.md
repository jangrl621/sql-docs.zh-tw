---
title: MSSQL_ENG021331 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021331 error
ms.assetid: 9acd75d9-fda1-44cd-ba17-20295ad53ea0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 9a5ae9febb846c70937a68a3cc085d3ea558a56a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68770323"
---
# <a name="mssqleng021331"></a>MSSQL_ENG021331
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|21331|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|無法將使用者指令碼檔案複製到散發者。(%ls)|  
  
## <a name="explanation"></a>說明  
 當手動初始化訂閱，且由複寫產生或在複寫命令中指定的指令碼無法儲存至指定目錄時，可能會出現此錯誤。 錯誤可能是權限問題所造成：當訂閱沒有使用快照集初始化，在發行者端執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶，就必須要有散發者端之快照集資料夾的寫入權限。  
  
## <a name="user-action"></a>使用者動作  
 請確定指定的快照集資料夾路徑正確，而且在發行者端執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶具有足夠的權限。  
  
## <a name="see-also"></a>另請參閱  
 [指定快照集選項](../../relational-databases/replication/snapshot-options.md)   
 [錯誤和事件參考 &#40;複寫&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [不使用快照集初始化交易式訂閱](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
