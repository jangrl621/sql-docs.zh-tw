---
title: 取消隱藏執行自訂報表警告 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], custom reports
ms.assetid: 0deed900-c910-4d12-aac0-6ab9e39eb068
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 14d7372258e3cc15eb3da6d5577145b588473388
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262128"
---
# <a name="unsuppress-run-custom-report-warnings"></a>取消隱藏執行自訂報表警告
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
自訂報表有兩個警告對話方塊。 此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中取消隱藏這些方塊的顯示。  
  
根據預設，[執行自訂報表]  對話方塊會在自訂報表執行之前顯示。 如果您選取了 [請不要再顯示這個警告]  核取方塊，將不再顯示此對話方塊。 此外，根據預設，當您開啟自訂報表，然後按一下連結來開啟另一份自訂報表時，就會顯示 [執行自訂報表]  對話方塊。 此對話方塊會顯示鑽研自訂報表檔案的完整路徑。 如果您選取了 [請不要再顯示這個警告]  核取方塊，將不再顯示此對話方塊。  
  
## <a name="SSMSProcedure"></a>使用 SQL Server Management Studio  
  
#### <a name="to-unsuppress-the-main-custom-report-warning-dialog-box"></a>取消隱藏主要自訂報表警告對話方塊  
  
1.  連接至 \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml。  
  
2.  以滑鼠右鍵按一下 **reports.xml**，然後按一下 [編輯]  。  
  
3.  將 **<SuppressWarning>true\<\/SuppressWarning> 變更為 <SuppressWarning>false\<\/SuppressWarning>** 。  
  
4.  重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
#### <a name="to-unsuppress-the-drill-through-custom-report-warning-dialog-box"></a>取消隱藏鑽研自訂報表警告對話方塊  
  
1.  連接至 \<*Server*>\\<*Share*>|\<*Drive*>\Documents and Settings\\<UserProfile>\Application Data\Microsoft\Microsoft SQL Server\130\Tools\Shell\reports.xml。  
  
2.  以滑鼠右鍵按一下 **reports.xml**，然後按一下 [編輯]  。  
  
3.  將 **<SuppressDrillthroughWarning>true\<\/SuppressDrillthroughWarning> 變更為 <SuppressDrillthroughWarning>false\<\/SuppressDrillthroughWarning>** 。  
  
4.  重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
[Management Studio 中的自訂報表](../../ssms/object/custom-reports-in-management-studio.md)  
[將自訂報表加入 Management Studio](../../ssms/object/add-a-custom-report-to-management-studio.md)  
[使用自訂報表搭配物件總管節點屬性](../../ssms/object/use-custom-reports-with-object-explorer-node-properties.md)  
  
