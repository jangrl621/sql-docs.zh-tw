---
title: 還原服務主要金鑰 | Microsoft 文件
ms.custom: ''
ms.date: 01/02/2019
ms.prod: sql
ms.reviewer: vanto
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- service master key [SQL Server], importing
- service master key [SQL Server], restoring
ms.assetid: 14bdbbbe-d384-4692-b670-4243d2466fe1
author: aliceku
ms.author: aliceku
ms.openlocfilehash: c16742fe161f947e6256537ce04f36f9a07a89a6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111626"
---
# <a name="restore-the-service-master-key"></a>還原服務主要金鑰
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] ，還原 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的服務主要金鑰。  
  
> [!WARNING]  
> 需要還原服務主要金鑰的情況不太可能發生在您身上。 萬一真的碰到了，就應該非常小心地進行。 如需詳細資訊，請參閱 [Back Up the Service Master Key](../../../relational-databases/security/encryption/back-up-the-service-master-key.md)。  
  
## <a name="before-you-begin"></a>開始之前  
  
### <a name="limitations-and-restrictions"></a>限制事項  
  
- 當還原服務主要金鑰時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會解密所有已利用目前的服務主要金鑰來加密的金鑰和秘密，然後利用從備份檔案載入的服務主要金鑰來加密它們。  
  
- 如果任何一項解密失敗，還原便會失敗。 您可以利用 FORCE 選項來省略錯誤，但這個選項會使所有無法解密的資料遺失。  
  
- 重新產生加密階層是一項需要大量資源的作業。 您應該將這項作業安排在低需求時進行。  
  
> [!CAUTION]  
> 服務主要金鑰是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 加密階層的根。 服務主要金鑰會直接或間接維護樹狀結構中之所有其他金鑰的安全。 如果在強制還原作業進行期間某相依金鑰無法解密，由該金鑰維護其安全的資料便會遺失。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>權限  
需要伺服器的 CONTROL SERVER 權限。  
  
## <a name="using-transact-sql"></a>使用 Transact-SQL  
  
### <a name="to-restore-the-service-master-key"></a>若要還原服務主要金鑰  
  
1. 從實體備份媒體或本機檔案系統上的目錄，擷取已備份的服務主要金鑰副本。  
  
2. 在 **[物件總管]** 中，連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]的執行個體。  
  
3. 在標準列上，按一下 **[新增查詢]** 。  
  
4. 複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。  
  
    ```sql
    -- Restores the service master key from a backup file.  
    RESTORE SERVICE MASTER KEY   
        FROM FILE = 'c:\temp_backups\keys\service_master_key'   
        DECRYPTION BY PASSWORD = '3dH85Hhk003GHk2597gheij4';  
    GO  
    ```  
  
    > [!NOTE]  
    > 金鑰的檔案路徑和金鑰的密碼 (如果有) 不同於上方指示。 請確定兩者都是您伺服器和金鑰設定專用的。
