---
title: ShortestLineTo (geography 資料型別) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ShortestLineTo_TSQL
- ShortestLineTo
dev_langs:
- TSQL
helpviewer_keywords:
- ShortestLineTo method (geography)
ms.assetid: 9d7c9885-5d1b-49ae-af31-5ef9fb8acaba
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 7844f1d38f5d2e6f36f971eb83d8961596483142
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042602"
---
# <a name="shortestlineto-geography-data-type"></a>ShortestLineTo (geography 資料類型)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  傳回具有兩點的 **LineString** 執行個體，代表兩個 **geography** 執行個體之間的最短距離。 所傳回 **LineString** 執行個體的長度是兩個 **geography** 執行個體之間的距離。  
  
## <a name="syntax"></a>語法  
  
```  
  
.ShortestLineTo ( geography_other )  
```  
  
## <a name="arguments"></a>引數  
 *geography_other*  
 指定第二個 **geography** 執行個體，呼叫 **geography** 執行個體正在嘗試判斷與其相距的最短距離。  
  
## <a name="return-types"></a>傳回類型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 傳回類型：**geography**  
  
 CLR 傳回型別：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 方法會傳回 **LineString** 執行個體，其端點在兩個非交集 **geography** 比較執行個體的框線上。 所傳回 **LineString** 的長度等於兩個 **geography** 執行個體之間的最短距離。 當兩個 **geography** 執行個體彼此交集時，會傳回空白 **LineString** 執行個體。  
  
## <a name="examples"></a>範例  
  
### <a name="a-calling-shortestlineto-on-non-intersecting-instances"></a>A. 在非交集的執行個體上呼叫 ShortestLineTo()  
 這個範例會求得 `CircularString` 執行個體和 `LineString` 執行個體之間的最短距離，並傳回連接兩點的 `LineString` 執行個體：  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.200928 47.454094)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
 ```  
  
### <a name="b-calling-shortestlineto-on-intersecting-instances"></a>B. 在交集的執行個體上呼叫 ShortestLineTo()  
 本範例會傳回空白 `LineString` 執行個體，因為 `LineString` 執行個體與 `CircularString` 執行個體交集：  
  
 ```
 DECLARE @g1 geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 DECLARE @g2 geography = 'LINESTRING(-119.119263 46.183634, -119.273071 47.107523, -120.640869 47.569114, -122.348 47.649, -122.681 47.655)';  
 SELECT @g1.ShortestLineTo(@g2).ToString();
``` 
  
## <a name="see-also"></a>另請參閱  
 [地理例項上擴充的方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)  
  
  
