---
title: 瞭解資料類型轉換 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 98fa7488-aac3-45b4-8aa4-83ed6ab638b4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d7029faf333c00fc18e4f35743706a012b76c1e7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68004181"
---
# <a name="understanding-data-type-conversions"></a>了解資料類型轉換

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

為了順利將 Java 程式設計語言資料類型轉換為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 提供 JDBC 規格所需的資料類型轉換。 為了增加彈性, 所有類型都可以在**Object**、 **String**和**byte []** 資料類型之間進行轉換。

## <a name="getter-method-conversions"></a>Getter 方法轉換

根據 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，下列圖表包含 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 類別之 get\<Type>() 方法的 JDBC 驅動程式轉換對應，以及 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 類別之 get\<Type> 方法的支援轉換。

![JDBCGetterConversions](../../connect/jdbc/media/jdbcgetterconversions.gif "JDBCGetterConversions")

JDBC 驅動程式的 getter 方法所支援的轉換有三種類別：

- **不失真 (x)** ：轉換的情況為，getter 類型與基礎伺服器類型相同或更小。 例如，在基礎伺服器十進位資料行上呼叫 getBigDecimal 時，不需要轉換。

- **轉換 (y)** ：從數值伺服器類型轉換為 Java 語言類型，這是一般轉換並且遵循 Java 語言轉換規則。 針對這些轉換，一定會截斷有效位數 (絕對不會進位)，而溢位則會當做目的地類型的模數來處理 (也就是較小)。 例如, 在包含 "1.9999" 的基礎**十進位**資料行上呼叫 getInt 將會傳回 "1"; 或者, 如果基礎**十進位**值是 "3000000000", 則**int**值會溢位為 "-1294967296"。

- **視資料而定 (z)** ：從基礎字元類型到數值類型的轉換，需要字元值包含可轉換為該類型的值。 不會執行其他轉換。 如果該值對於 getter 類型來說太大，則該值無效。 例如，如果在含有 "53" 的 varchar(50) 資料行上呼叫 getInt，則會當成 **int** 傳回值；但如果基礎值為 "xyz" 或 "3000000000"，則會擲回錯誤。

如果在**binary**、 **Varbinary**、 **Varbinary (max)** 或**image** column 資料類型上呼叫 getString, 則會以十六進位字串值傳回值。

## <a name="updater-method-conversions"></a>Updater 方法轉換

若為傳遞給 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) 類別之 update\<類型>() 方法的 Java 類型資料，則適用下列轉換。

![JDBCUpdaterConversions](../../connect/jdbc/media/jdbc_jdbcupdatterconversions.gif "JDBCUpdaterConversions")

JDBC 驅動程式的 updater 方法所支援的轉換有三種類別：

- **不失真 (x)** ：轉換的情況為，updater 類型與基礎伺服器類型相同或更小。 例如，在基礎伺服器十進位資料行上呼叫 updateBigDecimal 時，不需要轉換。

- **轉換 (y)** ：從數值伺服器類型轉換為 Java 語言類型，這是一般轉換並且遵循 Java 語言轉換規則。 針對這些轉換，一定會截斷有效位數 (絕對不會進位)，而溢位則會當做目的地 (較小) 類型的模數來處理。 例如, 在包含 "1.9999" 的基礎**int**資料行上呼叫 updateDecimal 會傳回 "1"; 或者, 如果基礎**十進位**值是 "3000000000", 則**int**值會溢位為 "-1294967296"。

- **視資料而定 (z)** ：從基礎來源資料類型轉換為目的地資料類型需要包含值可轉換為目的地類型。 不會執行其他轉換。 如果該值對於 getter 類型來說太大，則該值無效。 例如，如果在含有 "53" 的 int 資料行上呼叫 updateString，更新會成功；但如果基礎字串值為 "foo" 或 "3000000000"，則會擲回錯誤。

在**binary**、 **Varbinary**、 **Varbinary (max)** 或**image** column 資料類型上呼叫 updateString 時, 它會將字串值視為十六進位字串值來處理。

當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行資料類型是 **XML** 時，此資料值必須是有效的 **XML**。 呼叫 updateBytes、updateBinaryStream 或 updateBlob 方法時, 資料值應該是 XML 字元的十六進位字串標記法。 例如：

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

請注意，如果 XML 字元採用特定字元編碼，就需要位元組順序標示 (BOM)。

## <a name="setter-method-conversions"></a>Setter 方法轉換

若為傳遞給 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 類別和 [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) 類別之 set\<類型>() 方法的 Java 類型資料，則適用下列轉換。

![JDBCSetterConversions](../../connect/jdbc/media/jdbc_jdbcsetterconversions_v2.gif "JDBCSetterConversions")

伺服器會嘗試任何一種轉換，並會在發生失敗時傳回錯誤。

在**字串**資料類型的案例中, 如果值超過**VARCHAR**的長度, 則會對應至**LONGVARCHAR**。 同樣地, 如果值超過支援的**Nvarchar**長度, 則**NVARCHAR**會對應至**LONGNVARCHAR** 。 這一點對 **byte[]** 來說也相同。 長度超過**VARBINARY**的值會變成**LONGVARBINARY**。

JDBC 驅動程式的 setter 方法所支援的轉換有兩種類別：

