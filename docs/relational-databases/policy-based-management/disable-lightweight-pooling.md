---
title: 停用輕量型共用 | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 481bb43d-6fe5-497c-9096-971fb6bf733b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 155426b05311354153e03994f854f3860afad9c5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67940445"
---
# <a name="disable-lightweight-pooling"></a>停用輕量型共用
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  這個規則會檢查輕量型共用是否已經在伺服器上停用。 將 lightweightpooling 設定為 1 會使得 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 切換到 Fiber 模式排程。 Fiber 模式適用於 UMS 工作者的環境切換是重要效能瓶頸的某些狀況。 因為這個狀況非常罕見，所以 Fiber 模式幾乎不太會提高一般系統上的效能或延展性。  
  
## <a name="best-practices-recommendations"></a>最佳做法建議  
 只有在徹底測試之後、評估所有其他效能微調機會之後以及環境切換是您所在環境的已知問題時，才應該啟用 lightweightpooling 選項。  
  
 我們建議您不要針對日常作業使用 Fiber 模式排程，因為 Fiber 模式可能會抑制一般環境切換的好處而降低效能，而且使用執行緒本機存放裝置 (TLS) 或執行緒擁有之物件 (如 Mutex，這是一種 Win32 核心物件) 的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件無法在 Fiber 模式下正確運作。  
  
 若要移除輕量型共用，請執行以下陳述式，然後重新啟動： [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]。  
  
```sql  
sp_configure 'show advanced options', 1;  
GO  
sp_configure 'lightweight pooling', 0;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="for-more-information"></a>詳細資訊  
 [輕量型共用伺服器組態選項](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用原則式管理來監視和強制最佳做法](../../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
