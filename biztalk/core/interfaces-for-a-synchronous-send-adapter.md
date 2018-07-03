---
title: 傳送配接器介面同步 |Microsoft Docs
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
ms.openlocfilehash: 1602d19bc5b97231a25f5449f5837fce153c037d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008839"
---
# <a name="interfaces-for-a-synchronous-send-adapter"></a>同步傳送配接器介面
配接器在執行傳送作業當中阻止內送傳訊引擎呼叫執行緒時，它會同步傳送訊息。 為了能夠同步傳送訊息，配接器必須實作下列介面：  
  
- **IBTTransport**  
  
- **IBaseComponent**  
  
- **IBTTransportControl**  
  
- **IPersistPropertyBag**  
  
- **IBTTransmitter**  
  
  在同步傳送中，配接器傳送訊息時封鎖**TransmitMessage**，並傳回成功傳輸之後， `True.`  
  
  下圖顯示建立同步傳送配接器時所包含的物件互動。  
  
  ![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")  
  同步傳送訊息的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [請求-回應傳送配接器介面](../core/interfaces-for-a-solicit-response-send-adapter.md)