---
title: 呼叫預存程式 (OLE DB) |Microsoft Docs
description: 呼叫預存程序 (OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- calling stored procedures
- RPC escape sequence
- OLE DB, stored procedures
- parameters [OLE DB Driver for SQL Server], OLE DB
- ODBC CALL escape sequence
- stored procedures [OLE DB], calling
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 26e97354d54cb65578bcbb35d2c96fb6914270d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015206"
---
# <a name="stored-procedures---calling"></a>預存程序 - 呼叫
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  預存程序可以有零或多個參數。 它也可以傳回值。 使用 SQL Server 的 OLE DB 驅動程式時, 可以藉由下列方式傳遞預存程式的參數:  
  
-   將資料值寫入程式碼。  
  
-   使用參數標記 (?) 來指定參數、將程式變數繫結至參數標記，然後將資料值放在程式變數中。  
  
> [!NOTE]  
>  搭配 OLE DB 使用具名參數呼叫 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 預存程序時，參數名稱開頭必須是 '\@' 字元。 這是一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 特定的限制。 SQL Server 的 OLE DB 驅動程式會比 MDAC 更嚴格地強制執行此限制。  
  
 為支援參數，會在命令物件上公開 **ICommandWithParameters** 介面。 為使用參數，取用者會先呼叫 **ICommandWithParameters::SetParameterInfo** 方法 (或選擇性地準備呼叫 **GetParameterInfo** 方法的呼叫陳述式) 來描述提供者的參數。 接著，取用者會建立指定緩衝區結構的存取子，並將參數值放在此緩衝區中。 最後，它會將存取子的控制代碼與緩衝區的指標傳遞到 **Execute** 的緩衝區。 稍後呼叫 **Execute** 時，取用者會將新的參數值放在緩衝區中，並利用存取子控制代碼和緩衝區指標呼叫 **Execute**。  
  
 使用參數呼叫暫存預存程序的命令必須先呼叫 **ICommandWithParameters::SetParameterInfo** 來定義參數資訊，然後就可以成功準備命令。 這是因為暫存預存程序的內部名稱與用戶端所使用的外部名稱不同，而且 MSOLEDBSQL 無法查詢系統資料表來判斷暫存預存程序的參數資訊。  
  
 以下是參數繫結程序中的步驟：  
  
1.  在 DBPARAMBINDINFO 結構的陣列中填入參數資訊；也就是參數名稱、參數資料類型的提供者專屬名稱，或標準資料類型名稱等等。 陣列中的每個結構會描述一個參數。 接著，就會將此陣列傳遞到 **SetParameterInfo** 方法。  
  
2.  呼叫 **ICommandWithParameters::SetParameterInfo** 方法來描述提供者的參數。 **SetParameterInfo** 會指定每個參數的原生資料類型。 **SetParameterInfo** 引數為：  
  
    -   用於設定類型資訊之參數的數目。  
  
    -   用於設定類型資訊之參數序數的陣列。  
  
    -   DBPARAMBINDINFO 結構的陣列。  
  
3.  使用 **IAccessor::CreateAccessor** 命令建立參數存取子。 存取子會指定緩衝區的結構，並將參數值放在緩衝區中。 **CreateAccessor** 命令會從一組繫結建立存取子。 這些繫結可由取用者使用 DBBINDING 結構的陣列描述。 每個繫結都會與取用者緩衝區的單一參數產生關聯，而且會包含資訊，例如：  
  
    -   套用繫結之參數的序數。  
  
    -   繫結的項目 (資料值、其長度及其狀態)。  
  
    -   緩衝區中對每一個部分的位移。  
  
    -   存在於取用者緩衝區內之資料值的長度和類型。  
  
     存取子是由其類型為 HACCESSOR 的控制代碼識別。 此控制代碼會由 **CreateAccessor** 方法傳回。 每當取用者完成使用存取子時，取用者必須呼叫 **ReleaseAccessor** 方法來釋放所保留的記憶體。  
  
     當取用者呼叫 **ICommand::Execute** 之類的方法時，它會將控制代碼傳遞到存取子以及緩衝區本身的指標。 提供者會使用此存取子決定如何傳送包含在緩衝區中的資料。  
  
4.  填入 DBPARAMS 結構。 從中取用輸入參數值的取用者變數以及寫入輸出參數的取用者變數在執行階段都會傳遞到 DBPARAMS 結構的 **ICommand::Execute** 中。 DBPARAMS 結構包含三個元素：  
  
    -   根據存取子控制代碼指定的繫結，提供者從其中擷取輸入參數資料的緩衝區指標以及提供者傳回輸出參數資料的緩衝區指標。  
  
    -   緩衝區中的參數集數目。  
  
    -   存取子控制代碼會在步驟 3 中建立。  
  
5.  使用 **ICommand::Execute** 執行命令。  
  
## <a name="methods-of-calling-a-stored-procedure"></a>呼叫預存程序的方法  
 在中[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行預存程式時, SQL Server 的 OLE DB 驅動程式支援:  
  
-   ODBC CALL 逸出序列。  
  
-   遠端程序呼叫 (RPC) 逸出序列。  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] EXECUTE 陳述式。  
  
### <a name="odbc-call-escape-sequence"></a>ODBC CALL 逸出序列  
 如果您知道參數資訊，請呼叫 **ICommandWithParameters::SetParameterInfo** 方法來描述提供者的參數。 否則，在呼叫預存程序中使用 ODBC CALL 語法時，提供者會呼叫 Helper 函數來尋找預存程序參數資訊。  
  
 如果您不確定參數資訊 (參數中繼資料)，建議使用 ODBC CALL 語法。  
  
 使用 ODBC CALL 逸出序列呼叫程序的一般語法為：  
  
 {[ **?=** ]**call**_procedure\_name_[ **(** [*parameter*][ **,** [_parameter_]]... **)** ]}  
  
 例如：  
  
```  
{call SalesByCategory('Produce', '1995')}  
```  
  
### <a name="rpc-escape-sequence"></a>RPC 逸出序列  
 RPC 逸出序列類似於呼叫預存程序的 ODBC CALL 語法。 如果您要呼叫程序數次，RPC 逸出序列會在呼叫預存程序的三種方法之間，提供最佳效能。  
  
 當 RPC 逸出序列用於執行預存程序時，提供者不會呼叫任何 Helper 函數來判斷參數資訊 (如果是 ODBC CALL 語法，則會這麼做)。 RPC 語法比 ODBC CALL 語法簡單，因此命令集的剖析速度較快，可以增進效能。 在此情況下，您需要執行 **ICommandWithParameters::SetParameterInfo** 來提供參數資訊。  
  
 RPC 逸出序列要求您擁有傳回值。 如果預存程序沒有傳回值，伺服器預設會傳回 0。 此外，您無法在預存程序上開啟 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料指標。 預存程序會以隱含的方式準備，而 **ICommandPrepare::Prepare** 的呼叫將會失敗。 因為無法準備 RPC 呼叫, 所以您不能查詢資料行中繼資料。IColumnsInfo:: GetColumnInfo 和 IColumnsRowset:: GetColumnsRowset 會傳回 DB_E_NOTPREPARED。  
  
 如果您知道所有參數中繼資料，RPC 逸出序列是執行預存程序的建議方式。  
  
 這是呼叫預存程序之 RPC 逸出序列的範例：  
  
```  
{rpc SalesByCategory}  
```  
  
 如需示範 RPC escape 序列的範例應用程式, 請參閱[ &#40;使用 RPC 語法&#41;來執行預存程式和處理傳回碼和&#40;輸出&#41;參數 OLE DB](../../oledb/ole-db-how-to/results/execute-stored-procedure-with-rpc-and-process-output.md)。  
  
### <a name="transact-sql-execute-statement"></a>Transact-SQL EXECUTE 陳述式  
 ODBC CALL 逸出序列和 RPC 逸出序列都是呼叫預存程序而非 [EXECUTE](../../../t-sql/language-elements/execute-transact-sql.md) 陳述式的慣用方法。 SQL Server 的 OLE DB 驅動程式會使用的 RPC 機制[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]來優化命令處理。 此 RPC 通訊協定會排除在伺服器上完成的許多參數處理與陳述式剖析，藉以增加效能。  
  
 這是 [!INCLUDE[tsql](../../../includes/tsql-md.md)] **EXECUTE** 陳述式的範例：  
  
```  
EXECUTE SalesByCategory 'Produce', '1995'  
```  
  
## <a name="see-also"></a>另請參閱  
 [預存程序](../../oledb/ole-db/stored-procedures.md)  
  
  
