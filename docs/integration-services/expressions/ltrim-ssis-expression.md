---
title: LTRIM (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- leading blanks
- LTRIM function
ms.assetid: d082f42a-d7e7-49f5-a503-ac44ba630832
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 0e86f7056f03f54c9b49787a5eb12a7fde5c607d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941252"
---
# <a name="ltrim-ssis-expression"></a>LTRIM (SSIS 運算式)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  傳回移除開頭空白之後的字元運算式。  
  
> [!NOTE]  
>  LTRIM 不會移除空白字元，例如 Tab 鍵或換行字元。 Unicode 會為許多不同類型的空格提供字碼指標，但此功能只會辨識 Unicode 字碼指標 0x0020。 當將雙位元組字集 (DBCS) 字串轉換為 Unicode 時，它們可以包括 0x0020 以外的空格字元，但此功能無法移除這些空格。 若要移除所有種類的空格，您可以在從「指令碼」元件執行的指令碼中使用 Microsoft Visual Basic .NET LTrim 方法。  
  
## <a name="syntax"></a>語法  
  
```  
  
LTRIM(character expression)  
```  
  
## <a name="arguments"></a>引數  
 *character_expression*  
 要移除空白的字元運算式。  
  
## <a name="result-types"></a>結果類型  
 DT_WSTR  
  
## <a name="remarks"></a>Remarks  
 LTRIM 只適用於 DT_WSTR 資料類型。 如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 LTRIM 執行其作業前隱含轉換成 DT_WSTR 資料類型。 其他資料類型必須明確地轉換為 DT_WSTR 資料類型。 如需詳細資訊，請參閱 [Integration Services 資料類型](../../integration-services/data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](../../integration-services/expressions/cast-ssis-expression.md)。  
  
 如果引數為 Null，則 LTRIM 會傳回 Null 結果。  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會移除字串常值的開頭空白。 傳回結果為「Hello」。  
  
```  
LTRIM("    Hello")  
```  
  
 此範例會移除 **FirstName** 資料行中的開頭空白。  
  
```  
LTRIM(FirstName)  
```  
  
 此範例會移除 **FirstName** 變數的開頭空白。  
  
```  
LTRIM(@FirstName)  
```  
  
## <a name="see-also"></a>另請參閱  
 [RTRIM &#40;SSIS 運算式&#41;](../../integration-services/expressions/rtrim-ssis-expression.md)   
 [TRIM &#40;SSIS 運算式&#41;](../../integration-services/expressions/trim-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
