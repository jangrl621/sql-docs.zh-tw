---
title: 修改統計資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- statistics [SQL Server], modifying
- modifying statistics
ms.assetid: b06299ca-ed52-411a-b245-45eac4628c99
author: julieMSFT
ms.author: jrasnick
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 593a30631eed27db108c79dd70840d1fee3f6964
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134006"
---
# <a name="modify-statistics"></a>修改統計資料
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中修改現有統計資料。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [安全性](#Security)  
  
-   **若要使用下列項目修改統計資料：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 需要：  
  
-   使用者有資料表或檢視的 ALTER 權限。  
  
-   使用者必須是資料表或索引檢視表擁有者，或是下列其中一個角色的成員： **sysadmin** 固定伺服器角色、 **db_owner** 固定資料庫角色或 **db_ddladmin** 固定資料庫角色。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-modify-statistics"></a>若要修改統計資料  
  
1.  在 **[物件總管]** 中，按一下加號展開要在其中修改統計資料的資料庫。  
  
2.  按一下加號展開 **[資料表]** 資料夾。  
  
3.  按一下加號展開要在其中修改統計資料的資料表。  
  
4.  按一下加號展開 **[統計資料]** 資料夾。  
  
5.  以滑鼠右鍵按一下要修改的統計資料物件，然後選取 [屬性]  。  
  
6.  在 [統計資料屬性 - *statistics_name*]  對話方塊的 [一般]  頁面上，按一下 [加入]  、[移除]  、[上移]  、[下移]  或任何組合，以改變統計資料的屬性。 請記住，資料行在 [統計資料行]  方格中位置會大幅影響統計資料的效益。  
  
7.  按一下 [確定]  。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要修改統計資料**  
  
 您無法使用 Transact-SQL 陳述式來執行這項工作。 若要使用 Transact-SQL 來修改統計資料，您必須先刪除現有的統計資料，然後以新的屬性重新建立統計資料。  
  
 如需詳細資訊，請參閱 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md) 和 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)。  
  
  
