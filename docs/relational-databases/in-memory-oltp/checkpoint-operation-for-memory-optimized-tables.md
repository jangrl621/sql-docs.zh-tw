---
title: 記憶體最佳化資料表的檢查點作業 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 47975bd5-373f-43cd-946a-da8e8088b610
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0f3e07e6762a288fe646477ad0218e5f54eb3b2e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67951069"
---
# <a name="checkpoint-operation-for-memory-optimized-tables"></a>記憶體最佳化的資料表的檢查點作業
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  資料與差異檔案中的記憶體最佳化資料之檢查點需要定期出現，以推進交易記錄的使用中部分。 檢查點可讓記憶體最佳化的資料表還原或復原到上一個成功的檢查點，然後套用交易記錄的使用中部分，更新記憶體最佳化的資料表以完成還原。 以磁碟為基礎的資料表和記憶體最佳化資料表的檢查點作業是不同的作業。 下列內容描述以磁碟為基礎的資料表和記憶體最佳化資料表之間不同的狀況和檢查點行為：  
  
## <a name="manual-checkpoint"></a>手動檢查點  
 當您發出手動檢查點時，它會關閉以磁碟為基礎的資料表和記憶體最佳化資料表的檢查點。 使用中的資料檔案會關閉，即使它可能只有部分填滿。  
  
## <a name="automatic-checkpoint"></a>自動檢查點  
 自動檢查點對於磁碟資料表和記憶體最佳化資料表的實作不同，因為兩種資料表保存資料的方式不同。  
  
 對於磁碟資料表，自動檢查點是根據復原間隔組態選項取得 (如需詳細資訊，請參閱[變更資料庫的目標復原時間 &#40;SQL Server&#41;](../../relational-databases/logs/change-the-target-recovery-time-of-a-database-sql-server.md))。  
  
 對於記憶體最佳化資料表，自動檢查點是在交易記錄檔自上一個檢查點之後變得大於 1.5 GB 時取得。 此 1.5 GB 大小同時包含磁碟資料表和記憶體最佳化資料表的交易記錄。  
  
## <a name="see-also"></a>另請參閱  
 [建立及管理記憶體最佳化物件的儲存體](../../relational-databases/in-memory-oltp/creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
