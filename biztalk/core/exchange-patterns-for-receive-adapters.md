---
title: "交換模式的接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e505559e-66be-4c32-a2a8-a242cba10000
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cf8f36bb128d82a6d6b2e143320f89408f26680
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="exchange-patterns-for-receive-adapters"></a>接收配接器的交換模式
接收配接器會從「纜線」接收資料，然後當作訊息提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 此提交流程可以是單向或雙向的訊息交換模式。  
  
## <a name="one-way-submit"></a>單向提交  
 當接收配接器將訊息提交給 BizTalk 傳訊引擎時，首先需要建立新的 BizTalk 訊息。 IBaseMessage 主題的程式碼範例將告訴您怎麼進行。 由配接器設為訊息內文的資料流一般來說應為 Forward-Only 資料流，意思是它不會對先前讀入記憶體的資料進行快取處理。  
  
 配接器將訊息提交至引擎之前，必須撰寫**InboundTransportLocation**訊息至 BizTalk 訊息的系統命名空間中的內容屬性。 下列程式碼片段將說明這點：  
  
 `Assembly References:`  
  
 `Microsoft.XLANGs.BaseTypes.dll`  
  
 `Microsoft.BizTalk.Pipeline.dll`  
  
 `Microsoft.BizTalk.GlobalPropertySchemas.dll`  
  
```  
using Microsoft.BizTalk.Message.Interop;  
using Microsoft.XLANGs.BaseTypes;  
  
private static readonly PropertyBase InboundTransportLocationProp =   
new BTS.InboundTransportLocation();  
  
private void StampMsgCtxProps(  
IBaseMessage msg, string uri, string adapterType)  
{  
msg.Context.Write(  
 InboundTransportLocationProp.Name.Name,   
 InboundTransportLocationProperty.Name.Namespace,   
  uri);  
}  
```  
  
 此外，配接器也可以定義自己的屬性結構描述，並將與藉以接收訊息之結束點相關的訊息內容屬性寫入。 例如，HTTP 配接器可以將 HTTP 標頭寫入訊息內容，而 SMTP 接收器則可以將郵件主旨寫入訊息內容中。 對於諸如管線元件、協調流程排程，或是傳送配接器等下游元件而言，這項資訊可能會很有用。  
  
 當訊息準備好之後，就可以提交至「傳訊引擎」。 若要查看如何單向接收配接器可能會將訊息提交至引擎，請參閱程式碼範例[SubmitDirect （BizTalk Server 範例）](../core/submitdirect-biztalk-server-sample.md)。  
  
## <a name="request-response"></a>要求-回應  
 雙向接收配接器一般是用在單向或雙向接收埠上。 配接器藉由檢查 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態屬性包來決定所服務的接收位置為單向或雙向。 此程序中會說明**IBTTransportConfig.AddReceiveEndpoint 方法 (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
 下列物件互動圖表說明執行「要求-回應」訊息交換的流程。 配接器向傳輸 proxy 要求新批次，而其參考會傳入**IBTTransmitter**介面透過**SubmitRequestMessage**方法。 傳訊引擎會將此介面上的回應訊息傳遞使用**TransmitMessage**方法。  
  
 由於引擎在處理訊息時並不同步，有可能會發生下列情況：  
  
-   **BatchComplete**回呼可能會發生之前**完成**已傳回。  
  
-   對 TransmitMessage 的呼叫可能在 BatchComplete，甚至在 Done 傳回之前便已發生。  
  
 由於這兩種情況極為罕見，配接器應該避免這類事情發生。  
  
 我們建議您使用非同步且無法停止的呼叫來傳輸回應訊息。  
  
 BaseAdapter 專案具有公用程式類別， **StandardRequestResponseHandler**，會封裝這個主題所述的要求-回應語意。  
  
## <a name="request-response-message-time-outs"></a>要求-回應訊息逾時  
 當配接器提交要求-回應訊息時，需要指定要求訊息的逾時上**IBTTransportBatch.SubmitRequestMessage 方法 (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 回應訊息只有在不超出此逾時值時才會傳遞至配接器上。 一旦超出了逾時值，便會將負值通知 (NACK) 傳遞到配接器上，而非回應訊息。 如果配接器沒有指定逾時值，則引擎會使用預設的 20 分鐘逾時值。  
  
 您可以透過使用下列登錄機碼來控制內含式接收配接器的預設「要求-回應」訊息逾時值：  
  
 **DWORD**  
  
 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc {主機 Guid} \MessagingReqRespTTL**  
  
 外掛式接收配接器之登錄機碼位於不同的位置上：  
  
 **DWORD**  
  
 **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**  
  
 NACK (負值通知，Negative ACKnowledgements) 是 SOAP 錯誤，有兩種處理的方法。 一般來說配接器會將 NACK 傳回用戶端，讓用戶端來處理 NACK。 或者，可以設定負責處理回應訊息的傳輸管線，並使用對應或是自訂管線元件來變更回應訊息的內容。