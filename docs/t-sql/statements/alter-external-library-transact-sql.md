---
title: ALTER EXTERNAL LIBRARY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: machine-learning
ms.topic: language-reference
f1_keywords:
- ALTER EXTERNAL LIBRARY
- ALTER_EXTERNAL_LIBRARY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER EXTERNAL LIBRARY
author: dphansen
ms.author: davidph
manager: cgronlund
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=azuresqldb-current||=sqlallproducts-allversions'
ms.openlocfilehash: 461a9c27b456f3f3955d5bcb7229e0c4448a0996
ms.sourcegitcommit: 9062c5e97c4e4af0bbe5be6637cc3872cd1b2320
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68471140"
---
# <a name="alter-external-library-transact-sql"></a>ALTER EXTERNAL LIBRARY (Transact-SQL)  

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

修改現有外部套件程式庫的內容。

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||sqlallproducts-allversions"
> [!NOTE]
> 在 SQL Server 2017 中，支援 R 語言和 Windows 平台。 SQL Server 2019 CTP 2.4 和更新版本支援 Windows 和 Linux 平台上的 R、Python 和外部語言。
::: moniker-end

::: moniker range="=azuresqldb-current"
> [!NOTE]
> 在 Azure SQL Database 中，您可以藉由移除程式庫、使用 **sqlmlutils** 來安裝變更的版本以更改程式庫。 如需 **sqlmlutils** 的詳細資訊，請參閱[使用 sqlmlutils 新增套件](/azure/sql-database/sql-database-machine-learning-services-add-r-packages#add-a-package-with-sqlmlutils)。
::: moniker-end

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2019"></a>SQL Server 2019 的語法

```text
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = <language> )
[ ; ]

<file_spec> ::=
{
    (CONTENT = { <client_library_specifier> | <library_bits> | NONE}
    [, PLATFORM = <platform> )
}

<client_library_specifier> :: =
{
      '[\\computer_name\]share_name\[path\]manifest_file_name'
    | '[local_path\]manifest_file_name'
    | '<relative_path_in_external_data_source>'
}

<library_bits> :: =
{ 
      varbinary_literal 
    | varbinary_expression 
}

<platform> :: = 
{
      WINDOWS
    | LINUX
}

<language> :: = 
{
      'R'
    | 'Python'
    | <external_language>
}
```
::: moniker-end
::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
## <a name="syntax-for-sql-server-2017"></a>SQL Server 2017 的語法

```text
ALTER EXTERNAL LIBRARY library_name
[ AUTHORIZATION owner_name ]
SET <file_spec>
WITH ( LANGUAGE = 'R' )
[ ; ]

<file_spec> ::=
{
    (CONTENT = { <client_library_specifier> | <library_bits> | NONE}
    [, PLATFORM = WINDOWS )
}

<client_library_specifier> :: =
{
      '[\\computer_name\]share_name\[path\]manifest_file_name'
    | '[local_path\]manifest_file_name'
    | '<relative_path_in_external_data_source>'
}

<library_bits> :: =
{ 
      varbinary_literal 
    | varbinary_expression 
}
```
::: moniker-end

::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"
## <a name="syntax-for-azure-sql-database"></a>Azure SQL Database 的語法

```text
CREATE EXTERNAL LIBRARY library_name  
[ AUTHORIZATION owner_name ]  
FROM <file_spec> [ ,...2 ]  
WITH ( LANGUAGE = 'R' )  
[ ; ]  

<file_spec> ::=  
{  
    (CONTENT = <library_bits>)  
}  

<library_bits> :: =  
{ 
      varbinary_literal 
    | varbinary_expression 
}
```
::: moniker-end

### <a name="arguments"></a>引數

**library_name**

指定現有套件程式庫的名稱。 程式庫的範圍限制為使用者。 程式庫名稱在特定使用者或擁有者的內容中必須是唯一的。

程式庫名稱不能任意指派。 也就是說，您必須使用呼叫執行階段載入套件時所預期的名稱。

**owner_name**

指定擁有外部程式庫的使用者或角色名稱。

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions"
**file_spec**

指定適用於特定平台的套件內容。 只支援每個平台一個檔案成品。

檔案可以本機路徑或網路路徑形式來指定。 如果指定了資料來源選項，檔案名稱就可以是相對於 `EXTERNAL DATA SOURCE` 中所參考之容器的相對路徑。

(選擇性) 可以指定檔案的 OS 平台。 針對特定語言或執行階段，每個 OS 平台只允許一個檔案成品或內容。

::: moniker-end

**library_bits**

以十六進位常值的形式指定套件的內容，類似於組件。

如果您具備改變程式庫的必要權限，但在伺服器上的檔案存取受到限制，且您無法將內容儲存至伺服器可存取的路徑，這個選項就非常有用。

您可以改為以二進位格式的變數來傳遞套件內容。

::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
**PLATFORM = WINDOWS**

指定程式庫內容的平台。 修改現有程式庫以加入不同平台時，需要此值。
在 SQL Server 2017 中，Windows 是唯一支援的平台。
::: moniker-end

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
**平台**

指定程式庫內容的平台。 修改現有程式庫以加入不同平台時，需要此值。 
在 SQL Server 2019 中，支援 Windows 和 Linux 平台。
::: moniker-end

::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
**LANGUAGE = 'R'**

指定套件的語言。 SQL Server 2017 支援 R。
::: moniker-end

::: moniker range="=azuresqldb-current||=sqlallproducts-allversions"
**LANGUAGE = 'R'**

指定套件的語言。 Azure SQL Database 支援 R。
::: moniker-end

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
**language**

指定套件的語言。 此值可以是 **R**、**Python** 或外部語言的名稱 (請參閱[建立外部語言](create-external-language-transact-sql.md))。
::: moniker-end

## <a name="remarks"></a>Remarks

::: moniker range=">=sql-server-2017 <=sql-server-2017||=sqlallproducts-allversions"
對於 R 語言，必須先針對 Windows，以具備 .ZIP 副檔名的 ZIP 壓縮封存檔案形式備妥套件。 在 SQL Server 2017 中僅支援 Windows 平台。  
::: moniker-end

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
針對 R 語言，在使用檔案時，必須以具有 .ZIP 副檔名的 ZIP 壓縮封存檔案形式備妥套件。 

針對 Python 語言，.whl 或 .zip 檔案套件必須以壓縮封存檔案的型式準備。 若套件已經是 .zip 檔案，它必須包含在新的 .zip 檔案中。 目前不支援直接上傳 .whl 或 .zip 檔案的套件。
::: moniker-end

`ALTER EXTERNAL LIBRARY` 陳述式只會將程式庫位元上傳至資料庫。 當使用者在 [sp_execute_external_script (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) 中執行呼叫程式庫的程式碼時，就會安裝已修改的程式庫。

## <a name="permissions"></a>權限

根據預設，**dbo** 使用者或 **db_owner** 角色的任何成員都有執行 ALTER EXTERNAL LIBRARY 的權限。 此外，建立外部程式庫的使用者可以改變該外部程式庫。

## <a name="examples"></a>範例

下列範例會變更名為 `customPackage` 的外部程式庫。

::: moniker range=">=sql-server-2017||>=sql-server-linux-ver15||sqlallproducts-allversions"
### <a name="replace-the-contents-of-a-library-using-a-file"></a>使用檔案取代程式庫的內容

下列範例會使用包含更新位元的 ZIP 壓縮檔案，來修改名為 `customPackage` 的外部程式庫。

```sql
ALTER EXTERNAL LIBRARY customPackage 
SET 
  (CONTENT = 'C:\Program Files\Microsoft SQL Server\MSSQL14.MSSQLSERVER\customPackage.zip')
WITH (LANGUAGE = 'R');
```

若要安裝更新的程式庫，請執行 `sp_execute_external_script` 預存程序。

```sql
EXEC sp_execute_external_script 
@language =N'R', 
@script=N'library(customPackage)'
;
```
::: moniker-end

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
針對 SQL Server 2019 中的 Python 語言，只需要將範例中的 `'R'` 替換成 `'Python'` 即可正常運作。
::: moniker-end

### <a name="alter-an-existing-library-using-a-byte-stream"></a>使用位元組資料流改變現有程式庫

下列範例會以十六進位常值來傳遞新位元，藉以更改現有程式庫。

```SQL
ALTER EXTERNAL LIBRARY customLibrary 
SET (CONTENT = 0xABC123...) WITH (LANGUAGE = 'R');
```

::: moniker range=">=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions"
針對 SQL Server 2019 中的 Python 語言，只需要將範例中的 `'R'` 替換成 `'Python'` 即可正常運作。
::: moniker-end

> [!NOTE]
> 此程式碼範例僅示範語法；`CONTENT =` 中的二進位值已被截斷以提高可讀性，且並不會建立可運作的程式庫。 二進位變數的實際內容會更長。

## <a name="see-also"></a>另請參閱

[CREATE EXTERNAL LIBRARY (Transact-SQL)](create-external-library-transact-sql.md)  
[DROP EXTERNAL LIBRARY (Transact-SQL)](drop-external-library-transact-sql.md)  
[sys.external_library_files](../../relational-databases/system-catalog-views/sys-external-library-files-transact-sql.md)  
[sys.external_libraries](../../relational-databases/system-catalog-views/sys-external-libraries-transact-sql.md) 
