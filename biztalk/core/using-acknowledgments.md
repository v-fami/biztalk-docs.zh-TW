---
title: "使用通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
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
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0c3a5363ee70a67c5882088af9fa3d2f4b805823
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-acknowledgments"></a><span data-ttu-id="9571c-102">使用通知</span><span class="sxs-lookup"><span data-stu-id="9571c-102">Using Acknowledgments</span></span>
<span data-ttu-id="9571c-103">「BizTalk 傳訊引擎」會產生正值通知 (ACK) 和負值通知 (NACK)，以回應透過連接埠處理訊息期間發生的狀況。</span><span class="sxs-lookup"><span data-stu-id="9571c-103">The BizTalk Messaging Engine generates positive acknowledgments (ACK) and negative acknowledgments (NACK) in response to conditions encountered during the processing of a message through a port.</span></span> <span data-ttu-id="9571c-104">BizTalk Server 發佈正值通知表示訊息傳輸成功，發佈負值通知表示訊息傳輸失敗與訊息擱置。</span><span class="sxs-lookup"><span data-stu-id="9571c-104">BizTalk Server publishes a positive acknowledgment to indicate successful transmission of a message and a negative acknowledgment to indicate transmission failure and suspension of a message.</span></span>  
  
## <a name="why-use-acknowledgments"></a><span data-ttu-id="9571c-105">為什麼要使用通知？</span><span class="sxs-lookup"><span data-stu-id="9571c-105">Why Use Acknowledgments?</span></span>  
 <span data-ttu-id="9571c-106">正值和負值的通知提供強式回饋，您可以用來判斷訊息是否已送達目的地或在傳送途中發生一或多個問題。</span><span class="sxs-lookup"><span data-stu-id="9571c-106">Positive and negative acknowledgments provide strong feedback that you can use to determine if a message arrived at its destination or encountered one or more problems along the way.</span></span> <span data-ttu-id="9571c-107">例如在下列情況下，通知便非常有用：</span><span class="sxs-lookup"><span data-stu-id="9571c-107">For example, acknowledgments are useful when:</span></span>  
  
-   <span data-ttu-id="9571c-108">要監控新交易夥伴的接收埠之結構描述驗證和其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="9571c-108">You want to monitor a receive port for a new trading partner for schema validation and other errors.</span></span>  
  
