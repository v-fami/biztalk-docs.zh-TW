---
title: 傳送配接器介面同步 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0e1b397a-3a35-4447-8522-d8a5f39a42d7
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1012b52bf5c6ab564cc219926b97445e43f60dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256910"
---
# <a name="interfaces-for-a-synchronous-send-adapter"></a>同步傳送配接器介面
配接器在執行傳送作業當中阻止內送傳訊引擎呼叫執行緒時，它會同步傳送訊息。 為了能夠同步傳送訊息，配接器必須實作下列介面：  
  
-   **IBTTransport**  
  
-   **IBaseComponent**  
  
-   **IBTTransportControl**  
  
-   **IPersistPropertyBag**  
  
-   **IBTTransmitter**  
  
 在同步傳送中，配接器傳送訊息時封鎖**TransmitMessage**，和傳輸成功而傳回之後`True.`  
  
 下圖顯示建立同步傳送配接器時所包含的物件互動。  
  
 ![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")  
同步傳送訊息的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化，並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [傳送配接器的非同步介面。](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [傳送配接器的請求-回應的介面](../core/interfaces-for-a-solicit-response-send-adapter.md)