- **不失真 (x)** ：轉換的數值情況為，setter 類型與基礎伺服器類型相同或更小。 例如，在基礎伺服器**十進位**資料行上呼叫 setBigDecimal 時，不需要轉換。 針對數值到字元的轉換，Java **numeric** 資料類型會轉換為 **String**。 例如，以值 "53" 在 varchar(50) 資料行上呼叫 setDouble，就會在該目的地資料行中產生字元值 "53"。

- **轉換 (y)** ：從 Java **numeric** 類型轉換到較小的基礎伺服器 **numeric** 類型。 這是一般轉換並遵循 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 轉換慣例。 有效位數一律會截斷 (絕不進位)，而溢位則會擲回未支援的轉換錯誤。 例如，在基礎整數資料行上使用值為 "1.9999" 的 updateDecimal，會在目的地資料行中產生 "1"；但如果傳遞 "3000000000"，則驅動程式會擲回錯誤。

- **視資料而定 (z)** ：從 Java **String** 類型轉換到基礎 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型會依下列情況而定：此驅動程式將 **String** 值傳送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 視情況執行轉換。 如果 sendStringParametersAsUnicode 設定為 true 且底層 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型為 **image**，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允許將 **nvarchar** 轉換為 **image** 而且會擲回 SQLServerException。 如果 sendStringParametersAsUnicode 設定為 false 且基礎 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型為 **image**，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允許將 **varchar** 轉換為 **image** 且不會擲回例外狀況。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會執行這些轉換，並且在發生問題時將錯誤傳遞回 JDBC 驅動程式。

當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行資料類型是 **XML** 時，此資料值必須是有效的 **XML**。 呼叫 updateBytes、updateBinaryStream 或 updateBlob 方法時, 資料值應該是 XML 字元的十六進位字串標記法。 例如：

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

請注意，如果 XML 字元採用特定字元編碼，就需要位元組順序標示 (BOM)。

## <a name="conversions-on-setobject"></a>setObject 的轉換

> [!NOTE]  
> 適用于 SQL Server 的 Microsoft JDBC driver 4.2 (和更新版本) 支援 JDBC 4.1 和4.2。 如需4.1 和4.2 資料類型對應和轉換的詳細資料, 請參閱 jdbc driver 的[jdbc 4.1 合規性](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)和 Jdbc[驅動程式的 jdbc 4.2 相容](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)性, 以及下列資訊。

若為傳遞給 [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) 類別之 setObject(\<類型>) 方法的 Java 類型資料，則適用下列轉換。

![JDBCSetObjectConversions](../../connect/jdbc/media/jdbc_jdbcsetobjectconversions.gif "JDBCSetObjectConversions")

不具有指定目標類型的 setObject 方法會使用預設對應。 在**字串**資料類型的案例中, 如果值超過**VARCHAR**的長度, 則會對應至**LONGVARCHAR**。 同樣地, 如果值超過支援的**Nvarchar**長度, 則**NVARCHAR**會對應至**LONGNVARCHAR** 。 這一點對 **byte[]** 來說也相同。 長度超過**VARBINARY**的值會變成**LONGVARBINARY**。

JDBC 驅動程式的 setObject 方法所支援的轉換有三種類別：

- **不失真 (x)** ：轉換的數值情況為，setter 類型與基礎伺服器類型相同或更小。 例如，在基礎伺服器**十進位**資料行上呼叫 setBigDecimal 時，不需要轉換。 針對數值到字元的轉換，Java **numeric** 資料類型會轉換為 **String**。 例如，以值 "53" 在 varchar(50) 資料行上呼叫 setDouble，會在該目的地資料行中產生字元值 "53"。

- **轉換 (y)** ：從 Java **numeric** 類型轉換到較小的基礎伺服器 **numeric** 類型。 這是一般轉換並遵循 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 轉換慣例。 有效位數一律會截斷 (絕不進位)，而溢位則會擲回未支援的轉換錯誤。 例如，在基礎整數資料行上使用值為 "1.9999" 的 updateDecimal，會在目的地資料行中產生 "1"；但如果傳遞 "3000000000"，則驅動程式會擲回錯誤。

- **視資料而定 (z)** ：從 Java **String** 類型轉換到基礎 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型會依下列情況而定：此驅動程式將 **String** 值傳送到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 視情況執行轉換。 如果 sendStringParametersAsUnicode 連線屬性設定為 true 而且基礎 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型為 **image**，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允許將 **nvarchar** 轉換為 **image** 而且會擲回 SQLServerException。 如果 sendStringParametersAsUnicode 設定為 false 且基礎 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型為 **image**，則 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 允許將 **varchar** 轉換為 **image** 且不會擲回例外狀況。

[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會執行大量 set 轉換，並且在發生問題時將錯誤傳遞回 JDBC 驅動程式。 用戶端轉換是例外狀況, 只有在**日期**、**時間**、**時間戳記**、**布林**值和**字串**值的情況下才會執行。

當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料行資料類型是 **XML** 時，此資料值必須是有效的 **XML**。 呼叫 setObject(byte[], SQLXML)、setObject(inputStream, SQLXML) 或 setObject(Blob, SQLXML) 方法時，此資料值應該是 XML 字元的十六進位字串表示法。 例如：

```xml
<hello>world</hello> = 0x3C68656C6C6F3E776F726C643C2F68656C6C6F3E
```

請注意，如果 XML 字元採用特定字元編碼，就需要位元組順序標示 (BOM)。

## <a name="see-also"></a>另請參閱

[了解 JDBC Driver 資料類型](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)
