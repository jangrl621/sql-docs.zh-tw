---
title: '*= (乘法指派) (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '*=_TSQL'
- '*='
dev_langs:
- TSQL
helpviewer_keywords:
- compound operators, *=
- assignment operators, *=
- augmented operators, *=
- '*= (multiply equals)'
- '*= (multiplication assignment)'
ms.assetid: 816ff5dc-9a40-4c07-8351-39c194dbc079
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c6ad2f4cd1c650831415eb4fea8182eaf5fb81fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122094"
---
# <a name="-multiplication-assignment-transact-sql"></a>*= (乘法指派) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

兩數相乘，再將值設定為運算結果。 例如，如果變數 @x 等於 35，則 @x *= 2 會用 @x 的原始值乘以 2，然後將 @x 設定為該新值 (70)。  
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
expression *= expression  
```  
  
## <a name="arguments"></a>引數  
_expression_  
這是數值類別目錄中任何有效資料類型[運算式](../../t-sql/language-elements/expressions-transact-sql.md)，但是 **bit** 類型除外。  
  
## <a name="result-types"></a>結果類型  
傳回優先順序較高之引數的資料類型。 如需詳細資訊，請參閱[資料類型優先順序 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)。  
  
## <a name="remarks"></a>Remarks  
如需詳細資訊，請參閱 [&#42; &#40;乘法&#41; &#40;Transact-SQL&#41;](../../t-sql/language-elements/multiply-transact-sql.md)。  
  
## <a name="see-also"></a>另請參閱  
[複合運算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/compound-operators-transact-sql.md)   
[運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
[運算子 &#40;Transact-SQL&#41;](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
