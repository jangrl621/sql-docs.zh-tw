---
title: IsNull (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- IsNull (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- IsNull (geometry Data Type)
ms.assetid: f95813a5-26c0-48aa-bfb8-56d2a0980788
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: d0b05e5d73c75e340535c3323a8219dedf5be76d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101232"
---
# <a name="isnull-geometry-data-type"></a>IsNull (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

**geometry** 執行個體的類型為 Null。 如果執行個體不是 Null，就會傳回 0。
  
## <a name="syntax"></a>語法  
  
```  
.IsNull  
```  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 類型：**bit**  
  
 CLR 類型：**SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 `IsNull` 可用來測試 **geometry** 執行個體是否為 Null。 如果執行個體不是 Null，`IsNull` 就會傳回 0，但是，如果執行個體為 Null，則會傳回 Null。  
  
 這個方法主要是由 SQL Server 基礎結構所使用；不建議您使用 `IsNull` 來測試執行個體是否為 Null。  
  

## <a name="see-also"></a>另請參閱  
 [幾何例項上擴充的方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

