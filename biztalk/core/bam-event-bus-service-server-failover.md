---
title: "BAM 事件匯流排服務伺服器容錯移轉 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f12378c8-09bb-45c1-ade1-d9b20131461f
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c1fafc3e97d9905a6efd0de8ff0f389c2a389bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bam-event-bus-service-server-failover"></a>BAM 事件匯流排服務伺服器容錯移轉
BAM 事件匯流排服務包含容錯邏輯，可讓它從意外的失敗中復原和重新啟動，而不會遺失任何資料。  
  
 當您在多部電腦上啟用 BAM 事件匯流排服務時，如果服務發生錯誤，容錯移轉邏輯將會偵測到 BAM 事件匯流排服務已經終止，並自動在另一部電腦上啟動新的 BAM 事件匯流排服務執行個體。  
  
 下圖顯示 BAM 事件匯流排如何執行簡單負載平衡以處理電腦或網路的錯誤情況。 在 BAM 事件匯流排服務啟動前，先設定好兩個來源與一個目的地。  
  
 ![](../core/media/ebiz-bam-admin-evntbuspoolfail.gif "ebiz_bam_admin_evntbuspoolfail")  
BAM 事件匯流排服務進行負載平衡  
  
 BAM 事件匯流排服務執行下列動作以進行負載平衡：  
  
-   **答： Server1 處理來自 2 個來源 （工作階段） 的事件資料**。 在 BAM 事件匯流排服務的執行個體建立在 Server2 之前，BAM 事件匯流排協調流程執行個體會先建立在 Server1 上。 伺服器會發現已經沒有其他可用的伺服器，於是為 Src1 和 Src2 收取這兩個工作階段。  
  
-   **B: Server2 上線，並加入 BAM 事件匯流排集區**。 當一個 BAM 事件匯流排服務執行個體建立在 Server2 上之後，Server1 會捨棄一個工作階段，而 Server2 會收取該工作階段。  
  
-   **C: Server1 失敗**。 Server1 在 Server2 加入 BAM 事件匯流排集區後發生錯誤。  
  
-   **D: Server2 處理來自 2 個來源 （工作階段） 的事件資料**。 Server2 為 Src1 和 Src2 收取這兩個工作階段。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md)   
 [BAM 安全性建議](../core/bam-security-recommendations.md)   
 [商務活動監控 (BAM)](../core/business-activity-monitoring-bam.md)