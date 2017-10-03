---
title: "SAP 配接器之 WCF 通道模型的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, overview
- WCF channel model, creating messages for the SAP adapter
ms.assetid: 6192d637-efac-4580-8880-b5bae9d16f31
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8083f7dc691010f4128b3ddb99729b0b2b1ebd1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-sap-adapter"></a><span data-ttu-id="e5e68-102">SAP 配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="e5e68-102">Overview of the WCF channel model with the SAP adapter</span></span>
<span data-ttu-id="e5e68-103">若要叫用 Rfc、 tRFCs 或 Bapi 上 SAP 系統，或傳送 IDOC 至 SAP 系統，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="e5e68-103">To invoke RFCs, tRFCs, or BAPIs on an SAP system, or to send IDOCS to an SAP system, your code acts as a WCF client and sends outbound operations to the adapter.</span></span> <span data-ttu-id="e5e68-104">在 WCF 通道模型中，您的程式碼會透過通道傳送的要求訊息叫用的介面卡上的作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-104">In the WCF channel model, your code invokes operations on the adapter by sending a request message over a channel.</span></span>  
  
 <span data-ttu-id="e5e68-105">若要做為 tRFC 或 RFC 伺服器到 SAP 系統，您的程式碼做為 WCF 服務的行為。</span><span class="sxs-lookup"><span data-stu-id="e5e68-105">To act as a tRFC or RFC server to an SAP system, your code behaves as a WCF service.</span></span> <span data-ttu-id="e5e68-106">也就是說，配接器會叫用在您的程式碼的輸入的作業 — 比方說，RFC 或 ReceiveIdoc 作業 （若要以字串格式，從 SAP 系統接收 IDOC）。</span><span class="sxs-lookup"><span data-stu-id="e5e68-106">That is, the adapter invokes an inbound operation on your code—for example, an RFC or the ReceiveIdoc operation (to receive an IDOC in string format from an SAP system).</span></span> <span data-ttu-id="e5e68-107">在此案例中，您的程式碼會透過配接器從通道接收作業的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="e5e68-107">In this scenario, your code receives a request message for the operation over a channel from the adapter.</span></span>  
  
 <span data-ttu-id="e5e68-108">本節中的主題提供使用概觀[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="e5e68-108">The topics in this section provide an overview of using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] with the WCF channel model.</span></span>  
  
## <a name="wcf-channel-model-overview"></a><span data-ttu-id="e5e68-109">WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="e5e68-109">WCF Channel Model Overview</span></span>  
 <span data-ttu-id="e5e68-110">用戶端和服務交換的 SOAP 訊息來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="e5e68-110">Clients and services communicate by exchanging SOAP messages.</span></span> <span data-ttu-id="e5e68-111">WCF 通道模型是低層級的抽象概念，這個訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e5e68-111">The WCF channel model is a low-level abstraction of this message exchange.</span></span> <span data-ttu-id="e5e68-112">它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。</span><span class="sxs-lookup"><span data-stu-id="e5e68-112">It provides interfaces and types that enable you to send and receive messages by using a layered protocol stack called a channel stack.</span></span> <span data-ttu-id="e5e68-113">堆疊的每個圖層由通道時，所組成，且每個通道會建立從 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="e5e68-113">Each layer of the stack is composed of a channel, and each channel is created from a WCF binding.</span></span> <span data-ttu-id="e5e68-114">最低層級是傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="e5e68-114">At the lowest layer is the transport channel.</span></span> <span data-ttu-id="e5e68-115">傳輸通道會實作服務的用戶端之間的基礎傳輸機制，並呈現較高的層級 （及最終使用的應用程式） 的每個訊息**System.ServiceModel.Message**。</span><span class="sxs-lookup"><span data-stu-id="e5e68-115">The transport channel implements the underlying transport mechanism between a service and a client and presents each message to the higher layers (and ultimately the consuming application) as a **System.ServiceModel.Message**.</span></span> <span data-ttu-id="e5e68-116">WCF**訊息**類別是抽象的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5e68-116">The WCF **Message** class is an abstraction of a SOAP message.</span></span> <span data-ttu-id="e5e68-117">WCF 提供數個通道介面，稱為通道形狀，建立模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。</span><span class="sxs-lookup"><span data-stu-id="e5e68-117">WCF provides several channel interfaces, called channel shapes, that model the basic SOAP message exchange patterns, such as request-reply or one-way.</span></span> <span data-ttu-id="e5e68-118">WCF 傳輸繫結提供實作的其中一個或多個更高層次的通道形狀可用來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e5e68-118">A WCF transport binding provides an implementation of one or more channel shapes that higher layers can use to send and receive messages.</span></span> <span data-ttu-id="e5e68-119">如需 WCF 通道模型的詳細資訊，請參閱[通道模型概觀](https://msdn.microsoft.com/library/ms729840.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e5e68-119">For more information about the WCF channel model, see [Channel Model Overview](https://msdn.microsoft.com/library/ms729840.aspx).</span></span>
  
 <span data-ttu-id="e5e68-120">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]是 WCF 自訂傳輸繫結會公開為 WCF 服務的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="e5e68-120">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is a WCF custom transport binding that exposes an SAP system as a WCF service.</span></span>  
  