-   <span data-ttu-id="9571c-109">若貸款要求已順利傳送給夥伴進行核准時，要將此要求已送出等待核准的狀態標示為「進行中」，或傳輸失敗時 (例如，夥伴的伺服器已停止) 要將狀態標示為「已失敗」。</span><span class="sxs-lookup"><span data-stu-id="9571c-109">You want to mark the status of a loan request sent out for approval as "in process" if it is successfully sent to a partner for approval or "failed" if transmission fails (for example, if the partner's server is down).</span></span>  
  
-   <span data-ttu-id="9571c-110">處理包含多個訂單的交換且要追蹤已傳輸或傳輸失敗的訂單數量。</span><span class="sxs-lookup"><span data-stu-id="9571c-110">You process interchanges containing multiple purchase orders and want to track the number of orders that are transmitted or fail transmission.</span></span>  
  
 <span data-ttu-id="9571c-111">您都可以使用通知和使用篩選的以內容為基礎之路由來完成這些情況。</span><span class="sxs-lookup"><span data-stu-id="9571c-111">You can accomplish each of these scenarios by using acknowledgments and content-based routing that uses filters.</span></span>  
  
## <a name="routing-acknowledgments"></a><span data-ttu-id="9571c-112">路由通知</span><span class="sxs-lookup"><span data-stu-id="9571c-112">Routing Acknowledgments</span></span>  
 <span data-ttu-id="9571c-113">發佈 ACK 或 NACK 時，引起 ACK/NACK 之訊息的所有訊息內容屬性都會被降級。</span><span class="sxs-lookup"><span data-stu-id="9571c-113">When an ACK or NACK is published, all of the message context properties from the message that caused the ACK/NACK are demoted.</span></span> <span data-ttu-id="9571c-114">升級的任何屬性都不會流入通知。</span><span class="sxs-lookup"><span data-stu-id="9571c-114">Any properties that were promoted do not flow to the acknowledgment.</span></span> <span data-ttu-id="9571c-115">路由通知，以建置篩選條件使用的下列屬性**BTS**命名空間：</span><span class="sxs-lookup"><span data-stu-id="9571c-115">To route an acknowledgment, build a filter using the following properties from the **BTS** namespace:</span></span>  
  
|<span data-ttu-id="9571c-116">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="9571c-116">Property name</span></span>|<span data-ttu-id="9571c-117">資料類型</span><span class="sxs-lookup"><span data-stu-id="9571c-117">Data type</span></span>|<span data-ttu-id="9571c-118">Description</span><span class="sxs-lookup"><span data-stu-id="9571c-118">Description</span></span>|  
|-------------------|---------------|-----------------|  
|<span data-ttu-id="9571c-119">BTS.AckFailureCategory</span><span class="sxs-lookup"><span data-stu-id="9571c-119">BTS.AckFailureCategory</span></span>|<span data-ttu-id="9571c-120">xs:int</span><span class="sxs-lookup"><span data-stu-id="9571c-120">xs:int</span></span>|<span data-ttu-id="9571c-121">識別**ErrorCategory**，可讓和暫止的原因。</span><span class="sxs-lookup"><span data-stu-id="9571c-121">Identifies the **ErrorCategory**, which gives the place and reason for the suspension.</span></span>|  
|<span data-ttu-id="9571c-122">BTS.AckFailureCode</span><span class="sxs-lookup"><span data-stu-id="9571c-122">BTS.AckFailureCode</span></span>|<span data-ttu-id="9571c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-123">xs:string</span></span>|<span data-ttu-id="9571c-124">識別**ErrorCode**，可讓和暫止的原因。</span><span class="sxs-lookup"><span data-stu-id="9571c-124">Identifies the **ErrorCode**, which gives the place and reason for the suspension.</span></span>|  
|<span data-ttu-id="9571c-125">BTS.AckType</span><span class="sxs-lookup"><span data-stu-id="9571c-125">BTS.AckType</span></span>|<span data-ttu-id="9571c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-126">xs:string</span></span>|<span data-ttu-id="9571c-127">正值通知的值為 ACK，負值通知的值為 NACK。</span><span class="sxs-lookup"><span data-stu-id="9571c-127">Value is ACK for a positive acknowledgment and NACK for a negative acknowledgment.</span></span>|  
|<span data-ttu-id="9571c-128">BTS.AckID</span><span class="sxs-lookup"><span data-stu-id="9571c-128">BTS.AckID</span></span>|<span data-ttu-id="9571c-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-129">xs:string</span></span>|<span data-ttu-id="9571c-130">識別**MessageID**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-130">Identifies the **MessageID** of the original message.</span></span>|  
|<span data-ttu-id="9571c-131">BTS.AckOwnerID</span><span class="sxs-lookup"><span data-stu-id="9571c-131">BTS.AckOwnerID</span></span>|<span data-ttu-id="9571c-132">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-132">xs:string</span></span>|<span data-ttu-id="9571c-133">識別原始訊息的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="9571c-133">Identifies the instance ID from the original message.</span></span>|  
|<span data-ttu-id="9571c-134">BTS.CorrelationToken</span><span class="sxs-lookup"><span data-stu-id="9571c-134">BTS.CorrelationToken</span></span>|<span data-ttu-id="9571c-135">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-135">xs:string</span></span>|<span data-ttu-id="9571c-136">識別原始訊息的相互關聯 Token (若有的話)。</span><span class="sxs-lookup"><span data-stu-id="9571c-136">Identifies the correlation token from the original message if one is present.</span></span>|  
|<span data-ttu-id="9571c-137">BTS.AckDescription</span><span class="sxs-lookup"><span data-stu-id="9571c-137">BTS.AckDescription</span></span>|<span data-ttu-id="9571c-138">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-138">xs:string</span></span>|<span data-ttu-id="9571c-139">識別**ErrorDescription**，可讓和暫止的原因。</span><span class="sxs-lookup"><span data-stu-id="9571c-139">Identifies the **ErrorDescription**, which gives the place and reason for the suspension.</span></span>|  
|<span data-ttu-id="9571c-140">BTS.AckSendPortID</span><span class="sxs-lookup"><span data-stu-id="9571c-140">BTS.AckSendPortID</span></span>|<span data-ttu-id="9571c-141">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-141">xs:string</span></span>|<span data-ttu-id="9571c-142">識別**SendPortID**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-142">Identifies the **SendPortID** from the original message.</span></span>|  
|<span data-ttu-id="9571c-143">BTS.AckSendPortName</span><span class="sxs-lookup"><span data-stu-id="9571c-143">BTS.AckSendPortName</span></span>|<span data-ttu-id="9571c-144">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-144">xs:string</span></span>|<span data-ttu-id="9571c-145">識別**SendPortName**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-145">Identifies the **SendPortName** from the original message.</span></span>|  
|<span data-ttu-id="9571c-146">BTS.AckOutboundTransportLocation</span><span class="sxs-lookup"><span data-stu-id="9571c-146">BTS.AckOutboundTransportLocation</span></span>|<span data-ttu-id="9571c-147">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-147">xs:string</span></span>|<span data-ttu-id="9571c-148">識別**OutboundTransportLocation**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-148">Identifies the **OutboundTransportLocation** from the original message.</span></span>|  
|<span data-ttu-id="9571c-149">BTS.AckReceivePortID</span><span class="sxs-lookup"><span data-stu-id="9571c-149">BTS.AckReceivePortID</span></span>|<span data-ttu-id="9571c-150">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-150">xs:string</span></span>|<span data-ttu-id="9571c-151">識別**ReceivePortID**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-151">Identifies the **ReceivePortID** from the original message.</span></span>|  
|<span data-ttu-id="9571c-152">BTS.AckReceivePortName</span><span class="sxs-lookup"><span data-stu-id="9571c-152">BTS.AckReceivePortName</span></span>|<span data-ttu-id="9571c-153">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-153">xs:string</span></span>|<span data-ttu-id="9571c-154">識別**ReceivePortName**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-154">Identifies the **ReceivePortName** from the original message.</span></span>|  
|<span data-ttu-id="9571c-155">BTS.AckInboundTransportLocation</span><span class="sxs-lookup"><span data-stu-id="9571c-155">BTS.AckInboundTransportLocation</span></span>|<span data-ttu-id="9571c-156">xs:string</span><span class="sxs-lookup"><span data-stu-id="9571c-156">xs:string</span></span>|<span data-ttu-id="9571c-157">識別**InboundTransportLocation**原始訊息。</span><span class="sxs-lookup"><span data-stu-id="9571c-157">Identifies the **InboundTransportLocation** from the original message.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9571c-158">ACK 中不會存在包含錯誤訊息的屬性，因為它們只是發出確定傳遞的信號。</span><span class="sxs-lookup"><span data-stu-id="9571c-158">The properties that contain error information are not present in ACKs because they signal a positive delivery.</span></span>  
  
## <a name="negative-acknowledgment-message-body"></a><span data-ttu-id="9571c-159">負值通知的訊息內文</span><span class="sxs-lookup"><span data-stu-id="9571c-159">Negative Acknowledgment Message Body</span></span>  
 <span data-ttu-id="9571c-160">內容屬性中包含許多正值或負值通知的相關重要資訊。</span><span class="sxs-lookup"><span data-stu-id="9571c-160">Much of the important information about a positive or negative acknowledgment is contained in the context properties.</span></span> <span data-ttu-id="9571c-161">除了內容屬性以外，NACK 中也包含具有 SOAP 錯誤的訊息內文部分。</span><span class="sxs-lookup"><span data-stu-id="9571c-161">In addition to the context properties, NACKs also contain a message body part containing a SOAP fault.</span></span> <span data-ttu-id="9571c-162">SOAP 錯誤的格式如下：</span><span class="sxs-lookup"><span data-stu-id="9571c-162">The format of the SOAP fault is as follows:</span></span>  
  
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
  
 <span data-ttu-id="9571c-163">配接器引發的例外狀況訊息位於 ErrorDescription 項目的 [SOAP 詳細資料] 區段中。</span><span class="sxs-lookup"><span data-stu-id="9571c-163">The exception message raised by the adapter is in the SOAP Detail section in the ErrorDescription element.</span></span>  
  
### <a name="accessing-the-message-body-from-an-orchestration"></a><span data-ttu-id="9571c-164">從協調流程存取訊息內文</span><span class="sxs-lookup"><span data-stu-id="9571c-164">Accessing the Message Body from an Orchestration</span></span>  
 <span data-ttu-id="9571c-165">若您有一個協調流程連接埠要求傳遞通知，則傳輸失敗時擲出的 DeliveryFailureException 會從 NACK 訊息內文中包含的 SOAP 錯誤還原序列化。</span><span class="sxs-lookup"><span data-stu-id="9571c-165">If you have an orchestration port that requires delivery notification, the DeliveryFailureException that is thrown on a transmission failure is deserialized from the SOAP fault that is contained in the NACK message body.</span></span> <span data-ttu-id="9571c-166">若要從您的協調流程中存取例外狀況訊息字串，請將 DeliveryFailureException 轉換為 SoapException，然後存取 InnerXml，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="9571c-166">To access the exception message string from within your orchestration, cast the DeliveryFailureException to a SoapException and then access the InnerXml as shown in the following code:</span></span>  
  
```  
// Cast the DeliveryFailureException to a SoapException…  
System.Web.Services.Protocols.SoapException se = (System.Web.Services.Protocols.SoapException)e.InnerException;  
System.Diagnostics.Trace.WriteLine(se.Detail.InnerXml);  
//e is an Microsoft.XLANGs.BaseTypes.DeliveryFailureException  
//object type created in an Exception handler  
```  
  
 <span data-ttu-id="9571c-167">前面的程式碼範例傳回的 XML 片段應和下列類似：</span><span class="sxs-lookup"><span data-stu-id="9571c-167">The preceding code sample returns an XML fragment similar to the following:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<ns0:NACK Type="NACK" xmlns:ns0="http://schema.microsoft.com/BizTalk/2003/NACKMessage.xsd">  
  <NAckID>{FFB1A60B-E593-4620-8897-4E9C7030A937}</NAckID>  
  <ErrorCode>0xc0c01658</ErrorCode>  
  <ErrorCategory>0</ErrorCategory>  
  <ErrorDescription>There was a failure executing the send pipeline: "Microsoft.BizTalk.DefaultPipelines.XMLTransmit, Microsoft.BizTalk.DefaultPipelines, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" Source: "XML assembler" Send Port: "Failed Message" URI: "C:\Projects\Sample\Locations\Response\FM_%MessageID%.xml" Reason: This Assembler cannot retrieve a document specification using this type: "http://Sample#Unknown".</ErrorDescription>  
</ns0:NACK>  
```  
  
## <a name="when-is-an-acknowledgment-published"></a><span data-ttu-id="9571c-168">什麼時候發佈通知？</span><span class="sxs-lookup"><span data-stu-id="9571c-168">When Is an Acknowledgment Published?</span></span>  
 <span data-ttu-id="9571c-169">若至少有一個相符的訂閱，則正值 (ACK) 和負值 (NACK) 通知都會在失敗點發佈至 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="9571c-169">Both positive (ACK) and negative (NACK) acknowledgments are published to the MessageBox database at the point of failure provided there is at least one matching subscription.</span></span> <span data-ttu-id="9571c-170">例如，若 BizTalk Server 找不到從接收埠讀取的訊息之相符結構描述，也沒有 NACK 訂閱，則擱置訊息 (若尚未啟用失敗訊息路由) 且不發佈 NACK。</span><span class="sxs-lookup"><span data-stu-id="9571c-170">For example, if BizTalk Server cannot find a matching schema for a message read from a receive port and there are no NACK subscriptions, it suspends the message (if failed message routing has not been enabled) and does not publish a NACK</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9571c-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9571c-171">See Also</span></span>  
 <span data-ttu-id="9571c-172">[錯誤處理](../core/error-handling.md) </span><span class="sxs-lookup"><span data-stu-id="9571c-172">[Error Handling](../core/error-handling.md) </span></span>  
 [<span data-ttu-id="9571c-173">使用失敗的訊息路由</span><span class="sxs-lookup"><span data-stu-id="9571c-173">Using Failed Message Routing</span></span>](../core/using-failed-message-routing.md)