---
title: "Oracle E-business Suite 配接器的 WCF 通道模型概觀 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3afd2a97-5734-4c25-87a3-702d8461898b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d59965b4fe5a94ae29ac8459ef8b8d80999c1dc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="f804a-102">Oracle E-business Suite 配接器的 WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="f804a-102">Overview of the WCF channel model with the Oracle E-Business Suite adapter</span></span>
<span data-ttu-id="f804a-103">在叫用作業[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]，您的程式碼做為 WCF 用戶端，並將傳出作業傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="f804a-103">To invoke operations on the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], your code acts as a WCF client and sends outbound operations to the adapter.</span></span> <span data-ttu-id="f804a-104">在 WCF 通道模型中，您的程式碼會透過通道傳送的要求訊息叫用的介面卡上的作業。</span><span class="sxs-lookup"><span data-stu-id="f804a-104">In the WCF channel model, your code invokes operations on the adapter by sending a request message over a channel.</span></span>  
  
 <span data-ttu-id="f804a-105">要叫用傳入的作業，例如輪詢基礎資料變更使用接收訊息**輪詢**作業提供的配接器，您的程式碼做為 WCF 服務，並從配接器接收傳入的作業。</span><span class="sxs-lookup"><span data-stu-id="f804a-105">To invoke inbound operations, such as receiving polling-based data-changed messages using the **Poll** operation provided by the adapter, your code acts as a WCF service and receives the inbound operation from the adapter.</span></span> <span data-ttu-id="f804a-106">換句話說，您的程式碼會接收要求訊息從配接器透過通道。</span><span class="sxs-lookup"><span data-stu-id="f804a-106">In other words, your code receives a request message from the adapter over a channel.</span></span>  
  
 <span data-ttu-id="f804a-107">本節中的主題提供使用概觀[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="f804a-107">The topics in this section provide an overview of using the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] with the WCF channel model.</span></span>  
  
## <a name="wcf-channel-model-overview"></a><span data-ttu-id="f804a-108">WCF 通道模型概觀</span><span class="sxs-lookup"><span data-stu-id="f804a-108">WCF Channel Model Overview</span></span>  
 <span data-ttu-id="f804a-109">用戶端和服務交換的 SOAP 訊息來進行通訊。</span><span class="sxs-lookup"><span data-stu-id="f804a-109">Clients and services communicate by exchanging SOAP messages.</span></span> <span data-ttu-id="f804a-110">WCF 通道模型是低層級的抽象概念，這個訊息交換。</span><span class="sxs-lookup"><span data-stu-id="f804a-110">The WCF channel model is a low-level abstraction of this message exchange.</span></span> <span data-ttu-id="f804a-111">它提供介面和類型，可讓您傳送和接收訊息所使用的是稱為通道堆疊的多層式通訊協定堆疊。</span><span class="sxs-lookup"><span data-stu-id="f804a-111">It provides interfaces and types that enable you to send and receive messages by using a layered protocol stack called a channel stack.</span></span> <span data-ttu-id="f804a-112">堆疊的每個圖層由通道時，所組成，且每個通道會建立從 WCF 繫結。</span><span class="sxs-lookup"><span data-stu-id="f804a-112">Each layer of the stack is composed of a channel, and each channel is created from a WCF binding.</span></span> <span data-ttu-id="f804a-113">最低層級是傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="f804a-113">At the lowest layer is the transport channel.</span></span> <span data-ttu-id="f804a-114">傳輸通道會實作服務的用戶端之間的基礎傳輸機制，並呈現較高的層級 （及最終使用的應用程式） 的每個訊息**System.ServiceModel.Message**。</span><span class="sxs-lookup"><span data-stu-id="f804a-114">The transport channel implements the underlying transport mechanism between a service and a client and presents each message to the higher layers (and ultimately the consuming application) as a **System.ServiceModel.Message**.</span></span> <span data-ttu-id="f804a-115">WCF**訊息**類別是抽象的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="f804a-115">The WCF **Message** class is an abstraction of a SOAP message.</span></span> <span data-ttu-id="f804a-116">WCF 提供數個通道介面，稱為通道形狀，建立模型的基本 SOAP 訊息交換模式，例如要求-回覆或單向。</span><span class="sxs-lookup"><span data-stu-id="f804a-116">WCF provides several channel interfaces, called channel shapes, that model the basic SOAP message exchange patterns, such as request-reply or one-way.</span></span> <span data-ttu-id="f804a-117">WCF 傳輸繫結提供實作的其中一個或多個更高層次的通道形狀可用來傳送和接收訊息。</span><span class="sxs-lookup"><span data-stu-id="f804a-117">A WCF transport binding provides an implementation of one or more channel shapes that higher layers can use to send and receive messages.</span></span> <span data-ttu-id="f804a-118">WCF 通道模型的詳細資訊，請參閱 < 通道模型概觀 >，網址[http://go.microsoft.com/fwlink/?LinkId=82614](http://go.microsoft.com/fwlink/?LinkId=82614)。</span><span class="sxs-lookup"><span data-stu-id="f804a-118">For more information about the WCF channel model, see "Channel Model Overview" at [http://go.microsoft.com/fwlink/?LinkId=82614](http://go.microsoft.com/fwlink/?LinkId=82614).</span></span>  
  
 <span data-ttu-id="f804a-119">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]是 WCF 自訂傳輸繫結會公開為 WCF 服務的 Oracle E-business Suite 成品。</span><span class="sxs-lookup"><span data-stu-id="f804a-119">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is a WCF custom transport binding that exposes an Oracle E-Business Suite artifact as a WCF service.</span></span>  
  
