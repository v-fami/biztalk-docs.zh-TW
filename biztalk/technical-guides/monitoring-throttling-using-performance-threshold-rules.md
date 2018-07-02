---
title: 監視節流使用效能臨界值規則 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc2c3024-a54b-4485-8110-c2ec9ec52721
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d5bf8f327cbdb12ebe0723941afd6e37b5d2409
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968047"
---
# <a name="monitoring-throttling-using-performance-threshold-rules"></a>監視節流使用效能臨界值規則
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將會初始化節流，以保護系統不致達到無法復原的狀態。 節流可以表示發生問題，並協助您識別其來源。 您已識別為基礎的節流狀態瓶頸的原因之後，分析其他效能計數器，以縮小問題的來源。  
  
 比方說，在 MessageBox 資料庫上的高爭用情況可能是因為高 CPU 使用量，因而造成過度分頁至磁碟，進而可能記憶體不足所造成。 MessageBox 上的高爭用也可能因高鎖定爭用時，可能是由於磁碟機飽和。  
  
 監視訊息傳遞節流狀態 」 和 「 訊息發佈節流狀態，每個主控件執行個體，通常是疑難排解節流時啟動的好地方。 如果這些計數器的值不是零，則表示 BizTalk Server 系統中發生節流，並可進一步分析瓶頸的原因。 如需有關其他效能計數器的描述，請參閱[資料庫層中的識別瓶頸](http://go.microsoft.com/fwlink/?LinkID=154678)(<http://go.microsoft.com/fwlink/?LinkID=154678>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="biztalk-server-system-performance-counters"></a>BizTalk Server 系統效能計數器  
  
|Object|執行個體|計數器|監控目的|  
|------------|--------------|-------------|------------------------|  
|處理器|_Total|% 處理器時間|資源爭用|  
|處理|BTSNTSvc|虛擬位元組|記憶體流失/膨脹|  
|處理|BTSNTSvc|私用位元組|記憶體流失/膨脹|  
|處理|BTSNTSvc|控制碼計數|資源爭用|  
|處理|BTSNTSvc|執行緒計數|資源爭用|  
|實體磁碟|_Total|% 閒置時間|資源爭用|  
|實體磁碟|_Total|Current Disk Queue Length|資源爭用|  
  
## <a name="biztalk-application-counters"></a>BizTalk 應用程式計數器  
  
|Object|執行個體|計數器|描述|  
|------------|--------------|-------------|-----------------|  
|BizTalk 傳訊|RxHost|每秒接收文件數|內送速率|  
|BizTalk 傳訊|TxHost|每秒處理文件數|外寄速率|  
|XLANGs/協調流程|PxHost|已完成的協調流程/秒|處理速率|  
|BizTalk: MessageBox： 一般計數器|MsgBoxName|多工緩衝處理大小|所有主控件佇列總計大小|  
|BizTalk: MessageBox： 一般計數器|MsgBoxName|追蹤資料大小|MessageBox 上的 TrackingData 資料表大小|  
|BizTalk: MessageBox： 主控件計數器|PxHost:MsgBoxName|主控件佇列 - 長度|指定主控件佇列中的訊息數|  
|BizTalk: MessageBox： 主控件計數器|TxHost:MsgBoxName|主控件佇列 - 長度|指定主控件佇列中的訊息數|  
|BizTalk： 訊息代理程式|RxHost|資料庫大小|發佈 (PxHost) 佇列的大小|  
|BizTalk： 訊息代理程式|PxHost|資料庫大小|發佈 (TxHost) 佇列的大小|  
|BizTalk： 訊息代理程式|HostName|訊息傳遞節流狀態|影響 XLANG 和輸出傳輸|  
|BizTalk： 訊息代理程式|HostName|訊息發佈節流狀態|影響 XLANG 和輸入傳輸|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [監視節流](../technical-guides/monitoring-for-throttling.md)