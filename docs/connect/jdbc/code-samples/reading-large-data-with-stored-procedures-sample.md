---
title: 使用預存程序讀取大型資料範例 | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 58c76635-a117-4661-8781-d6cb231c5809
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 22d510cec069a828588a6fdcd95fb366dbd27158
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957147"
---
# <a name="reading-large-data-with-stored-procedures-sample"></a>使用預存程序讀取大型資料範例

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

此 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 範例應用程式將示範如何從預存程序中擷取大型 OUT 參數。

此範例的程式碼檔案名稱為 ExecuteStoredProcedure.java，可在下列位置找到：

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples\adaptive
```

## <a name="requirements"></a>需求

若要執行此範例應用程式，您必須存取 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 範例資料庫。 請您也將 classpath 設定為包含 mssql-jdbc jar 檔案。 如需如何設定 classpath 的詳細資訊，請參閱[使用 JDBC 驅動程式](../../../connect/jdbc/using-the-jdbc-driver.md)。

> [!NOTE]  
> [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 提供 mssql-jdbc 類別庫檔案，可根據您慣用的 Java Runtime Environment (JRE) 設定來使用。 如需選擇哪個 JAR 檔案的詳細資訊，請參閱 [JDBC Driver 的系統需求](../../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)。

在 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 範例資料庫中建立下列預存程序：

```sql
CREATE PROCEDURE GetLargeDataValue
  (@Document_ID int,
   @Document_ID_out int OUTPUT,
   @Document_Title varchar(50) OUTPUT,  
   @Document_Summary nvarchar(max) OUTPUT)  

AS
BEGIN
   SELECT @Document_ID_out = DocumentID,
          @Document_Title = Title,  
          @Document_Summary = DocumentSummary
    FROM  Production.Document  
    WHERE DocumentID = @Document_ID  
END  
```

## <a name="example"></a>範例

在下列範例中，範例程式碼會建立與 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal_md.md)] 資料庫的連線。 接著，範例程式碼會建立範例資料，並使用參數化查詢更新 Production.Document 資料表。 然後，範例程式碼會使用 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 類別的 [getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverstatement.md) 方法來取得適應性緩衝模式，並且執行 GetLargeDataValue 預存程序。 請注意，從 JDBC Driver 2.0 版開始，responseBuffering 連接屬性預設設定為 "adaptive"。

最後，範例程式碼會顯示利用 OUT 參數傳回的資料，同時示範如何在資料流上使用 `mark` 和 `reset` 方法來重新讀取任何部分的資料。

[!code[JDBC#UsingAdaptiveBuffering2](../../../connect/jdbc/codesnippet/Java/reading-large-data-with-_1_1.java)]

## <a name="see-also"></a>另請參閱

[使用大型資料](../../../connect/jdbc/code-samples/working-with-large-data.md)
