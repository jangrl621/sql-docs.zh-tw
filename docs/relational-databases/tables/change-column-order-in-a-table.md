---
title: 變更資料表中的資料行順序 | Microsoft Docs
ms.custom: ''
ms.date: 06/15/2018
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], change order in a table
- column order, change
ms.assetid: cd99ef56-9085-431a-a0fc-58e7add5399f
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b792338b5576926f1012bed59ac60c4d88fb11f1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101385"
---
# <a name="change-column-order-in-a-table"></a>變更資料表中的資料行順序
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的資料表設計工具中變更資料行的順序。  
  
> [!CAUTION]  
>  變更資料表的資料行順序可能影響相依於特定資料行順序的程式碼和應用程式。 這些包含查詢、檢視、預存程序、使用者自訂函數，以及用戶端應用程式。 在對資料行順序進行任何變更之前，請審慎考慮。 最佳作法是在應用程式和查詢層級指定傳回資料行的順序。 您不應該仰賴使用 SELECT *，根據資料表中定義資料行的順序，按照預期的順序傳回所有資料行。 請務必按照您想要顯示資料行的順序，在查詢和應用程式中依名稱指定資料行。  
  
 **本主題內容**  
  
-   **若要使用下列項目來變更資料行順序：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-change-the-column-order"></a>若要變更資料行順序  
  
1.  在 [物件總管]  中，以滑鼠右鍵按一下包含要重新排序之資料行的資料表，然後按一下 [設計]  。  
  
2.  選取要重排順序之資料行名稱左邊的方塊。  
  
3.  將資料行拖曳到資料表中的其他位置。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **若要變更資料行順序**  
  
 您無法使用 Transact-SQL 陳述式來執行這項工作。  
  
###  <a name="TsqlExample"></a>  
