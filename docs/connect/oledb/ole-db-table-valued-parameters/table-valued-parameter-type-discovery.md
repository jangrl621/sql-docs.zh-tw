---
title: 資料表值參數類型探索 |Microsoft Docs
description: 使用 SQL Server OLE DB 驅動程式的資料表值參數類型探索
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, type discovery
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 4e824e39a44985dc2f46a1a27c7b5b4e8d05a6dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68015288"
---
# <a name="table-valued-parameter-type-discovery"></a>資料表值參數類型探索
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  如果命令文字已經提供給 OLE DB 提供者，取用者 (也就是使用 OLE DB Driver for SQL Server 的用戶端應用程式) 便可以探索每一個命令參數的類型。 知道了資料表值參數的類型之後，取用者就可以針對資料表值參數的每一個個別資料行來探索中繼資料資訊。  
  
 大部分參數類型的 ICommandWithParameters:: GetParameterInfo 都支援程式參數的類型資訊。 從 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 開始，隨著使用者定義型別和 **xml** 資料類型的導入，GetParameterInfo 方法不足以支撐這個用途，因為透過 ICommandWithParameters 提供使用者定義型別資訊 (名稱、結構描述和目錄) 是不可行的。 已定義新介面 ISSCommandWithParameters 來提供擴充類型資訊。  
  
 對於資料表值參數, 您也可以使用 ISSCommandWithParameters 介面來探索詳細資訊。 在準備命令物件之後, 用戶端會呼叫 ISSCommandWithParameters:: GetParameterInfo。 如果是資料表值參數，DBPARAMINFO 結構的 *wType* 成員會由提供者設定為 DBTYPE_TABLE。 DBPARAMINFO 結構的 *ulParamSize* 欄位具有 ~0 的值。  
  
 然後取用者會使用 ISSCommandWithParameters::GetParameterProperties 來要求其他屬性 (資料表值參數類型目錄名稱、資料表值參數類型結構描述名稱、資料表值參數類型名稱、資料行排序和預設資料行)。  
  
 如果在知道了類型名稱之後要擷取個別資料行資訊，取用者必須呼叫 IOpenRowset::OpenRowsetor 或取得 DBSCHEMA_TABLE_TYPE_COLUMNS 資料列集，其方式是將資料表值參數類型名稱指定為資料表名稱。  
  
## <a name="see-also"></a>另請參閱  
 [資料表值參數 &#40;OLE DB&#41;](../../oledb/ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)   
 [使用資料表值參數 &#40;OLE DB&#41;](../../oledb/ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
