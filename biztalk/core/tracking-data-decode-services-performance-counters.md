---
title: "追蹤資料解碼服務效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733450b1-71b5-48a4-9ac3-cd880324440c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 501e321c5ad0126a39ad9ebbd3a5d2d687f121b0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="tracking-data-decode-services-performance-counters"></a>追蹤資料解碼服務效能計數器
效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。  
  
 下列效能計數器會在每個主控件執行個體可存取**biztalk: Tdds**效能物件類別：  
  
|**類別目錄**|**計數器**|**說明**|  
|------------------|-----------------|---------------------|  
|BizTalk:TDDS|正在處理的批次|目前 SQL 交易正在處理的批次數。|  
||認可的批次|對目的資料庫認可的批次數。|  
||正在處理的事件|目前 SQL 交易正在處理的事件數。|  
||認可的事件|一秒內對目的資料庫確認的事件數。|  
||正在處理的記錄|目前 SQL 交易正在處理的記錄數。|  
||認可的記錄|一秒內對目的資料庫確認的記錄數。|  
||批次總數|TDDS 已處理的批次總數。|  
||事件總數|TDDS 已處理的事件總數。|  
||失敗的批次總數|TDDS 無法執行的批次總數。|  
||失敗的事件總數|TDDS 無法執行的事件總數。|  
||記錄總數|TDDS 已處理的記錄總數。|  
  
## <a name="to-access-performance-counters"></a>存取效能計數器  
 使用下列步驟來存取效能計數器。  
  
#### <a name="if-you-are-using-windows-2008"></a>若是使用 Windows 2008  
  
1.  按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。  
  
2.  在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。  
  
3.  在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Tdds**效能計數器物件，然後選取要監視的計數器  
  
4.  在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。  若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。  
  
5.  新增計數器後, 按一下**確定**。  
  
     選取的效能計數器隨即出現在**效能監視器**螢幕。  
  
## <a name="see-also"></a>請參閱  
 [效能秘訣和訣竅](../core/performance-tips-and-tricks.md)   
 [測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [透過主控件節流將資源使用最佳化](../core/optimizing-resource-usage-through-host-throttling.md)