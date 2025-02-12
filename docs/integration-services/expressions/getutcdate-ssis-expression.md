---
title: GETUTCDATE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], GETUTCDATE
- current date
- UTC time
- GETUTCDATE function
ms.assetid: 2282339c-c24f-493e-8e66-181ea8af5ad0
author: janinezhang
ms.author: janinez
ms.openlocfilehash: cfa01a936ad4c788c48033512d165934775cebdd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68080913"
---
# <a name="getutcdate-ssis-expression"></a>GETUTCDATE (SSIS 運算式)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  使用 DT_DBTIMESTAMP 格式，傳回 UTC 時間格式 (世界標準時間或格林威治標準時間) 的系統目前日期。 GETUTCDATE 函數不接受引數。  
  
## <a name="syntax"></a>語法  
  
```  
  
GETUTCDATE()  
```  
  
## <a name="arguments"></a>引數  
 None  
  
## <a name="result-types"></a>結果類型  
 DT_DBTIMESTAMP  
  
## <a name="expression-examples"></a>運算式範例  
 此範例會傳回 UTC 時間格式的目前日期之年份。  
  
```  
DATEPART("year",GETUTCDATE())  
```  
  
 此範例會傳回 **ModifiedDate** 資料行中的日期與目前 UTC 日期之間的天數。  
  
```  
DATEDIFF("dd",ModifiedDate,GETUTCDATE())  
```  
  
 此範例會將目前的 UTC 日期加上三個月。  
  
```  
DATEADD("Month",3,GETUTCDATE())  
```  
  
## <a name="see-also"></a>另請參閱  
 [GETDATE &#40;SSIS 運算式&#41;](../../integration-services/expressions/getdate-ssis-expression.md)   
 [函數 &#40;SSIS 運算式&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  
