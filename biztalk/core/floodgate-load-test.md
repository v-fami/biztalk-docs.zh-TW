---
title: 大量負載測試 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- LoadGen tool, simulating floodgate events
- performance, floodgate peaks
- floodgate events [performance]
ms.assetid: 937f2478-339b-4ae2-b107-56f3a4bfc579
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74954d8b94207832ceee5bbb699a7de1a245f61b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246206"
---
# <a name="floodgate-load-test"></a>大量負載測試
本主題中的資訊是指中所說明的測試[測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)。  
  
## <a name="what-causes-floodgate-events"></a>什麼造成了大量事件？  
 有許多案例僅少數高尖峰時段 (也稱為**大量事件**) 的訊息抵達系統每一天。 在這些尖峰期間，輸送量可能相當低。 這類實例的範例包含：  
  
-   例如，股市開始與結束時的股票交易  
  
-   例如，每日交易結束期間進行對帳的銀行系統  
  
 其他的事件類型會造成與大量事件類似的積存行為。 例如，若夥伴傳送位址離線而必須重試和 (或) 擱置該位址的訊息，則會導致積存一直累積。 當夥伴重新上線時，可能就有大量的擱置訊息需要重送，而造成另一種類型的大量事件。 以下的系統測試會說明此行為。  
  
## <a name="simulating-a-floodgate-event"></a>模擬大量事件  
 對於此測試，系統一開始的運作大約是可維持之輸送量上限的一半，所以當然是相當穩定。 接著，若模擬大量事件，負載產生工具會設定在短時間內，以 410 msgs/sec 進行傳送 (與加速測試一樣)。 以下所示的為測量每秒接收的訊息及多工緩衝處理深度而產生的負載設定檔。  
  
 **大量負載測試的負載設定檔**  
  
 ![大量負載的效能監視器顯示](../core/media/bts06-floodgate-load.gif "BTS06_Floodgate_Load")  
  
 請注意，從圖中看到多工緩衝處理資料表在大量事件期間快速累積積存。 不過，由於事件的時間相當短，且事件之後的後續接收速率低於可維持速率的上限，因此清除工作能夠執行並從事件復原，而不用要求系統停止接收。 對於這個特殊測試，MessageBox 是位於 SQL Server 2005 上；此測試從開始到結束大約需 45 分鐘的時間。  
  
 當然，每個系統都是不同的，因此您所需的時間也可能不一樣。 確定可以復原的最佳方式是，實際執行前先測試具有代表性的負載。  
  
## <a name="see-also"></a>另請參閱  
 [測量引擎 MST 的測試案例](../core/test-scenarios-for-measuring-mst-of-the-engine.md)   
 [使用設定儀表板，以便讓 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)   
 [加速負載測試](../core/overdrive-load-test.md)   
 [持續性負載測試](../core/sustainable-load-test.md)