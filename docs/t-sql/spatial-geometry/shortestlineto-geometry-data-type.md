---
title: ShortestLineTo (geometry 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geometry)
ms.assetid: 39a2d0e4-4f93-4e94-a27e-6ad9537cfe74
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 4bb425d07d566f4bb06d18a8f74f493a649fa8b4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68101017"
---
# <a name="shortestlineto-geometry-data-type"></a>ShortestLineTo (geometry 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

傳回具有兩點的 **LineString** 執行個體，代表兩個 **geometry** 執行個體之間的最短距離。 所傳回 **LineString** 執行個體的長度是兩個 **geometry** 執行個體之間的距離。
  
## <a name="syntax"></a>語法  
  
```  
  
.ShortestLineTo ( geometry_other )  
```  
  
## <a name="arguments"></a>引數  
 *geometry_other*  
 呼叫 **geometry** 執行個體的第二個 **geometry** 執行個體正在嘗試判斷與其相距的最短距離。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geometry**  
  
 CLR 傳回型別：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 方法會傳回 **LineString** 執行個體，其端點在兩個非交集 **geometry** 比較執行個體的框線上。 所傳回 **LineString** 的長度等於兩個 **geometry** 執行個體之間的最短距離。 當兩個 **geometry** 執行個體彼此交集時，會傳回空白 **LineString** 執行個體。  
  
## <a name="examples"></a>範例  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. 在非交集的執行個體上呼叫 ShortestLineTo()  
 這個範例會求得 `CircularString` 執行個體和 `LineString` 執行個體之間的最短距離，並傳回連接兩點的 `LineString` 執行個體：  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(-4 7, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. 在交集的執行個體上呼叫 ShortestLineTo()  
 本範例會傳回空白 `LineString` 執行個體，因為 `LineString` 執行個體與 `CircularString` 執行個體交集：  
  
```
 DECLARE @g1 geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
 DECLARE @g2 geometry = 'LINESTRING(0 5, 7 10, 3 7)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
## <a name="see-also"></a>另請參閱  
 [ShortestLineTo &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/shortestlineto-geography-data-type.md)  
  
  

