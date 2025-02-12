---
title: 建立維護計畫 (維護計畫設計介面) | Microsoft 文件
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Maintenance Plan Design Surface
ms.assetid: 2ef803ee-a9f8-454a-ad63-fedcbe6838d1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7b39b4391780a8133dae199e39638a6db77d73aa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68083898"
---
# <a name="create-a-maintenance-plan-maintenance-plan-design-surface"></a>建立維護計畫 (維護計畫設計介面)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的維護計畫設計介面，建立單一伺服器或多伺服器維護計畫。 雖然 **[維護計畫精靈]** 最適用於建立基本的維護計畫，但使用設計介面建立計畫時可讓您利用加強的工作流程。  
  
 **本主題內容**  
  
-   **開始之前：**  
  
     [限制事項](#Restrictions)  
  
     [安全性](#Security)  
  
-   [使用維護計畫設計介面建立維護計畫](#SSMSProcedure)  
  
##  <a name="BeforeYouBegin"></a> 開始之前  
  
###  <a name="Restrictions"></a> 限制事項  
  
-   若要建立多伺服器維護計畫，必須設定多伺服器環境，其中包含一個主要伺服器以及一或多個目標伺服器。 多伺服器維護計畫必須在主要伺服器上建立和維護。 您可以在目標伺服器上檢視這些計畫，但不能加以維護。  
  
-   **db_ssisadmin** 角色和 **dc_admin** 角色的成員可以將其權限提高為 **sysadmin**。 能夠提高權限是因為這些角色可以修改 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝；這些封裝可藉由使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 的 **sysadmin** 安全性內容由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行。 若要在執行維護計畫、資料收集組和其他 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝時預防此權限提高，請將執行封裝的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業設為使用有限權限的 Proxy 帳戶，或是只將 **sysadmin** 成員加入 **db_ssisadmin** 和 **dc_admin** 角色。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> 權限  
 若要建立或管理維護計畫，您必須是 **系統管理員 (sysadmin)** 固定伺服器角色的成員。 只有在使用者是 **sysadmin** 固定伺服器角色的成員時，[物件總管] 才會顯示 **[維護計畫]** 節點。  
  
##  <a name="SSMSProcedure"></a> 使用維護計畫設計介面  
  
#### <a name="to-create-a-maintenance-plan"></a>若要建立維護計畫  
  
1.  在 [物件總管] 中，按一下加號以展開您要建立維護計畫的伺服器。  
  
2.  按一下加號展開 **[管理]** 資料夾。  
  
3.  以滑鼠右鍵按一下 [維護計畫]  資料夾，然後選取 [新增維護計畫]  。  
  
4.  在 **[新增維護計畫]** 對話方塊中的 **[名稱]** 方塊，輸入計畫的名稱，然後按一下 **[確定]** 。 這會開啟工具箱和 *maintenance_plan_name* [設計]  介面，並在主要方格中建立預設的 [子計畫_1]  子計畫。  
  
     設計空間的標頭中有下列選項。  
  
     **加入子計畫**  
     新增可設定的子計畫。  
  
     **子計畫屬性**  
     在主要方格中，顯示選定子計畫的 [子計畫屬性]  對話方塊。 或者，請按兩下方格中的子計畫，顯示 [子計畫屬性]  對話方塊。 如需有關此對話方塊的詳細資訊，請參閱下文。  
  
     **刪除選取的子計畫**  
     刪除選取的子計畫。  
  
     **子計畫排程**  
     顯示選定子計畫的 [新增作業排程]  對話方塊。  
  
     **移除排程**  
     從選取的子計畫移除排程。  
  
     **管理連接**  
     顯示 [管理連接]  對話方塊。 用於將其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體連接加入維護計畫。 如需有關此對話方塊的詳細資訊，請參閱下文。  
  
     **報表與記錄**  
     顯示 [報表與記錄]  對話方塊。 如需有關此對話方塊的詳細資訊，請參閱下文。  
  
     **伺服器**  
     顯示 [伺服器]  對話方塊，用來選取將執行子計畫工作的伺服器。 只有多伺服器環境中的主要伺服器才會啟用這個選項。 如需詳細資訊，請參閱[建立多伺服器環境](../../ssms/agent/create-a-multiserver-environment.md)和[維護計畫 &#40;Servers&#41;](../../relational-databases/maintenance-plans/maintenance-plan-servers.md)。  
  
     **名稱**  
     顯示維護計畫名稱。 針對新的維護計畫，名稱會在維護計畫設計師開啟之前，於對話方塊中指定。 若要重新命名維護計畫，請以滑鼠右鍵按一下物件總管中的計畫，然後按一下 [重新命名]  。  
  
     **說明**  
     檢視或指定維護計畫的描述。 描述的最大長度是 512 個字元。  
  
     **設計師介面**  
     設計維護計畫並予以維護。 使用設計師介面即可將維護工作加入計畫、從計畫中移除工作、指定工作間的優先順序連結以及指出工作分支和平行處理原則。  
  
     兩個工作間的優先順序連結會建立工作間的關聯性。 只有在第一個工作 (「前導工作」  ) 的執行結果符合指定的準則時，才會執行第二個工作 (「相依工作」  )。 一般而言，指定的執行結果會是 **[成功]** 、 **[失敗]** 或 **[完成]** 。 如需詳細資訊，請參閱以下的步驟 **8** 。  
  
5.  在設計空間的標頭中，按兩下 [子計畫_1]  ，然後在 [子計畫屬性]  對話方塊中輸入子計畫的名稱和描述。  
  
     **[子計畫屬性]** 對話方塊有下列選項。  
  
     **[名稱]**  
     子計畫的名稱。  
  
     **說明**  
     子計畫的簡短描述。  
  
     **排程**  
     指出將執行子計畫的排程。 按一下 **[子計畫排程]** 以開啟 **[新增作業排程]** 對話方塊。 按一下 **[移除排程]** ，從子計畫中刪除排程。  
  
     **執行身分** 清單  
     選取要用來執行此子工作的帳戶。  
  
6.  按一下 **[子計畫排程]** ，在 **[新增作業排程]** 對話方塊中輸入排程詳細資料。  
  
7.  若要建立子計畫，請從 **[工具箱]** 將工作流程元素拖放至計畫設計介面。 按兩下工作以開啟要設定工作選項的對話方塊。  
  
     **[工具箱]** 中有下列維護計畫工作：  
  
    -   **備份資料庫工作**  
  
    -   **檢查資料庫完整性工作**  
  
    -   **執行 SQL Server Agent 作業工作**  
  
    -   **執行 T-SQL 陳述式工作**  
  
    -   **記錄清除工作**  
  
    -   **維護清除工作**  
  
    -   **通知操作員工作**  
  
    -   **重建索引工作**  
  
    -   **重新組織索引工作**  
  
    -   **壓縮資料庫工作**  
  
    -   **更新統計資料工作**  
  
     若要將工作加入 **[工具箱]** 中：  
  
    1.  在 **[工具]** 功能表中按一下 **[選擇工具箱項目]** 。  
  
    2.  選取您要顯示在 **[工具箱]** 中的工具，然後按一下 **[確定]** 。  
  
     將維護計畫工作加入 **[工具箱]** 之後，這些工作也會出現在 **[維護計畫精靈]** 中。 如需上述個別工作的詳細資訊，請參閱 [啟動維護計畫精靈](../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md#SSMSProcedure) 下的 **使用維護計畫精靈**。  
  
8.  若要定義工作之間的工作流程：  
  
    1.  以滑鼠右鍵按一下前導工作，然後選取 [加入優先順序條件約束]  。  
  
    2.  在 **[控制流程]** 對話方塊中的 **[到]** 清單，選取相依工作，然後按一下 **[確定]** 。  
  
    3.  按兩下這兩個工作之間的連接子以開啟 **[優先順序條件約束編輯器]** 對話方塊。  
  
         **[優先順序條件約束編輯器]** 對話方塊中有下列選項。  
  
         **條件約束選項**  
         定義條件約束在兩個工作之間的工作方式。  
  
         **評估作業**  清單  
         指定優先順序條件約束所使用的評估作業。 這些作業有：[條件約束]  、[運算式]  、[運算式與條件約束]  ，以及 [運算式或條件約束]  。  
  
         **值** 清單  
         指定條件約束值：[成功]  、[失敗]  或 [完成]  。 **[成功]** 是預設值。  
  
        > [!NOTE]  
        >  優先順序條件約束線條若是綠色代表 [成功]  、紅色代表 [失敗]  ，而藍色代表 [完成]  。  
  
         **運算式**  
         如果使用的是 [運算式]  、[運算式與條件約束]  或 [運算式或條件約束]  作業，請鍵入運算式。 運算式必須評估為布林。  
  
         **測試**  
         驗證運算式。  
  
         **多個條件約束**  
         定義多個條件約束如何交互操作，以控制受條件約束之工作的執行。  
  
         **邏輯 AND**  
         選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。 所有運算式都必須評估為 True。 這個選項是預設值。  
  
        > [!NOTE]  
        >  此種類型的優先順序條件約束會顯示為綠色、紅色或藍色的實線。  
  
         **邏輯 OR**  
         選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。 必須至少有一個條件約束評估為 True。  
  
        > [!NOTE]  
        >  此種類型的優先順序條件約束會顯示為綠色、紅色或藍色的虛線。  
  
9. 若要新增其他子計畫，其中包含依不同排程執行的工作，請按一下工具列上的 **[加入子計畫]** ，以開啟 **[子計畫屬性]** 對話方塊。  
  
10. 若要新增不同伺服器的連接：  
  
    1.  在設計空間的工具列中，按一下 **[管理連接]** 。  
  
    2.  在 **[管理連接]** 對話方塊中，按一下 **[加入]** 。  
  
    3.  在 **[連接屬性]** 對話方塊的 **[連接名稱]** 方塊中，輸入正在建立的連接名稱。  
  
    4.  在 [指定下列內容以連接到 SQL Server 資料]  下的 [選取或輸入伺服器名稱]  方塊中，輸入要使用的 SQL Server 名稱，或按一下省略符號 **(...)** ，然後在 [SQL Server]  對話方塊中選取伺服器。 如果您從 **[SQL Server]** 對話方塊中選取伺服器，請按一下 **[確定]** 。  
  
    5.  在 **[輸入登入伺服器的資訊]** 底下，選取 **[使用 Windows NT 整合式安全性]** 或 **[使用特定的使用者名稱和密碼]** 。 如果您選擇使用特定的使用者名稱和密碼，請在 **[使用者名稱]** 和 **[密碼]** 方塊中分別輸入該資訊。  
  
    6.  在 **[連接屬性]** 對話方塊中，按一下 **[確定]** 。  
  
    7.  在 **[管理連接]** 對話方塊中，按一下 **[關閉]** 。  
  
11. 若要指定報表選項：  
  
    1.  在設計空間的工具列中，按一下 **[報表與記錄]** 。  
  
    2.  在 **[報表與記錄]** 對話方塊中的 **[報表]** 底下，選取 **[產生文字檔報表]** 、 **[傳送報表至電子郵件收件者]** 或兩者。  
  
        1.  如果您選取 **[產生文字檔報表]** ，請選取 **[建立新檔案]** 或 **[附加至檔案]** 。  
  
        2.  根據上述選項，透過在 **[資料夾]** 或 **[檔案名稱]** 方塊中輸入資訊，輸入新檔案或要附加之檔案的名稱和完整路徑。 或者，按一下省略符號 **(...)** ，然後從 [尋找資料夾 -_server\_name_]  或 [尋找資料庫檔案 -_server\_name_]  對話方塊中選取資料夾或檔案名稱的路徑。  
  
        3.  如果您選取 **[傳送報表至電子郵件收件者]** ，請在 **[代理程式操作員]** 清單中選取電子郵件報表的收件者。  
  
            > [!NOTE]  
            >  SQL Server Agent 必須設定為使用 Database Mail，才能傳送郵件。 如需相關資訊，請參閱 [Configure SQL Server Agent Mail to Use Database Mail](../../relational-databases/database-mail/configure-sql-server-agent-mail-to-use-database-mail.md)  
  
    3.  若要儲存更詳細的資訊，請在 **[記錄]** 底下選取 **[記錄擴充資訊]** 。  
  
    4.  若要將維護計畫結果資訊寫入其他伺服器，請選取 **[記錄到遠端伺服器]** ，然後從 **[連接]** 清單中選取伺服器連接，或按一下 **[新增]** 並在 **[連接屬性]** 對話方塊中輸入連接資訊。  
  
    5.  在 **[報表與記錄]** 對話方塊中，按一下 **[確定]** 。  
  
12. 若要在記錄檔檢視器中檢視結果，請在物件總管  中以滑鼠右鍵按一下 [維護計畫]  資料夾或特定維護計畫，然後選取 [檢視記錄]  。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

     The following options are available on the **Log File Viewer -**_server\_name_ dialog box.  
  
     **Load Log**  
     Open a dialog box where you can specify a log file to load.  
  
     **Export**  
     Open a dialog box that lets you export the information that is shown in the **Log file summary** grid to a text file.  
  
     **Refresh**  
     Refresh the view of the selected logs. The **Refresh** button rereads the selected logs from the target server while applying any filter settings.  
  
     **Filter**  
     Open a dialog box that lets you specify settings that are used to filter the log file, such as **Connection**, **Date**, or other **General** filter criteria.  
  
     **Search**  
     Search the log file for specific text. Searching with wildcard characters is not supported.  
  
     **Stop**  
     Stops loading the log file entries. For example, you can use this option if a remote or offline log file takes a long time to load, and you only want to view the most recent entries.  
  
     **Log file summary**  
     This information panel displays a summary of the log file filtering. If the file is not filtered, you will see the following text, **No filter applied**. If a filter is applied to the log, you will see the following text, **Filter log entries where:** \<filter criteria>.  
  
     **Date**  
     Displays the date of the event.  
  
     **Source**  
     Displays the source feature from which the event is created, such as the name of the service (MSSQLSERVER, for example). This does not appear for all log types.  
  
     **Message**  
     Displays any messages associated with the event.  
  
     **Log Type**  
     Displays the type of log to which the event belongs. All selected logs appear in the log file summary window.  
  
     **Log Source**  
     Displays a description of the source log in which the event is captured.  
  
     **Selected row details**  
     Select a row to display additional details about the selected event row at the bottom of the page. The columns can be reordered by dragging them to new locations in the grid. The columns can be resized by dragging the column separator bars in the grid header to the left or right. Double-click the column separator bars in the grid header to automatically size the column to the content width.  
  
     **Instance**  
     The name of the instance on which the event occurred. This is displayed as *computer name*\\*instance name*.  
  
  
