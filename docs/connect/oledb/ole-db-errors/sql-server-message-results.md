---
title: SQL Server 訊息結果 |Microsoft Docs
description: SQL Server 訊息結果
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 05d731f418bad21f9e8ec32c620b352c5663994a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67994916"
---
# <a name="sql-server-message-results"></a>SQL Server 訊息結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式不會產生 OLE DB Driver for SQL Server 資料列集或執行時受到影響之資料列的計數：  
  
-   PRINT  
  
-   具有 10 或更低嚴重性的 RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 這些陳述式會傳回一或多個參考用訊息，或使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 傳回參考用訊息來取代資料列集或計數結果。 成功執行時, SQL Server 的 OLE DB 驅動程式會傳回 S_OK, 而訊息可供 SQL Server 取用者的 OLE DB 驅動程式使用。  
  
 SQL Server 的 OLE DB 驅動程式會傳回 S_OK, 而且在執行許多[!INCLUDE[tsql](../../../includes/tsql-md.md)]語句或取用者執行 SQL Server 成員函式的 OLE DB 驅動程式之後, 會有一或多個參考訊息可供使用。  
  
 每個成員函數執行之後，不管傳回碼的值為何、傳回的 **IRowset** 或 **IMultipleResults** 介面參考是否存在，或者受影響的資料列計數為何，允許動態指定查詢文字的 OLE DB Driver for SQL Server 取用者都應該會檢查錯誤介面。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤](../../oledb/ole-db-errors/errors.md)  
  
  
