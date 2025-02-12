---
title: next 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c83fe6aa33d77db98fcdfc757b9bf219a45a9b15
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67976766"
---
# <a name="next-method-sqlserverresultset"></a>next 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  從資料指標的目前位置，將資料指標向下移動到下一個資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>傳回值  
 如果新的目前資料列有效, 則**為 true** 。 如果沒有其他要處理的資料列, 則**為 false** 。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 next 方法是由 java.sql.ResultSet 介面中的 next 方法指定。  
  
 結果集資料指標一開始位於第一個資料列的前面。 第一次呼叫 next 方法會讓第一個資料列成為目前的資料列，第二次呼叫會讓第二個資料列成為目前的資料列，依此類推。  
  
 如果已經針對目前的資料列開啟輸入資料流，則呼叫 next 方法將會以隱含的方式關閉它。 當讀取新的資料列時，將會清除 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件的警告鏈結。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
