---
title: NULL (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- NULL function
- null values [Integration Services]
ms.assetid: df144237-3fbb-41ac-8624-efd92b6522b9
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 86add979aa790e438454c319dee68b8df95a6669
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968092"
---
# <a name="null-ssis-expression"></a>NULL (SSIS 運算式)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  傳回所要求資料類型的 Null 值。  
  
## <a name="syntax"></a>語法  
  
```  
  
NULL(typespec)  
```  
  
## <a name="arguments"></a>引數  
 *typespec*  
 是有效的資料類型。 如需詳細資訊，請參閱 [Integration Services 資料類型](../../integration-services/data-flow/integration-services-data-types.md)。  
  
## <a name="result-types"></a>結果類型  
 任何含有 Null 值的有效資料類型。  
  
## <a name="remarks"></a>Remarks  
 如果引數為 Null，則 NULL 會傳回 Null 結果。  
  
 某些資料類型需要使用參數才能要求 Null 值。 下表列出這些資料類型及其參數。  
  
|資料類型|參數|範例|  
|---------------|---------------|-------------|  
|DT_STR|*charcount*<br /><br /> *codepage*|(DT_STR,30,1252) 會使用 1252 字碼頁將 30 個字元轉換成 DT_STR 資料類型。|  
|DT_WSTR|*charcount*|(DT_WSTR,20) 會將 20 個字元轉換成 DT_WSTR 資料類型。|  
|DT_BYTES|*bytecount*|(DT_BYTES,50) 將 50 個位元組轉換為 DT_BYTES 資料類型。|  
|DT_DECIMAL|*scale*|(DT_DECIMAL,2) 將數值轉換為 DT_DECIMAL 資料類型，使用 2 位小數位數。|  
|DT_NUMERIC|*有效位數*<br /><br /> *scale*|(DT_NUMERIC,10,3) 將數值轉換為 DT_NUMERIC 資料類型，使用 10 位有效位數與 3 位小數位數。|  
|DT_TEXT|*codepage*|(DT_TEXT,1252) 將值轉換為 DT_TEXT 資料類型，使用 1252 字碼頁。|  
  
## <a name="expression-examples"></a>運算式範例  
 這些範例會傳回下列資料類型的 Null 值：DT_STR、DT_DATE 和 DT_BOOL。  
  
```  
NULL(DT_STR,10,1252)  
NULL(DT_DATE)  
NULL(DT_BOOL)  
```  
  
## <a name="see-also"></a>另請參閱  
 [ISNULL &#40;SSIS 運算式&#41;](../../integration-services/expressions/isnull-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
