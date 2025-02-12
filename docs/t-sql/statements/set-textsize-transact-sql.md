---
title: SET TEXTSIZE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 04/12/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TEXTSIZE_TSQL
- TEXTSIZE
- SET_TEXTSIZE_TSQL
- SET TEXTSIZE
dev_langs:
- TSQL
helpviewer_keywords:
- SET TEXTSIZE statement
- SELECT statement [SQL Server], text size returned
- size [SQL Server], text and image data
- TEXTSIZE option
- text size returned [SQL Server]
ms.assetid: 787154a6-39a6-4dd6-a6d0-67b4364f95d5
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b7e0a949e132f01ce82e46a6e8b4c1d761c1a52a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100047"
---
# <a name="set-textsize-transact-sql"></a>SET TEXTSIZE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定 SELECT 陳述式傳回的 **varchar(max)** 、**nvarchar(max)** 、**varbinary(max)** 、**text**、**ntext** 和 **image** 資料大小。  
  
> [!IMPORTANT]
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的未來版本將會移除 **ntext**、**text** 及 **image** 資料類型。 請避免在新的開發工作中使用這些資料類型，並規劃修改目前在使用這些資料類型的應用程式。 請改用 **nvarchar(max)** 、 **varchar(max)** 和 **varbinary(max)** 。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
SET TEXTSIZE { number }   
```  
  
## <a name="arguments"></a>引數  
 *number*  
 是 **varchar(max)** 、**nvarchar(max)** 、**varbinary(max)** 、**text**、**ntext** 或 **image** 資料長度 (以位元組為單位)。 *number* 是整數，最大值為 2147483647 (2GB)。  值為 -1 表示沒有限制。 值為 0 時，會將大小重設為預設值 4KB。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (10.0 及更高版本) 和 ODBC Driver for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會在連線時自動指定 `-1` (無限制)。  
  
 **比 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008 舊的驅動程式：** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者 (第 9 版) 在連接時，都會將 TEXTSIZE 設為 2147483647。  
  
## <a name="remarks"></a>Remarks  
 設定 SET TEXTSIZE 會影響 @@TEXTSIZE 函式。  
  
 SET TEXTSIZE 的設定是在執行階段進行設定，而不是在剖析階段進行設定。  
  
## <a name="permissions"></a>權限  
 需要 **public** 角色的成員資格。  
  
## <a name="see-also"></a>另請參閱  
 [@@TEXTSIZE &#40;Transact-SQL&#41;](../../t-sql/functions/textsize-transact-sql.md)   
 [資料類型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [SET 陳述式 &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)  
  
  
