---
title: "BAM 效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], performance counters
- performance, counters [BAM]
ms.assetid: e23f7038-36a5-4957-bc73-47011763d109
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4307f72f149405fbc04e4e6cc51efe87229c2bff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-performance-counters"></a>BAM 效能計數器
效能計數器可以讓您針對 BAM 事件匯流排服務所執行的特定工作進行監控。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下表列出「商務活動監控」的可用效能計數器。  
  
|計數器|說明|  
|-------------|-----------------|  
|正在處理的事件|目前 BAM 事件匯流排服務正在處理的事件數|  
|正在處理的批次|目前 BAM 事件匯流排服務正在處理的批次數|  
|認可的事件|在上一秒內 BAM 事件匯流排服務對 SQL Server 認可的事件數。|  
|認可的記錄|在上一秒內 BAM 事件匯流排服務對 SQL Server 認可的記錄數。|  
|認可的批次|在上一秒內 BAM 事件匯流排服務對 SQL Server 認可的批次數。|  
|事件總數|從啟動到現在 BAM 事件匯流排服務已經處理的事件數。|  
|記錄總數|從啟動到現在 BAM 事件匯流排服務已經處理的記錄數。|  
|批次總數|從啟動到現在 BAM 事件匯流排服務已經處理的批次數。|  
|失敗的批次總數|從啟動到現在 BAM 事件匯流排服務無法處理的批次數。|  
|失敗的事件總數|從啟動到現在 BAM 事件匯流排服務無法處理的事件數。|  
  
 在「效能監視器」(perfmon) 中，效能計數器位於 BizTalk:TDDS 效能物件下。 效能計數器的執行個體名稱是來源伺服器名稱和來源資料庫名稱的組合。 如果同一台電腦上有兩個 BAM 事件匯流排服務在兩個不同的來源資料庫上執行，您將會看見兩個 BAM 事件匯流排服務計數器的執行個體。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [管理 BAM](../core/managing-bam.md)