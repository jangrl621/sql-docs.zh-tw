---
title: 使用語意搜尋在文件中尋找主要片語 | Microsoft Docs
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- semantic search [SQL Server], key phrase queries
ms.assetid: 6ee3676e-ed5d-43ec-aeca-1eed78967111
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 97ec2ae45c173660c4c18b36d3c20210614c2df6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082896"
---
# <a name="find-key-phrases-in-documents-with-semantic-search"></a>使用語意搜尋找到文件中的主要片語
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  描述如何在設定為統計語意索引的文件或文字資料行中尋找主要片語。  

##  <a name="howtofind"></a> 使用 SEMANTICKEYPHRASETABLE 在文件中尋找主要片語  
 若要在特定文件中識別主要片語，或識別包含特定主要片語的文件，請查詢 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md) 函數。  
  
 SEMANTICKEYPHRASETABLE 會傳回包含零個、一個或多個資料列的資料表，表示與指定之資料表資料行相關聯的主要片語。 您可以在 SELECT 陳述式的 FROM 子句中參考這個資料列集函數，就像是一般資料表名稱一樣。  
  
> [!NOTE]  
>  在此版本中，只有單一字會針對語意搜尋編製索引，多字片語 (ngrams) 則不會編製索引。 此外，相同字的不同形式會個別編制索引，例如 "computer" 和 "computers" 會個別編制索引。  
  
 如需 SEMANTICKEYPHRASETABLE 函數所需之參數及其傳回之結果資料表的詳細資訊，請參閱 [semantickeyphrasetable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/semantickeyphrasetable-transact-sql.md)。  
  
> [!IMPORTANT]  
>  您設定為目標的資料行必須已啟用全文檢索和語意索引。  
  
###  <a name="HowToTopPhrases"></a> 範例 1：在特定文件中尋找前幾個主要片語  
 下列範例會從 AdventureWorks 範例資料庫之 Production.Document 資料表 Document 資料行 @DocumentId 變數所指定的文件中，擷取前 10 個主要片語。 @DocumentId 變數是指來自全文檢索索引之索引鍵資料行的值。  
  
```sql  
SELECT TOP(10) KEYP_TBL.keyphrase  
FROM SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document,  
    @DocumentId  
    ) AS KEYP_TBL  
ORDER BY KEYP_TBL.score DESC;  
GO  
```  
  
 **SEMANTICKEYPHRASETABLE** 函數會使用索引搜尋有效率地擷取這些結果，而不會使用資料表掃描。  
  
###  <a name="HowToTopDocuments"></a> 範例 2：尋找包含特定主要片語的前幾份文件  
 下列範例會從 AdventureWorks 範例資料庫 Production.Document 資料表的 Document 資料行中，擷取前 25 份包含主要片語的 "Bracket" 的文件。  
  
```sql  
SELECT TOP (25) DOC_TBL.DocumentID, DOC_TBL.DocumentSummary  
FROM Production.Document AS DOC_TBL  
    INNER JOIN SEMANTICKEYPHRASETABLE  
    (  
    Production.Document,  
    Document  
    ) AS KEYP_TBL  
ON DOC_TBL.DocumentID = KEYP_TBL.document_key  
WHERE KEYP_TBL.keyphrase = 'Bracket'  
ORDER BY KEYP_TBL.Score DESC;  
GO  
```  
  
  
