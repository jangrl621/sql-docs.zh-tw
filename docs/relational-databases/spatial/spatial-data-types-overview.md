---
title: 空間資料類型概觀 | Microsoft Docs
ms.date: 11/01/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- geometry data type [SQL Server], understanding
- geography data type [SQL Server], spatial data
- planar spatial data [SQL Server], geometry data type
- spatial data types [SQL Server]
ms.assetid: 1615db50-69de-4778-8be6-4e058c00ccd4
author: MladjoA
ms.author: mlandzic
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2abe169f1666a1ce44b96130a52ef8edbc5a788e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68048517"
---
# <a name="spatial-data-types-overview"></a>空間資料類型概觀
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  
空間資料有兩種類型： **geometry** 資料類型支援平面或 Euclidean (扁平表面) 資料。 **geometry** 資料類型同時符合開放式地理空間協會 (Open Geospatial Consortium, OGC) 的 SQL 簡單特徵規格 1.1.0 版，而且符合 SQL MM (ISO 標準)。
此外， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也支援 **geography** 資料類型，它會儲存橢圓體 (圓形表面) 資料，例如 GPS 經緯度座標。

##  <a name="objects"></a> 空間資料物件  
**geometry** 和 **geography** 資料類型支援十六種空間資料物件或執行個體類型。 但是，其中只有十一種執行個體類型「可具現化」  ；因此，您可以在資料庫中建立及處理這些執行個體 (或加以具現化)。 這些執行個體會從父資料類型衍生某些屬性，這些資料類型會將其區分為 **Points**、 **LineStrings, CircularStrings**、 **CompoundCurves**、 **Polygons**、 **CurvePolygons** ，或是 **geometry** 中的多個 **geography** 或 **GeometryCollection**執行個體。 **Geography** 類型具有一種額外的執行個體類型： **FullGlobe**。  

下圖說明 **geometry** 和 **geometry** 資料類型所根據的 **geography** 階層。 可具現化的 **geometry** 和 **geography** 類型是以藍色標示。  

![geom_hierarchy](../../relational-databases/spatial/media/geom-hierarchy.gif) 

如圖中所指示， **geometry** 和 **geography** 資料類型中，十種可具現化的類型為 **Point**、 **MultiPoint**、 **LineString**、 **CircularString**、 **MultiLineString**、 **CompoundCurve**、 **Polygon**、 **CurvePolygon**、 **MultiPolygon**和 **GeometryCollection**。 geography 資料類型還有一種額外的可具現化類型：**FullGlobe**。 **geometry** 和 **geography** 類型可以辨識特定的執行個體 (只要格式正確)，即使未明確定義執行個體亦然。 例如，如果您使用 STPointFromText() 方法明確定義 **Point** 執行個體，則只要方法輸入的格式正確， **geometry** 和 **geography** 會將此執行個體辨識為 **Point**。 如果您使用 `STGeomFromText()` 方法定義相同的執行個體， **geometry** 和 **geography** 資料類型都會將此執行個體辨識為 **Point**。  

geometry 和 geography 類型的子類型可區分為簡單與集合類型。  某些方法 (例如 `STNumCurves()` ) 只能使用簡單類型。  

簡單類型包括：  
-   [Point](../../relational-databases/spatial/point.md)  
-   [LineString](../../relational-databases/spatial/linestring.md)  
-   [CircularString](../../relational-databases/spatial/circularstring.md)  
-   [CompoundCurve](../../relational-databases/spatial/compoundcurve.md)  
-   [多邊形](../../relational-databases/spatial/polygon.md)  
-   [CurvePolygon](../../relational-databases/spatial/curvepolygon.md)  

集合類型包括：  
-   [MultiPoint](../../relational-databases/spatial/multipoint.md)  
-   [MultiLineString](../../relational-databases/spatial/multilinestring.md)  
-   [MultiPolygon](../../relational-databases/spatial/multipolygon.md)  
-   [GeometryCollection](../../relational-databases/spatial/geometrycollection.md)  

##  <a name="differences"></a> Geometry 和 geography 資料類型之間的差異  
這兩種類型的空間資料通常會有非常類似的行為，但是儲存及操作資料的方式會有一些重要的差異。  

### <a name="how-connecting-edges-are-defined"></a>連接邊緣的定義方式  
**LineString** 和 **Polygon** 類型的定義資料僅為頂點。  幾何類型中兩個頂點的連接邊緣為直線。  不過，地理位置類型中兩個頂點的連接邊緣為兩個頂點的最短大橢圓弧形。  大橢圓形是橢圓體與經過其中心之平面的交集，而大橢圓弧形為大橢圓形上的弧形線段。  

### <a name="how-circular-arc-segments-are-defined"></a>圓弧線段的定義方式  
geometry 類型的圓弧線段定義於 XY 笛卡兒座標平面上 (忽略 Z 值)。 geography 類型的圓弧線段則由參考球面的曲線線段定義。 參考球面上的任何緯線都可由兩個互補的圓弧定義，其中這兩個弧形的點都具有固定緯度角度。  

