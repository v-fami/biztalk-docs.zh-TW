---
title: 傳送配接器介面請求-回應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c54650e8-dbfb-4c66-843b-0b82c8183dd4
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5056092886ad9d73d3db3dcc910038bc7dcd6e4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024132"
---
# <a name="interfaces-for-a-solicit-response-send-adapter"></a>請求-回應傳送配接器介面
傳送配接器使用與接收配接器相同的批次機制，將回應訊息提交回伺服器。  
  
> [!NOTE]
>  建議請求-回應配接器以非同步方式處理訊息。 如果配接器以同步方式處理訊息，會有訊息重複的風險。  
  
 傳送配接器必須實作下列介面，才能以請求-回應模式運作：  
  
- **IBTTransport**  
  
- **IBaseComponent**  
  
- **IBTTransportControl**  
  
- **IPersistPropertyBag**  
  
- **IBTTransmitter**  
  
- **IBTTransmitterBatch**並**IBTBatchTransmitter** （如果您是需要傳送批次處理）  
  
- **IBTBatchCallBack**  
  
  物件互動包含的步驟如下：  
  
1. 配接器傳送請求訊息之後，會接收到來自該目的地伺服器的回應訊息， 然後，便可從傳輸 Proxy 取得批次。  
  
2. 配接器新增至批次回應訊息，藉由呼叫**Submitresponsemessage**。  
  
3. 配接器提交批次，藉由呼叫**ibttransportproxy:: Done**傳入的指標，其**IBTBatchComplete**從傳訊引擎回呼介面。  
  
4. 傳訊引擎會呼叫的介面卡**ibtbatchcallback:: Batchcomplete**回呼方法，使用傳輸 proxy 通知它提交作業的結果。  
  
   下圖顯示建立請求-回應傳送配接器時所包含的物件互動。  
  
   ![](../core/media/ebiz-sdk-devadapter13.gif "ebiz_sdk_devadapter13")  
   請求-回應傳送配接器的互動圖表  
  
## <a name="see-also"></a>另請參閱  
 [配接器變數](../core/adapter-variables.md)   
 [開發傳送配接器](../core/developing-a-send-adapter.md)   
 [具現化並初始化傳送配接器](../core/instantiating-and-initializing-a-send-adapter.md)   
 [傳送配接器同步介面](../core/interfaces-for-a-synchronous-send-adapter.md)   
 [介面的非同步傳送配接器](../core/interfaces-for-an-asynchronous-send-adapter.md)   
 [同步批次支援傳送配接器介面](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md)   
 [非同步批次支援傳送配接器介面](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md)   
 [交易式非同步批次支援傳送配接器介面](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)