## <a name="supported-channel-shapes-for-the-oracle-e-business-suite-adapter"></a><span data-ttu-id="f804a-120">支援 Oracle E-business Suite 配接器的通道形狀</span><span class="sxs-lookup"><span data-stu-id="f804a-120">Supported Channel Shapes for the Oracle E-Business Suite Adapter</span></span>  
 <span data-ttu-id="f804a-121">配接器實作下列的 WCF 通道形狀：</span><span class="sxs-lookup"><span data-stu-id="f804a-121">The adapter implements the following WCF channel shapes:</span></span>  
  
-   <span data-ttu-id="f804a-122">**IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**)。</span><span class="sxs-lookup"><span data-stu-id="f804a-122">**IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**).</span></span> <span data-ttu-id="f804a-123">**IRequestChannel**介面實作的用戶端的要求-回覆訊息交換。</span><span class="sxs-lookup"><span data-stu-id="f804a-123">The **IRequestChannel** interface implements the client side of a request-reply message exchange.</span></span> <span data-ttu-id="f804a-124">您可以使用**IRequestChannel**若要執行您要使用回應的作業，例如若要執行 SELECT 查詢介面資料表上。</span><span class="sxs-lookup"><span data-stu-id="f804a-124">You can use an **IRequestChannel** to perform operations for which you want to consume a response, for example to perform a SELECT query on an interface table.</span></span>  
  
-   <span data-ttu-id="f804a-125">**IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**)。</span><span class="sxs-lookup"><span data-stu-id="f804a-125">**IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**).</span></span> <span data-ttu-id="f804a-126">此圖形會實作單向訊息交換的用戶端。</span><span class="sxs-lookup"><span data-stu-id="f804a-126">This shape implements the client side of a one-way message exchange.</span></span> <span data-ttu-id="f804a-127">您可以使用**IOutputChannel**叫用作業，您不需要耗用的回應，例如若要呼叫的程序沒有 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="f804a-127">You can use an **IOutputChannel** to invoke an operation for which you do not need to consume a response, for example to call a procedure that has no OUT parameters.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="f804a-128">所有基礎呼叫配接器對 Oracle 用戶端為同步。</span><span class="sxs-lookup"><span data-stu-id="f804a-128">All underlying calls by the adapter to the Oracle client are synchronous.</span></span> <span data-ttu-id="f804a-129">這包括透過叫用作業的結果將會是 Oracle 用戶端呼叫**IOutputChannel**。</span><span class="sxs-lookup"><span data-stu-id="f804a-129">This includes calls to the Oracle client that are the result of operations invoked over an **IOutputChannel**.</span></span> <span data-ttu-id="f804a-130">當您使用**IOutputChannel**，配接器會捨棄對 Oracle 用戶端從收到的回應。</span><span class="sxs-lookup"><span data-stu-id="f804a-130">When you use an **IOutputChannel**, the adapter discards the response received from the Oracle client.</span></span>  
  
