---
title: updateAsciiStream 方法 (java.io.InputStream) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1dcc3d4f-ae30-45c0-afad-a531358807af
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9acd8b75a7152a8e10faeb7f80d6d02c070ad2f0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67985513"
---
# <a name="updateasciistream-method-int-javaioinputstream"></a>updateAsciiStream 方法 (int, java.io.InputStream)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用 ASCII 資料流值，更新指定的資料行。  
  
## <a name="syntax"></a>語法  
  
```  
  
public void updateAsciiStream(int columnIndex,  
                              java.io.InputStream x)  
```  
  
#### <a name="parameters"></a>參數  
 *columnIndex*  
  
 指出資料行索引的 **int**。  
  
 *x*  
  
 InputStream 物件。  
  
## <a name="exceptions"></a>例外狀況  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 這個 updateAsciiStream 方法是由 sql-dmo 介面中的 updateAsciiStream 方法指定。  
  
 這個方法會從 InputStream 物件，將 ASCII 字元 (位元組) 傳遞到可轉換的字元資料行，這些是 Unicode 的 ASCII 範圍 [0x00 - 0x7F]，以及 874、932、936、949、950 和 1250 到 1258 的字碼頁。 這個方法會執行轉換，直到目的地定序頁面。 嘗試更新無法轉換的目的地資料行，將擲回例外狀況。 若是處理二進位資料行，則會傳遞未經處理位元組。  
  
 針對**image**、 **text**和**Ntext** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]資料類型使用這個方法可能會影響效能。  
  
## <a name="see-also"></a>另請參閱  
 [updateAsciiStream 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateasciistream-method-sqlserverresultset.md)   
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
