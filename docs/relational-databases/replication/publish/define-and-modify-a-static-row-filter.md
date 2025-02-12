---
title: 定義及修改靜態資料列篩選 | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- modifying filters, static row
- static row filters
- filters [SQL Server replication], static row
ms.assetid: a6ebb026-026f-4c39-b6a9-b9998c3babab
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: cbb1985f30dc87520273da62e62a34bc838d5b6a
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2019
ms.locfileid: "68764106"
---
# <a name="define-and-modify-a-static-row-filter"></a>定義及修改靜態資料列篩選
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中定義及修改靜態資料列篩選。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [建議](#Recommendations)  
  
-   **若要定義及修改靜態資料列篩選，請使用：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   如果您在初始化發行集的訂閱後，新增、修改或刪除靜態資料列篩選，則必須在進行變更後產生新的快照集並重新初始化所有訂閱。 如需屬性變更需求的詳細資訊，請參閱[變更發行集與發行項屬性](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)。  
  
-   如果為點對點異動複寫啟用發行集，則無法篩選資料表。  
  
###  <a name="Recommendations"></a> 建議  
  
-   由於這些篩選都是靜態的，所以所有訂閱者都將收到相同子集的資料。 如果您需要動態篩選屬於合併式發行集之資料表發行項內的資料，好讓每一個訂閱者都會收到不同的資料分割，請參閱＜ [針對合併發行項定義及修改參數化資料列篩選](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)＞。 合併式複寫也可讓您根據現有的資料列篩選來篩選相關的資料列。 如需詳細資訊，請參閱 [定義和修改合併發行項之間的聯結篩選](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 您可以在 [新增發行集精靈] 的 [篩選資料表的資料列]  頁面上，或是在 [發行集屬性 - \<發行集>]  對話方塊的 [篩選資料列]  頁面上，定義、修改及刪除靜態資料列篩選。 如需使用精靈及存取對話方塊的詳細資訊，請參閱[建立發行集](../../../relational-databases/replication/publish/create-a-publication.md)和[檢視及修改發行集屬性](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)。  
  
#### <a name="to-define-a-static-row-filter"></a>若要定義靜態資料列篩選  
  
1.  在 [新增發行集精靈] 的 [篩選資料表的資料列]  頁面上，或是在 [發行集屬性 - \<發行集>]  對話方塊的 [篩選資料列]  頁面上，您所採取的動作會視發行集類型而定：  
  
    -   對於快照式或交易式發行集，請按一下 **[加入]** 。  
  
    -   對於合併式發行集，請按一下 **[加入]** ，然後按一下 **[加入篩選]** 。  
  
2.  在 **[加入篩選]** 對話方塊中，從下拉式清單方塊中選取要篩選的資料表。  
  
3.  在 **[篩選陳述式]** 文字區域中建立篩選陳述式。 您可直接在文字區域輸入，也可以從 **[資料行]** 清單方塊中拖曳資料行。  
  
    > [!NOTE]  
    >  WHERE 子句應使用兩部份命名；不支援三部份及四部份命名。 如果發行集來自「Oracle 發行者」，則 WHERE 子句必須與 Oracle 語法相容。  
  
    -   **[篩選陳述式]** 文字區域包括預設文字，其格式為：  
  
        ```sql  
        SELECT <published_columns> FROM [schema].[tablename] WHERE  
        ```  
  
    -   預設的文字無法變更；使用標準 SQL 語法，在 WHERE 關鍵字後面輸入篩選子句。 完整的篩選子句應類似於：  
  
        ```sql  
        SELECT <published_columns> FROM [HumanResources].[Employee] WHERE [LoginID] = 'adventure-works\ranjit0'  
        ```  
  
    -   靜態資料列篩選可以包含使用者定義函數。 含有使用者定義函數的靜態資料列篩選之完整的篩選子句應類似於：  
  
        ```sql  
        SELECT <published_columns> FROM [Sales].[SalesOrderHeader] WHERE MyFunction([Freight]) > 100  
        ```  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  如果您在 [發行集屬性 - \<發行集>]  對話方塊中，請按一下 [確定]  以儲存並關閉對話方塊。  

[!INCLUDE[freshInclude](../../../includes/paragraph-content/fresh-note-steps-feedback.md)]

#### <a name="to-modify-a-static-row-filter"></a>若要修改靜態資料列篩選  
  
1.  在 [新增發行集精靈] 的 [篩選資料表的資料列]  頁面上，或是在 [發行集屬性 - \<發行集>]  對話方塊的 [篩選資料列]  頁面上，從 [已篩選的資料表]  窗格中選取一個篩選，然後按一下 [編輯]  。  
  
2.  在 **[編輯篩選]** 對話方塊中，修改篩選。  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-delete-a-static-row-filter"></a>若要刪除靜態資料列篩選  
  
1.  在 [新增發行集精靈] 的 [篩選資料表的資料列]  頁面上，或是在 [發行集屬性 - \<發行集>]  對話方塊的 [篩選資料列]  頁面上，從 [已篩選的資料表]  窗格中選取一個篩選，然後按一下 [刪除]  。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 當您建立資料表發行項時，可以定義 WHERE 子句從發行項篩選資料列。 您也可以在定義資料列篩選之後，加以變更。 您可以使用複寫預存程序來以程式設計的方式建立及修改靜態資料列篩選。  
  
#### <a name="to-define-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a>為快照式或交易式發行集定義靜態資料列篩選  
  
1.  定義要篩選的發行項。 如需詳細資訊，請參閱 [定義發行項](../../../relational-databases/replication/publish/define-an-article.md)。  
  
2.  在發行集資料庫的發行者端，執行 [sp_articlefilter &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)。 針對 **@article** 指定發行項的名稱、針對 **@publication** 指定發行集的名稱、針對 **@filter_name** 指定篩選的名稱，並針對 **@filter_clause** (不包括 `WHERE`) 指定篩選子句。  
  
3.  如果仍然必須定義資料行篩選，請參閱＜ [定義及修改資料行篩選](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)＞。 否則，執行 [sp_articleview &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)。 針對 **@publication** 指定發行集的名稱、針對 **@article** 指定篩選的發行項名稱，並針對 **@filter_clause** 中定義及修改靜態資料列篩選。 這樣會針對篩選的發行項建立同步處理物件。  
  
#### <a name="to-modify-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a>為快照式或交易式發行集修改靜態資料列篩選  
  
1.  在發行集資料庫的發行者端，執行 [sp_articlefilter &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)。 針對 **@article** 指定發行項的名稱、針對 **@publication** 指定發行集的名稱、針對 **@filter_name** 指定新的篩選名稱，並針對 **@filter_clause** (不包括 `WHERE`) 指定篩選子句。 由於這項變更將會讓現有訂閱中的資料失效，所以請針對 **@force_reinit_subscription** 指定 **@force_reinit_subscription** 中定義及修改靜態資料列篩選。  
  
2.  在發行集資料庫的發行者端，執行 [sp_articleview &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)。 針對 **@publication** 指定發行集的名稱、針對 **@article** 指定篩選的發行項名稱，並針對 **@filter_clause** 中定義及修改靜態資料列篩選。 這樣會重新建立可定義篩選之發行項的檢視。  
  
3.  針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。 如需詳細資訊，請參閱 [建立和套用初始快照集](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)。  
  
4.  重新初始化訂閱。 如需詳細資訊，請參閱 [重新初始化訂閱](../../../relational-databases/replication/reinitialize-subscriptions.md)。  
  
#### <a name="to-delete-a-static-row-filter-for-a-snapshot-or-transactional-publication"></a>為快照式或交易式發行集刪除靜態資料列篩選  
  
1.  在發行集資料庫的發行者端，執行 [sp_articlefilter &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)。 針對 **@article** 指定發行項的名稱、針對 **@publication** 指定發行集的名稱、針對 **@filter_name** 指定 NULL 的值，並針對 **@filter_clause** 中定義及修改靜態資料列篩選。 由於這項變更將會讓現有訂閱中的資料失效，所以請針對 **@force_reinit_subscription** 指定 **@force_reinit_subscription** 中定義及修改靜態資料列篩選。  
  
2.  針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。 如需詳細資訊，請參閱 [建立和套用初始快照集](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)。  
  
3.  重新初始化訂閱。 如需詳細資訊，請參閱 [重新初始化訂閱](../../../relational-databases/replication/reinitialize-subscriptions.md)。  
  
#### <a name="to-define-a-static-row-filter-for-a-merge-publication"></a>為合併式發行集定義靜態資料列篩選  
  
1.  在發行集資料庫的發行者端，執行 [sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)。 針對 **@subset_filterclause** (不包括 `WHERE`) 指定篩選子句。 如需詳細資訊，請參閱 [定義發行項](../../../relational-databases/replication/publish/define-an-article.md)。  
  
2.  如果仍然必須定義資料行篩選，請參閱＜ [定義及修改資料行篩選](../../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)＞。  
  
#### <a name="to-modify-a-static-row-filter-for-a-merge-publication"></a>為合併式發行集修改靜態資料列篩選  
  
1.  在發行集資料庫的發行者端，執行 [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)。 針對 **@publication** 指定發行集的名稱、針對 **@article** 指定篩選的發行項名稱、針對 **@property** 指定 **@property** 指定新的篩選名稱，並針對 **@value** (不包括 `WHERE`) 指定篩選子句。 由於這項變更將會讓現有訂閱中的資料失效，所以請針對 **@force_reinit_subscription** 中定義及修改靜態資料列篩選。  
  
2.  針對此發行集重新執行快照集代理程式作業，以產生更新的快照集。 如需詳細資訊，請參閱 [建立和套用初始快照集](../../../relational-databases/replication/create-and-apply-the-initial-snapshot.md)。  
  
3.  重新初始化訂閱。 如需詳細資訊，請參閱 [重新初始化訂閱](../../../relational-databases/replication/reinitialize-subscriptions.md)。  
  
###  <a name="TsqlExample"></a> 範例 (Transact-SQL)  
 在此異動複寫範例中，會以水平方式篩選此發行項，以移除所有不再生產的產品。  
  
 [!code-sql[HowTo#sp_AddTranArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_1.sql)]  
  
 在此合併式複寫範例中，會以水平方式篩選發行項，以便只傳回屬於指定之銷售人員的資料列。 也會使用聯結篩選。 如需詳細資訊，請參閱 [定義和修改合併發行項之間的聯結篩選](../../../relational-databases/replication/publish/define-and-modify-a-join-filter-between-merge-articles.md)。  
  
 [!code-sql[HowTo#sp_AddMergeArticle](../../../relational-databases/replication/codesnippet/tsql/define-and-modify-a-stat_2.sql)]  
  
## <a name="see-also"></a>另請參閱  
 [針對合併發行項定義及修改參數化資料列篩選](../../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)   
 [變更發行集與發行項屬性](../../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [篩選發行的資料](../../../relational-databases/replication/publish/filter-published-data.md)   
 [針對合併式複寫篩選發行的資料](../../../relational-databases/replication/merge/filter-published-data-for-merge-replication.md)  
  
  
