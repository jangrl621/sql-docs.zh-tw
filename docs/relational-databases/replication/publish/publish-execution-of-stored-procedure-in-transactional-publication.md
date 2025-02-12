---
title: 在交易式發行集中發行預存程序的執行項 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: ad6e985006ffb1d6ad2e95d7d36b966e92e180b9
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68769807"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>在交易式發行集中發行預存程序的執行項
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  指定應在 [發行項屬性 - \<發行項>]  對話方塊中發行預存程序的執行 (而不僅是其定義)。 [新增發行集精靈] 與 [發行集屬性 - \<發行集>]  對話方塊中都有提供此對話方塊。 如需使用精靈和存取對話方塊的詳細資訊，請參閱[建立發行集](../../../relational-databases/replication/publish/create-a-publication.md)和[檢視和修改發行集屬性](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)。  
  
 初始化訂閱時，會將程序的定義 (CREATE PROCEDURE 陳述式) 複寫到訂閱者；在發行者端執行程序時，複寫會在訂閱者端執行對應的程序。  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>若要發行預存程序的執行  
  
1.  在 [新增發行集精靈] 的 [發行項]  頁面上，或是在 [發行集屬性 - \<發行集>]  對話方塊中，選取一個預存程序。  
  
2.  按一下 **[發行項屬性]** ，然後再按 **[設定反白顯示預存程序的屬性]** 。  
  
3.  在 [發行項屬性 - \<發行項>]  對話方塊中，為 [複寫]  選項指定下列其中一個值：  
  
    -   **[預存程序的執行]**  
  
    -   **[SP 的序列式交易執行]**  
  
         這是建議選項，因為它只會在程序於可序列化的交易內執行時複寫程序執行。 如果預存程序在序列化交易外部執行，則對已發行資料表中所做的資料變更會複寫為一連串的資料管理語言 (DML) 陳述式。  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  如果您在 [發行集屬性 - \<發行集>]  對話方塊中，請按一下 [確定]  以儲存並關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