## <a name="supported-channel-shapes-for-the-sap-adapter"></a><span data-ttu-id="e5e68-121">支援 SAP 配接器的通道形狀</span><span class="sxs-lookup"><span data-stu-id="e5e68-121">Supported Channel Shapes for the SAP Adapter</span></span>  
 <span data-ttu-id="e5e68-122">配接器實作下列的 WCF 通道形狀：</span><span class="sxs-lookup"><span data-stu-id="e5e68-122">The adapter implements the following WCF channel shapes:</span></span>  
  
-   <span data-ttu-id="e5e68-123">**IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。</span><span class="sxs-lookup"><span data-stu-id="e5e68-123">**IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**).</span></span> <span data-ttu-id="e5e68-124">**IRequestChannel**介面實作的用戶端的要求-回覆訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e5e68-124">The **IRequestChannel** interface implements the client side of a request-reply message exchange.</span></span> <span data-ttu-id="e5e68-125">您可以使用**IRequestChannel**執行作業，您想要取用的回應，例如若要叫用傳回的資料在 SAP 系統上的 RFC。</span><span class="sxs-lookup"><span data-stu-id="e5e68-125">You can use an **IRequestChannel** to perform operations for which you want to consume a response, for example to invoke an RFC on the SAP system that returns data.</span></span>  
  
-   <span data-ttu-id="e5e68-126">**IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。</span><span class="sxs-lookup"><span data-stu-id="e5e68-126">**IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**).</span></span> <span data-ttu-id="e5e68-127">此圖形會實作單向訊息交換的用戶端。</span><span class="sxs-lookup"><span data-stu-id="e5e68-127">This shape implements the client side of a one-way message exchange.</span></span> <span data-ttu-id="e5e68-128">您可以使用**IOutputChannel**叫用作業，您不需要使用的回應，例如若要叫用的 RFC，SAP 系統不會傳回任何資料。</span><span class="sxs-lookup"><span data-stu-id="e5e68-128">You can use an **IOutputChannel** to invoke an operation for which you do not need to consume a response, for example to invoke an RFC on the SAP system that does not return any data.</span></span>  
  
