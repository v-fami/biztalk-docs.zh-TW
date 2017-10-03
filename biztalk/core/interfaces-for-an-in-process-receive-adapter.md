---
title: "介面的內含式接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ed668d9-7512-4026-a8f3-df05aeed4df6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7135471700cf640f61b56506ad159b5c47c7d877
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-in-process-receive-adapter"></a>內含式接收配接器的介面
「傳訊引擎」會具現化和設定內含式配接器，並傳入傳輸 Proxy 以允許配接器存取其功能。 若要啟用組態並與傳輸 Proxy 繫結，配接器必須實作下列的組態介面：  
  
-   **IBTTransport**  
  
-   **IBTTransportControl**  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
 （選擇性） 如果配接器想要接收處理常式資訊初始化期間，需要實作**IPersistPropertyBag**。  
  
 「傳訊引擎」會建立配接器的執行個體、初始化該執行個體，然後設定接收位置的組態。 傳訊引擎傳送至配接器的屬性包**AddReceiveEndpoint**方法呼叫。 該屬性包含有接收位置和接收處理常式的組態。 組態是以 XML 樣式屬性包的形式儲存在資料庫中。 「傳訊引擎」會從 XML 讀取 XML 並解除凍結屬性包。 在至少新增一個端點 (接收位置) 後，配接器便會開始提交訊息。  
  
> [!NOTE]
>  配接器應該不會封鎖傳訊引擎會呼叫這類**IBTTransportControl.Initialize**， **IPersistPropertyBag.Load**，和**IBTTransportConfig.AddReceiveEndpoint**. 在這些呼叫中執行過多的處理，便會對服務啟動時間造成影響。  
  
 下圖顯示在建立內含式接收配接器時所牽涉的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter11.gif "ebiz_sdk_devadapter11")  
內含式接收配接器的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發接收配接器](../core/developing-a-receive-adapter.md)   
 [具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [介面的外掛式接收配接器](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [交易式批次支援接收配接器介面](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)   
 [接收配接器同步要求-回應的介面](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)