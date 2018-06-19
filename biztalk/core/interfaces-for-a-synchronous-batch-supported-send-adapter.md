---
title: 同步批次支援傳送配接器介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2b191c41-ca4f-4d2b-bd15-a93ad87a743d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ab61fd6624468e0464cfe0c648fcc868bd20005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257670"
---
# <a name="interfaces-for-a-synchronous-batch-supported-send-adapter"></a>同步批次支援傳送配接器介面
能識別批次的配接器可以同步或非同步地傳送訊息，並能執行交易式的傳送作業。 若要傳送訊息的批次，傳送配接器必須實作下列介面：  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchTransmitter**  
  
-   **IBTTransmitterBatch**  
  
 對於同步批次傳送，傳訊引擎會從配接器取得批次，並將需要傳輸的訊息新增到該批次中。 傳訊引擎中新增每個訊息的批次並傳送訊息，它會呼叫時，才**完成**批次的方法。 配接器傳回`True`如**bDeleteMessage**對於要以同步方式傳輸每個訊息。 配接器應該將訊息資料，而非訊息指標儲存在其**TransmitMessage**實作。 這是因為在傳回 `True` 之後，訊息指標已經不再有效，而且不該再遭到使用，或是存入快取以便稍後使用。  
  
 下圖顯示在建立同步批次支援的傳送配接器時所牽涉的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter6.gif "ebiz_sdk_devadapter6")  
同步提交訊息的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [傳送配接器的請求-回應的介面](../core/interfaces-for-a-solicit-response-send-adapter.md)