-   <span data-ttu-id="e5e68-129">**IReplyChannel** (**System.ServiceModel.Channels.IReplyChannel**)。</span><span class="sxs-lookup"><span data-stu-id="e5e68-129">**IReplyChannel** (**System.ServiceModel.Channels.IReplyChannel**).</span></span> <span data-ttu-id="e5e68-130">此圖形會實作服務端的要求-回覆訊息交換。</span><span class="sxs-lookup"><span data-stu-id="e5e68-130">This shape implements the service side of a request-reply message exchange.</span></span> <span data-ttu-id="e5e68-131">您可以使用**IReplyChannel**實作 RFC 或 tRFC 伺服器，或是從 SAP 系統接收 Idoc。</span><span class="sxs-lookup"><span data-stu-id="e5e68-131">You can use an **IReplyChannel** to implement an RFC or tRFC server or to receive IDOCs from a SAP system.</span></span>  
  
 <span data-ttu-id="e5e68-132">像任何 WCF 繫結，[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用以提供應用程式程式碼的通道處理站模式。</span><span class="sxs-lookup"><span data-stu-id="e5e68-132">Like any WCF binding, the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses a factory pattern to provide channels to application code.</span></span> <span data-ttu-id="e5e68-133">您使用**Microsoft.Adapters.SAPBinding**物件建立的執行個體：</span><span class="sxs-lookup"><span data-stu-id="e5e68-133">You use a **Microsoft.Adapters.SAPBinding** object to create instances of:</span></span>  
  
-   <span data-ttu-id="e5e68-134">**System.ServiceModel.ChannelFactory\<IRequestChannel >**提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-134">**System.ServiceModel.ChannelFactory\<IRequestChannel>** to provide **IRequestChannel** channels you can use to invoke request-response operations on the adapter.</span></span>  
  
-   <span data-ttu-id="e5e68-135">**System.ServiceModel.ChannelFactory\<IOutputChannel >**提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-135">**System.ServiceModel.ChannelFactory\<IOutputChannel>** to provide **IOutputChannel** channels you can use to invoke one-way operations on the adapter.</span></span>  
  
-   <span data-ttu-id="e5e68-136">**System.ServiceModel.IChannelListener\<IReplyChannel >**提供**IReplyChannel**通道可用來從配接器接收要求-回應作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-136">**System.ServiceModel.IChannelListener\<IReplyChannel>** to provide **IReplyChannel** channels you can use to receive request-response operations from the adapter.</span></span>  
  
## <a name="creating-messages-for-the-sap-adapter-in-the-wcf-channel-model"></a><span data-ttu-id="e5e68-137">SAP 配接器 WCF 通道模型中建立訊息</span><span class="sxs-lookup"><span data-stu-id="e5e68-137">Creating Messages for the SAP Adapter in the WCF Channel Model</span></span>  
 <span data-ttu-id="e5e68-138">在 WCF 中**System.ServiceModel.Channels.Message**類別會提供在記憶體中表示 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5e68-138">In WCF the **System.ServiceModel.Channels.Message** class provides an in memory representation of a SOAP message.</span></span> <span data-ttu-id="e5e68-139">您建立**訊息**叫用靜態執行個體**Message.Create**方法。</span><span class="sxs-lookup"><span data-stu-id="e5e68-139">You create a **Message** instance by invoking the static **Message.Create** method.</span></span>  
  
 <span data-ttu-id="e5e68-140">有兩個重要的部分 SOAP 訊息，您必須指定當您建構**訊息**將傳送至執行個體[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e5e68-140">There are two important parts to the SOAP message that you must specify when you construct a **Message** instance to send to the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
-   <span data-ttu-id="e5e68-141">訊息動作是 SOAP 訊息標頭的字串。</span><span class="sxs-lookup"><span data-stu-id="e5e68-141">The message action is a string that is part of the SOAP message header.</span></span> <span data-ttu-id="e5e68-142">訊息動作識別應該叫用作業[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e5e68-142">The message action identifies the operation that should be invoked on [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="e5e68-143">下列範例示範 SD_RFC_CUSTOMER_GET RFC，SAP 系統上叫用指定的訊息動作： `http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET`。</span><span class="sxs-lookup"><span data-stu-id="e5e68-143">The following shows the message action that is specified to invoke the SD_RFC_CUSTOMER_GET RFC on an SAP system: `http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET`.</span></span>  
  
-   <span data-ttu-id="e5e68-144">訊息內文包含作業的參數資料。</span><span class="sxs-lookup"><span data-stu-id="e5e68-144">The message body contains the parameter data for the operation.</span></span> <span data-ttu-id="e5e68-145">訊息本文由格式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]要求的作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-145">The message body is composed of well-formed XML that corresponds to the message schema expected by the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for the requested operation.</span></span> <span data-ttu-id="e5e68-146">下列的訊息本文會包含 SD_RFC_CUSTOMER_GET RFC，SAP 系統上的參數。</span><span class="sxs-lookup"><span data-stu-id="e5e68-146">The following message body contains the parameters for the SD_RFC_CUSTOMER_GET RFC on an SAP system.</span></span>  
  
    ```  
    <SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>  
    ```  
  
 <span data-ttu-id="e5e68-147">如需有關資訊[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e68-147">For information about the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] message schemas and message actions for operations, see [Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).</span></span>  
  
 <span data-ttu-id="e5e68-148">**Message.Create**方法多載，而且提供了許多不同的選項來提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="e5e68-148">The **Message.Create** method is overloaded and offers many different options for providing the message body.</span></span> <span data-ttu-id="e5e68-149">下列程式碼示範如何建立**訊息**所使用的執行個體**System.Xml.XmlReader**提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="e5e68-149">The following code shows how to create a **Message** instance by using an **System.Xml.XmlReader** to supply the message body.</span></span> <span data-ttu-id="e5e68-150">在此程式碼中，訊息本文會讀取字串常數。</span><span class="sxs-lookup"><span data-stu-id="e5e68-150">In this code, the message body is read from a string constant.</span></span>  
  
```  
//create an XML message to send to the SAP system  
//We are invoking the SD_RFC_CUSTOMER_GET RFC.  
//The XML below specifies that we want to search for customers with names starting with "AB"  
string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> \<KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
//create an XML reader from the input XML  
XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
//create a WCF message from the XML reader  
Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="e5e68-151">您必須提供中的訊息動作您**訊息**執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5e68-151">You must provide a message action in your **Message** instance.</span></span> <span data-ttu-id="e5e68-152">這通常是當**訊息**建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="e5e68-152">This is typically done when the **Message** instance is created.</span></span>  
  
## <a name="streaming-support-on-the-sap-adapter-in-the-wcf-channel-model"></a><span data-ttu-id="e5e68-153">在 SAP 中的配接器的 WCF 通道模型的資料流支援</span><span class="sxs-lookup"><span data-stu-id="e5e68-153">Streaming Support on the SAP Adapter in the WCF Channel Model</span></span>  
 <span data-ttu-id="e5e68-154">如何建立及取用您 SAP 配接器與交換的訊息會決定如何將訊息串流您的程式碼與配接器之間。</span><span class="sxs-lookup"><span data-stu-id="e5e68-154">How you create and consume the messages that you exchange with the SAP adapter determines how the message is streamed between your code and the adapter.</span></span>  
  
### <a name="node-streaming"></a><span data-ttu-id="e5e68-155">節點資料流</span><span class="sxs-lookup"><span data-stu-id="e5e68-155">Node streaming</span></span>  
 <span data-ttu-id="e5e68-156">節點資料流是唯一的層級的資料流支援除了 SendIdoc 和 ReceiveIdoc 作業以外的所有作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-156">Node streaming is the only level of streaming supported for all operations except the SendIdoc and ReceiveIdoc operations.</span></span>  
  
 <span data-ttu-id="e5e68-157">若要執行節點資料流處理訊息時，您：</span><span class="sxs-lookup"><span data-stu-id="e5e68-157">To perform node streaming for a message, you:</span></span>  
  
-   <span data-ttu-id="e5e68-158">建立外寄訊息使用**XmlReader**提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="e5e68-158">Create an outbound message using an **XmlReader** to supply the message body.</span></span>  
  
-   <span data-ttu-id="e5e68-159">使用內送的訊息使用**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="e5e68-159">Consume an inbound message using an **XmlReader**.</span></span> <span data-ttu-id="e5e68-160">您藉由呼叫取得讀取器**GetReaderAtBodyContents**方法在輸入**訊息**。</span><span class="sxs-lookup"><span data-stu-id="e5e68-160">You get the reader by calling the **GetReaderAtBodyContents** method on the inbound **Message**.</span></span>  
  
### <a name="node-value-streaming"></a><span data-ttu-id="e5e68-161">節點值的資料流</span><span class="sxs-lookup"><span data-stu-id="e5e68-161">Node-value Streaming</span></span>  
 <span data-ttu-id="e5e68-162">因為 SendIdoc 和 ReceiveIdoc 作業包含在字串中的單一 XML 節點下的 IDOC 資料 (\<idocData >)、 配接器支援節點值資料流處理這些作業。</span><span class="sxs-lookup"><span data-stu-id="e5e68-162">Because the SendIdoc and ReceiveIdoc operations contain the IDOC data in a string under a single XML node (\<idocData>), the adapter supports node-value streaming on these operations.</span></span>  
  
 <span data-ttu-id="e5e68-163">若要執行這些作業的資料流處理的節點值，您可以：</span><span class="sxs-lookup"><span data-stu-id="e5e68-163">To perform node-value streaming for these operations, you can:</span></span>  
  
-   <span data-ttu-id="e5e68-164">建立 SendIdoc 要求訊息 （輸出） 使用**BodyWriter**實作節點值來提供訊息內文資料流。</span><span class="sxs-lookup"><span data-stu-id="e5e68-164">Create the SendIdoc request message (outbound) using a **BodyWriter** that implements node-value streaming to supply the message body.</span></span>  
  
-   <span data-ttu-id="e5e68-165">使用 ReceiveIdoc 要求訊息 （輸入） 藉由呼叫**WriteBodyContents**方法在訊息與**XmlDictionaryWriter**實作節點值的資料流。</span><span class="sxs-lookup"><span data-stu-id="e5e68-165">Consume the ReceiveIdoc request message (inbound) by calling the **WriteBodyContents** method on the message with an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
 <span data-ttu-id="e5e68-166">如需串流處理使用 WCF 通道模型 （字串） 的一般檔案 Idoc 的詳細資訊，請參閱[SAP 使用 WCF 通道模型中的資料流處理一般檔案 Idoc](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e68-166">For more information about streaming flat file (string) IDOCs using the WCF channel model, see [Streaming Flat-File IDOCs in SAP using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e68-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e68-167">See Also</span></span>  
[<span data-ttu-id="e5e68-168">開發應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="e5e68-168">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)