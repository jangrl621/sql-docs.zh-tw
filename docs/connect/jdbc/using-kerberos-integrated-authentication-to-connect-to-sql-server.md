---
title: 使用 Kerberos 整合驗證連線至 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 894da21c079b776524c07cab8b8f223bae769aee
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916237"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>使用 Kerberos 整合式驗證連接到 SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

從 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 開始，應用程式可使用 **authenticationScheme** 連線屬性來指定要使用類型 4 Kerberos 整合驗證連線至資料庫。 如需連接屬性的詳細資訊, 請參閱[設定連接屬性](../../connect/jdbc/setting-the-connection-properties.md)。 如需有關 Kerberos 的詳細資訊, 請參閱[Microsoft kerberos](https://go.microsoft.com/fwlink/?LinkID=100758)。

當您搭配 Java **Krb5LoginModule** 使用整合驗證時，可使用 [Class Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html) (類別 Krb5LoginModule) 設定模組。

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會為 IBM Java VM 設定下列屬性：

- **useDefaultCcache = true**
- **moduleBanner = false**

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 會為其他所有 Java VM 設定下列屬性：

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

在之前 , 應用程式可以使用 integratedSecurity 連接屬性, 並藉由參考 sqljdbc_auth, 指定整合式驗證 (使用 Kerberos 或 NTLM, 視可用的方式而定), 如下所示:  [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]如[建立連接 URL](../../connect/jdbc/building-the-connection-url.md)中所述。  

從 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 開始，應用程式可使用 **authenticationScheme** 連線屬性來指定透過純 Java Kerberos 實作使用 Kerberos 整合驗證連線到資料庫：

- 如果您想要使用**Krb5LoginModule**進行整合式驗證, 您仍然必須指定**integratedSecurity = true**連接屬性。 您也會指定**authenticationScheme = JAVAKerberos**連接屬性。

- 若要繼續搭配使用整合式驗證與**sqljdbc_auth**, 只需指定**integratedSecurity = true**連接屬性 (並選擇性地**authenticationScheme = NativeAuthentication**)。

- 如果您指定**authenticationScheme = JAVAKerberos** , 但未同時指定**integratedSecurity = true**, 驅動程式將會忽略**authenticationScheme**連接屬性, 而且預期會找到使用者名稱和密碼。連接字串中的認證。

當使用資料來源建立連線時，您可以透過程式設計的方式，使用 **setAuthenticationScheme** 設定驗證配置，並 (選擇性) 使用 **setServerSpn** 為 Kerberos 連線設定 SPN。

已加入新的記錄器來支援 Kerberos 驗證：com.microsoft.sqlserver.jdbc.internals.KerbAuthentication。 如需詳細資訊，請參閱[追蹤驅動程式作業](../../connect/jdbc/tracing-driver-operation.md)。

以下指導方針可幫助您設定 Kerberos：

1. 在 Windows 的登錄中, 將**AllowTgtSessionKey**設定為1。 如需詳細資訊，請參閱 [Windows Server 2003 中的 Kerberos 通訊協定登錄項目與 KDC 設定金鑰](https://support.microsoft.com/kb/837361)。
2. 確定 Kerberos 組態 (UNIX 環境中的 krb5.conf) 指向您的環境所適用的正確領域和 KDC。
3. 使用 kinit 或登入網域來初始化 TGT 快取。
4. 當使用 **authenticationScheme=JavaKerberos** 的應用程式在 Windows Vista 或 Windows 7 作業系統上執行時，您應使用標準使用者帳戶。 但您若是在系統管理員帳戶下執行應用程式，該應用程式就必須以系統管理員的權限執行。

> [!NOTE]  
> 只有 Microsoft JDBC Driver 4.2 以上 (含) 版本支援 serverSpn 連線屬性。

## <a name="service-principal-names"></a>服務主要名稱

服務主要名稱 (SPN) 是用戶端用以唯一識別服務執行個體的名稱。

您可以使用 **serverSpn** 連線屬性指定 SPN，或直接讓驅動程式為您建置 (預設)。 此屬性的格式為："MSSQLSvc/fqdn:port\@REALM"，其中 fqdn 是完整網域名稱，port 是連接埠號碼，REALM 是以大寫字母表示的 SQL Server Kerberos 領域。 此選項的 REALM 部分並非必要，只在您 Kerberos 設定的預設領域與伺服器的領域相同，而且預設不會加入時才需要。 如果您想要支援跨領域驗證案例，且其中 Kerberos 設定中的預設領域和伺服器的領域不同，則您必須以 serverSpn 屬性設定 SPN。

例如, 您的 SPN 可能會如下所示: 「MSSQLSvc/some-\@ZZZZ。企業.CONTOSO.COM」

如需有關服務主要名稱 (SPN) 的詳細資訊，請參閱：

- [如何在 SQL Server 中使用 Kerberos 驗證](https://support.microsoft.com/kb/319723)

- [搭配 SQL Server 使用 Kerberos](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> 在6.2 版的 JDBC driver 之前, 若要正確使用跨領域 Kerberos, 您必須明確地設定**serverSpn**。
>
> 從6.2 版本中, 驅動程式預設將能夠建立**serverSpn** , 即使使用跨領域 Kerberos 也一樣。 雖然一個也可以明確使用**serverSpn** 。

## <a name="creating-a-login-module-configuration-file"></a>建立登入模組組態檔

您可以選擇指定 Kerberos 組態檔。 如果未指定組態檔，以下設定便有效：

Sun JVM  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

IBM JVM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

如果您決定建立登入模組組態檔，此檔案必須遵循以下格式：

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

登入組態檔是由一個或多個項目組成，每一個項目都會指定哪一個基礎驗證技術應該用於特定應用程式。 例如，

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

所以每一個登入模組組態檔項目都是由一個名稱以及緊接在後的一個或多個 LoginModule-specific 項目所組成，其中每一個 LoginModule-specific 項目都是以分號結尾，而且整組 LoginModule-specific 項目會括在大括號中。 每一個組態檔項目都是以分號結尾。

除了允許驅動程式使用登入模組組態檔中指定的設定來取得 Kerberos 認證以外，驅動程式也可以使用現有的認證。 當您的應用程式必須使用多份使用者認證建立連線時即可使用。

驅動程式會嘗試使用現有的認證 (如果可用的話)，然後再嘗試使用指定的登入模組進行登入。 因此，當使用 `Subject.doAs` 方法在特定內容下執行程式碼時，將會使用傳遞給 `Subject.doAs` 呼叫的認證來建立連線。

如需詳細資訊，請參閱 [JAAS 登入組態檔](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html)和 [Class Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html) (類別 Krb5LoginModule)。

從 Microsoft JDBC Driver 6.2 開始, 可以選擇性地使用連接屬性`jaasConfigurationName`來傳遞登入模組設定檔的名稱, 如此一來, 每個連接都有自己的登入設定。

## <a name="creating-a-kerberos-configuration-file"></a>建立 Kerberos 組態檔

如需 Kerberos 組態檔的詳細資訊，請參閱 [Kerberos 需求](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html)。

這是網域設定檔範例，其中 YYYY 與 ZZZZ 是網域名稱。

```ini
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  

[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  

[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  

        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  

```

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>啟用網域組態檔和登入模組組態檔

您可以使用 Djava.security.krb5.conf 來啟用網域組態檔。 您可以使用 **-Djava**來啟用登入模組設定檔案。

例如, 您可以使用下列命令來啟動應用程式:

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>確認可以透過 Kerberos 存取 SQL Server

在 SQL Server Management Studio 中執行以下查詢：

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

確定您擁有執行這個查詢的必要權限。

## <a name="constrained-delegation"></a>限制委派

從 Microsoft JDBC Driver 6.2 開始, 驅動程式支援 Kerberos 限制委派。 委派的認證可以用 jgss. GSSCredential 物件的形式傳入, 驅動程式會使用這些認證來建立連接。

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>使用主體名稱和密碼的 Kerberos 連接

從 Microsoft JDBC Driver 6.2 開始, 驅動程式可以使用連接字串中傳遞的主體名稱和密碼來建立 Kerberos 連接。

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

如果使用者屬於 krb5 檔案中所設定的 default_realm, 則 username 屬性不需要領域。 當`userName`和`password`設定搭配`integratedSecurity=true;` 和`authenticationScheme=JavaKerberos;`屬性時, 會以使用者名稱的值作為 Kerberos 主體, 以及提供的密碼來建立連接。

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>從相同網域上的 Unix 電腦使用 Kerberos 驗證

本指南假設已有運作中的 Kerberos 設定。 在具有作用中 Kerberos 驗證的 Windows 電腦上執行下列程式碼, 以確認上述是否為 true。 如果成功, 程式碼會將「驗證配置: KERBEROS」列印到主控台。 在提供的外部不需要其他執行時間旗標、相依性或驅動程式設定。 相同的程式碼區塊可以在 Linux 上執行, 以確認連線成功。

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. 網域將用戶端電腦加入至與伺服器相同的網域。
2. 選擇性設定預設的 Kerberos 票證位置。 藉由設定`KRB5CCNAME`環境變數, 最方便的方式就是這麼做。
3. 藉由產生新的票證, 或將現有憑證放在預設的 Kerberos 票證位置, 以取得 Kerberos 票證。 若要產生票證, 只要使用終端機並透過「使用者」 `kinit USER@DOMAIN.AD`和「網域」初始化票證即可。AD "分別是主體和網域。 例如：`kinit SQL_SERVER_USER03@MICROSOFT.COM`。 票證會在預設票證位置或`KRB5CCNAME`路徑中產生 (如果已設定)。
4. 終端機會提示輸入密碼, 請輸入密碼。
5. 透過確認票證`klist`中的認證, 並確認認證是您要用於驗證的認證。
6. 執行上述範例程式碼, 並確認 Kerberos 驗證成功。

## <a name="see-also"></a>另請參閱

[使用 JDBC Driver 連接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
