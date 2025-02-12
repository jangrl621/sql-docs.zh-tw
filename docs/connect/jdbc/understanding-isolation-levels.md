---
title: 瞭解隔離等級 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2c41e23a-da6c-4650-b5fc-b5fe53ba65c3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6cfbc099d88a96574439fa8c178b12629d92782c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916645"
---
# <a name="understanding-isolation-levels"></a>了解隔離等級

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

交易可指定隔離等級，以定義某個交易必須與其他交易所修改之資源或資料隔離的程度。 隔離等級是以並行副作用來表示，例如，允許中途讀取或虛設項目讀取。  
  
交易隔離等級可控制下列項目：  
  
- 在讀取資料時是否採用鎖定，以及要求哪一類型的鎖定。  
  
- 保留讀取鎖定的時間長度。  
  
- 讀取作業是否參考另一個交易修改的資料列：  
  
  - 封鎖資料列上的獨佔鎖定直到釋放它為止。  
  
  - 擷取在啟動陳述式或交易時即存在的資料列認可版本。  
  
  - 讀取未認可的資料修改。  

選擇交易隔離等級並不會影響為保護資料修改所取得的鎖定。 交易永遠都會取得它所修改之任何資料的獨佔鎖定，並保留該鎖定直到交易完成為止，不論為該交易所設定的隔離等級為何皆同。 對於讀取作業，交易隔離等級主要是定義對於其他交易所做修改之影響的保謢等級。  
  
較低的隔離等級將可讓更多的使用者同時存取資料，但也會增加使用者可能遇到並行作用 (例如，中途讀取或遺失的更新) 的數目。 相反地，較高的隔離等級將可減少使用者遇到並行作用的類型，但是將需要更多的系統資源，而且會增加一個交易封鎖另一個交易的可能性。 選擇適當的隔離等級需視應用程式的資料完整性需求與每個隔離等級的額外負荷平衡而定。 最高的隔離等級為可序列化，可確保每次交易重複讀取作業時都能擷取相同的資料，但它是透過執行鎖定層級來達成此目的，因此在多使用者系統中有可能會影響其他使用者。 最低隔離等級為讀取未認可，可以擷取其他交易已修改但尚未認可的資料。 在讀取未認可中可能會發生所有的並行副作用，但由於沒有讀取鎖定或版本控制，因此可將負擔降到最低。  

## <a name="remarks"></a>Remarks

 下表顯示不同隔離等級所允許的並行副作用。  
  
| 隔離等級  | 中途讀取 | 不可重複讀取 | 虛設項目 (Phantom) |
| ---------------- | ---------- | ------------------- | ------- |
| 讀取未認可 | 是        | 是                 | 是     |
| 讀取認可   | 否         | 是                 | 是     |
| 可重複讀取  | 否         | 否                  | 是     |
| 快照式         | 否         | 否                  | 否      |
| 可序列化     | 否         | 否                  | 否      |
  
交易必須至少在可重複讀取的隔離等級執行，以防在兩個交易個別擷取相同的資料列，然後在稍後根據原始擷取的值更新資料列時可能發生的更新遺失。 如果兩個交易都使用單一 UPDATE 陳述式更新資料列，而且沒有以先前擷取的值做為更新的基礎，就不會在讀取認可的預設隔離等級發生更新的遺失。  

若要設定交易的隔離等級，您可以使用 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) 類別的 [setTransactionIsolation](../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md) 方法。 這個方法會根據下列其中一個連線常數，接受 **int** 值作為其引數：  

```java
con.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED);  
```

若要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的新快照隔離等級，您可以使用其中一個 `SQLServerConnection` 常數：  

```java
con.setTransactionIsolation(SQLServerConnection.TRANSACTION_SNAPSHOT);  
```

或者，您可以使用：  

```java
con.setTransactionIsolation(Connection.TRANSACTION_READ_COMMITTED + 4094);  
```

如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 隔離等級的詳細資訊，請參閱 [!INCLUDE[ssDE](../../includes/ssde_md.md)] 線上叢書的＜[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的隔離等級＞。  

## <a name="see-also"></a>另請參閱

[使用 JDBC Driver 執行交易](../../connect/jdbc/performing-transactions-with-the-jdbc-driver.md)  
