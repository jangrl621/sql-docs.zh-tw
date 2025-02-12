---
title: JDBC Driver 應用程式範例 |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e136b87c-a138-45d6-8c3e-bcef94b7e483
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3227aa1fc886c72b1655fc8ef9770be2c914af3a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945831"
---
# <a name="sample-jdbc-driver-applications"></a>範例 JDBC 驅動程式應用程式

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 範例應用程式會示範 JDBC 驅動程式的各種功能。 此外，它們也示範當搭配 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫使用 JDBC 驅動程式時，您可以遵循的良好程式設計作法。  
  
所有的範例應用程式都包含在可以在本機電腦上編譯並執行的 *.java 程式碼檔案中，而且它們位於下列位置的各個子資料夾中：  

```bash
\<installation directory>\sqljdbc_<version>\<language>\samples  
```

本節的主題說明如何設定並執行範例應用程式，並包括範例應用程式示範內容的討論。  
  
## <a name="in-this-section"></a>本節內容  
  
| 主題                                                                                                        | Description                                                                                                                                                                                                                                                             |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [連接及擷取資料](../../connect/jdbc/connecting-and-retrieving-data.md)                       | 這些範例應用程式示範如何連線到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫。 它們也示範從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫擷取資料的不同方法。 |
| [使用資料類型 &#40;JDBC&#41;](../../connect/jdbc/working-with-data-types-jdbc.md)                 | 這些範例應用程式示範如何使用 JDBC 驅動程式資料類型方法，來使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的資料。                                                                                           |
| [使用結果集](../../connect/jdbc/working-with-result-sets.md)                                   | 這些範例應用程式示範如何使用結果集，來處理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中包含的資料。                                                                                                         |
| [使用大型資料](../../connect/jdbc/working-with-large-data.md)                                     | 這些範例應用程式會示範如何使用自適性緩衝來擷取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫中的大數值資料，而沒有伺服器資料指標的負擔。                                                      |
| [SQL 資料探索與分類](../../connect/jdbc/data-discovery-classification-sample.md) | 這個範例應用程式會示範如何使用 JDBC 驅動程式, 從 ResultSet 物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中, 抓取資料庫中所包含的資料探索和分類資訊。                                      |
  
## <a name="see-also"></a>另請參閱

[JDBC Driver 概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
