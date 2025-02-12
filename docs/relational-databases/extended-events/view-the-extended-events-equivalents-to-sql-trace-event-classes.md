---
title: 檢視同等於 SQL 追蹤事件類別的擴充事件 | Microsoft 文件
ms.custom: ''
ms.date: 03/05/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace, extended events equivalents
- extended events [SQL Server], SQL Trace equivalents
- extended events [SQL Server], user configurable events
ms.assetid: 7f24104c-201d-4361-9759-f78a27936011
author: MightyPen
ms.author: genemi
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 968dadccedcd2b58a7ff69bd0d098cf5779a4338
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903403"
---
# <a name="view-the-extended-events-equivalents-to-sql-trace-event-classes"></a>檢視同等於 SQL 追蹤事件類別的擴充事件項目

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  如果您想要使用「擴充事件」來收集同等於 SQL 追蹤事件類別和資料行的事件資料，了解 SQL 追蹤事件如何對應到「擴充事件」事件和動作會非常實用。  
  
 您可以使用下列程序來檢視同等於每一個 SQL 追蹤事件及其關聯資料行的「擴充事件」事件和動作。  
  
## <a name="to-view-the-extended-events-equivalents-to-sql-trace-events-using-query-editor"></a>若要使用查詢編輯器檢視相當於 SQL 追蹤事件的擴充事件

- 從 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的查詢編輯器執行下列查詢：

   ```sql
   USE MASTER;
   GO
   SELECT DISTINCT
      tb.trace_event_id,
      te.name            AS 'Event Class',
      em.package_name    AS 'Package',
      em.xe_event_name   AS 'XEvent Name',
      tb.trace_column_id,
      tc.name            AS 'SQL Trace Column',
      am.xe_action_name  AS 'Extended Events action'
   FROM
                sys.trace_events         te
      LEFT JOIN sys.trace_xe_event_map   em ON te.trace_event_id  = em.trace_event_id
      LEFT JOIN sys.trace_event_bindings tb ON em.trace_event_id  = tb.trace_event_id
      LEFT JOIN sys.trace_columns        tc ON tb.trace_column_id = tc.trace_column_id
      LEFT JOIN sys.trace_xe_action_map  am ON tc.trace_column_id = am.trace_column_id
   ORDER BY te.name, tc.name
   ```

當您檢視結果時，請注意下列事項：  

- 如果事件類別資料行以外的所有其他資料行都傳回 NULL，表示並未從 SQL 追蹤移轉事件類別。  
  
-   如果只有擴充事件動作資料行中的值為 NULL，表示下列其中一個條件成立：  
  
    -   SQL 追蹤資料行對應到與「擴充事件」事件相關聯的其中一個資料欄位。  
  
        > [!NOTE]  
        > 每一個「擴充事件」事件都有一組預設資料欄位，這些欄位會自動包含在結果集內。  
  
    -   此動作資料行並沒有有意義的「擴充事件」同等項目。 其中一個範例就是 SQL 追蹤中的 EventClass 資料行。 「擴充事件」中不需要此資料行，因為事件名稱有相同的用途。  
  
-   如果是使用者可設定的 SQL 追蹤事件類別 (透過 UserConfigurable:9 的 UserConfigurable:1)，擴充事件會使用單一事件來取代這些項目。 此事件命名為 user_event。 這個事件是使用 sp_trace_generateevent 所引發，這與 SQL 追蹤所使用的預存程序相同。 不論傳遞給預存程序的事件識別碼為何，都會傳回 user_event 事件。 但是，event_id 欄位會當作事件資料的一部分傳回。 這可讓您建立以事件識別碼為基礎的述詞。 例如，如果您在程式碼中使用 UserConfigurable:0 (事件識別碼 = 82)，您可以將 user_event 事件加入至工作階段中，並指定 'event_id = 82' 的述詞。 因此，您不必變更程式碼，因為 sp_trace_generateevent 預存程序會產生擴充事件 user_event 事件及同等的 SQL 追蹤事件類別。  
  
## <a name="see-also"></a>另請參閱  
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)  
  
  
