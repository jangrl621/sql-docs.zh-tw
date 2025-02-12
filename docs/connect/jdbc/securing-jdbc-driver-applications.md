---
title: 保護 JDBC Driver 應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 90724ec6-a9cb-43ef-903e-793f89410bc0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c539e94b9fdcd3d1cd281e1a0f1043eec55739bc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67945749"
---
# <a name="securing-jdbc-driver-applications"></a>保護 JDBC Driver 應用程式

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

加強 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 應用程式的安全性不僅是避免常犯的編碼錯誤而已。 存取資料的應用程式有許多攻擊者可以用於擷取、操作或破壞敏感性資料的潛在錯誤點。 了解安全性的各個層面相當重要，包括在應用程式的設計階段處理威脅模型到其最終的部署，以及繼續持續的維護。  
  
本節中的主題描述一些常見的安全性考量，包括連接字串、驗證使用者輸入，以及一般應用程式安全性。  
  
## <a name="in-this-section"></a>本節內容  
  
| 主題                                                                            | Description                                                                                                                                                           |
| -------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [保護連接字串](../../connect/jdbc/securing-connection-strings.md) | 描述協助保護連接資料來源時所使用之資訊的技術。                                                                                    |
| [驗證使用者輸入](../../connect/jdbc/validating-user-input.md)             | 描述驗證使用者輸入的技術。                                                                                                                          |
| [應用程式安全性](../../connect/jdbc/application-security.md)               | 描述如何使用 Java 原則權限協助保護 JDBC 驅動程式應用程式。                                                                                |
| [使用 SSL 加密](../../connect/jdbc/using-ssl-encryption.md)               | 描述如何使用安全通訊端層 (SSL) 建立包含 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的安全通訊通道。 |
| [FIPS 模式](../../connect/jdbc/fips-mode.md)                                     | 描述如何在 FIPS 相容模式中使用 JDBC 驅動程式。                                                                                                              |
  
## <a name="see-also"></a>另請參閱  

 [JDBC Driver 概觀](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
