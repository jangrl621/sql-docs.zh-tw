---
title: 參數查詢 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- parameter queries [SQL Server]
ms.assetid: 4897c41a-324a-47b8-a30b-cbc9e9e19a8b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 8c7f9d141edc20a981618b29776e8f9e7106bd19
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68263247"
---
# <a name="parameter-queries-visual-database-tools"></a>參數查詢 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
有時候您想要建立可以使用多次的查詢，但每次都使用不同的值。 例如，您可能經常執行查詢尋找由某位作者所寫的所有 `title_ids` 。 除了每次使用的作者 ID 或名稱不同外，每次要求時您可以執行相同的查詢。  
  
若要建立不同時候具有不同值的查詢，您必須在查詢中使用參數。 參數為一預留位置，執行查詢時提供參數值即可。 使用參數的 SQL 陳述式將如下所示，其中「?」是指作者的 ID 之參數：  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
## <a name="where-you-can-use-parameters"></a>使用參數的位置  
您可以使用參數作為常值的預留位置 (不論是文字或數值)。 通常參數可做為個別資料列或群組的搜尋條件中之預留位置 (即在 SQL 陳述式的 WHERE 或 HAVING 子句中)。  
  
您可以使用參數當做運算式中的預留位置。 例如，您可以利用每次執行查詢時都提供不同折扣值來計算折扣價格。 若要完成這項作業，您可以指定下列運算式：  
  
```  
(price * ?)  
```  
  
## <a name="specifying-unnamed-and-named-parameters"></a>指定未具名和具名參數  
您可以指定兩種類型的參數：未具名和具名。 未具名參數為問號 (?)，您可以放在查詢中需要提示或取代常值的位置。 例如，如果使用未具名參數搜尋 `titleauthor` 資料表中的作者 ID， [SQL 窗格](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) 中產生的結果陳述式將如下所示：  
  
```  
SELECT title_id  
FROM titleauthor  
WHERE (au_id = ?)  
```  
  
當您在 [查詢和檢視表設計工具](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md)執行查詢時， [查詢參數對話方塊](../../ssms/visual-db-tools/query-parameters-dialog-box-visual-database-tools.md) 會出現「?」作為參數的名稱。  
  
或者您也可以指定參數名稱。 如果查詢中有多個參數，具名參數則特別有用。 例如，如果您使用具名參數在 `authors` 資料表中搜尋作者的名字和姓氏，SQL 窗格中產生的結果陳述式將如下所示：  
  
```  
SELECT au_id  
FROM authors  
WHERE au_fname = %first name% AND  
      au_lname = %last name%  
```  
  
> [!TIP]  
> 在建立具名參數查詢之前，必須先定義前置和後置字元。  
  
當您在查詢和檢視表設計工具執行查詢時， [查詢參數對話方塊](../../ssms/visual-db-tools/query-parameters-dialog-box-visual-database-tools.md) 會出現具名參數清單。  
  
## <a name="see-also"></a>另請參閱  
[使用參數查詢 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/query-with-parameters-visual-database-tools.md)  
[支援的查詢類型 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[設計查詢和檢視使用說明主題 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
