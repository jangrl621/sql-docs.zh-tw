---
title: isClosed 方法 (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e79b5b53-16b0-42a3-be4e-542a77a21e12
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fe4d41448fdd65d3cb4a56f873432e747f564ef6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977699"
---
# <a name="isclosed-method-sqlserverstatement"></a>isClosed 方法 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指出這個 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件是否已關閉。  
  
## <a name="syntax"></a>語法  
  
```  
  
public boolean isClosed()  
```  
  
## <a name="return-value"></a>傳回值  
 如果這個 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 物件已關閉，則為 **true**；如果仍為開啟，則為 **false**。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 isClosed 方法是由 sql 語句介面中的 isClosed 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerStatement 成員](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 類別](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
