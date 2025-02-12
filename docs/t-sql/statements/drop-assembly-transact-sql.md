---
title: DROP ASSEMBLY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP ASSEMBLY
- DROP_ASSEMBLY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- deleting assemblies
- assemblies [CLR integration], removing
- dropping assemblies
- WITH NO DEPENDENTS option
ms.assetid: 452d181a-a8e6-44a3-975d-29966d01b18d
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 6b5b788ef8978ce88fdb3d8aa0567724023fd5cc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67984288"
---
# <a name="drop-assembly-transact-sql"></a>DROP ASSEMBLY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  從目前資料庫移除組件及其所有相關聯的檔案。 組件是使用 [CREATE ASSEMBLY](../../t-sql/statements/create-assembly-transact-sql.md) 來建立，並且使用 [ALTER ASSEMBLY](../../t-sql/statements/alter-assembly-transact-sql.md) 來修改。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
DROP ASSEMBLY [ IF EXISTS ] assembly_name [ ,...n ]  
[ WITH NO DEPENDENTS ]  
[ ; ]  
```  
  
## <a name="arguments"></a>引數  
 *IF EXISTS*  
 **適用於**：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 至[目前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658))。  
  
 只有在組件已存在時，才有條件地將它卸除。  
  
 *assembly_name*  
 這是您要卸除的組件名稱。  
  
 WITH NO DEPENDENTS  
 如果指定的話，只會卸除 *assembly_name*，而不會卸除該組件參考的任何相依組件。 若未指定，DROP ASSEMBLY 就會卸除 *assembly_name* 和所有的相依組件。  
  
## <a name="remarks"></a>Remarks  
 卸除一個組件，會從資料庫移除組件及其所有相關聯的檔案 (例如，原始程式碼和偵錯檔案)。  
  
 如果未指定 WITH NO DEPENDENTS，DROP ASSEMBLY 就會卸除 *assembly_name* 和所有的相依組件。 如果卸除任何相依組件失敗，DROP ASSEMBLY 便會傳回錯誤。  
  
 如果組件是由資料庫中的另一個組件所參考，或者如果它是由目前資料庫中的 Common Language Runtime (CLR) 函數、程序、觸發程序、使用者自訂類型或彙總所使用，DROP ASSEMBLY 就會傳回錯誤。  
  
 DROP ASSEMBLY 不會影響任何參考目前正在執行之組件的程式碼。 不過，DROP ASSEMBLY 執行之後，嘗試叫用該組件程式碼就會失敗。  
  
## <a name="permissions"></a>權限  
 需要組件的擁有權或 CONTROL 權限。  
  
## <a name="examples"></a>範例  
 下列範例假設組件 `HelloWorld` 已經建立在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中。  
  
```  
DROP ASSEMBLY Helloworld ;  
```  
  
## <a name="see-also"></a>另請參閱  
 [CREATE ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/create-assembly-transact-sql.md)   
 [ALTER ASSEMBLY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-assembly-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [取得組件的相關資訊](../../relational-databases/clr-integration/assemblies-getting-information.md)  
  
  
