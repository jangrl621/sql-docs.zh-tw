---
title: moveToCurrentRow 方法 (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11a92c879995d198658853ef9b5cec9d00449230
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976834"
---
# <a name="movetocurrentrow-method-sqlserverresultset"></a>moveToCurrentRow 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  將資料指標移動到記住的資料指標位置，通常該位置是目前資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void moveToCurrentRow()  
```  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 moveToCurrentRow 方法是由 sql-dmo 介面中的 moveToCurrentRow 方法指定。  
  
 如果資料指標不在插入資料列上，這個方法將沒有作用。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