### <a name="measurements-in-spatial-data-types"></a>空間資料類型的度量  
在平面或扁平表面系統中，系統會使用與座標相同的度量單位來測量距離和區域。 使用 **geometry** 資料類型時，(2, 2) 與 (5, 6) 之間的距離就是 5 單位 (不論所用的單位為何)。  

在橢圓體 (或圓形地球) 系統中，會使用經緯度來提供座標。 不過，長度和面積通常會使用公尺和平方公尺來測量，但這樣的測量可能取決於 **geography** 執行個體的空間參考識別碼 (SRID)。 **geography** 資料類型最常見的度量單位是公尺。  

### <a name="orientation-of-spatial-data"></a>空間資料的方向  
在平面系統中，多邊形的環形方向不是重要的因素。 例如，((0, 0), (10, 0), (0, 20), (0, 0)) 描述的多邊形與 ((0, 0), (0, 20), (10, 0), (0, 0)) 描述的多邊形相同。 OGC 的 SQL 簡單特徵規格並未指示環形順序，而且 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 並未強制使用環形順序。  

在橢圓體系統中，多邊形如果沒有方向的話，將沒有任何意義或是會模稜兩可。 例如，包圍赤道的環形是要描述北半球還是南半球？ 如果我們使用 **geography** 資料類型來儲存空間執行個體，就必須指定此環形的方向，並正確描述此執行個體的位置。 在橢圓體系統中，多邊形的內部是由左側規則定義。  

在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，當相容性層級為 100 以下時， **geography** 資料類型就具有下列限制：  
-   每一個 **geography** 執行個體都必須納入單一半球。 大於半球的空間物件將無法儲存。  
-   當來自開放式地理空間協會 (Open Geospatial Consortium, OGC) 已知的文字 (Well-Known Text, WKT) 或已知的二進位 (Well-Known Binary, WKB) 表示法的任何 **geography** 執行個體產生大於半球的物件時，都會擲回 **ArgumentException**。  
-   需要兩個 **geography** 執行個體輸入的 **geography** 資料類型方法 (例如 STIntersection()、STUnion()、STDifference() 和 STSymDifference())，將會在這些方法的結果未納入單一半球時，傳回 null。 如果輸出超過單一半球，STBuffer() 也會傳回 null。  

在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中， **FullGlobe** 是一種特殊類型的多邊形，它涵蓋了整個地球。 **FullGlobe** 有面積，但沒有框線或頂點。  

### <a name="outer-and-inner-rings-not-important-in-geography-data-type"></a>外部和內部環形在 `geography` 類型中不重要  
OGC 的 SQL 簡單特徵規格討論了外部環形和內部環形，但是這樣的區別對於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **geography** 資料類型沒有很大的意義。多邊形的任何環形都可以當作外部環形。  

