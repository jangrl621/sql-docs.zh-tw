---
title: 選擇資料來源 (SQL Server 匯入和匯出精靈) | Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql13.dts.impexpwizard.chooseadatasource.f1
ms.assetid: ebf28a62-dfc1-4b39-9db5-df1919e5fccb
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 64487ec1d93411046ae0e776f2f82b35c7b6eea7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68102637"
---
# <a name="choose-a-data-source-sql-server-import-and-export-wizard"></a>選擇資料來源 (SQL Server 匯入和匯出精靈)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  在 [歡迎使用] 頁面之後，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈會顯示 [選擇資料來源]  。 在此頁面上，您可以提供資料來源及其連接方式的相關資訊。
  
如需您可以使用之資料來源的資訊，請參閱 [我可以使用哪些資料來源和目的地？](../../integration-services/import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

> [!NOTE]
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 匯入和匯出精靈會利用 SQL Server Integration Services (SSIS)。 因此，適用於 SSIS 的相同限制也適用於該精靈。  例如，預設新增的 ErrorCode 和 ErrorColumn 資料行，如[處理資料中的錯誤](../../integration-services/data-flow/error-handling-in-data.md)中所述。

## <a name="screen-shot-of-the-choose-a-data-source-page"></a>[選擇資料來源] 頁面的螢幕擷取畫面 
下圖顯示精靈中 [選擇資料來源]  頁面的第一個部分。 頁面的其餘部分會有不同數目的選項，視您選擇的資料來源而定。

![選擇來源](../../integration-services/import-export-data/media/choose-source.png)

## <a name="choose-a-data-source"></a>選擇資料來源
 **資料來源**  
選取可連接到來源的資料提供者來指定資料來源。

-   **一般來說，您可以從資料提供者的名稱來辨識您需要的資料提供者**，因為提供者的名稱通常會包含資料來源的名稱，例如「一般檔案」  來源、Microsoft *Excel*、Microsoft *Access*、.Net Framework Data Provider for *SqlServer*、.Net Framework Data Provider for *Oracle*。

-   **如果您有適用於資料來源的 ODBC 驅動程式**，請選取 .NET Framework Data Provider for ODBC。 然後輸入驅動程式的特定資訊。 ODBC 驅動程式未列在資料來源的下拉式清單中。 .Net Framework Data Provider for ODBC 作用為 ODBC 驅動程式的包裝函式。 如需詳細資訊，請參閱[連線至 ODBC 資料來源](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)。

-   **您的資料來源可能有一個以上的提供者可用。** 通常，您可以選取適用於來源的任何提供者。 例如，若要連線至 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，您可以使用 .NET Framework Data Provider for SQL Server 或 SQL Server ODBC 驅動程式。 (清單中依然還會有其他提供者，但已不再支援。) 

## <a name="my-data-source-isnt-in-the-list"></a>我的資料來源不在清單中
-   您可能必須從 Microsoft 或協力廠商**下載資料提供者**。 [資料來源]  清單中可用的資料提供者清單，僅包括您在電腦上安裝的提供者。 如需您可以使用之資料來源的資訊，請參閱 [我可以使用哪些資料來源和目的地？](import-and-export-data-with-the-sql-server-import-and-export-wizard.md#wizardSources)

-   **您是否有適用於資料來源的 ODBC 驅動程式？** ODBC 驅動程式並未列在下拉式資料來源清單中。 如果您有適用於資料來源的 ODBC 驅動程式，請選取 .NET Framework Data Provider for ODBC。 然後輸入驅動程式的特定資訊。 .Net Framework Data Provider for ODBC 用作為 ODBC 驅動程式的包裝函式。 如需詳細資訊，請參閱[連線至 ODBC 資料來源](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)。

-   **64 位元和 32 位元提供者：** 如果您是執行 64 位元精靈，就不會看到只安裝 32 位元提供者的資料來源，反之亦然。

> [!NOTE]
> 若要使用 64 位元版本的 [SQL Server 匯入和匯出精靈]，您必須安裝 SQL Server。 SQL Server Data Tools (SSDT) 和 SQL Server Management Studio (SSMS) 是 32 位元應用程式，而且只會安裝 32 位元檔案 (包含 32 位元版本的精靈)。

## <a name="after-you-choose-a-data-source"></a>選擇資料來源之後
選擇資料來源之後，[選擇資料來源]  頁面的其餘部分會有不同數目的選項，視您選擇的資料提供者而定。

若要連線至常用的資料來源，請參閱下列其中一個頁面。
-   [連線到 SQL Server](../../integration-services/import-export-data/connect-to-a-sql-server-data-source-sql-server-import-and-export-wizard.md)
-   [連接到 Oracle](../../integration-services/import-export-data/connect-to-an-oracle-data-source-sql-server-import-and-export-wizard.md)
-   [連線至一般檔案 (文字檔)](../../integration-services/import-export-data/connect-to-a-flat-file-data-source-sql-server-import-and-export-wizard.md)
-   [連線至 Excel](../../integration-services/import-export-data/connect-to-an-excel-data-source-sql-server-import-and-export-wizard.md)
-   [連線至 Access](../../integration-services/import-export-data/connect-to-an-access-data-source-sql-server-import-and-export-wizard.md)
-   [使用 ODBC 連線](../../integration-services/import-export-data/connect-to-an-odbc-data-source-sql-server-import-and-export-wizard.md)
-   [連線至 Azure Blob 儲存體](../../integration-services/import-export-data/connect-to-azure-blob-storage-sql-server-import-and-export-wizard.md)
-   [連線至 PostgreSQL](../../integration-services/import-export-data/connect-to-a-postgresql-data-source-sql-server-import-and-export-wizard.md)
-   [連線至 MySQL](../../integration-services/import-export-data/connect-to-a-mysql-data-source-sql-server-import-and-export-wizard.md)

若要了解如何連線至此處未列出的資料提供者的資訊，請參閱[連接字串參考](https://www.connectionstrings.com/)。 此第三方網站包含範例連接字串，以及資料提供者及其所需連線資訊的更多資訊。

## <a name="whats-next"></a>下一步
 在您提供資料來源及其連接方式的相關資訊之後，下一個頁面為 [選擇目的地]  。 在此頁面上，您可以提供資料目的地及其連接方式的相關資訊。 如需詳細資訊，請參閱 [選擇目的地](../../integration-services/import-export-data/choose-a-destination-sql-server-import-and-export-wizard.md)。

## <a name="see-also"></a>另請參閱
[透過匯入和匯出精靈的簡單範例開始使用](../../integration-services/import-export-data/get-started-with-this-simple-example-of-the-import-and-export-wizard.md)

[!INCLUDE[get-help-options](../../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../../includes/paragraph-content/contribute-to-content.md)]
