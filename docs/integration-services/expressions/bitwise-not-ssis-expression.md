---
title: ~ (位元 Not) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: janinezhang
ms.author: janinez
ms.openlocfilehash: a76e1690f93065a001094675f38c7ff388b2203a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68033997"
---
# <a name="-bitwise-not-ssis-expression"></a>~ (位元 Not) (SSIS 運算式)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  執行整數的位元否定運算。 此運算子可套用至帶正負號及不帶正負號的整數資料類型。  
  
## <a name="syntax"></a>語法  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a>引數  
 *integer_expression*  
 是任何整數資料類型的有效運算式。 *integer*_*expression* 是整數，會轉換成二進位數字以進行位元運算。 如需詳細資訊，請參閱 [Integration Services 資料類型](../../integration-services/data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>結果類型  
 傳回 *integer_expression*的資料類型。  
  
## <a name="remarks"></a>Remarks  
 None  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會在數字 170 (0000 0000 1010 1010) 上執行位元 ~ (NOT) 運算。 此數字為帶正負號的整數。  
  
```  
  
~ 170  
```  
  
 運算式評估結果為 -170 (1111111101010101)。  
  
 0000000010101010  
  
 ---------------------\-  
  
 1111111101010101  
  
## <a name="see-also"></a>另請參閱  
 [運算子優先順序與關聯性](../../integration-services/expressions/operator-precedence-and-associativity.md)   
 [運算子 &#40;SSIS 運算式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
