---
title: getGeneratedKeys 方法 (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d47ff96fe493053e7a953cfbae53e52be95a0d62
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67982947"
---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>getGeneratedKeys 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取執行這個 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件最後所建立的任何自動產生索引鍵。  
  
## <a name="syntax"></a>語法  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>傳回值  
 ResultSet 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getGeneratedKeys 方法是由 sql 語句介面中的 getGeneratedKeys 方法指定。  
  
 如需如何使用此方法的詳細資訊, 請參閱[使用自動產生的金鑰](../../../connect/jdbc/using-auto-generated-keys.md)。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
