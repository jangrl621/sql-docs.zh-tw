---
title: 使用自訂字典自訂斷詞工具行為 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: search, sql-database
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 548072483f4a6c8ea0669fce13aaab0595ec4c97
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68082945"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a>使用自訂字典自訂斷詞工具行為
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  您可以建立語言特有自訂字典檔案，以自訂特定語言之斷詞工具的行為。 例如，您可以防止斷詞工具中斷特定詞彙或模式。  
  
 如需詳細資訊，請參閱下列 SharePoint 文章：  
  
 [建立自訂字典 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，將自訂字典檔案放入下列資料夾中：  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 建立或變更自訂字典檔案之後，請使用下列命令重新啟動 SQL 全文檢索背景程式啟動器：  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