如需有關 OGC 規格的詳細資訊，請參閱下列主題：  
-   [OGC 規格，簡單特徵存取第一部 - 常見架構](https://go.microsoft.com/fwlink/?LinkId=93627)  
-   [OGC 規格，簡單特徵存取第二部 - SQL 選項](https://go.microsoft.com/fwlink/?LinkId=93628) \(英文\)  

##  <a name="circular"></a> 圓弧線段  
三種可具現化的類型可以採用圓弧線段：**CircularString**、**CompoundCurve** 和 **CurvePolygon**。  圓弧線段是由二維平面中的三個點定義，而且第三個點不得與第一個點相同。  

圖 A 和 B 顯示一般圓弧線段。 請注意，這三個點如何分別位於圓形的圓周上。  

圖 C 和 D 顯示如何將直線線段定義為圓弧線段。  請注意，仍然需要三個點才能定義圓弧線段，這與只由兩個點定義的一般直線線段不同。  
在圓弧線段類型上運作的方法會使用直線線段來模擬圓弧。用於模擬弧形的直線線段數目將取決於弧形的長度和曲度。您可以針對每種圓弧線段類型儲存 Z 值。不過，方法不會在計算中使用 Z 值。  

> [!NOTE]  
> 如果針對圓弧線段提供了 Z 值，則圓弧線段中所有點的這些值都必須相同，系統才會接受輸入。 例如：系統可接受 `CIRCULARSTRING(0 0 1, 2 2 1, 4 0 1)` ，但無法接受 `CIRCULARSTRING(0 0 1, 2 2 2, 4 0 1)` 。  

### <a name="linestring-and-circularstring-comparison"></a>LineString 和 CircularString 的比較  
此範例會示範如何使用 **LineString** 執行個體和 **CircularString** 執行個體來儲存完全相同的等腰三角形：  

```sql
DECLARE @g1 geometry;
DECLARE @g2 geometry;
SET @g1 = geometry::STGeomFromText('LINESTRING(1 1, 5 1, 3 5, 1 1)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(1 1, 3 1, 5 1, 4 3, 3 5, 2 3, 1 1)', 0);
IF @g1.STIsValid() = 1 AND @g2.STIsValid() = 1
  BEGIN
      SELECT @g1.ToString(), @g2.ToString()
      SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length]
  END
```  

請注意， **CircularString** 執行個體需要使用七個點來定義三角形，但是 **LineString** 執行個體只需要使用四個點來定義三角形。 這是因為 **CircularString** 執行個體會儲存圓弧線段而非直線線段。 因此，儲存在 **CircularString** 執行個體中的三角形側邊為 ABC、CDE 和 EFA，而儲存在 **LineString** 執行個體中的三角形側邊為 AC、CE 和 EA。  

請設想下列範例：  

```sql
SET @g1 = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 4 0)', 0);
SET @g2 = geometry::STGeomFromText('CIRCULARSTRING(0 0, 2 2, 4 0)', 0);
SELECT @g1.STLength() AS [LS Length], @g2.STLength() AS [CS Length];
```

[!INCLUDE[ssResult](../../includes/ssresult-md.md)]

```
LS LengthCS Length
5.65685...6.28318...
```

**CircularString** 執行個體會使用較少的點來儲存曲線界限，而精確度卻高於 **LineString** 執行個體。 **CircularString** 執行個體適合用於儲存圓形邊界，像是從特定點起算的二十英哩搜尋半徑。 **LineString** 執行個體適合用於儲存線性邊界，像是方形的城市街區。  

### <a name="linestring-and-compoundcurve-comparison"></a>LineString 和 CompoundCurve 的比較  
下列程式碼範例會示範如何使用 **LineString** 和 **CompoundCurve** 執行個體來儲存相同的圖形：

```sql
SET @g = geometry::Parse('LINESTRING(2 2, 4 2, 4 4, 2 4, 2 2)');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2), (4 2, 4 4), (4 4, 2 4), (2 4, 2 2))');
SET @g = geometry::Parse('COMPOUNDCURVE((2 2, 4 2, 4 4, 2 4, 2 2))');
```

在上述範例中， **LineString** 執行個體或 **CompoundCurve** 執行個體都可以儲存此圖形。  下一個範例會使用 **CompoundCurve** 來儲存圓形圖配量：  

```sql
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(2 2, 1 3, 0 2),(0 2, 1 0, 2 2))');  
```  

**CompoundCurve** 執行個體可以直接儲存圓弧線段 (2 2, 1 3, 0 2)，而 **LineString** 執行個體則必須將曲線轉換成許多較小的直線線段。  

### <a name="circularstring-and-compoundcurve-comparison"></a>CircularString 和 CompoundCurve 的比較  
下列程式碼範例會示範如何將圓形圖配量儲存在 **CircularString** 執行個體中：  

```sql
DECLARE @g geometry;
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)');
SELECT @g.ToString(), @g.STLength();
```

若要使用 **CircularString** 執行個體來儲存圓形圖配量，每個直線線段都必須使用三個點。  如果中繼點為未知，則必須計算此點，或者直線線段的端點必須加倍，如下列程式碼片段所示：  

```sql
SET @g = geometry::Parse('CIRCULARSTRING( 0 0, 3 6.3246, 3 6.3246, 0 7, -3 6.3246, 0 0, 0 0)');
```

**CompoundCurve** 執行個體同時允許 **LineString** 和 **CircularString** 元件，因此只需要知道圓形圖配量之直線線段的兩個點。  此程式碼範例會示範如何使用 **CompoundCurve** 來儲存相同的圖形：  
```sql
DECLARE @g geometry;
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING( 3 6.3246, 0 7, -3 6.3246), (-3 6.3246, 0 0, 3 6.3246))');
SELECT @g.ToString(), @g.STLength();
```

### <a name="polygon-and-curvepolygon-comparison"></a>Polygon 和 CurvePolygon 的比較  
**CurvePolygon** 執行個體可以在定義其外部與內部環形時，使用 **CircularString** 和 **CompoundCurve** 執行個體。  **Polygon** 執行個體不能使用圓弧線段類型：**CircularString** 和 **CompoundCurve**。  

## <a name="see-also"></a>另請參閱  
- [空間資料 (SQL Server)](https://msdn.microsoft.com/library/bb933790.aspx) 
- [geometry 資料類型方法參考](https://msdn.microsoft.com/library/bb933973.aspx) 
- [geography 資料類型方法參考](https://msdn.microsoft.com/library/028e6137-7128-4c74-90a7-f7bdd2d79f5e)   
- [STNumCurves &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stnumcurves-geometry-data-type.md)   
- [STNumCurves &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)   
- [STGeomFromText &#40;geometry 資料類型&#41;](../../t-sql/spatial-geometry/stgeomfromtext-geometry-data-type.md)   
- [STGeomFromText &#40;geography 資料類型&#41;](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
