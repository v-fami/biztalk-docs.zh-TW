---
title: 使用通知 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, publishing
- messages, acknowledgements
- BTS.AckSendPortID property
- BTS.AckSendPortName property
- BTS.AckType property
- BTS.AckFailureCode property
- BTS.AckID property
- acknowledgements, positive
- SOAP fault
- BTS.AckReceivePortID property
- BTS.AckReceivePortName property
- BTS.AckInboundTransportLocation property
- BTS.AckOutboundTransportLocation property
- messages, successful transmission
- BTS.AckDescription property
- orchestrations, messages
- acknowledgements, negative
- BTS.CorrelationToken property
- BTS.AckFailureCategory property
- positive acknowledgements (ACK)
- BTS.AckOwnerID property
ms.assetid: 2e5986d4-9633-4b7b-8ff3-fa3da93c5400
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fe568185bde471bea9396786e58c31ced960d23
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968183"
---
# <a name="using-acknowledgments"></a>使用通知
「BizTalk 傳訊引擎」會產生正值通知 (ACK) 和負值通知 (NACK)，以回應透過連接埠處理訊息期間發生的狀況。 BizTalk Server 發佈正值通知表示訊息傳輸成功，發佈負值通知表示訊息傳輸失敗與訊息擱置。  
  
## <a name="why-use-acknowledgments"></a>為什麼要使用通知？  
 正值和負值的通知提供強式回饋，您可以用來判斷訊息是否已送達目的地或在傳送途中發生一或多個問題。 例如在下列情況下，通知便非常有用：  
  
- 要監控新交易夥伴的接收埠之結構描述驗證和其他錯誤。  
  
- 若貸款要求已順利傳送給夥伴進行核准時，要將此要求已送出等待核准的狀態標示為「進行中」，或傳輸失敗時 (例如，夥伴的伺服器已停止) 要將狀態標示為「已失敗」。  
  
- 處理包含多個訂單的交換且要追蹤已傳輸或傳輸失敗的訂單數量。  
  
  您都可以使用通知和使用篩選的以內容為基礎之路由來完成這些情況。  
  
## <a name="routing-acknowledgments"></a>路由通知  
 發佈 ACK 或 NACK 時，引起 ACK/NACK 之訊息的所有訊息內容屬性都會被降級。 升級的任何屬性都不會流入通知。 路由傳送通知，建置使用的下列屬性篩選**BTS**命名空間：  
  
|屬性名稱|資料類型|描述|  
|-------------------|---------------|-----------------|  
|BTS.AckFailureCategory|xs:int|識別**ErrorCategory**，它提供位置和暫止原因。|  
|BTS.AckFailureCode|xs:string|識別**ErrorCode**，它提供位置和暫止原因。|  
|BTS.AckType|xs:string|正值通知的值為 ACK，負值通知的值為 NACK。|  
|BTS.AckID|xs:string|識別**MessageID**原始訊息。|  
|BTS.AckOwnerID|xs:string|識別原始訊息的執行個體識別碼。|  
|BTS.CorrelationToken|xs:string|識別原始訊息的相互關聯 Token (若有的話)。|  
|BTS.AckDescription|xs:string|識別**ErrorDescription**，它提供位置和暫止原因。|  
|BTS.AckSendPortID|xs:string|識別**SendPortID**原始訊息。|  
|BTS.AckSendPortName|xs:string|識別**SendPortName**原始訊息。|  
|BTS.AckOutboundTransportLocation|xs:string|識別**OutboundTransportLocation**原始訊息。|  
|BTS.AckReceivePortID|xs:string|識別**ReceivePortID**原始訊息。|  
|BTS.AckReceivePortName|xs:string|識別**ReceivePortName**原始訊息。|  
|BTS.AckInboundTransportLocation|xs:string|識別**InboundTransportLocation**原始訊息。|  
  
> [!NOTE]
>  ACK 中不會存在包含錯誤訊息的屬性，因為它們只是發出確定傳遞的信號。  
  
## <a name="negative-acknowledgment-message-body"></a>負值通知的訊息內文  
 內容屬性中包含許多正值或負值通知的相關重要資訊。 除了內容屬性以外，NACK 中也包含具有 SOAP 錯誤的訊息內文部分。 SOAP 錯誤的格式如下：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<SOAP:Envelope xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" SOAP:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
  <SOAP:Body>  
    <SOAP:Fault>  
      <faultcode>Microsoft BizTalk Server Negative Acknowledgment </faultcode>  
      <faultstring>An error occurred while processing the message, refer to the details section for more information </faultstring>  
      <faultactor>C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml</faultactor>  
      <detail>  
        <ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
          <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
          <ErrorCode>0xc0c01658</ErrorCode>  
          <ErrorCategory>0</ErrorCategory>  
          <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".  </ErrorDescription>  
        </ns0:NACK>  
      </detail>  
    </SOAP:Fault>  
  </SOAP:Body>  
</SOAP:Envelope>  
```  
  
 配接器引發的例外狀況訊息位於 ErrorDescription 項目的 [SOAP 詳細資料] 區段中。  
  
### <a name="accessing-the-message-body-from-an-orchestration"></a>從協調流程存取訊息內文  
 若您有一個協調流程連接埠要求傳遞通知，則傳輸失敗時擲出的 DeliveryFailureException 會從 NACK 訊息內文中包含的 SOAP 錯誤還原序列化。 若要從您的協調流程中存取例外狀況訊息字串，請將 DeliveryFailureException 轉換為 SoapException，然後存取 InnerXml，如下列程式碼所示：  
  
```  
// Cast the DeliveryFailureException to a SoapException…  
System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
//e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
//object type created in an Exception handler  
```  
  
 前面的程式碼範例傳回的 XML 片段應和下列類似：  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
  <ErrorCode>0xc0c01658</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".</ErrorDescription>  
</ns0:NACK>  
```  
  
## <a name="when-is-an-acknowledgment-published"></a>什麼時候發佈通知？  
 若至少有一個相符的訂閱，則正值 (ACK) 和負值 (NACK) 通知都會在失敗點發佈至 MessageBox 資料庫。 例如，若 BizTalk Server 找不到從接收埠讀取的訊息之相符結構描述，也沒有 NACK 訂閱，則擱置訊息 (若尚未啟用失敗訊息路由) 且不發佈 NACK。  
  
## <a name="see-also"></a>另請參閱  
 [錯誤處理](../core/error-handling.md)   
 [使用失敗的訊息路由](../core/using-failed-message-routing.md)