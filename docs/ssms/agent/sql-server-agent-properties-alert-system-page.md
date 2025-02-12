---
title: SQL Server Agent 屬性 (警示系統頁面) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.alert.f1
ms.assetid: 3e6d3bfd-20ee-4593-86cc-f65b1c08c69d
author: markingmyname
ms.author: maghan
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 92db1bf98b3a50aa619333ba0107034d24106855
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265315"
---
# <a name="sql-server-agent-properties-alert-system-page"></a>SQL Server Agent 屬性 (警示系統頁面)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支援多數 (但非全部) 的 SQL Server Agent 功能。 如需詳細資料，請參閱 [Azure SQL Database 受控執行個體與 SQL Server 之間的 T-SQL 差異](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此頁面來檢視和修改 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示所傳送的訊息設定。  
  
## <a name="options"></a>選項。  
**郵件工作階段**  
此章節中的選項會設定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 郵件。  
  
**啟用郵件設定檔**  
啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 郵件。 依預設，未啟用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 郵件。  
  
**郵件系統**  
設定郵件系統供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 使用。 Database Mail  
  
> [!NOTE]  
> 在變更電子郵件系統之後，您必須重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 服務，才能使變更生效。  
  
**郵件設定檔**  
設定設定檔供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 使用。 您也可以選取 [\<新增 Database Mail 設定檔>]  ，以建立新的設定檔。  
  
**呼叫器電子郵件**  
本節中的選項可以讓您設定傳送到呼叫器號碼的電子郵件訊息，以搭配呼叫系統使用。  
  
**呼叫器電子郵件位址格式**  
此章節可以讓您指定位址格式，以及呼叫器電子郵件中所包含的主旨。  
  
**收件者**  
指定訊息之 [收件者]  的選項  
  
**Prefix**  
在傳送到呼叫器的訊息之 [收件者]  的開頭處，輸入系統要求的任何固定文字。  
  
**呼叫器**  
在前置詞與後置詞之間包含訊息的電子郵件地址。  
  
**後置詞**  
在傳送到呼叫器的訊息之 [收件者]  的結尾處，輸入呼叫器系統要求的任何固定文字。  
  
**副本**  
指定訊息之 [副本]  的選項。  
  
**Prefix**  
在傳送到呼叫器的訊息之 [副本]  的開頭處，輸入系統要求的任何固定文字。  
  
**呼叫器**  
在前置詞與後置詞之間包含訊息的電子郵件地址。  
  
**後置詞**  
在傳送到呼叫器的訊息之 [副本]  的結尾處，輸入呼叫器系統要求的任何固定文字。  
  
**主旨**  
指定訊息主旨的選項。  
  
**Prefix**  
在傳送到呼叫器的訊息之 [主旨]  的開頭處，輸入呼叫器系統要求的任何固定文字。  
  
**後置詞**  
在傳送到呼叫器的訊息之 [主旨]  的結尾處，輸入呼叫器系統要求的任何固定文字。  
  
**在通知訊息中包含主體**  
在傳送給呼叫器的訊息中，包含電子郵件訊息的主體。  
  
**保全操作員**  
此章節可以讓您指定保全操作員的選項。  
  
**啟用保全操作員**  
指定保全操作員。  
  
**[運算子]**  
設定要接收保全通知的操作員名稱。  
  
**通知使用**  
設定通知保全操作員的方法。  
  
**Token 取代**  
此章節可讓您啟動作業步驟 Token，這些 Token 可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示所執行的作業中使用。 如需有關作業步驟 Token 的詳細資訊，請參閱 [在作業步驟中使用 Token](../../ssms/agent/use-tokens-in-job-steps.md)。  
  
> [!IMPORTANT]  
> 在 Windows 事件記錄檔上具有寫入權限的任何 Windows 使用者，可以存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 警示所啟動的作業步驟。 為了避免此安全性風險，依預設會停用在警示啟動的作業中可以使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Token。 這些 Token 包括： **$(A-DBN)** 、 **$(A-SVR)** 、 **$(A-ERR)** 、 **$(A-SEV)** 和 **$(A-MSG)** 。  
>   
> 如果您需要使用這些 Token，在啟用之前，請確定只有信任的 Windows 安全性群組的成員，例如 Administrators 群組，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 所在的電腦的事件記錄檔上才具有寫入權限。  
  
**取代回應警示之所有作業的 Token**  
選取此核取方塊，以允許在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 警示所啟動的作業上取代 Token。  
  
## <a name="see-also"></a>另請參閱  
[運算子](../../ssms/agent/operators.md)  
[設定 SQL Server Agent Mail 使用 Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
[Database Mail](../../relational-databases/database-mail/database-mail.md)  
  
