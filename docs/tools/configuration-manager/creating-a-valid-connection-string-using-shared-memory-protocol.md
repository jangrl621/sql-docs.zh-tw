---
title: 使用共用記憶體通訊協定建立有效的連接字串 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- connection strings [Database Engine], shared memory
- aliases [SQL Server], shared memory
ms.assetid: 5fff42e8-377f-4b40-b0c8-b02393f8a1af
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: a3d1e40e1909b7ab3129f63fc89c8bc20f4873b3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010175"
---
# <a name="creating-a-valid-connection-string-using-shared-memory-protocol"></a>使用共用記憶體通訊協定建立有效的連接字串
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  從在同一部電腦上執行的用戶端連接到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可使用共用記憶體通訊協定。 共用記憶體並沒有可設定的內容。 連接時永遠會先嘗試使用共用記憶體，而且您無法將它從 **[用戶端通訊協定內容]** 清單上之 **[啟用的通訊協定]** 清單的最高位置移除。 您可以停用「共用記憶體」通訊協定，這在針對其他通訊協定中的其中一個通訊協定進行疑難排解時非常有幫助。  
  
 您不能使用共用記憶體通訊協定來建立別名，但如果已啟用共用記憶體，則可以使用名稱來連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)] ，以建立共用記憶體連接。 共用記憶體連接字串使用 `lpc:<servername>[\instancename]`格式。  
  
## <a name="connecting-to-the-local-server"></a>連接到本機伺服器  
 連接到與用戶端在同一部電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，可以使用 **(local)** 作為伺服器名稱。 但不建議這麼做，因為會造成模糊不清，但是若確實知道用戶端正在預期的電腦上執行，這就很有用。 例如，為行動式、非連接的使用者 (例如銷售人員) 建立應用程式 (亦即 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將會在膝上型電腦上執行並儲存專案資料) 時，連接到 **(local)** 的用戶端一律會連接到在膝上型電腦上執行的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 可以使用 **localhost** 或句點 ( **.** ) 來取代 **(local)** 。  
  
## <a name="verifying-your-connection-protocol"></a>驗證您的連接通訊協定  
 下列查詢會傳回目前連接所使用的通訊協定。  
  
```  
SELECT net_transport   
FROM sys.dm_exec_connections   
WHERE session_id = @@SPID;  
  
```  
  
## <a name="examples"></a>範例:  
 您可以使用下列名稱來連接到具有共用記憶體通訊協定 (且已啟用) 的本機電腦：  
  
 `<servername>`  
  
 `<servername>\<instancename>`  
  
 `(local)`  
  
 `localhost`  
  
 您不能建立共用記憶體連接的別名。  
  
> [!NOTE]  
>  在 [伺服器]  方塊中指定 IP 位址會建立 TCP/IP 連接。  
  
## <a name="see-also"></a>另請參閱  
 [Creating a Valid Connection String Using TCP IP](../../tools/configuration-manager/creating-a-valid-connection-string-using-tcp-ip.md)   
 [使用具名管道建立有效的連接字串](https://msdn.microsoft.com/library/90930ff2-143b-4651-8ae3-297103600e4f)   
 [選擇網路通訊協定](https://msdn.microsoft.com/library/6565fb7d-b076-4447-be90-e10d0dec359a)  
  
  
