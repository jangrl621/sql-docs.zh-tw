---
title: SQL Server 2016 的 SQL Server 記憶體內部 OLTP 內部 | Microsoft Docs
ms.custom: ''
ms.date: 09/14/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b14da361-a6b8-4d85-b196-7f2f13650f44
author: jodebrui
ms.author: jodebrui
ms.openlocfilehash: ca36f8c9716b9160b4d6eaeee26201bf03b42927
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111737"
---
# <a name="sql-server-in-memory-oltp-internals-for-sql-server-2016"></a>SQL Server 2016 的 SQL Server 記憶體內部 OLTP 內部
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

**摘要：** SQL Server 2014 中引進了記憶體內部 OLTP，其經常以其代號名稱 "Hekaton" 稱呼。
這項強大技術可讓您利用大量的記憶體和眾多數十個核心，以提升 OLTP 作業的效能，最高達 30 到 40 倍！ SQL Server 2016 透過移除 SQL Server 2014 中的多種限制並增強內部處理演算法，持續投資記憶體內部 OLTP，讓記憶體內部 OLTP 的改良更完善。 本報告描述自 SQL Server 2016 RTM 起的 SQL Server 2016 的記憶體內部 OLTP 技術實作。 使用記憶體內部 OLTP，資料表可宣告為「記憶體最佳化」以啟用記憶體內部 OLTP 的功能。 記憶體最佳化的資料表為完全交易式，且可使用 Transact-SQL 存取。 Transact-SQL 預存程序、觸發程序及純量 UDF 可編譯為機器碼，以進一步提升記憶體最佳化的資料表效能。 引擎設計為高度並行存取且不會受到封鎖。    
  
**作者：** Kalen Delaney  
  
**技術校閱：** Sunil Agarwal 及 Jos de Bruijn  
  
**發行日期：** 2016 年 6 月  
  
**適用於：** SQL Server 2016  
  
若要檢閱文件，請下載 [SQL Server 2016 的 SQL Server 記憶體內部 OLTP 內部](https://download.microsoft.com/download/8/3/6/8360731A-A27C-4684-BC88-FC7B5849A133/SQL_Server_2016_In_Memory_OLTP_White_Paper.pdf) 文件。   
