---
title: SupportsDataDefinitionAndDataManipulationTransactions 方法 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsDataDefinitionAndDataManipulationTransactions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fe91c601-9bb3-4364-9131-575a94d3a1b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6f6fd9ac18586c72d1be1a6a4ae5c545b0633d94
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67969529"
---
# <a name="supportsdatadefinitionanddatamanipulationtransactions-method-sqlserverdatabasemetadata"></a>supportsDataDefinitionAndDataManipulationTransactions 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取值，此值指出這個資料庫是否支援在交易中同時使用資料定義陳述式和資料操作陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean supportsDataDefinitionAndDataManipulationTransactions()  
```  
  
## <a name="return-value"></a>傳回值  
 如果支援,**則為 true** 。 否則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 suportsDataDefinitionAndDataManipulationTransactions 方法是由 JAVA.sql.databasemetadata 介面中的 suportsDataDefinitionAndDataManipulationTransactions 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成員](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 類別](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
