---
title: 管理方案和專案的檔案 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], files
- .ssmssln files
- .ssmsmobileproj files
- .ssmsasproj files
- .ssmssqlproj files
- .sqlsuo files
- files [SQL Server Management Studio], projects
ms.assetid: e19d2859-0b97-4727-ac27-c4c226d86b2f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: fbaa867ae3ab2683507c773c411d965a46cf795b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68262868"
---
# <a name="files-that-manage-solutions-and-projects"></a>管理方案和專案的檔案
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
 此主題描述 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]專用的檔案類型。 依預設，所有方案及其專案都建立在 \My Documents\SQL Server Management Studio Projects 中。  


## <a name="management-studio-solution-files"></a>Management Studio 方案檔  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 所用的檔案類型與 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] 或 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Visual Studio 不同。 這代表您無法在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 Visual Studio 中開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull_md.md)] 方案。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 方案檔可讓方案總管顯示一個用以管理檔案的圖形介面。  
   
|延伸模組|檔案類型|Description|建立者|  
|-------------|-------------|---------------|--------------|  
|.ssmssln|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 方案物件|提供參考 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 專案、專案項目和方案之磁碟位置的環境|[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]|  
  
## <a name="management-studio-project-files"></a>Management Studio 專案檔  
專案依照方案包含方案檔 (用來管理方案中的物件) 的相同方式來包含專案檔。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 針對專案所建立之專案檔的類型，會隨著用來建立專案的範本而不同。 下表說明針對每個專案所建立之檔案的類型。  
   
|延伸模組|專案範本|  
|-------------|--------------------|  
|.ssmssqlproj|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 指令碼專案|  
|.ssmsasproj|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)] 指令碼專案|  
   
## <a name="location-of-solution-level-files"></a>方案層級檔案的位置  
依預設，方案層級的檔案是建立在方案所建立的第一個專案之實體目錄中。 您可以建立一個方案來指定方案的目錄，也可以在建立新專案時指定目錄。  
 
如果目錄結構類似於 [方案總管] 所顯示的邏輯結構，專案和方案檔會比較容易尋找，團隊的其他開發人員也比較容易共用它們。  
   
## <a name="see-also"></a>另請參閱  
[利用編碼管理檔案](../../ssms/solution/manage-files-with-encoding.md)  
[其他檔案](../../ssms/solution/miscellaneous-files.md)  
[方案總管](../../ssms/solution/solution-explorer.md)  
[方案 &#40;SQL Server Management Studio&#41;](../../ssms/solution/solutions-sql-server-management-studio.md)  
[專案 &#40;SQL Server Management Studio&#41;](../../ssms/solution/projects-sql-server-management-studio.md)  
[方案總管原始檔控制](https://msdn.microsoft.com/library/ms173879.aspx)  
  
