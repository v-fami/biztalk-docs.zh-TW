---
title: 非同步批次支援傳送配接器介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d38b8b87-508a-499b-86b2-846938050b44
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc579995821a97dc588b2221f8a7dd2e9cd1e136
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36993015"
---
# <a name="interfaces-for-an-asynchronous-batch-supported-send-adapter"></a>非同步批次支援傳送配接器介面
批次感知的配接器可以同步或非同步地傳送訊息，而且可以執行交易式的傳送作業。 若要傳送訊息的批次，傳送配接器必須實作下列介面：  
  
- **IBTTransport**  
  
- **IBaseComponent**  
  
- **IBTTransportControl**  
  
- **IPersistPropertyBag**  
  
- **IBTBatchTransmitter**  
  
- **IBTTransmitterBatch**  
  
  對於非同步批次傳送，傳訊引擎會從配接器取得批次，並將需要傳輸的訊息新增到該批次中。 當傳訊引擎會呼叫時，才會傳送訊息**完成**在批次上的方法。 對於要以非同步方式傳輸的每個訊息，配接器都會傳回 `False`。 接著配接器會從配接器 Proxy 取得批次，並刪除它已成功傳輸的訊息。  
  
  下圖顯示在建立非同步批次支援的傳送配接器時所牽涉的物件互動。  
  
  ![](../core/media/ebiz-sdk-devadapter7.gif "ebiz_sdk_devadapter7")  
  非同步傳送訊息的工作流程  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)   
 [請求-回應傳送配接器介面](../core/interfaces-for-a-solicit-response-send-adapter.md)