---
title: MSSQL_ENG004929 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG004929 error
ms.assetid: 1d9b1d88-1fbf-4089-b392-687d3b0220ca
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 0a9300f76bb5447866a4de8d79b1b89492e4a197
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68766704"
---
# <a name="mssqleng004929"></a>MSSQL_ENG004929
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>訊息詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|4929|  
|事件來源|MSSQLSERVER|  
|元件|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|符號名稱||  
|訊息文字|無法改變 %S_MSG '%.*ls'，因為它正在為複寫而發行。|  
  
## <a name="explanation"></a>說明  
 這個錯誤通常是在您嘗試在針對異動複寫所發行資料表上卸除主索引鍵條件約束時發生。 異動複寫的每個已發行資料表都需要主索引鍵，因此不能卸除條件約束。  
  
## <a name="user-action"></a>使用者動作  
 若要卸除條件約束，請先卸除與資料表關聯的發行項。 如需詳細資訊，請參閱[在現有發行集中加入和卸除發行項](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)。 如果在未複寫的資料庫中發生這個錯誤，請執行 [sp_removedbreplication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)，以確保資料庫中的物件不會標示為已複寫。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤和事件參考 &#40;複寫&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
