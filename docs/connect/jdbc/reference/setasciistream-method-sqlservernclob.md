---
title: setAsciiStream 方法 (SQLServerNClob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 043a94108bdb7c8938f06e8bf1d4bf58651fbf21
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67975372"
---
# <a name="setasciistream-method-sqlservernclob"></a>setAsciiStream 方法 (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  擷取資料流，此資料流將用於從指定位置開始，將 ASCII 字元寫入到這個 **java.sql.NClob** 物件所代表的 **NCLOB** 值。  
  
## <a name="syntax"></a>語法  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>參數  
 *pos*  
  
 開始寫入至 **NCLOB** 物件的位置，第一個位置是 1。  
  
## <a name="return-value"></a>傳回值  
 OutputStream 物件，表示 ASCII 編碼字元可寫入其中的資料流。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>備註  
 這個 setAsciiStream 方法是由 NClob 介面中的 setAsciiStream 方法指定。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerNClob 方法](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 成員](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 類別](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
