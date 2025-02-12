---
title: 使用自動產生的金鑰 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 55a062c7-45ce-40e3-9a6f-4a0f4da4e2a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 55541d7487f27a6fa4e38fef8baf47a6ef3ff6d2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68003982"
---
# <a name="using-auto-generated-keys"></a>使用自動產生的金鑰

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 支援使用選用的 JDBC 3.0 API 來擷取自動產生的資料列識別碼。 此功能的主要價值是提供一個方法，使 IDENTITY 值可供正在更新資料庫資料表的應用程式使用，而不需要查詢和第二次往返於伺服器。

因為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援對識別碼使用虛擬資料行；所以，若更新時必須使用自動產生的金鑰功能，則必須是對包含 IDENTITY 資料行的資料表操作。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 只允許每個資料表有一個 IDENTITY 資料行。 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) 類別的 [getGeneratedKeys](../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md) 方法所傳回的結果集只會有一個資料行，且傳回的資料行名稱為 GENERATED_KEYS。 如果對不含 IDENTITY 資料行的資料表要求產生的金鑰，則 JDBC 驅動程式將傳回 Null 結果集。

例如，在 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫中建立下列資料表：

```sql
CREATE TABLE TestTable
   (Col1 int IDENTITY,
    Col2 varchar(50),
    Col3 int);  
```

在下列範例中，[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] 範例資料庫的開啟連線會傳遞至函式、建構一個將資料新增至資料表的 SQL 陳述式，然後執行該陳述式並顯示 IDENTITY 資料行值。

[!code[JDBC#UsingAutoGeneratedKeys1](../../connect/jdbc/codesnippet/Java/using-auto-generated-keys_1.java)]

## <a name="see-also"></a>另請參閱

[搭配使用陳述式與 JDBC Driver](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)
