---
title: 空間結果視窗 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c2d5a477-6496-4d01-adee-7322ebdfadf3
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 20cc4b1c97e7153fc93d810fba18742a0bb2e24b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68267724"
---
# <a name="spatial-results-window"></a>空間結果視窗
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [空間結果]  視窗會提供檢視空間資料的視覺化對應工具。 若要檢視空間結果，您的查詢結果必須包含一個具有幾何或地理位置資料的空間資料行。  
  
> [!NOTE]  
>  只有當您的結果傳回至 [結果]  視窗中的方格時，才能使用 [空間結果]  視窗。 如果您指定要將結果傳回成文字，就無法使用這個視窗。  
  
## <a name="options"></a>選項。  
 **選取空間資料行**  
 在查詢結果的空間資料行中，指定您想要檢視的空間資料行。 一次只能選取一個資料行。  
  
 **選取標籤資料行**  
 在查詢結果所傳回的資料行中，指定要標示空間資料的非空間資料行。 一次只能選取一個資料行。  
  
 當查詢只有傳回 Point 執行個體時，就無法使用這個選項。  
  
 **選取投射**  
 以四種投影方式中的其中一種顯示地理資料：等量矩形 (Equirectangular)、麥卡托 (Mercator)、羅賓森 (Robinson) 或彭納 (Bonne)。  
  
 幾何資料無法使用此選項。  
  
 **顯示比例**  
 在指數刻度上調整對應顯示。  
  
 **顯示格線**  
 開啟或關閉座標格線。  
  
 若為多邊形形狀，只有當此形狀夠大，足以容納標籤文字時，才會顯示標籤。 若要顯示小型形狀的標籤，請調整顯示比例。  
  
> [!NOTE]  
>  您無法標示 Point 執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [檢視物件總管中的空間資料](../../relational-databases/scripting/view-spatial-data-in-object-explorer.md)   
 [空間資料 &#40;SQL Server&#41;](../../relational-databases/spatial/spatial-data-sql-server.md)   
 [Database Engine 查詢編輯器 &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [查詢與文字編輯器 &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
