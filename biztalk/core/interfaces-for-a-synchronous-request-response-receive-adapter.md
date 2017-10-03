---
title: "介面的同步要求-回應接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0c60832-52b5-4d2c-81ec-94c46c375b15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9abd84bab5da623c2dff61c6e07a5898110588af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-request-response-receive-adapter"></a>同步要求-回應接收配接器介面
所有的接收配接器都必須實作下列介面，才能以要求-回應模式運作：  
  
-   **IBTTransport**  
  
-   **IBTTransportControl** （只有一般配接器）  
  
-   **IBTTransportConfig**  
  
-   **IBaseComponent**  
  
-   **IPersistPropertyBag**  
  
-   **IBTBatchCallBack**  
  
-   **IBTTransmitter**  
  
 支援要求-回應通訊協定的接收配接器 (例如 HTTP 接收配接器) 在提交要求訊息時都會執行下列動作：  
  
1.  接收配接器接收內送要求訊息。 它從傳輸 proxy 取得批次呼叫**Ibttransportproxy**方法**IBTTransportProxy**介面。 在這個呼叫配接器用來傳遞的回呼指標實作**IBTBatchCallBack.BatchComplete**方法。  
  
2.  配接器新增到批次要求訊息，藉由呼叫**SubmitRequestMessage**方法**IBTTransportBatch**介面，針對每個要求訊息一次。  
  
3.  當已新增的所有訊息時，配接器會呼叫**完成**方法**IBTTransportBatch**介面，提交給傳訊引擎透過傳輸 proxy 批次。  
  
4.  處理批次之後，傳訊引擎會叫用配接器的**IBTBatchCallBack.BatchComplete**透過傳輸 proxy 的回呼方法。 提交的狀態將以對應於批次中各個訊息的 HRESULT 值陣列，傳送至配接器。 如果批次在管線或協調流程中失敗，則會將 SOAP 錯誤訊息傳回給配接器，以做為回應。  
  
5.  內送要求訊息可能有協調流程訂閱者。 在協調流程完成且已處理的要求訊息後，「 傳訊引擎會傳送透過傳輸 proxy 將回應訊息至配接器藉由呼叫配接器的**TransmitMessage** 方法**IBTTransmitter**介面。  
  
6.  配接器會傳送回應訊息，並刪除 MessageBox 資料庫中的原始訊息。  
  
 下圖顯示在建立同步要求-回應接收配接器時所牽涉的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter3.gif "ebiz_sdk_devadapter3")  
接收配接器提交同步訊息的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發接收配接器](../core/developing-a-receive-adapter.md)   
 [具現化，並初始化接收配接器](../core/instantiating-and-initializing-a-receive-adapter.md)   
 [介面的內含式接收配接器](../core/interfaces-for-an-in-process-receive-adapter.md)   
 [介面的外掛式接收配接器](../core/interfaces-for-an-isolated-receive-adapter.md)   
 [接收配接器批次支援的介面](../core/interfaces-for-a-batch-supported-receive-adapter.md)   
 [交易式批次支援接收配接器介面](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)