---
title: SQL Server 登入對話方塊 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 76326eeb-1144-4b9f-85db-50524c655d30
author: MightyPen
ms.author: v-jizho2
ms.openlocfilehash: fcfde122b978fa1e77baa690a1f3e09417dab1c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989418"
---
# <a name="sql-server-login-dialog-box-odbc"></a>SQL Server 登入對話方塊 (ODBC)

當您呼叫 ODBC 連接，但卻沒有為驅動程式指定足夠的資訊以連接至 SQL Server 時，ODBC 驅動程式就會顯示 [SQL Server 登入]  對話方塊。

## <a name="options"></a>選項。

### <a name="server"></a>[伺服器]

在您的網路上 SQL Server 實例的名稱。 從清單中選取伺服器或執行個體名稱，或在 [伺服器]  方塊中鍵入伺服器或執行個體名稱。 (選擇性) 您可以在用戶端電腦上使用 [SQL Server 設定管理員]  建立伺服器別名，並在 [伺服器]  方塊中鍵入該名稱。

如果您使用的電腦與 SQL Server 的相同，則可輸入 "(local)"。 接著，即使執行的是非網路版的 SQL Server，您也可連接到 SQL Server 的本機執行個體。

如需不同網路類型伺服器名稱的詳細資訊，請參閱《SQL Server 線上叢書》中的 SQL Server 安裝文件。

### <a name="authentication-mode"></a>驗證模式

從下列其中一項選取驗證模式:
- 具有登入識別碼和密碼的**SQL Server**
- 使用目前登入的使用者帳戶進行**Windows 整合**式驗證
- 具有登入識別碼和密碼的**Active Directory 密碼**
- 使用目前登入的使用者帳戶**Active Directory 整合**式驗證
- 使用登入識別碼進行的 **Active Directory 互動式**驗證

如需驗證模式的詳細資訊, 請參閱[資料來源嚮導畫面 2](../../../connect/odbc/windows/dsn-wizard-2.md) 。

### <a name="server-spn"></a>伺服器 SPN

如果您使用了信任連接，就可以指定伺服器的服務主要名稱 (SPN)。

### <a name="login-id"></a>登入識別碼

如果**驗證模式**設定為 [ **SQL Server** ] 或 [ **Active Directory 密碼**] 或 [ **Active Directory 互動式**], 則指定要用於連接的 SQL Server 或 Azure Active Directory 登入識別碼。 否則, 就會停用 [**登入識別碼**] 方塊。

### <a name="password"></a>[密碼]

如果 [**驗證模式]** 設定為 [ **SQL Server** ] 或 [ **Active Directory 密碼**], 則指定用於連接之 SQL Server 或 Azure Active Directory 登入識別碼的密碼。 否則, 就會停用 [**密碼**] 方塊。

### <a name="options"></a>選項。

顯示或隱藏 [選項]  群組。 如果 [伺服器]  具有值，即會啟用 [選項]  按鈕。

### <a name="change-password"></a>變更密碼

選取此方塊時，會顯示 [新密碼]  和 [確認新密碼]  方塊。

### <a name="new-password"></a>新密碼

指定新的密碼。

### <a name="confirm-new-password"></a>確認新密碼

再次指定新密碼，以進行確認。

### <a name="database"></a>[資料庫]

指定用於連接的預設資料庫。 此設定會覆寫伺服器上指定用於登入的預設資料庫。 如果未指定任何資料庫，則連接會使用伺服器上指定用於登入的預設資料庫。

### <a name="mirror-server"></a>鏡像伺服器

指定要鏡像處理之資料庫的容錯移轉夥伴名稱。

### <a name="mirror-spn"></a>鏡像 SPN

(選擇性) 您可以指定鏡像伺服器的 SPN。 鏡像伺服器的 SPN 會用於用戶端與伺服器之間的相互驗證。

### <a name="language"></a>語言

指定要用於 SQL Server 系統訊息的國家/地區語言。 執行 SQL Server 的電腦必須安裝此語言。 此設定會覆寫伺服器上指定用於登入的預設語言。 如果未指定任何語言，則連接會使用伺服器上指定用於登入的預設語言。

### <a name="application-name"></a>Application Name

(選擇性) 指定要針對 **sys.sysprocesses** 中的此連接，儲存在資料列上的 **program_name** 資料行中的應用程式名稱。

### <a name="workstation-id"></a>工作站 ID

(選擇性) 指定要針對 **sys.sysprocesses** 中的此連接，儲存在資料列上的 **hostname** 資料行中的工作站識別碼。

### <a name="use-strong-encryption-for-data"></a>使用高度加密資料

若選取此選項, 透過連接傳遞的資料將會加密。 預設會加密登入，即使清除該核取方塊亦然。

### <a name="trust-server-certificate"></a>信任伺服器憑證

只有在已啟用 [**對資料使用強式加密**] 時, 才適用此選項。 選取此選項時, 將不會驗證服務器的憑證是否具有伺服器的正確主機名稱, 並由受信任的憑證授權單位單位發行。

## <a name="see-also"></a>另請參閱

[Windows 上適用於 SQL Server 的 Microsoft ODBC 驅動程式](../../../connect/odbc/windows/microsoft-odbc-driver-for-sql-server-on-windows.md)
