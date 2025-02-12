---
title: 運算子優先順序與關聯性 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- associativity [Integration Services]
- precedence [Integration Services]
ms.assetid: 5094164f-dabc-45b5-b611-384feb2b3fe3
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 2b5ad688f3ca9192f80b45d7141b7d9ec9576a58
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68085715"
---
# <a name="operator-precedence-and-associativity"></a>運算子優先順序與關聯性

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  在運算式評估工具支援的一組運算子中，每個運算子在優先順序階層中都有指定的優先順序，且包含評估的方向。 運算子的評估方向即為運算子關聯性。 具有較高優先順序的運算子會在低優先順序的運算子之前評估。 如果複雜的運算式有多個運算子時，運算子優先順序即決定運算子執行的順序。 執行的順序對結果值會有很大的影響。 某些運算子的優先順序相同。 如果運算式含有多個優先順序相同的運算子，則會按照左到右或右到左的方向評估運算子。  
  
 下表按高到低的順序列出運算子的優先順序。 同層級的運算子擁有相同的優先順序。  
  
|運算子符號|運算類型|關聯性|  
|---------------------|-----------------------|-------------------|  
|( )|運算式|由左至右|  
|-、!、~|一元 (Unary)|由右至左|  
|轉換|一元 (Unary)|由右至左|  
|*, / ,%|乘法|由左至右|  
|+、 -|加法|由左至右|  
|\<, >, \<=, >=|關聯式|由左至右|  
|==, !=|等式|由左至右|  
|&|位元 AND|由左至右|  
|^|位元排除 OR|由左至右|  
|&#124;|位元包含 OR|由左至右|  
|&&|邏輯 AND|由左至右|  
|&#124;&#124;|邏輯 OR|由左至右|  
|? 所解碼的字元：|條件運算式|由右至左|  
  
## <a name="see-also"></a>另請參閱  
 [運算子 &#40;SSIS 運算式&#41;](../../integration-services/expressions/operators-ssis-expression.md)  
  
  