-   <span data-ttu-id="f804a-131">**IInputChannel** (**System.ServiceModel.Channels.IInputChannel**)。</span><span class="sxs-lookup"><span data-stu-id="f804a-131">**IInputChannel** (**System.ServiceModel.Channels.IInputChannel**).</span></span> <span data-ttu-id="f804a-132">此圖形會實作服務端的單向訊息交換。</span><span class="sxs-lookup"><span data-stu-id="f804a-132">This shape implements the service side of a one-way message exchange.</span></span> <span data-ttu-id="f804a-133">您使用**IInputChannel**從配接器接收內送的訊息。</span><span class="sxs-lookup"><span data-stu-id="f804a-133">You use an **IInputChannel** to receive inbound messages from the adapter.</span></span>  
  
 <span data-ttu-id="f804a-134">像任何 WCF 繫結，[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]用以提供應用程式程式碼的通道處理站模式。</span><span class="sxs-lookup"><span data-stu-id="f804a-134">Like any WCF binding, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] uses a factory pattern to provide channels to application code.</span></span> <span data-ttu-id="f804a-135">您使用**Microsoft.Adapters.OracleEBSBinding**物件建立的執行個體：</span><span class="sxs-lookup"><span data-stu-id="f804a-135">You use a **Microsoft.Adapters.OracleEBSBinding** object to create instances of:</span></span>  
  
-   <span data-ttu-id="f804a-136">**System.ServiceModel.ChannelFactory\<IRequestChannel >**提供**IRequestChannel**通道可用來叫用的介面卡上的要求-回應作業。</span><span class="sxs-lookup"><span data-stu-id="f804a-136">**System.ServiceModel.ChannelFactory\<IRequestChannel>** to provide **IRequestChannel** channels you can use to invoke request-response operations on the adapter.</span></span>  
  
-   <span data-ttu-id="f804a-137">**System.ServiceModel.ChannelFactory\<IOutputChannel >**提供**IOutputChannel**通道可用來叫用的介面卡上的單向作業。</span><span class="sxs-lookup"><span data-stu-id="f804a-137">**System.ServiceModel.ChannelFactory\<IOutputChannel>** to provide **IOutputChannel** channels you can use to invoke one-way operations on the adapter.</span></span>  
  
-   <span data-ttu-id="f804a-138">**System.ServiceModel.IChannelListener\<IInputChannel >**提供**IInputChannel**可用來從配接器接收內送的訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="f804a-138">**System.ServiceModel.IChannelListener\<IInputChannel>** to provide **IInputChannel** channels you can use to receive inbound messages from the adapter.</span></span>  
  
