---
title: registerOutParameter 方法 (int, int, java.lang.String) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (int, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3eb5c384-6751-4d50-be23-0c2ccc35593c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1bf855697561638c0d4ca560c345bf2d21e4b027
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975917"
---
# <a name="registeroutparameter-method-int-int-javalangstring"></a>registerOutParameter 方法 (int, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  在給定 JDBC 型別和型別名稱的指定序數位置中註冊 OUT 參數。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void registerOutParameter(int index,  
                                 int sqlType,  
                                 java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>參數  
 *index*  
  
 **int**，指出參數的序數位置。  
  
 *sqlType*  
  
 JDBC 型別程式碼，如 java.sql.Types 中所定義。  
  
 *typeName*  
  
 **String**，包含完整的 SQL 類型名稱。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 registerOutParameter 方法是由 JAVA.sql.callablestatement 介面中的 registerOutParameter 方法指定。  
  
 從 JDBC Driver 3.0 開始, 當*sqlType*的類型為**sendTimeAsDatetime**時, 這個方法的行為會由連接屬性 ([設定連接屬性](../../../connect/jdbc/setting-the-connection-properties.md)) 和[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [SQLServerDataSource. Sqlserverdatasource.setsendtimeasdatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)。  
  
 如需詳細資訊, 請參閱設定將[java. Time 值傳送至伺服器的方式](../../../connect/jdbc/configuring-how-java-sql-time-values-are-sent-to-the-server.md)。  
  
## <a name="see-also"></a>另請參閱  
 [registerOutParameter 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成員](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 類別](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
