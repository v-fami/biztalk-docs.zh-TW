---
title: 接收配接器的交換模式。 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e505559e-66be-4c32-a2a8-a242cba10000
caps.latest.revision: 21
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc93f587e8d04e93e96a8e326abfcc68c51daf69
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37004815"
---
# <a name="exchange-patterns-for-receive-adapters"></a><span data-ttu-id="3eda6-102">接收配接器的交換模式</span><span class="sxs-lookup"><span data-stu-id="3eda6-102">Exchange Patterns for Receive Adapters</span></span>
<span data-ttu-id="3eda6-103">接收配接器會從「纜線」接收資料，然後當作訊息提交給 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3eda6-103">Receive adapters receive data from the "wire" and submit it as a message into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="3eda6-104">此提交流程可以是單向或雙向的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="3eda6-104">This submittal process can be a one-way or a two-way message exchange pattern.</span></span>  
  
## <a name="one-way-submit"></a><span data-ttu-id="3eda6-105">單向提交</span><span class="sxs-lookup"><span data-stu-id="3eda6-105">One-Way Submit</span></span>  
 <span data-ttu-id="3eda6-106">當接收配接器將訊息提交給 BizTalk 傳訊引擎時，首先需要建立新的 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="3eda6-106">For a receive adapter to submit a message into the BizTalk Messaging Engine, it first needs to create a new BizTalk message.</span></span> <span data-ttu-id="3eda6-107">IBaseMessage 主題的程式碼範例將告訴您怎麼進行。</span><span class="sxs-lookup"><span data-stu-id="3eda6-107">The code sample in the IBaseMessage topic shows how this is done.</span></span> <span data-ttu-id="3eda6-108">由配接器設為訊息內文的資料流一般來說應為 Forward-Only 資料流，意思是它不會對先前讀入記憶體的資料進行快取處理。</span><span class="sxs-lookup"><span data-stu-id="3eda6-108">The stream that the adapter sets as the message body should typically be a forward-only stream, meaning that it should not cache the data that it has previously read into memory.</span></span>  
  
 <span data-ttu-id="3eda6-109">配接器會將訊息提交至引擎之前，必須撰寫**InboundTransportLocation**訊息至 BizTalk 訊息的系統命名空間中的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="3eda6-109">Before the adapter submits the message into the engine, it must write the **InboundTransportLocation** message context property in the system namespace onto the BizTalk message.</span></span> <span data-ttu-id="3eda6-110">下列程式碼片段將說明這點：</span><span class="sxs-lookup"><span data-stu-id="3eda6-110">This is illustrated in the following code fragment:</span></span>  
  
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
  
 <span data-ttu-id="3eda6-111">此外，配接器也可以定義自己的屬性結構描述，並將與藉以接收訊息之結束點相關的訊息內容屬性寫入。</span><span class="sxs-lookup"><span data-stu-id="3eda6-111">In addition, the adapter may define its own property schemas and write message context properties pertaining to the endpoint over which it received the message.</span></span> <span data-ttu-id="3eda6-112">例如，HTTP 配接器可以將 HTTP 標頭寫入訊息內容，而 SMTP 接收器則可以將郵件主旨寫入訊息內容中。</span><span class="sxs-lookup"><span data-stu-id="3eda6-112">For example, an HTTP adapter might write the HTTP headers to the message context, and an SMTP receiver might write the subject of the mail to the message context.</span></span> <span data-ttu-id="3eda6-113">對於諸如管線元件、協調流程排程，或是傳送配接器等下游元件而言，這項資訊可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="3eda6-113">This information may be useful to downstream components such as pipeline components, orchestration schedules, or a send adapter.</span></span>  
  
 <span data-ttu-id="3eda6-114">當訊息準備好之後，就可以提交至「傳訊引擎」。</span><span class="sxs-lookup"><span data-stu-id="3eda6-114">After the messages are prepared, they can be submitted into the Messaging Engine.</span></span> <span data-ttu-id="3eda6-115">若要查看如何單向接收配接器可能會將訊息提交至引擎，請參閱程式碼範例[SubmitDirect （BizTalk Server 範例）](../core/submitdirect-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="3eda6-115">To see how a one-way receive adapter might submit a message into the engine, see the code sample [SubmitDirect (BizTalk Server Sample)](../core/submitdirect-biztalk-server-sample.md).</span></span>  
  
## <a name="request-response"></a><span data-ttu-id="3eda6-116">要求-回應</span><span class="sxs-lookup"><span data-stu-id="3eda6-116">Request-Response</span></span>  
 <span data-ttu-id="3eda6-117">雙向接收配接器一般是用在單向或雙向接收埠上。</span><span class="sxs-lookup"><span data-stu-id="3eda6-117">Two-way receive adapters are typically used on one-way or two-way receive ports.</span></span> <span data-ttu-id="3eda6-118">配接器藉由檢查 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 組態屬性包來決定所服務的接收位置為單向或雙向。</span><span class="sxs-lookup"><span data-stu-id="3eda6-118">The adapter determines whether the receive location it is servicing is a one-way or two-way port by inspecting the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration property bag.</span></span> <span data-ttu-id="3eda6-119">會說明此程序**IBTTransportConfig.AddReceiveEndpoint 方法 (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="3eda6-119">This process is explained in the **IBTTransportConfig.AddReceiveEndpoint Method (COM)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 <span data-ttu-id="3eda6-120">下列物件互動圖表說明執行「要求-回應」訊息交換的流程。</span><span class="sxs-lookup"><span data-stu-id="3eda6-120">The following object interaction diagram illustrates the process of performing a request-response message exchange.</span></span> <span data-ttu-id="3eda6-121">配接器向傳輸 proxy 要求新批次，並傳入其參考**IBTTransmitter**介面透過**SubmitRequestMessage**方法。</span><span class="sxs-lookup"><span data-stu-id="3eda6-121">The adapter requests a new batch from the transport proxy and passes in its reference to the **IBTTransmitter** interface through the **SubmitRequestMessage** method.</span></span> <span data-ttu-id="3eda6-122">傳訊引擎會提供回應訊息，此介面上的使用**TransmitMessage**方法。</span><span class="sxs-lookup"><span data-stu-id="3eda6-122">The Messaging Engine delivers the response message on this interface by using the **TransmitMessage** method.</span></span>  
  
 <span data-ttu-id="3eda6-123">由於引擎在處理訊息時並不同步，有可能會發生下列情況：</span><span class="sxs-lookup"><span data-stu-id="3eda6-123">Because the engine is processing messages asynchronously, it is possible for the following to happen:</span></span>  
  
- <span data-ttu-id="3eda6-124">**BatchComplete**回呼可能會發生在之前**完成**已傳回。</span><span class="sxs-lookup"><span data-stu-id="3eda6-124">The **BatchComplete** callback might occur before **Done** has returned.</span></span>  
  
- <span data-ttu-id="3eda6-125">對 TransmitMessage 的呼叫可能在 BatchComplete，甚至在 Done 傳回之前便已發生。</span><span class="sxs-lookup"><span data-stu-id="3eda6-125">The call to TransmitMessage might be made before BatchComplete and even before Done.</span></span>  
  
  <span data-ttu-id="3eda6-126">由於這兩種情況極為罕見，配接器應該避免這類事情發生。</span><span class="sxs-lookup"><span data-stu-id="3eda6-126">While both of these scenarios are rare, the adapter should protect itself against this.</span></span>  
  
  <span data-ttu-id="3eda6-127">我們建議您使用非同步且無法停止的呼叫來傳輸回應訊息。</span><span class="sxs-lookup"><span data-stu-id="3eda6-127">It is recommended that the response message is transmitted using an asynchronous non-blocking call.</span></span>  
  
  <span data-ttu-id="3eda6-128">BaseAdapter 專案具有公用程式類別， **StandardRequestResponseHandler**，封裝要求-回應語意，本主題所述。</span><span class="sxs-lookup"><span data-stu-id="3eda6-128">The BaseAdapter project has a utility class, **StandardRequestResponseHandler**, that encapsulates the request-response semantics explained in this topic.</span></span>  
  
## <a name="request-response-message-time-outs"></a><span data-ttu-id="3eda6-129">要求-回應訊息逾時</span><span class="sxs-lookup"><span data-stu-id="3eda6-129">Request-Response Message Time-Outs</span></span>  
 <span data-ttu-id="3eda6-130">當配接器提交的要求-回應訊息時，它必須在指定的要求訊息的逾時**IBTTransportBatch.SubmitRequestMessage 方法 (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="3eda6-130">When an adapter submits a request-request message, it needs to specify the time-out of the request message on the **IBTTransportBatch.SubmitRequestMessage Method (COM)** API [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="3eda6-131">回應訊息只有在不超出此逾時值時才會傳遞至配接器上。</span><span class="sxs-lookup"><span data-stu-id="3eda6-131">A response message will be delivered to the adapter only within this time-out period.</span></span> <span data-ttu-id="3eda6-132">一旦超出了逾時值，便會將負值通知 (NACK) 傳遞到配接器上，而非回應訊息。</span><span class="sxs-lookup"><span data-stu-id="3eda6-132">After the time-out expires, a negative acknowledgment (NACK) will be delivered to the adapter instead of the response message.</span></span> <span data-ttu-id="3eda6-133">如果配接器沒有指定逾時值，則引擎會使用預設的 20 分鐘逾時值。</span><span class="sxs-lookup"><span data-stu-id="3eda6-133">If the adapter does not specify a time-out value, the engine uses the default value of 20 minutes.</span></span>  
  
 <span data-ttu-id="3eda6-134">您可以透過使用下列登錄機碼來控制內含式接收配接器的預設「要求-回應」訊息逾時值：</span><span class="sxs-lookup"><span data-stu-id="3eda6-134">The default time-out for request-response messages may be controlled by using the following registry key for in-process receive adapters:</span></span>  
  
 <span data-ttu-id="3eda6-135">**DWORD**</span><span class="sxs-lookup"><span data-stu-id="3eda6-135">**DWORD**</span></span>  
  
 <span data-ttu-id="3eda6-136">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc {主機 Guid} \MessagingReqRespTTL**</span><span class="sxs-lookup"><span data-stu-id="3eda6-136">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc{Host Guid}\MessagingReqRespTTL**</span></span>  
  
 <span data-ttu-id="3eda6-137">外掛式接收配接器之登錄機碼位於不同的位置上：</span><span class="sxs-lookup"><span data-stu-id="3eda6-137">The registry key is in a different location for isolated receive adapters:</span></span>  
  
 <span data-ttu-id="3eda6-138">**DWORD**</span><span class="sxs-lookup"><span data-stu-id="3eda6-138">**DWORD**</span></span>  
  
 <span data-ttu-id="3eda6-139">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**</span><span class="sxs-lookup"><span data-stu-id="3eda6-139">**HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\BTSSvc.3.0\MessagingReqRespTTL**</span></span>  
  
 <span data-ttu-id="3eda6-140">NACK (負值通知，Negative ACKnowledgements) 是 SOAP 錯誤，有兩種處理的方法。</span><span class="sxs-lookup"><span data-stu-id="3eda6-140">NACKs (Negative ACKnowledgements) are SOAP faults and there are two ways to handle them.</span></span> <span data-ttu-id="3eda6-141">一般來說配接器會將 NACK 傳回用戶端，讓用戶端來處理 NACK。</span><span class="sxs-lookup"><span data-stu-id="3eda6-141">Typically the adapter returns the NACK to the client and the client handles the NACK.</span></span> <span data-ttu-id="3eda6-142">或者，可以設定負責處理回應訊息的傳輸管線，並使用對應或是自訂管線元件來變更回應訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="3eda6-142">Alternatively the transmit pipeline handling the response message may be configured to change the contents of the response message, by using either a map or a custom pipeline component.</span></span>