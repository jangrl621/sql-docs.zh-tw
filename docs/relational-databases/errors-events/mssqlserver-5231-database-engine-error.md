---
title: MSSQLSERVER_5231 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5231 (Database Engine error)
ms.assetid: 6954ae84-ed0b-4f4c-9d0a-e73f3d71476c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2cd4a8208925f6e0fe0a0fed4b162b4eb7361009
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122957"
---
# <a name="mssqlserver5231"></a>MSSQLSERVER_5231
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|5231|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|DBCC4_DEADLOCK_SKIPPED_OBJECT|  
|訊息文字|物件識別碼 O_ID (物件 'NAME')：嘗試鎖定此物件進行檢查時發生死結。 已經略過這個物件，不會處理。|  
  
## <a name="explanation"></a>說明  
DBCC 嘗試鎖定物件時發生死結，並已選擇 DBCC 做為死結犧牲者。 將不會處理此物件。  
  
## <a name="user-action"></a>使用者動作  
None  
  
