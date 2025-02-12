---
title: getTablePrivileges 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getTablePrivileges
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0610d667-a16d-4201-a14b-0a40048911e1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d0fe3b01fd02bf48fb5f38707530e3b3344133e6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979225"
---
# <a name="gettableprivileges-method-sqlserverdatabasemetadata"></a>getTablePrivileges 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取各個資料表之存取權限的描述，這些資料表會透過給定的目錄、結構描述或資料表名稱模式提供。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.sql.ResultSet getTablePrivileges(java.lang.String catalog,  
                                             java.lang.String schema,  
                                             java.lang.String table)  
```  
  
#### <a name="parameters"></a>參數  
 *catalog*  
  
 包含目錄名稱的 **String**。 提供 null 給這個參數，將指出不需要使用目錄名稱。  
  
 *schema*  
  
 包含結構描述名稱模式的 **String**。 提供 null 給這個參數，將指出不需要使用結構描述名稱。  
  
 *table*  
  
 包含資料表名稱模式的 **String**。  
  
## <a name="return-value"></a>傳回值  
 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getTablePrivileges 方法是由 java.sql.DatabaseMetaData 介面中的 getTablePrivileges 方法指定。  
  
 透過 getTablePrivileges 方法所傳回的結果將包含下列資訊：  
  
|[屬性]|類型|Description|  
|----------|----------|-----------------|  
|TABLE_CAT|**String**|目錄的名稱。|  
|TABLE_SCHEM|**String**|資料表結構描述名稱。|  
|TABLE_NAME|**String**|資料表名稱。|  
|GRANTOR|**String**|授與存取權的物件。|  
|GRANTEE|**String**|接收存取權的物件。|  
|PRIVILEGE|**String**|授與的存取類型。|  
|IS_GRANTABLE|**String**|指出是否允許被授與者授與存取權給其他使用者。|  
  
> [!NOTE]  
>  如需 getTablePrivileges 方法所傳回資料的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 線上叢書》中的＜sp_table_privileges (Transact-SQL)＞。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 getTablePrivileges 方法來傳回 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 範例資料庫中 Person.Contact 資料表中的存取權限。  
  
```  
public static void executeGetTablePrivileges(Connection con) {  
   try {  
      DatabaseMetaData dbmd = con.getMetaData();  
      ResultSet rs = dbmd.getTablePrivileges("AdventureWorks", "Person", "Contact");  
      ResultSetMetaData rsmd = rs.getMetaData();  
  
      // Display the result set data.  
      int cols = rsmd.getColumnCount();  
      while(rs.next()) {  
         for (int i = 1; i <= cols; i++) {  
            System.out.println(rs.getString(i));  
         }  
      }  
      rs.close();  
   }   
  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
