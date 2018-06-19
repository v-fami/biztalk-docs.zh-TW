---
title: 交易式非同步批次支援傳送配接器的介面，|Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e5b2dbdf-e6ba-4b58-a0a5-fc78feaf5c35
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 948000883c092c8e247b1d4f41fb2bc7e2280e40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257710"
---
# <a name="interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter"></a>交易式非同步批次支援傳送配接器介面
傳送配接器可以在需要交易式的訊息傳輸時建立及控制交易。 若要支援交易式的傳送，配接器必須實作下列介面：  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchTransmitter**  
  
-   **IBTTransmitterBatch**  
  
-   **IBTBatchCallBack**  
  
 配接器建立 MSDTC 交易，並傳回該物件的呼叫中的指標**BeginBatch**方法**IBTTransmitterBatch**介面。 傳訊引擎會呼叫此方法來取得批次，並透過該批次將外寄訊息公佈至傳送配接器。 當配接器完成傳送作業並認可或回復交易時，它會使用通知傳訊引擎交易的結果**DTCCommitConfirm**方法**IBTDTCCommitConfirm**介面。  
  
 下圖顯示在執行交易式傳送作業時，傳輸 Proxy 和傳送配接器之間的互動。  
  
 ![](../core/media/ebiz-sdk-devadapter8.gif "ebiz_sdk_devadapter8")  
非同步傳送交易式訊息的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [傳送配接器的請求-回應的介面](../core/interfaces-for-a-solicit-response-send-adapter.md)