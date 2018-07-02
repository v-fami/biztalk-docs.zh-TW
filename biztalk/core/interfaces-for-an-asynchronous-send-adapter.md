---
title: 傳送配接器介面非同步 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6a214716-8f39-400d-a111-ba1b92a284b4
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd90aa9c5d010acc4d73a66220964ebdcb31e1f0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980351"
---
# <a name="interfaces-for-an-asynchronous-send-adapter"></a>非同步傳送配接器介面
每次傳送一個訊息的配接器可以同步或非同步地傳送訊息。 配接器在執行傳送作業期間使用個別執行緒，而不封鎖傳輸 Proxy 執行緒時，它會非同步傳送訊息。 為了能夠非同步傳送訊息，配接器必須實作下列介面：  
  
- **IBTTransport**  
  
- **IBaseComponent**  
  
- **IBTTransportControl**  
  
- **IPersistPropertyBag**  
  
- **IBTTransmitter**  
  
  下列步驟說明傳送配接器在「傳訊引擎」要求下，為了從伺服器中傳輸訊息，所執行的動作順序：  
  
1.  傳訊引擎會使用傳輸 proxy 將外寄訊息至傳送配接器，藉由呼叫**TransmitMessage**方法**IBTTransmitter**介面。  
  
2.  配接器會立即傳回從**TransmitMessage**後儲存訊息以傳送到某些內部佇列，並傳回`False`如**bDeleteMessage**。 這會告知「傳訊引擎」，訊息將會以非同步方式傳輸。  
  
3.  配接器使用專屬的執行緒集區傳送訊息。  
  
4.  在傳送作業完成之後，配接器會從 MessageBox 資料庫刪除原始訊息。 它會從傳訊引擎使用中取得一批**IBTTransportBatch.GetBatch**方法的傳輸 proxy，然後再呼叫**DeleteMessage**。  
  
     下圖顯示建立非同步傳送配接器時所包含的物件互動。  
  
     ![](../core/media/ebiz-sdk-devadapter5.gif "ebiz_sdk_devadapter5")  
非同步傳送訊息的工作流程  
  
> [!NOTE]
>  建議配接器應計算目前處理中訊息的數目。 此配接器應該封鎖**Terminate**的訊息計數達到零以前的方法。 對於傳送配接器而言，應該會以適當方式處理進行中的訊息。 這表示，已成功非同步傳遞的任何訊息都應該從配接器的私用應用程式訊息佇列中刪除，以免將訊息傳送兩次。 一般情況下，在後**Terminate**稱為 「 傳訊引擎它不會接受發佈新訊息的配接器的要求。 唯一的例外是請求-回應組相關的回應訊息。  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [請求-回應傳送配接器介面](../core/interfaces-for-a-solicit-response-send-adapter.md)