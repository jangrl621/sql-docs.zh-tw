---
title: getColumnLabel 方法 (SQLServerResultSetMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getColumnLabel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cf67692c-24aa-49e6-8e88-a47d4e8c021c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9784c4aa2dd892473e4ac0ef46f0e8f62d359c5f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67952951"
---
# <a name="getcolumnlabel-method-sqlserverresultsetmetadata"></a>getColumnLabel 方法 (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  取得指定之資料行之列印輸出和顯示中所使用的建議標題。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.lang.String getColumnLabel(int column)  
```  
  
#### <a name="parameters"></a>參數  
 *column*  
  
 指出資料行索引的 **int**。  
  
## <a name="return-value"></a>傳回值  
 **String**，其中包含資料行的標題。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 getColumnLabel 方法是由 ResultSetMetaData 介面中的 getColumnLabel 方法指定。  
  
 這個方法會傳回資料行的別名名稱。 如果沒有別名名稱，這個方法會傳回資料行名稱。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSetMetaData 方法](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData 成員](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData 類別](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