### <a name="creating-messages-for-the-oracle-enterprise-business-solution-in-the-wcf-channel-model"></a><span data-ttu-id="f804a-139">正在建立 「 訊息 Oracle Enterprise 商務解決方案中的 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="f804a-139">Creating Messages for the Oracle Enterprise Business Solution in the WCF Channel Model</span></span>  
 <span data-ttu-id="f804a-140">在 WCF 中**System.ServiceModel.Channels.Message**類別會提供在記憶體中表示 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="f804a-140">In WCF the **System.ServiceModel.Channels.Message** class provides an in memory representation of a SOAP message.</span></span> <span data-ttu-id="f804a-141">您建立**訊息**叫用靜態執行個體**Message.Create**方法。</span><span class="sxs-lookup"><span data-stu-id="f804a-141">You create a **Message** instance by invoking the static **Message.Create** method.</span></span>  
  
 <span data-ttu-id="f804a-142">有兩個重要的部分 SOAP 訊息，您必須指定當您建立**訊息**將傳送至執行個體[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f804a-142">There are two important parts to the SOAP message that you must specify when you create a **Message** instance to send to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
-   <span data-ttu-id="f804a-143">訊息動作是 SOAP 訊息標頭的字串。</span><span class="sxs-lookup"><span data-stu-id="f804a-143">The message action is a string that is part of the SOAP message header.</span></span> <span data-ttu-id="f804a-144">訊息動作識別 Oracle E-business suite 中叫用的作業。</span><span class="sxs-lookup"><span data-stu-id="f804a-144">The message action identifies the operation that should be invoked on the Oracle E-Business Suite.</span></span> <span data-ttu-id="f804a-145">下列範例示範叫用指定的訊息動作**客戶介面**下的並行程式**應收帳款**Oracle E-business Suite 中的應用程式： `ConcurrentPrograms/AR/RACUST`。</span><span class="sxs-lookup"><span data-stu-id="f804a-145">The following shows the message action specified to invoke the **Customer Interface** concurrent program under the **Receivables** application in Oracle E-Business Suite: `ConcurrentPrograms/AR/RACUST`.</span></span>  
  
-   <span data-ttu-id="f804a-146">訊息內文包含作業的參數資料。</span><span class="sxs-lookup"><span data-stu-id="f804a-146">The message body contains the parameter data for the operation.</span></span> <span data-ttu-id="f804a-147">訊息本文由格式正確對應至所預期的訊息結構描述的 XML 組成[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]要求的作業。</span><span class="sxs-lookup"><span data-stu-id="f804a-147">The message body is composed of well-formed XML that corresponds to the message schema expected by the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] for the requested operation.</span></span> <span data-ttu-id="f804a-148">下列的訊息本文指定要求訊息來叫用**客戶介面**並行處理程式。</span><span class="sxs-lookup"><span data-stu-id="f804a-148">The following message body specifies a request message to invoke the **Customer Interface** concurrent program.</span></span>  
  
    ```  
    <RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
      <Description>Customer Interface Program</Description>  
      <StartTime></StartTime>  
      <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
      <ORG_ID>203</ORG_ID>  
    </RACUST>  
  
    ```  
  
 <span data-ttu-id="f804a-149">如需有關資訊[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]訊息結構描述和訊息作業的動作，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle E-business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md)。</span><span class="sxs-lookup"><span data-stu-id="f804a-149">For information about the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] message schemas and message actions for operations, see [Messages and Message Schemas for BizTalk Adapter for Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).</span></span>  
  
 <span data-ttu-id="f804a-150">**建立**方法多載，而且提供了許多不同的選項來提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="f804a-150">The **Create** method is overloaded and offers many different options for providing the message body.</span></span> <span data-ttu-id="f804a-151">下列程式碼示範如何建立**訊息**所使用的執行個體**XmlReader**提供訊息內文。</span><span class="sxs-lookup"><span data-stu-id="f804a-151">The following code shows how to create a **Message** instance by using an **XmlReader** to supply the message body.</span></span> <span data-ttu-id="f804a-152">在此程式碼，是從檔案讀取訊息本文。</span><span class="sxs-lookup"><span data-stu-id="f804a-152">In this code, the message body is read from a file.</span></span>  
  
```  
XmlReader readerIn = XmlReader.Create("ConcProgRequest.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "ConcurrentPrograms/AR/RACUST",  
    readerIn);  
```  
  
 <span data-ttu-id="f804a-153">其中，ConProgRequest.xml 包含要求訊息。</span><span class="sxs-lookup"><span data-stu-id="f804a-153">where, ConProgRequest.xml contains the request message.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f804a-154">您必須提供中的訊息動作您**訊息**執行個體。</span><span class="sxs-lookup"><span data-stu-id="f804a-154">You must provide a message action in your **Message** instance.</span></span> <span data-ttu-id="f804a-155">這通常是當**訊息**建立執行個體。</span><span class="sxs-lookup"><span data-stu-id="f804a-155">This is typically done when the **Message** instance is created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f804a-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f804a-156">See Also</span></span>  
 [<span data-ttu-id="f804a-157">開發 Oracle E-business Suite 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="f804a-157">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)