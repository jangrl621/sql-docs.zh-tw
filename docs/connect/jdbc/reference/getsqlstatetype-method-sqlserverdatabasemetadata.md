---
title: getSQLStateType 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76faa3bcaccac4f75d95dc49276c669a5631b5a8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979728"
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>getSQLStateType 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指出由 SQLException.getSQLState 方法傳回的 SQLSTATE 是 X/Open (現在稱為 Open Group)、SQL CLI、SQL99 (JDBC 3.0) 或 SQL:2003 (JDBC 4.0)。  
  
## <a name="syntax"></a>語法  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>傳回值  
 指出 SQLSTATE 類型的 **int**，可能是下列其中一個值：  
  
-   針對 JAVA Runtime Environment 版本 5.0: 如果**xopenStates**連接屬性設定為**true**, 則這個方法會傳回 java.sql.databasemetadata. sqlStateXOpen。 否則，DatabaseMetaData.sqlStateSQL99。  
  
-   針對 JAVA Runtime Environment 版本 6.0: 如果**xopenStates**連接屬性設定為**true**, 則這個方法會傳回 java.sql.databasemetadata. sqlStateXOpen。 否則, JAVA.sql.databasemetadata. sqlStateSQL。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getSQLStateType 方法是由 JAVA.sql.databasemetadata 介面中的 getSQLStateType 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
