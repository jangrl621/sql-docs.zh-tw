---
title: SQLServerStatement 類別 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ec24963c-8b51-4838-91e9-1fbfa2347451
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 89547655fd734ca9e6e340d94832dea5816f2733
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67970373"
---
# <a name="sqlserverstatement-class"></a>SQLServerStatement 類別
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  代表 JDBC 陳述式功能的基本實作。  
  
 **套件：** com.microsoft.sqlserver.jdbc  
  
 **實作：** [ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
public class SQLServerStatement  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerStatement 類別也針對 JDBC 備妥及可呼叫的陳述式提供許多基底類別實作方法。 SQLServerStatement 類別的基本角色是執行 SQL 陳述式，然後將更新計數和結果集傳回給使用者應用程式。  
  
 這個類別支援解除包裝為 SQLServerStatement 類別、ISQLServerStatement 介面和 sql-dmo 介面。 如需詳細資訊, 請參閱包裝函式[和介面](../../../connect/jdbc/wrappers-and-interfaces.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [JDBC 驅動程式 API 參考](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
