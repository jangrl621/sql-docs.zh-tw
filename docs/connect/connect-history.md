---
title: Microsoft SQL Server 的驅動程式歷程記錄 |Microsoft Docs
ms.custom: ''
ms.date: 05/04/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 05936a9555cacfc88c9219e19bc57772109ed047
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957516"
---
# <a name="driver-history-for-microsoft-sql-server"></a>Microsoft SQL Server 的驅動程式歷程記錄

本頁面說明用來連接到 SQL Server 的 Microsoft 歷程記錄資料連線技術。

## <a name="odbc"></a>ODBC

有三個不同世代適用於 SQL Server 的 Microsoft ODBC 驅動程式。 第一個「SQL Server」 ODBC 驅動程式仍然隨附于[Windows 資料存取元件](#microsoft-or-windows-data-access-components)中。 不建議將此驅動程式用於新的開發。 從 SQL Server 2005 開始, [SQL Server Native Client](#sql-server-native-client)包含 odbc 介面, 而且是 SQL Server 2005 到 SQL Server 2012 所隨附的 odbc 驅動程式。 不建議將此驅動程式用於新的開發。 在 SQL Server 2012 之後, [Microsoft ODBC Driver for SQL Server](#microsoft-odbc-driver-for-sql-server)就是最新的伺服器功能所更新的驅動程式。

### <a name="sql-server-native-client"></a>SQL Server Native Client

SQL Server Native Client 是用來 OLE DB 和 ODBC 的獨立程式庫。 SQL Server Native Client (通常是縮寫的 SNAC) 包含在 SQL Server 2005 到2012。 SQL Server Native Client 可以用於需要利用 SQL Server 2005 中引進的新功能到 SQL Server 2012 的應用程式。 (SQL Server 中的這些新功能不會更新 Microsoft/Windows 資料存取元件)。針對 SQL Server 2012 以外的新功能, SQL Server Native Client 將不會更新。 如果您想要利用新的 SQL Server 功能, 請切換到 [Microsoft ODBC Driver for SQL Server] 或 [適用于 SQL Server 的 Microsoft OLE DB 驅動程式]。

如需 SQL Server Native Client 的完整檔, 請參閱[SQL Server Native Client 檔](../relational-databases/native-client/sql-server-native-client-programming.md)。

### <a name="microsoft-odbc-driver-for-sql-server"></a>Microsoft ODBC Driver for SQL Server

在 SQL Server 2012 之後, SQL Server 的主要 ODBC 驅動程式已開發併發行為 Microsoft ODBC Driver for SQL Server。 如需詳細資訊, 請參閱[Microsoft ODBC Driver for SQL Server 檔](./odbc/microsoft-odbc-driver-for-sql-server.md)。

## <a name="ole-db"></a>OLE DB

有三個不同世代的 Microsoft OLE DB Provider for SQL Server。 第一個 "Microsoft OLE DB Provider for SQL Server" (SQLOLEDB) 仍隨附於 [Windows Data Access Component](#microsoft-or-windows-data-access-components)。 此提供者不會更新為新功能, 因此不建議使用此驅動程式進行新的開發。 從 SQL Server 2005 開始, [SQL Server Native Client](#sql-server-native-client)包含 OLE DB 提供者介面 (SQLNCLI), 而且是 SQL Server 2005 到 SQL Server 2017 所隨附的 OLE DB 提供者。 [已在 2011 年宣布取代](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) \(英文\) 它，因此，不建議使用此驅動程式來進行新開發。 在2017中, OLE DB 資料存取技術後來[undeprecated, 而新規劃的版本已](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/)針對2018宣佈。 新的 OLE DB 提供者稱為「適用于 SQL Server 的 Microsoft OLE DB 驅動程式」 (內含 MSOLEDBSQL.H), 目前已維護並受支援。

## <a name="adonet"></a>ADO.NET

ADO.NET 是由 Microsoft .NET Framework 引進, 並持續改進和維護。 這是 Microsoft .NET Framework 的核心元件。 如需詳細資訊, 請參閱[Microsoft ADO.NET for SQL Server](ado-net/microsoft-ado-net-for-sql-server.md)。

## <a name="jdbc"></a>JDBC

### <a name="microsoft-jdbc-driver-for-sql-server"></a>用於 SQL Server 的 Microsoft JDBC 驅動程式

以2000引進的 Microsoft JDBC Driver for SQL Server 會繼續改善及維護。 這是2016中的開放原始碼。 如需最新資訊, 包括如何下載驅動程式, 請參閱[JDBC driver 的總覽](./jdbc/overview-of-the-jdbc-driver.md)。

## <a name="php"></a>PHP

### <a name="microsoft-drivers-for-php-for-sql-server"></a>用於 SQL Server 之 PHP 的 Microsoft 驅動程式

以開放原始碼專案的2009引進, 適用于 PHP for SQL Server 的 Microsoft 驅動程式會繼續改善及維護。 如需最新資訊, 包括如何下載 PHP 驅動程式, 請參閱[適用于 php 的 Microsoft 驅動程式 SQL Server](./php/microsoft-php-driver-for-sql-server.md)。

## <a name="nodejs"></a>Node.js

### <a name="microsoft-driver-for-nodejs-for-sql-server"></a>適用于 node.js 的 Microsoft 驅動程式 SQL Server

適用于 node.js 的 Microsoft 驅動程式 SQL Server 可讓 Microsoft Windows 和 Microsoft Windows Azure 上的 node.js 應用程式存取 Microsoft SQL Server 和 Microsoft Windows Azure SQL Database。 開發工作不再著重于此驅動程式。 不建議使用適用于 node.js 的 Microsoft 驅動程式來建立新的應用程式, 以進行 SQL Server。

如需適用于 SQL Server 的 Microsoft Driver for node.js 的詳細資訊, 請參閱[windowsazure.storage/Node-sqlserver](https://github.com/Azure/node-sqlserver)。

### <a name="tedious"></a>覺得

Microsoft 目前提供並支援 node.js 中的開放原始碼乏味模組, 以使用 JavaScript 連接到 SQL Server。 如需詳細資訊, 請參閱[Node.js Driver for SQL Server](./node-js/node-js-driver-for-sql-server.md)。

## <a name="microsoft-or-windows-data-access-components"></a>Microsoft 或 Windows 資料存取元件

Microsoft/Windows 資料存取元件 (MDAC/WDAC) 隨附于 Windows, 可支援應用程式回溯相容性, 而且不屬於目前的 SQL Server 技術堆疊。 MDAC/WDAC 中的元件不會新增任何新功能, 因此不建議將它們用於新的應用程式開發。

基於本檔的目的, 您可以根據技術和產品, 將 MDAC/WDAC 堆疊分割成下列元件:

* **ADO**(包括 ADOMD 和 ADOX)
* **OLE DB**(包括 OLE DB 核心服務、SQL Server OLE DB 提供者、Oracle OLE DB 提供者、ODBC 驅動程式的 OLE DB 提供者、資料圖形提供者和遠端 Data Provider)
* **ODBC**(包括 ODBC 驅動程式管理員、SQL ODBC 驅動程式和 Oracle ODBC 驅動程式)

### <a name="mdacwdac-components"></a>MDAC/WDAC 元件

MDAC/WDAC 包含下列元件:

* **ODBC:** Microsoft 開放式資料庫連接 (ODBC) 介面是 C 程式設計語言介面，可讓應用程式從各種不同的資料庫管理系統 (DBMS) 存取資料。 使用此 API 的應用程式僅限於存取關聯式資料來源。
* **OLE DB:** OLE DB 是一組 COM 介面, 用於存取各種資料存放區中的資料。 有 OLE DB 提供者, 可存取資料庫、檔案系統、訊息存放區、目錄服務、工作流程和檔存放區中的資料。
* **ADO:** ActiveX Data Objects (ADO) 提供高階的程式設計模型。 雖然比直接編碼至 OLE DB 或 ODBC 的效能小很多, 但 ADO 很容易學習和使用。 它可以從指令碼語言 (例如 Microsoft Visual Basic Scripting Edition (VBScript) 或 Microsoft JScript) 使用。
* **ADOMD:** .ADO 多維度 (ADOMD) 是用於多維度資料提供者，例如 Microsoft OLAP 提供者，也就是 Microsoft Analysis Services 提供者。 自 MDAC 2.0 之後, 尚未對其進行重大功能增強。
* **ADOX:** 適用于 DDL 和安全性的 ADO 延伸模組 (ADOX) 可讓您建立和修改資料庫、資料表、索引或預存程式的定義。 您可以使用 ADOX 搭配任何提供者。 Microsoft Jet OLE DB 提供者提供 ADOX 的完整支援, 而 Microsoft SQL Server OLE DB 提供者則提供有限的支援。
* **Microsoft SQL Server 網路程式庫:** SQL Server 網路程式庫可讓 SQLOLEDB 和 SQLODBC 與 SQL Server 資料庫通訊。 下列 SQL Server 網路程式庫在 MDAC/WDAC 版本中已被取代: Banyan Vines、AppleTalk、ServerNet、IPX/SPX、Giganet 和 RPC。 TCP/IP 和具名管道會繼續受到支援, 並可在64位 Windows 作業系統上使用。
* **MSDASQL:** Microsoft OLE DB Provider for ODBC (MSDASQL) 可讓來存取資料來源的 ODBC 驅動程式透過 OLE DB 和 ADO (在內部使用 OLEDB） 建置的應用程式。 MSDASQL 是連接到 ODBC (而不是資料庫) 的 OLEDB 提供者。 當資料來源沒有直接 OLE DB 提供者存在時, 它就是用來從 OLE DB 到 ODBC 驅動程式的橋接器。 MSDASQL 隨附于 Windows 作業系統, 而 Windows Server 2008 和 Vista SP1 是第一版的 Windows 版本, 其中包含64位版本的技術。

### <a name="deprecated-mdacwdac-components"></a>已淘汰的 MDAC/WDAC 元件

目前的 MDAC/WDAC 版本仍然支援這些元件, 但在未來的版本中可能會將它們移除。 在開發新的應用程式時, Microsoft 建議您避免使用這些元件。 此外, 當您升級或修改現有的應用程式時, 請移除對這些元件的任何相依性。

* **SQLOLEDB:** Microsoft OLE DB Provider for SQL Server (SQLOLEDB)，可支援 Microsoft SQL server 的存取，已被取代。 可能不支援與 SQL Server 未來版本的連線。 在 Windows 7 之後, 將會從作業系統中移除連接到 SQL Server 7 之前版本的功能。 新的應用程式應該使用適用于 SQL Server 的 Microsoft OLE DB 驅動程式 (內含 MSOLEDBSQL.H), 其支援新的 SQL Server 功能。 現有的應用程式應該遷移至 Microsoft OLE DB 驅動程式以進行 SQL Server, 以獲得更好的效能、可靠性和支援能力。 如需詳細資訊, 請參閱[將應用程式更新為從 MDAC SQL Server 的 OLE DB 驅動](oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md)程式。
* **SQLODBC:** Microsoft SQL Server ODBC 驅動程式 (SQLODBC) (支援 Microsoft SQL Server 的存取) 已被取代。 可能不支援與 SQL Server 未來版本的連線。 在 Windows 7 之後, 將會從作業系統中移除連接到 SQL Server 7 之前版本的功能。 新的應用程式應該使用 Windows 上的 Microsoft ODBC Driver for SQL Server, 其支援新的 SQL Server 功能。 現有的應用程式也應該遷移到 Microsoft ODBC Driver for SQL Server, 以獲得更好的效能、可靠性和支援能力。 如需相關資訊, 請參閱[將應用程式更新為從 MDAC SQL Server Native Client](../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)。
* **Microsoft Jet 資料庫引擎 4.0:** 從2.6 版開始, MDAC 不再包含 Jet 元件。 換句話說, MDAC 2.6、2.7 和2.8 並不包含 Microsoft Jet、Microsoft Jet OLE DB 提供者、ODBC 桌面資料庫驅動程式, 或 Jet 資料存取物件 (DAO)。 

  沒有64位版本的 Jet 資料庫引擎、Jet OLEDB 驅動程式、Jet ODBC 驅動程式或 Jet DAO 可用。 如需詳細資訊，請參閱[知識庫文章 957570](https://support.microsoft.com/kb/957570)。 在64位版本的 Windows 上, 32 位的 Jet 會在 Windows WOW64 子系統下執行。 如需有關 WOW64 的詳細資訊, 請參閱[MSDN WOW64 檔](/windows/desktop/WinProg64/wow64-implementation-details)。 原生64位應用程式無法與在 WOW64 中執行的32位 Jet 驅動程式通訊。

  Microsoft 不會使用 Microsoft Jet, 而是在開發需要關聯式資料存放區的新非 Microsoft 存取應用程式時, 建議您使用[Microsoft SQL Server Express 版本](https://www.microsoft.com/sql-server/sql-server-editions-express)。 這些新的或已轉換的 Jet 應用程式可以繼續使用 Jet, 目的是要使用 Microsoft Office 2003 和舊版檔案 (.mdb 和 .xls) 來進行非主要的資料儲存。 不過, 針對這些應用程式, 您應該規劃從 Jet 遷移至 Microsoft Access 資料庫引擎。 您可以[下載 Microsoft Access 資料庫引擎](https://www.microsoft.com/download/details.aspx?id=54920), 這可讓您讀取和寫入 office 2003 (.mdb 和 .xls) 或 office 2007 (* .accdb、* xlsm、* .xlsx 和 *. .xlsb) 檔案格式中既有的檔案。

  > [!IMPORTANT]
  > 如需特定使用限制, 請參閱 2007 Office System 使用者授權合約。

  > [!NOTE]
  > SQL Server 應用程式也可以透過 2007 Office 系統驅動程式, 存取 2007 Office System 和更早版本的檔案, SQL Server 異質資料連接和整合服務功能。 此外, 64 位 SQL Server 應用程式可以在64位 Windows 上使用32位 SQL Server Integration Services (SSIS), 以存取32位的 Jet 和 2007 Office 系統檔案。

* **MSDADS:** 透過適用于資料成形的 Microsoft OLE DB 提供者 (MSDADS), 您可以在應用程式中建立索引鍵、欄位或資料列集之間的階層式關聯性。 自 MDAC 2.1 之後, 尚未進行任何主要的功能增強。 此提供者已被取代。 Microsoft 建議您使用 XML, 而不是 MSDADS。
* **ORACLE ODBC 和 oracle OLE DB:** Microsoft Oracle ODBC 驅動程式 (Oracle ODBC) 和 Microsoft OLE DB Provider for Oracle (Oracle OLE DB) 提供對 Oracle 資料庫伺服器的存取權。 它們是使用 Oracle Call Interface (OCI) 第7版所建立, 並提供完整的 Oracle 7 支援。 此外, 它也會使用 Oracle 7 模擬來為 Oracle 8 資料庫提供有限的支援。 Oracle 不再支援使用 OCI 第7版呼叫的應用程式。 這些技術已淘汰。 如果您使用 Oracle 資料來源, 則應該遷移至 Oracle 提供的驅動程式和提供者。
* **RDS:** 遠端資料服務 (RDS) 是透過網際網路或近端內部網路存取遠端的 ADO 資料錄集物件的專屬 Microsoft 機制。 RDS 已被取代;自 MDAC 2.1 之後, 尚未對 RDS 進行重大功能增強。 Microsoft 發行了具有大量 SOAP 功能的 .NET Framework, 並取代了 RDS 元件。 在 Windows 7 之後, 所有 RDS 伺服器元件都會從作業系統中移除。
* **JRO:** Jet 複寫物件 (JRO) 已被取代。 JRO 會在 ADO with jet ( *.mdb) 資料庫中使用, 以建立及壓縮 jet 資料庫 (.mdb) 並執行 jet Replication Management。MDAC 2.7 將會是它的最後一次發行。[JRO] 將無法在64位 Windows 作業系統上使用。Microsoft Access 2007 檔案格式 (* .accdb) 不支援 JRO。
* **16 位 ODBC 支援:** 如果您使用的是16位應用程式, 您應該遷移至32位應用程式。 16位功能已被取代, 而且會從64位作業系統中移除。 如需詳細資訊，請參閱[知識庫文章 896458](https://support.microsoft.com/kb/896458)。
* **OLEDB 簡單提供者 (MSDAOSP):** OLEDB Simple 提供者提供了一個架構, 可讓您透過簡單的資料快速建立 OLE DB 提供者。 MSDAOSP 已被取代。
* **ODBC 資料指標程式庫:** ODBC 資料指標程式庫 (ODBCCR32) 提供有限的用戶端資料指標。 ODBC 資料指標程式庫已被取代;您的應用程式可以使用伺服器端資料指標實作為替代方案。
* **OLE DB 跨進程介面遠端處理:** OLEDB 介面遠端處理 (msdaps .dll) 嘗試讓 OLE DB 提供者無法執行進程。 OLEDB 跨進程介面遠端功能已被取代。
* **AppleTalk 和 Banyan VINES SQL 網路程式庫:** Banyan Vines、AppleTalk、ServerNet、IPX/SPX、Giganet 和 RPC SQL 網路程式庫已淘汰。 如果您使用任何一種技術, 您應該將應用程式修改為使用其中一個其他網路程式庫, 例如 TCP/IP 和具名管道。

### <a name="mdacwdac-releases"></a>MDAC/WDAC 版本

以下是過去 MDAC/WDAC 版本的支援案例清單, 從最早的開始。

* **Mdac 1.5、mdac 2.0 和 mdac 2.1:** 這些版本的 MDAC 是透過 Microsoft Windows NT Option Pack、Microsoft Windows Platform SDK 或 MDAC 網站發行的獨立發行版本。 已不再支援這些版本的 MDAC。
* **MDAC 2.5:** 這個版本的 MDAC 是隨附在 Windows 2000 作業系統。 MDAC 2.5 的 Service pack 隨附于對應的 Windows 2000 service pack 中。
* **MDAC 2.6:** MDAC 2.6 RTM、 SP1 和 SP2 是分別隨附於 Microsoft SQL Server 2000 RTM、 SP1 和 SP2。 此外, 這些 MDAC service pack 已根據 Microsoft SQL Server 2000 service pack 發行排程發行至 MDAC 網站。 您可以在 Windows 2000、Windows Millennium Edition、Windows NT、Windows 95 和 Windows 98 平臺上安裝此版本的 MDAC 和其 service pack。 不再支援此版本的 MDAC。
* **MDAC 2.7:** 這個版本的 MDAC 已隨附於 Microsoft Windows XP RTM 和 SP1 作業系統。 您可以在 Windows 2000、Windows Millennium、Windows NT 和 Windows 98 平臺上安裝此版本的 MDAC 和其 service pack。 您只能透過作業系統或其服務套件, 在 Windows XP 平臺上安裝此版本。 不再支援此版本的 MDAC。
* **MDAC 2.8:** 這個版本的 MDAC 已隨附於 Windows Server 2003 和 Windows XP SP2 和更新版本。 您也可以在 Windows 2000 上安裝此版本的 MDAC 和其 service pack。

  * 32位版本的 MDAC 2.8 也會在 Windows Server 2003 發行給客戶時, 同時發行至 MDAC 網站。
  * 64位版本的 MDAC 2.8 已與64位版本的 Windows Server 2003 和 Windows XP 一起發行。

* **Windows Data Access Components (WDAC):** MDAC 從 Windows Vista 和 Windows Server 2008 開始, 將其名稱變更為 WDAC-「Windows 資料存取元件」。 WDAC 會納入為作業系統的一部分, 而且不會針對轉散發而分別提供。 WDAC 的維修性受限於作業系統的生命週期。

  32位和64位版本的 WDAC 分別與32位和64位版本的 Windows 作業系統一起發行。

## <a name="obsolete-data-access-technologies"></a>過時的資料存取技術

過時的技術是在數個產品版本中尚未增強或更新的技術, 將從未來的產品版本中排除。 當您撰寫新的應用程式時, 請勿使用這些技術。 當您修改使用這些技術所撰寫的現有應用程式時, 請考慮將這些應用程式遷移至 ADO.NET 或其他目前的技術。

下列元件被視為已淘汰:

* **DB-Library:** DB 程式庫是 SQL Server 特有的程式設計模型，包括 C Api。 因為 SQL Server 6.5, 所以沒有 DB-LIBRARY 的增強功能。 其最終版本是使用 SQL Server 2000, 而且不會移植到64位的 Windows 作業系統。
* **內嵌 SQL (E-SQL):** E-SQL 是一種 SQL Server 特定的程式設計模型, 可讓 Transact-sql 語句內嵌在 Visual C 程式碼中。 自 SQL Server 6.5 之後, 尚未對電子 SQL 進行任何增強功能。 其最終版本是使用 SQL Server 2000, 而且不會移植到64位的 Windows 作業系統。
* **資料存取物件 (DAO):** DAO 提供 JET (Access) 資料庫的存取權。 此 API 可從 Microsoft Visual Basic、Microsoft Visual C++和指令碼語言中使用。 它包含在 Microsoft Office 2000 和 Office XP 中。 DAO 3.6 是這項技術的最終版本。 它將無法在64位的 Windows 作業系統上使用。
* **遠端資料物件 (RDO):** RDO 是特別為了存取遠端 ODBC 關聯式資料來源而設計, 讓您更輕鬆地使用 ODBC, 而不需要複雜的應用程式程式碼。 它包含在 Microsoft Visual Basic 第4、5和6版中。 RDO 版本2.0 是這項技術的最終版本。

[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
