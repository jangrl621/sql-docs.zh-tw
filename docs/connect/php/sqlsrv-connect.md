---
title: sqlsrv_connect | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_connect
apitype: NA
helpviewer_keywords:
- connecting to the server
- API Reference, sqlsrv_connect
- connection pooling support
- sqlsrv_connect
ms.assetid: 37836b49-258e-45ce-9549-b8bd85d6952d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 11da2b4eca130eafe93a01315aaa1f6d9919632c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015045"
---
# <a name="sqlsrvconnect"></a>sqlsrv_connect
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

建立連接資源，並開啟連接。 依預設會使用 Windows 驗證來嘗試連接。  
  
## <a name="syntax"></a>語法  
  
```  
  
sqlsrv_connect( string $serverName [, array $connectionInfo])  
```  
  
#### <a name="parameters"></a>參數  
*$serverName*：一個字串，指定要建立連接之伺服器的名稱。 執行個體名稱 (例如 "myServer\instanceName") 或通訊埠編號 (例如 "myServer, 1521") 可以納入為此字串的一部分。 如需此參數之可用選項的完整描述，請參閱[搭配 SQL Native Client 使用連接字串關鍵字](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)的＜ODBC 驅動程式連接字串關鍵字＞一節中的＜Server 關鍵字＞。  
  
從 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]3.0 版開始，您也可以透過 `"(localdb)\instancename"`指定 LocalDB 執行個體。 如需詳細資訊，請參閱[支援 LocalDB](../../connect/php/php-driver-for-sql-server-support-for-localdb.md)。  
  
此外，從 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]3.0 版開始，您也可以指定虛擬網路名稱，以連接到 AlwaysOn 可用性群組。 如需有關[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]支援的[!INCLUDE[ssHADR](../../includes/sshadr_md.md)]詳細資訊, 請參閱[高可用性和嚴重損壞修復的支援](../../connect/php/php-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)。  
  
*$connectionInfo* [選擇性]：一個關聯**陣列**，其中包含連線屬性 (例如 **array**("Database" => "AdventureWorks"))。 如需支援陣列的索引鍵清單，請參閱 [Connection Options](../../connect/php/connection-options.md) 。  
  
## <a name="return-value"></a>傳回值  
PHP 連接資源。 如果連接無法成功建立並開啟，則傳回 **false** 。  
  
## <a name="remarks"></a>Remarks  
如果未在選用 *$connectionInfo* 參數中指定 *UID* 和 *PWD* 索引鍵的值，則會使用 Windows 驗證嘗試進行連接。 如需關於連接到伺服器的詳細資訊，請參閱 [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md) 和 [How to: Connect Using SQL Server Authentication](../../connect/php/how-to-connect-using-sql-server-authentication.md)。  
  
## <a name="example"></a>範例  
下列範例會使用 Windows 驗證建立及開啟連接。 此範例假設本機電腦上已安裝 SQL Server 和 [AdventureWorks](https://www.codeplex.com/SqlServerSamples) 資料庫。 從命令列執行範例時，所有輸出都會寫入至主控台。  
  
```  
<?php  
/*  
Connect to the local server using Windows Authentication and specify  
the AdventureWorks database as the database in use. To connect using  
SQL Server Authentication, set values for the "UID" and "PWD"  
 attributes in the $connectionInfo parameter. For example:  
$connectionInfo = array("UID" => $uid, "PWD" => $pwd, "Database"=>"AdventureWorks");  
*/  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
  
if( $conn )  
{  
     echo "Connection established.\n";  
}  
else  
{  
     echo "Connection could not be established.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
//-----------------------------------------------  
// Perform operations with connection.  
//-----------------------------------------------  
  
/* Close the connection. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>另請參閱  
[SQLSRV 驅動程式 API 參考](../../connect/php/sqlsrv-driver-api-reference.md)

[Connecting to the Server](../../connect/php/connecting-to-the-server.md)

[關於文件中的程式碼範例](../../connect/php/about-code-examples-in-the-documentation.md)  
  
