---
title: TOKENCOUNT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1c0efed1-c2b3-4f20-a3a1-ad91283b7c0a
author: janinezhang
ms.author: janinez
ms.openlocfilehash: b7883ec1ed76f5b619c395e317a13a3fb57f091c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67967679"
---
# <a name="tokencount-ssis-expression"></a>TOKENCOUNT (SSIS 運算式)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  傳回包含以分隔符號分隔之 Token 的字串中的 Token 數。  
  
## <a name="syntax"></a>語法  
  
```  
TOKENCOUNT(character_expression, delimiter_string)  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 包含以分隔符號分隔之 Token 的字串。  
  
 *delimiter_string*  
 包含分隔符號字元的字串。 例如，"; ," 包含分號、空格和逗號三個分隔符號字元。  
  
## <a name="result-types"></a>結果類型  
 DT_I4  
  
## <a name="remarks"></a>Remarks  
 下列備註適用於 TOKEN 函數：  
  
-   分隔符號字串可以包含一個或多個分隔符號字元。  
  
-   前導分隔符號會予略過。  
  
-   TOKENCOUNT 只適用於 DT_WSTR 資料類型。 如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 TOKEN 執行其作業前隱含轉換成 DT_WSTR 資料類型。 其他資料類型必須明確地轉換為 DT_WSTR 資料類型。  
  
-   如果 character_expression 為 Null，TOKENCOUNT 會傳回 0 (零)。  
  
-   您可以使用變數和資料行做為此運算式的引數。  
  
## <a name="expression-examples"></a>運算式範例  
 在下列範例中，TOKENCOUNT 函式傳回 3 是因為字串包含三個權杖："01"、"12"、"2011"。  
  
```  
TOKENCOUNT("01/12/2011", "/")  
```  
  
 下列範例中因有四個權杖 ("a"、"little"、"white"、"dog")，所以 TOKENCOUNT 函式會傳回 4。  
  
```  
TOKENCOUNT("a little white dog"," ")  
```  
  
 在下列範例中，TOKENCOUNT 函數會傳回 1。 此函數會剖析輸入字串中的分隔符號，但因為字串中不具分隔符號，所以會直接加入整個字串做為第一個 Token。  
  
```  
TOKENCOUNT("a little white dog","|")  
```  
  
 在下列範例中，TOKENCOUNT 函數會傳回 4。 此範例中的分隔符號字串包含 5 個分隔符號。 輸入字串中包含 "a"、"little"、"white"、"dog" 4 個權杖。  
  
```  
TOKENCOUNT("a:little|white dog","| ,.:")  
```  
  
 在下列範例中，TOKENCOUNT 函數會傳回 4。 其將忽略所有的前導空格字元。  
  
```  
TOKENCOUNT("        a little white dog", " ")  
```  
  
## <a name="see-also"></a>另請參閱  
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
