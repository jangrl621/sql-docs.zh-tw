---
title: 日期和時間改善 |Microsoft Docs
description: SQL Server OLE DB 驅動程式的日期和時間改善
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 170404a4f90be10c848c8f15b7663c330f67495a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67989119"
---
# <a name="date-and-time-improvements"></a>日期和時間改善
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  本主題描述中[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]所加入日期和時間資料類型 SQL Server 支援的 OLE DB 驅動程式。  
  
 如需日期/時間改善的詳細資訊, 請參閱[OLE DB &#40; &#41;的日期和時間改善](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)。  
  
 如需示範這項功能之範例應用程式的詳細資訊，請參閱 [SQL Server 資料程式設計範例](https://msftdpprodsamples.codeplex.com/)。  
  
## <a name="usage"></a>使用方式  
 下列章節描述使用新日期和時間類型的各種方式。  
  
### <a name="use-date-as-a-distinct-data-type"></a>將 Date 當做不同的資料類型使用  
 從開始[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], 增強的日期/時間類型支援可讓您更有效率地使用 DBTYPE_DBDATE OLE DB 類型。  
  
### <a name="use-time-as-a-distinct-data-type"></a>將 Time 當做不同的資料類型使用  
 OLE DB 已經有只包含時間的資料類型 DBTYPE_DBTIME，其精確度為 1 秒。
  
 新 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 時間資料類型的小數秒精確度為 100 奈秒。 這需要 OLE DB 驅動程式中 SQL Server 的新類型: DBTYPE_DBTIME2。 為使用不含小數秒的時間而撰寫的現有應用程式可以使用 time(0) 資料行。 除非應用程式依賴中繼資料中所傳回的類型，否則現有的 OLE DB DBTYPE_TIME 及其對應結構應該正常運作。  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>使用包含擴充小數秒精確度的 Time 做為不同的資料類型  
 有些應用程式 (例如，處理序控制項和製造應用程式) 必須能夠處理精確度高達 100 奈秒的時間資料。 OLE DB 中此用途的新類型為 DBTYPE_DBTIME2。  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>使用包含擴充小數秒精確度的 Datetime  
 OLE DB 已經定義一個精確度高達 1 奈秒的類型。 不過，此類型已由現有的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 應用程式所使用，而且此類應用程式的精確度應該只有一秒的 1/300。 新的 **datetime2(3)** 類型與現有的日期時間類型不直接相容。 如果這有影響應用程式行為的風險，應用程式必須使用新的 DBCOLUMN 旗標來判斷實際的伺服器類型。    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>使用包含擴充小數秒精確度和時區的 Datetime  
 某些應用程式需要包含時區資訊的日期時間值。 這是新的 DBTYPE_DBTIMESTAMPOFFSET 類型所支援的。
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>搭配與現有轉換一致的用戶端轉換使用 Date/Time/Datetime/Datetimeoffset 資料  
 轉換會以一致的方式擴充，以包含 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 中所推出之所有日期和時間類型之間的轉換。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
