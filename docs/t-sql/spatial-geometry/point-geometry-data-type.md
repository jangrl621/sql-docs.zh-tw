---
title: Point (geometry 資料類型) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Point
- Point_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Point (geometry Data Type)
ms.assetid: 7a2e593a-4d4c-4214-b0c5-02d1ac46bc66
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 3a0c9f31f0e724c56c22a46653eb56d51f2616fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101031"
---
# <a name="point-geometry-data-type"></a>Point (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

從 **Point** 執行個體的 X 和 Y 值及 SRID 來建構代表它的 **geometry** 執行個體。
  
## <a name="syntax"></a>語法  
  
```  
  
Point ( X, Y, SRID )  
```  
  
## <a name="arguments"></a>引數  
 *X*  
 這是 **float** 運算式，代表所要產生之 **Point** 的 X 座標。  
  
 *Y*  
 這是 **float** 運算式，代表所要產生之 **Point** 的 Y 座標。  
  
 *SRID*  
 這是 **int** 運算式，代表要傳回之 **geometry** 執行個體的空間參考識別碼 (SRID)。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geometry**  
  
 CLR 傳回型別：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>範例  
 下列範例會使用 `Point()` 建立 `geometry` 例項。  
  
```  
DECLARE @g geometry;   
SET @g = geometry::Point(1, 10, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另請參閱  
 [擴充的靜態幾何方法](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

