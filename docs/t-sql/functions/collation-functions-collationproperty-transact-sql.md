---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
author: MikeRayMSFT
ms.author: mikeray
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 842c70125c5d311f36df50afa72feae47c47bd55
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064708"
---
# <a name="collation-functions---collationproperty-transact-sql"></a>定序函式 - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

此函式會傳回所要求的指定定序屬性。
  
![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>語法  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>引數  
*collation_name*  
定序的名稱。 *collation_name* 引數具有 **nvarchar(128)** 資料類型，而且沒有預設值。
  
*property*  
定序屬性。 *property* 引數具有 **varchar(128)** 資料類型，而且可以有下列任何一個值：
  
|屬性名稱|Description|  
|---|---|
|**CodePage**|定序的非 Unicode 字碼頁。 這是用於 **varchar** 資料的字元集。 請參閱 [Appendix G DBCS/Unicode Mapping Tables](https://msdn.microsoft.com/library/cc194886.aspx) (附錄 G DBCS/Unicode 對應資料表) 和 [Appendix H Code Pages](https://msdn.microsoft.com/library/cc195051.aspx) (附錄 H 字碼頁) 來翻譯這些值，以及查看其字元對應。<br /><br />基底資料類型：**int**|  
|**LCID**|定序的 Windows 地區設定識別碼。 這是用於排序與比較規則的文化特性。 請參閱 [LCID Structure](https://msdn.microsoft.com/library/cc233968.aspx) (LCID 結構)，以翻譯這些值 (您必須先轉換成 **varbinary**)。<br /><br />基底資料類型：**int**|  
|**ComparisonStyle**|Windows 的定序比較樣式。 若是二進位定序，會傳回 0 - (\_BIN) 及 (\_BIN2) 兩者皆然 - 以及區分所有屬性時 - (\_CS\_AS\_KS\_WS) 和 (\_CS\_AS\_KS\_WS\_SC) 和 (\_CS\_AS\_KS\_WS\_VSS)。 位元遮罩值：<br /><br /> 忽略大小寫：1<br /><br /> 忽略腔調字：2<br /><br /> 忽略假名：65536<br /><br /> 忽略寬度：131072<br /><br /> 注意：variation-selector-sensitive (\_VSS) 選項仍不會在此值中表示，即使它會影響比較行為也是一樣。<br /><br />基底資料類型：**int**|  
|**版本(Version)**|定序版本。 傳回值介於 0 到 3 之間的值。<br /><br /> 名稱含有 "140" 的定序) 都會傳回 3。<br /><br /> 名稱含有 "100" 的定序) 都會傳回 2。<br /><br /> 名稱含有 "90" 的定序) 都會傳回 1。<br /><br /> 所有其他定序都會傳回 0。<br /><br />基底資料型別：**tinyint**|  
  
## <a name="return-types"></a>傳回類型
**sql_variant**
  
## <a name="examples"></a>範例  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>另請參閱
[sys.fn_helpcollations &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

