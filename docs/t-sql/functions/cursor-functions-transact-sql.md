---
title: 資料指標函式 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- functions [SQL Server], cursors
- cursor functions
ms.assetid: 7d9daa10-4c50-4212-9400-42120222b2b8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4f7e49dc39d95e4d5bcce285040f8a598e6935ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68026294"
---
# <a name="cursor-functions-transact-sql"></a>資料指標函數 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

這些純量函式會傳回資料指標的相關資訊：
  
|||  
|-|-|  
|[@@CURSOR_ROWS](../../t-sql/functions/cursor-rows-transact-sql.md)|[CURSOR_STATUS](../../t-sql/functions/cursor-status-transact-sql.md)|  
|[@@FETCH_STATUS](../../t-sql/functions/fetch-status-transact-sql.md)||  
  
所有資料指標函數都不具決定性。 換言之，這些函式並非每次執行時，都會傳回相同的結果，即便使用同一組輸入值也是如此。 如需函式確定性的詳細資訊，請參閱[決定性和非決定性函式](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)。
  
## <a name="see-also"></a>另請參閱
[內建函數 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)
  
  
