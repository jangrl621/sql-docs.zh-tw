---
title: 設定資料來源屬性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f3363d05-07fc-4bf8-ae5e-2a7a968808ad
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 97e285f5f2680e028a9d8fd00901e3e977ffdd80
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004428"
---
# <a name="setting-the-data-source-properties"></a>設定資料來源屬性

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

資料來源為在 Java Platform Enterprise Edition (Java EE) 環境中建立 JDBC 連接所慣用的機制。 資料來源提供連接、共用連接及分散式連接，而未在 Java 程式碼內將連接屬性寫入程式碼。 所有 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 資料來源可分別使用適當的 setter 與 getter 方法，以設定或取得任何屬性的值。

Java EE 產品 (例如應用程式伺服器及 servlet/JSP 引擎) 通常會讓您設定資料庫存取的資料來源。 只要設定能讓您將屬性輸入成 property=value 組，即可指定在[設定連線屬性](../../connect/jdbc/setting-the-connection-properties.md)主題中所列的任一屬性。

如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料來源的詳細資訊，請參閱 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) 類別。 如需如何使用 SQLServerDataSource 類別來連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資料庫的範例, 請參閱[資料來源範例](../../connect/jdbc/data-source-sample.md)。

## <a name="see-also"></a>另請參閱

[使用 JDBC Driver 連接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
