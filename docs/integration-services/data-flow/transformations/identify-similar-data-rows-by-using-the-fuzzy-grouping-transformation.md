---
title: 使用模糊群組轉換來識別相似的資料列 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Fuzzy Grouping transformation
- match similar data [Integration Services]
- similar data rows [Integration Services]
- fuzzy matches
ms.assetid: ffcb41a6-e23d-49ea-8c32-ac980e3dc495
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 04dd344f9d62e3bc10d26c66a87c8e4bf8395787
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67944328"
---
# <a name="identify-similar-data-rows-by-using-the-fuzzy-grouping-transformation"></a>使用模糊群組轉換來識別相似的資料列

[!INCLUDE[ssis-appliesto](../../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  若要加入和設定「模糊群組」轉換，封裝必須至少包含一個「資料流程」工作和一個來源。  
  
### <a name="to-implement-fuzzy-grouping-transformation-in-a-data-flow"></a>在資料流程中實作「模糊群組」轉換  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 專案。  
  
2.  在 [方案總管] 中，按兩下封裝將其開啟。  
  
3.  按一下 [資料流程]  索引標籤，然後將「模糊群組」轉換從 [工具箱]  拖曳到設計介面。  
  
4.  將連接子從資料來源或前一轉換拖曳至「模糊群組」轉換，以便將「模糊群組」轉換連接到資料流程。  
  
5.  按兩下「模糊群組」轉換。  
  
6.  在 [模糊群組轉換編輯器]  對話方塊的 [連線管理員]  索引標籤上，選取連接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的 OLE DB 連線管理員。  
  
    > [!NOTE]  
    >  該轉換需要到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫的連接，以建立暫存資料表和索引。  
  
7.  按一下 [資料行]  索引標籤，並在 [可用的輸入資料行]  清單中，選取用於識別資料集中相似資料列之輸入資料行的核取方塊。  
  
8.  選取 [通過]  資料行中的核取方塊，以識別要傳遞至轉換輸出的輸入資料行。 重複資料列的識別處理中未包含傳遞資料行。  
  
    > [!NOTE]  
    >  用於群組的輸入資料行會自動選取為傳遞資料行，並且在用於群組時，無法取消對它們的選取。  
  
9. (選擇性) 在 [輸出別名]  資料行中更新輸出資料行的名稱。  
  
10. (選擇性) 在 [群組輸出別名]  資料行中更新已清除資料行的名稱。  
  
    > [!NOTE]  
    >  資料行的預設名稱是具有 "_clean" 後置詞之輸入資料行的名稱。  
  
11. (選擇性) 在 [比對類型]  資料行中更新要使用的比對類型。  
  
    > [!NOTE]  
    >  至少一個資料行必須使用模糊比對。  
  
12. 在 [最小相似度]  資料行中指定最小相似度層級資料行。 值長度必須介於 0 到 1 之間。 值愈接近 1，必須形成群組之輸入資料行中的值會愈相似。 最小相似度 1 表示完全相符。  
  
13. (選擇性) 在 [相似度輸出別名]  資料行中更新相似度資料行的名稱。  
  
14. 若要指定資料值中數字的處理方式，請更新 [數字]  資料行中的值。  
  
15. 若要指定如何將轉換與資料行中的字串資料進行比較，請修改 [比較旗標]  資料行中之比較選項的預設選擇。  
  
16. 按一下 [進階]  索引標籤，以修改資料行的名稱，轉換會將這些資料行加入唯一資料列識別碼 (_key_in)、重複資料列識別碼 (_key_out) 和相似度值 (_score) 的輸出。  
  
17. (選擇性) 藉由移動滑動軸來調整相似度臨界值。  
  
18. (選擇性) 清除 Token 分隔符號核取方塊，以忽略資料中的分隔符號。  
  
19. 按一下 [確定]  。  
  
20. 若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。  
  
## <a name="see-also"></a>另請參閱  
 [Fuzzy Grouping Transformation](../../../integration-services/data-flow/transformations/fuzzy-grouping-transformation.md)   
 [Integration Services 轉換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Integration Services 路徑](../../../integration-services/data-flow/integration-services-paths.md)   
 [資料流程工作](../../../integration-services/control-flow/data-flow-task.md)  
  
  
