---
title: catalog.delete_environment_variable (SSISDB 資料庫) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 894b3bdb-aa34-463e-aba4-1b68ad96a0ef
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d047bd8af1ed8a30daa9dc1d550029a7a62279ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68112252"
---
# <a name="catalogdeleteenvironmentvariable-ssisdb-database"></a>catalog.delete_environment_variable (SSISDB 資料庫)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  從 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 目錄中的環境刪除環境變數。  
  
## <a name="syntax"></a>語法  
  
```sql  
delete_environment_variable [ @folder_name = ] folder_name  
    , [ @environment_name = ] environment_name  
    , [ @variable_name = ] variable_name  
```  
  
## <a name="arguments"></a>引數  
 [ @folder_name = ] *folder_name*  
 包含環境之資料夾的名稱。 *folder_name* 是 **nvarchar(128)** 。  
  
 [ @environment_name = ] *environment_name*  
 包含變數之環境的名稱。 *environment_name* 是 **nvarchar(128)** 。  
  
 [ @variable_name = ] *variable_name*  
 要刪除之變數的名稱。 *variable_name* 是 **nvarchar(128)** 。  
  
## <a name="return-code-value"></a>傳回碼值  
 0 (成功)  
  
## <a name="result-sets"></a>結果集  
 None  
  
## <a name="permissions"></a>權限  
 這個預存程序需要下列其中一個權限：  
  
-   環境的 READ 和 MODIFY 權限  
  
-   **ssis_admin** 資料庫角色的成員資格  
  
-   **系統管理員**伺服器角色的成員資格  
  
## <a name="errors-and-warnings"></a>錯誤和警告  
 下列清單將描述可能會引發錯誤或警告的某些條件：  
  
-   環境名稱無效  
  
-   環境變數不存在  
  
  
