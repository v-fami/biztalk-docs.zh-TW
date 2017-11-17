---
title: "最佳化管線效能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5137747-0dcf-4c96-90a7-01afb92f56a6
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4311efd0d23e29b63f02fc34b1650a894d29d335
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-pipeline-performance"></a><span data-ttu-id="60fcd-102">將管線效能最佳化</span><span class="sxs-lookup"><span data-stu-id="60fcd-102">Optimizing Pipeline Performance</span></span>
<span data-ttu-id="60fcd-103">本主題描述的管線中的效能最佳化的指導方針[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="60fcd-103">This topic describes guidelines for optimizing performance of pipelines in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
## <a name="best-practices-for-optimizing-performance-of-biztalk-server-pipelines"></a><span data-ttu-id="60fcd-104">最佳化效能的 BizTalk Server 管線的最佳作法</span><span class="sxs-lookup"><span data-stu-id="60fcd-104">Best practices for optimizing performance of BizTalk Server pipelines</span></span>  
  
1.  <span data-ttu-id="60fcd-105">因為管線元件對效能有顯著的影響 （例如，通過管線元件會執行 XML 組合器/解譯器管線元件優於最多 30%），請務必執行任何自訂管線元件以最佳方式，才能在您的部署中執行。</span><span class="sxs-lookup"><span data-stu-id="60fcd-105">Because pipeline components have a significant impact on performance (for example, a pass-through pipeline component performs up to 30 percent better than an XML assembler/disassembler pipeline component), make sure that any custom pipeline components perform optimally before implementing them in your deployment.</span></span> <span data-ttu-id="60fcd-106">如果您想要最大化 BizTalk 應用程式的整體效能，最小化您的自訂管線中的管線元件的數目。</span><span class="sxs-lookup"><span data-stu-id="60fcd-106">Minimize the number of pipeline components in your custom pipelines if you want to maximize the overall performance of your BizTalk application.</span></span>  
  
2.  <span data-ttu-id="60fcd-107">您也可以改善整體效能降低管線元件中的訊息持續性頻率和透過編碼自己的元件備援性降到最低。</span><span class="sxs-lookup"><span data-stu-id="60fcd-107">You also can improve overall performance by reducing the message persistence frequency in your pipeline component and by coding your component to minimize redundancy.</span></span> <span data-ttu-id="60fcd-108">每個自訂組件和特別的成品，可能會中斷與自訂追蹤元件，相同的效能，應該測試個別狀況負載過重，系統會使用完整的容量時，觀察其行為並找出任何可能的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="60fcd-108">Every custom assembly and in particular artifacts that could potentially disrupt performance, like custom tracking components, should be tested separately under heavy load condition to observe their behavior when the system is working at full capacity and to find any possible bottlenecks.</span></span>  
  
3.  <span data-ttu-id="60fcd-109">如果您要讀取的輸入的訊息內的管線元件，請避免整個文件載入記憶體使用**XmlDocument**物件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-109">If you need to read the inbound message inside a pipeline component, avoid loading the entire document into memory using an **XmlDocument** object.</span></span> <span data-ttu-id="60fcd-110">執行個體所需的空間數量**XmlDocument**類別來載入及建立記憶體中表示的 XML 文件是實際的訊息大小的 10 倍。</span><span class="sxs-lookup"><span data-stu-id="60fcd-110">The amount of space required by an instance of the **XmlDocument** class to load and create an in-memory representation of a XML document is up to 10 times the actual message size.</span></span> <span data-ttu-id="60fcd-111">若要讀取訊息，您應該使用**XmlTextReader**以及下列類別的執行個體的物件：</span><span class="sxs-lookup"><span data-stu-id="60fcd-111">In order to read a message, you should use an **XmlTextReader** object along with an instance of the following classes:</span></span>  
  
    -   <span data-ttu-id="60fcd-112">**VirtualStream (Microsoft.BizTalk.Streaming.dll)** -這個類別的原始程式碼位於管線 SDK 下的兩個位置，如下所示： SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。</span><span class="sxs-lookup"><span data-stu-id="60fcd-112">**VirtualStream (Microsoft.BizTalk.Streaming.dll)** - The source code for this class is located in two locations under the Pipelines SDK as follows: SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler and SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.</span></span>  
  
    -   <span data-ttu-id="60fcd-113">**ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**。</span><span class="sxs-lookup"><span data-stu-id="60fcd-113">**ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**.</span></span>  
  
    -   <span data-ttu-id="60fcd-114">**SeekAbleReadOnlyStream** -這個類別的原始程式碼位於管線 SDK 下的兩個位置，如下所示： SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。</span><span class="sxs-lookup"><span data-stu-id="60fcd-114">**SeekAbleReadOnlyStream** - The source code for this class is located in two locations under the Pipelines SDK as follows: SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler and SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm.</span></span>  
  
4.  <span data-ttu-id="60fcd-115">使用 PassThruReceive 管線和 PassThruTransmit 標準管線盡可能。</span><span class="sxs-lookup"><span data-stu-id="60fcd-115">Use the PassThruReceive and the PassThruTransmit standard pipelines whenever possible.</span></span> <span data-ttu-id="60fcd-116">它們不包含任何管線元件，且不會執行任何處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="60fcd-116">They do not contain any pipeline component and do not perform any processing of the message.</span></span> <span data-ttu-id="60fcd-117">基於這個理由，他們可以確保在接收或傳送訊息的最大效能。</span><span class="sxs-lookup"><span data-stu-id="60fcd-117">For this reason, they ensure maximum performance in receiving or sending messages.</span></span> <span data-ttu-id="60fcd-118">如果您要將二進位文件發佈到 BizTalk MessageBox 和 PassThruTransmit 管線的傳送埠上，如果您需要傳送出二進位訊息，您可以使用 PassThruReceive 管線的接收位置上。</span><span class="sxs-lookup"><span data-stu-id="60fcd-118">You can use a PassThruReceive pipeline on a receive location if you need to publish a binary document to the BizTalk MessageBox and a PassThruTransmit pipeline on a send port if you need to send out a binary message.</span></span> <span data-ttu-id="60fcd-119">您也可以在繫結至協調流程，如果訊息已格式化，並已準備好要傳送的實體傳送埠上使用 PassThruTransmit 管線。</span><span class="sxs-lookup"><span data-stu-id="60fcd-119">You can also use the PassThruTransmit pipeline on a physical send port bound to an orchestration if the message has been formatted and is ready to be transmitted.</span></span> <span data-ttu-id="60fcd-120">您必須使用不同的方式，如果您需要完成下列動作之一：</span><span class="sxs-lookup"><span data-stu-id="60fcd-120">You will need to use a different approach if you need to accomplish one of the following actions:</span></span>  
  
    -   <span data-ttu-id="60fcd-121">升級屬性輸入的 XML 或一般檔案訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="60fcd-121">Promote properties on the context of an inbound XML or Flat File message.</span></span>  
  
    -   <span data-ttu-id="60fcd-122">適用於接收位置內的對應。</span><span class="sxs-lookup"><span data-stu-id="60fcd-122">Apply a map inside a receive location.</span></span>  
  
    -   <span data-ttu-id="60fcd-123">適用於訂閱的訊息的協調流程中的對應。</span><span class="sxs-lookup"><span data-stu-id="60fcd-123">Apply a map in an orchestration that subscribes to a message.</span></span>  
  
    -   <span data-ttu-id="60fcd-124">套用訂閱了訊息的傳送埠上的對應。</span><span class="sxs-lookup"><span data-stu-id="60fcd-124">Apply a map on a send port that subscribes to a message.</span></span>  
  
     <span data-ttu-id="60fcd-125">若要完成其中一個動作，您必須探查和探索文件類型的接收管線內並指派 MessageType 內容屬性 （命名空間 #root 名稱） 值。</span><span class="sxs-lookup"><span data-stu-id="60fcd-125">To accomplish one of these actions, you must probe and discover the document type inside the receive pipeline and assign the (namespace#root-name) value to the MessageType context property.</span></span> <span data-ttu-id="60fcd-126">這項作業通常被透過解譯器元件，例如 Xml 解譯器元件 (XmlDasmComp) 或一般檔案解譯器元件 (FFDasmComp)。</span><span class="sxs-lookup"><span data-stu-id="60fcd-126">This operation is typically accomplished by a disassembler component such as the Xml Disassembler component (XmlDasmComp) or the Flat File disassembler component (FFDasmComp).</span></span> <span data-ttu-id="60fcd-127">在此情況下，您需要使用標準 （比方說，XmlReceive 管線） 或自訂管線，其中包含標準或自訂解譯器元件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-127">In this case, you need to use a standard (for instance, XmlReceive pipeline) or a custom pipeline that contains a standard or a custom disassembler component.</span></span>  
  
5.  <span data-ttu-id="60fcd-128">取得資源越好並發行這些儘早越好。</span><span class="sxs-lookup"><span data-stu-id="60fcd-128">Acquire resources as late as possible and release them as early as possible.</span></span> <span data-ttu-id="60fcd-129">比方說，如果您要在資料庫上存取資料，請開啟連接晚盡可能並儘快將它關閉。</span><span class="sxs-lookup"><span data-stu-id="60fcd-129">For example, if you need to access data on a database, open the connection as late as possible and close it as soon as possible.</span></span> <span data-ttu-id="60fcd-130">使用 C# using 陳述式隱含地發行可處置的物件或 finally 區塊的 catch-try-finally 陳述式來明確處置物件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-130">Use the C# using statement to implicitly release disposable objects or the finally block of a try-catch-finally statement to explicitly dispose your objects.</span></span> <span data-ttu-id="60fcd-131">檢測您的原始程式碼，以便輕鬆地偵錯您的元件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-131">Instrument your source code to make your components simple to debug.</span></span>  
  
6.  <span data-ttu-id="60fcd-132">排除任何您並非絕對必要，以加速處理訊息的管線元件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-132">Eliminate any components from your pipelines that are not strictly required to speed up message processing.</span></span>  
  
7.  <span data-ttu-id="60fcd-133">內接收管線中，您應該在只有在訊息路由 （協調流程、 傳送埠） 或降級的訊息內容屬性 （傳送埠） 必須升級至訊息內容的項目。</span><span class="sxs-lookup"><span data-stu-id="60fcd-133">Inside a receive pipeline, you should promote items to the message context only if you need them for message routing (Orchestrations, Send Ports) or demotion of message context properties (Send Ports).</span></span>  
  
8.  <span data-ttu-id="60fcd-134">如果您需要以納入中繼資料訊息，而且您不使用中繼資料的輸入路由或降級的目的，使用**IBaseMessageContext.Write**方法，而非**IBaseMessageContext.Promote**方法。</span><span class="sxs-lookup"><span data-stu-id="60fcd-134">If you need to include metadata with a message, and you don't use the metadata for routing or demotion purposes, use the **IBaseMessageContext.Write** method instead of the **IBaseMessageContext.Promote** method.</span></span>  
  
9. <span data-ttu-id="60fcd-135">如果您要使用 XPath 運算式的訊息中擷取資訊，請避免整個文件載入記憶體使用**XmlDocument**物件只是為了使用**SelectNodes**或**SelectSingleNode**方法。</span><span class="sxs-lookup"><span data-stu-id="60fcd-135">If you need to extract information from a message using an XPath expression, avoid loading the entire document into memory using an **XmlDocument** object just to use the **SelectNodes** or **SelectSingleNode** methods.</span></span> <span data-ttu-id="60fcd-136">或者，使用中所述的技巧[最佳化記憶體使用量與 Streaming](../technical-guides/optimizing-memory-usage-with-streaming.md)。</span><span class="sxs-lookup"><span data-stu-id="60fcd-136">Alternatively, use the techniques described in [Optimizing Memory Usage with Streaming](../technical-guides/optimizing-memory-usage-with-streaming.md).</span></span>  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-pipelines"></a><span data-ttu-id="60fcd-137">使用資料流載入在管線中的訊息時所需的記憶體使用量降到最低</span><span class="sxs-lookup"><span data-stu-id="60fcd-137">Use streaming to minimize the memory footprint required when loading messages in pipelines</span></span>  
 <span data-ttu-id="60fcd-138">下列技術會描述如何載入在管線中的訊息時，將訊息的記憶體使用量降到最低。</span><span class="sxs-lookup"><span data-stu-id="60fcd-138">The following techniques describe how to minimize the memory footprint of a message when loading the message into a pipeline.</span></span>  
  
### <a name="use-readonlyseekablestream-and-virtualstream-to-process-a-message-from-a-pipeline-component"></a><span data-ttu-id="60fcd-139">使用 ReadOnlySeekableStream 和 VirtualStream 來處理來自管線元件的訊息</span><span class="sxs-lookup"><span data-stu-id="60fcd-139">Use ReadOnlySeekableStream and VirtualStream to process a message from a pipeline component</span></span>  
 <span data-ttu-id="60fcd-140">公認的最佳做法是避免將整個訊息載入記憶體內的管線元件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-140">It is considered a best practice to avoid loading the entire message into memory inside pipeline components.</span></span> <span data-ttu-id="60fcd-141">最好的方法是將使用自訂資料流實作，然後再為已讀取要求的輸入資料流、 自訂資料流實作會包裝基礎資料流讀取和處理資料讀取時 （以純粹的串流處理方式）。</span><span class="sxs-lookup"><span data-stu-id="60fcd-141">A preferable approach is to wrap the inbound stream with a custom stream implementation, and then as read requests are made, the custom stream implementation reads the underlying, wrapped stream and processes the data as it is read (in a pure streaming manner).</span></span> <span data-ttu-id="60fcd-142">這可以是很難實作，而且不可能，根據所需的資料流處理。</span><span class="sxs-lookup"><span data-stu-id="60fcd-142">This can be very hard to implement and may not be possible, depending on what needs to be done with the stream.</span></span> <span data-ttu-id="60fcd-143">在此情況下，使用**ReadOnlySeekableStream**和**VirtualStream** Microsoft.BizTalk.Streaming.dll 所公開的類別。</span><span class="sxs-lookup"><span data-stu-id="60fcd-143">In this case, use the **ReadOnlySeekableStream** and **VirtualStream** classes exposed by the Microsoft.BizTalk.Streaming.dll.</span></span> <span data-ttu-id="60fcd-144">中也會提供這些實作[任意 XPath 屬性處理常式 （BizTalk Server 範例）](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) BizTalk SDK 中。**ReadOnlySeekableStream**可確保資料指標可以重新定位到資料流的開頭。</span><span class="sxs-lookup"><span data-stu-id="60fcd-144">An implementation of these is also provided in [Arbitrary XPath Property Handler (BizTalk Server Sample)](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) in the BizTalk SDK.**ReadOnlySeekableStream** ensures that the cursor can be repositioned to the beginning of the stream.</span></span> <span data-ttu-id="60fcd-145">**VirtualStream**會使用 MemoryStream 就內部而言，除非大小已超過指定臨界值，在此情況下則會寫入資料流至檔案系統。</span><span class="sxs-lookup"><span data-stu-id="60fcd-145">The **VirtualStream** will use a MemoryStream internally, unless the size is over a specified threshold, in which case it will write the stream to the file system.</span></span> <span data-ttu-id="60fcd-146">使用下列兩個資料流中組合 (使用**VirtualStream**為永續性儲存體**ReadOnlySeekableStream**) 提供 「 seekability 」 和 「 檔案系統的溢位 」 功能。</span><span class="sxs-lookup"><span data-stu-id="60fcd-146">Use of these two streams in combination (using **VirtualStream** as persistent storage for the **ReadOnlySeekableStream**) provides both “seekability” and “overflow to file system” capabilities.</span></span> <span data-ttu-id="60fcd-147">這適合處理大型訊息而不將整個訊息載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="60fcd-147">This accommodates the processing of large messages without loading the entire message into memory.</span></span> <span data-ttu-id="60fcd-148">下列程式碼可用於管線元件中實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="60fcd-148">The following code could be used in a pipeline component to implement this functionality.</span></span>  
  
```  
int bufferSize = 0x280;  
int thresholdSize = 0x100000;  
Stream vStream = new VirtualStream(bufferSize, thresholdSize);  
Stream seekStream = new ReadOnlySeekableStream(inboundStream, vStream, bufferSize);  
```  
  
 <span data-ttu-id="60fcd-149">此程式碼藉由公開 bufferSize 提供 「 溢位閾值 」，而且 thresholdSize 變數在每個接收位置或傳送埠組態。</span><span class="sxs-lookup"><span data-stu-id="60fcd-149">This code provides an “overflow threshold” by exposing bufferSize and thresholdSize variables on each receive location or send port configuration.</span></span> <span data-ttu-id="60fcd-150">然後可以由開發人員或系統管理員針對不同的訊息類型和不同的組態 （例如 32 位元與調整此溢位臨界值64 位元)。</span><span class="sxs-lookup"><span data-stu-id="60fcd-150">This overflow threshold can then be adjusted by developers or administrators for different message types and different configurations (such as 32-bit vs. 64-bit).</span></span>  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-given-ibasemessage-object-from-within-a-custom-pipeline-component"></a><span data-ttu-id="60fcd-151">使用 XPathReader 和 XPathCollection 擷取給定的 IBaseMessage 物件，從自訂管線元件中。</span><span class="sxs-lookup"><span data-stu-id="60fcd-151">Using XPathReader and XPathCollection to extract a given IBaseMessage object from within a custom pipeline component.</span></span>  
 <span data-ttu-id="60fcd-152">如果需要從 XML 文件，而不是使用特定值**SelectNodes**和**SelectSingleNode** XmlDocument 類別所公開的方法使用 XPathReader 類別的執行個體Microsoft.BizTalk.XPathReader.dll 組件所提供，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="60fcd-152">If specific values need to be pulled from an XML document, instead of using the **SelectNodes** and **SelectSingleNode** methods exposed by the XmlDocument class, use an instance of the XPathReader class provided by the Microsoft.BizTalk.XPathReader.dll assembly as illustrated in the following code example.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60fcd-153">特別是，使用 SelectNodes 或 SelectSingleNode XmlDocument 可能會提供更佳的效能比使用 XPathReader，但是 XPathReader 可讓您將您的應用程式的一般記憶體設定檔較小的訊息。</span><span class="sxs-lookup"><span data-stu-id="60fcd-153">For smaller messages especially, using an XmlDocument with SelectNodes or SelectSingleNode may provide better performance than using XPathReader, but XPathReader allows you to keep a flat memory profile for your application.</span></span>  
  
 <span data-ttu-id="60fcd-154">這個範例示範如何使用 XPathReader 和 XPathCollection 擷取給定**IBaseMessage**物件內的自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-154">This example shows how to use the XPathReader and XPathCollection to extract a given **IBaseMessage** object from within a custom pipeline component.</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage message)  
{  
    try  
    {  
        ...  
        IBaseMessageContext messageContext = message.Context;  
        if (string.IsNullOrEmpty(xPath) && string.IsNullOrEmpty(propertyValue))  
        {  
            throw new ArgumentException(...);  
        }  
        IBaseMessagePart bodyPart = message.BodyPart;  
        Stream inboundStream = bodyPart.GetOriginalDataStream();  
        VirtualStream virtualStream = new VirtualStream(bufferSize, thresholdSize);  
        ReadOnlySeekableStream readOnlySeekableStream = new ReadOnlySeekableStream(inboundStream, virtualStream, bufferSize);  
        XmlTextReader xmlTextReader = new XmlTextReader(readOnlySeekableStream);  
        XPathCollection xPathCollection = new XPathCollection();  
        XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
        xPathCollection.Add(xPath);  
        bool ok = false;  
        while (xPathReader.ReadUntilMatch())  
        {  
            if (xPathReader.Match(0) && !ok)  
            {  
                propertyValue = xPathReader.ReadString();  
                messageContext.Promote(propertyName, propertyNamespace, propertyValue);  
                ok = true;  
            }  
        }  
        readOnlySeekableStream.Position = 0;  
        bodyPart.Data = readOnlySeekableStream;  
    }  
    catch (Exception ex)  
    {  
        if (message != null)  
        {  
            message.SetErrorInfo(ex);  
        }  
        ...  
        throw ex;  
    }  
    return message;  
}  
```  
  
## <a name="use-xmlreader-and-xmlwriter-with-xmltranslatorstream-to-process-a-message-from-a-pipeline-component"></a><span data-ttu-id="60fcd-155">使用 XMLReader 和 XMLWriter XMLTranslatorStream 來處理訊息的管線元件</span><span class="sxs-lookup"><span data-stu-id="60fcd-155">Use XMLReader and XMLWriter with XMLTranslatorStream to process a message from a pipeline component</span></span>  
 <span data-ttu-id="60fcd-156">實作自訂管線元件會使用以資料流的方法，另一個方法是使用.NET **XmlReader**和**XmlWriter**類別搭配**XmlTranslatorStream** BizTalk Server 所提供的類別。</span><span class="sxs-lookup"><span data-stu-id="60fcd-156">Another method for implementing a custom pipeline component which uses a streaming approach is to use the .NET **XmlReader** and **XmlWriter** classes in conjunction with the **XmlTranslatorStream** class provided by BizTalk Server.</span></span> <span data-ttu-id="60fcd-157">例如， **NamespaceTranslatorStream** Microsoft.BizTalk.Pipeline.Components 組件所包含的類別繼承自**XmlTranslatorStream**而且可用來取代舊的命名空間以新資料流中包含的 XML 文件中。</span><span class="sxs-lookup"><span data-stu-id="60fcd-157">For example, the **NamespaceTranslatorStream** class contained in the Microsoft.BizTalk.Pipeline.Components assembly inherits from **XmlTranslatorStream** and can be used to replace an old namespace with a new one in the XML document contained in the stream.</span></span> <span data-ttu-id="60fcd-158">若要使用這項功能內的自訂管線元件，您可以包裝原始資料流的新執行個體訊息內文部分的**NamespaceTranslatorStream**類別，並傳回第二個。</span><span class="sxs-lookup"><span data-stu-id="60fcd-158">In order to use this functionality inside a custom a pipeline component, you can wrap the original data stream of the message body part with a new instance of the **NamespaceTranslatorStream** class and return the latter.</span></span> <span data-ttu-id="60fcd-159">以這種方式將傳入的訊息未讀取或處理在管線元件，但在相同管線的後續元件所讀取的資料流，或最後取用文件發佈至 BizTalk Server 之前，訊息代理程式時，才MessageBox。</span><span class="sxs-lookup"><span data-stu-id="60fcd-159">In this way the inbound message is not read or processed inside the pipeline component, but only when the stream is read by a subsequent component in the same pipeline or is finally consumed by the Message Agent before publishing the document to the BizTalk Server MessageBox.</span></span>  
  
 <span data-ttu-id="60fcd-160">下列範例說明如何使用這項功能。</span><span class="sxs-lookup"><span data-stu-id="60fcd-160">The following example illustrates how to use this functionality.</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage message)  
{  
   IBaseMessage outboundMessage = message;  
   try  
   {  
      if (context == null)  
      {  
         throw new ArgumentException(Resources.ContextIsNullMessage);  
      }  
      if (message == null)  
      {  
         throw new ArgumentException(Resources.InboundMessageIsNullMessage);  
      }  
  
      IBaseMessagePart bodyPart = message.BodyPart;  
      Stream stream = new NamespaceTranslatorStream(context,   
                                                    bodyPart.GetOriginalDataStream(),   
                                                    oldNamespace,   
                                                    newNamespace);  
      context.ResourceTracker.AddResource(stream);  
      bodyPart.Data = stream;  
   }  
   catch (Exception ex)  
   {  
      if (message != null)  
      {  
         message.SetErrorInfo(ex);  
      }  
  
      throw ex;  
   }  
   return outboundMessage;  
}  
```  
  
## <a name="using-resourcetracker-in-custom-pipeline-components"></a><span data-ttu-id="60fcd-161">自訂管線元件中使用 ResourceTracker</span><span class="sxs-lookup"><span data-stu-id="60fcd-161">Using ResourceTracker in Custom Pipeline Components</span></span>  
 <span data-ttu-id="60fcd-162">管線元件應該管理其建立之物件的存留期和執行記憶體回收，因為已不再需要這些物件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-162">A pipeline component should manage the lifetime of the objects it creates and perform garbage collection as soon as these objects are no longer required.</span></span>  <span data-ttu-id="60fcd-163">如果管線元件想到結束的管線執行時，最後一個物件的存留期，則您必須將這類物件加入您的管線可能會從管線內容擷取資源追蹤程式。</span><span class="sxs-lookup"><span data-stu-id="60fcd-163">If the pipeline component wants the lifetime of the objects to last until the end of pipeline execution, then you must add such objects to the resource tracker that your pipeline may fetch from the pipeline context.</span></span>  
  
 <span data-ttu-id="60fcd-164">資源追蹤程式會使用下列類型的物件：</span><span class="sxs-lookup"><span data-stu-id="60fcd-164">The resource tracker is used for the following types of objects:</span></span>  
  
-   <span data-ttu-id="60fcd-165">資料流物件</span><span class="sxs-lookup"><span data-stu-id="60fcd-165">Stream objects</span></span>  
  
-   <span data-ttu-id="60fcd-166">COM 物件</span><span class="sxs-lookup"><span data-stu-id="60fcd-166">COM objects</span></span>  
  
-   <span data-ttu-id="60fcd-167">IDisposable 物件</span><span class="sxs-lookup"><span data-stu-id="60fcd-167">IDisposable objects</span></span>  
  
 <span data-ttu-id="60fcd-168">訊息引擎可確保在適當的時間之後完全執行管線，不論它是否成功或失敗,，並釋出所有原生資源加入至資源追蹤程式。</span><span class="sxs-lookup"><span data-stu-id="60fcd-168">The message engine ensures that all the native resources that are added to the resource tracker are released at an appropriate time, that is after the pipeline is completely executed, regardless of whether it was successful or failed.</span></span> <span data-ttu-id="60fcd-169">資源追蹤程式執行個體以及它會追蹤物件存留期是由管線內容物件來管理。</span><span class="sxs-lookup"><span data-stu-id="60fcd-169">The lifetime of the Resource Tracker instance and the objects that it is tracking is managed by the pipeline context object.</span></span> <span data-ttu-id="60fcd-170">管線內容可供所有類型的管線元件，透過實作 IPipelineContext 介面的物件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-170">The pipeline context is made available to all types of pipeline components through an object that implements the IPipelineContext interface.</span></span>  
  
 <span data-ttu-id="60fcd-171">例如，下列程式碼片段會說明如何在自訂管線元件中使用 ResourceTracker 屬性的範例。</span><span class="sxs-lookup"><span data-stu-id="60fcd-171">For example, the following code snippet is a sample that illustrates how to use ResourceTracker property in custom pipeline components.</span></span> <span data-ttu-id="60fcd-172">若要使用 ResourceTracker 屬性，程式碼片段會使用下列參數`IPipelineContext.ResourceTracker.AddResource`。</span><span class="sxs-lookup"><span data-stu-id="60fcd-172">To use ResourceTracker property, the code snippet uses the following parameter `IPipelineContext.ResourceTracker.AddResource`.</span></span> <span data-ttu-id="60fcd-173">在此參數：</span><span class="sxs-lookup"><span data-stu-id="60fcd-173">In this parameter:</span></span>  
  
-   <span data-ttu-id="60fcd-174">IPipelineContext 介面會定義用來存取所有的文件處理特定介面的方法。</span><span class="sxs-lookup"><span data-stu-id="60fcd-174">IPipelineContext interface defines the methods used to access all document processing-specific interfaces.</span></span>  
  
-   <span data-ttu-id="60fcd-175">ResourceTracker 屬性參考 IPipelineContext，而且用來追蹤會在管線處理結尾明確處置的物件。</span><span class="sxs-lookup"><span data-stu-id="60fcd-175">ResourceTracker property references IPipelineContext and is used to keep track of objects that will be explicitly disposed at the end of pipeline processing.</span></span>  
  
-   <span data-ttu-id="60fcd-176">ResourceTracker.AddResource 方法用來追蹤 COM 物件、 可處置的物件和資料流，並應該一定可以用在自訂管線元件內來明確關閉 （資料流）、 dispose （IDisposable 物件） 或這些釋放 （COM 物件）訊息發佈到 BizTalk MessageBox 時，資源類型。</span><span class="sxs-lookup"><span data-stu-id="60fcd-176">ResourceTracker.AddResource method is used to keep track of COM objects, Disposable objects and Streams, and should always be used inside a custom pipeline component to explicitly close (streams), dispose (IDisposable objects) or release (COM objects) these types of resources when a message is published to the BizTalk MessageBox.</span></span>  
  
```  
public IBaseMessage Execute(IPipelineContext pContext, IBaseMessage pInMsg)  
  
{  
      IBaseMessage outMessage = pContext.GetMessageFactory().CreateMessage();  
  
      IBaseMessagePart outMsgBodyPart = pContext.GetMessageFactory().CreateMessagePart();  
  
      outMsgBodyPart.Charset = Encoding.UTF8.WebName;   
  
      outMsgBodyPart.ContentType = "text/xml";  
  
//Code to load message content in the MemoryStream object//  
  
      MemoryStream messageData = new MemoryStream();  
  
   //The MemoryStream needs to be closed after the whole pipeline has executed, thus adding it into ResourceTracker//  
  
      pContext.ResourceTracker.AddResource(messageData);  
  
//Custom pipeline code to load message data into xmlPayload//  
  
      XmlDocument xmlPayLoad = new XmlDocument();  
  
      xmlPayLoad.Save(messageData);  
  
      messageData.Seek(0, SeekOrigin.Begin);  
  
//The new stream is assigned to the message part’s data//  
  
      outMsgBodyPart.Data = messageData;  
  
// Pipeline component logic here//  
  
      return outMessage;  
  
}  
```  
  
## <a name="comparison-of-loading-messages-into-pipelines-using-an-in-memory-approach-and-using-a-streaming-approach"></a><span data-ttu-id="60fcd-177">載入訊息至管線，使用記憶體中的方法與使用資料流處理方式的比較</span><span class="sxs-lookup"><span data-stu-id="60fcd-177">Comparison of loading messages into pipelines using an in-memory approach and using a streaming approach</span></span>  
 <span data-ttu-id="60fcd-178">下列資訊取自 Nic Barden 部落格、 [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228)。</span><span class="sxs-lookup"><span data-stu-id="60fcd-178">The following information was taken from Nic Barden’s blog, [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228).</span></span> <span data-ttu-id="60fcd-179">下表提供摘要的比較載入訊息至管線，使用記憶體中的方法與使用資料流的方式。</span><span class="sxs-lookup"><span data-stu-id="60fcd-179">This table provides a summarized comparison of loading messages into pipelines using an in-memory approach and using a streaming approach.</span></span>  
  
|<span data-ttu-id="60fcd-180">比較...</span><span class="sxs-lookup"><span data-stu-id="60fcd-180">Comparison of...</span></span>|<span data-ttu-id="60fcd-181">串流處理</span><span class="sxs-lookup"><span data-stu-id="60fcd-181">Streaming</span></span>|<span data-ttu-id="60fcd-182">在記憶體中</span><span class="sxs-lookup"><span data-stu-id="60fcd-182">In memory</span></span>|  
|----------------------|---------------|---------------|  
|<span data-ttu-id="60fcd-183">每個訊息的記憶體使用量</span><span class="sxs-lookup"><span data-stu-id="60fcd-183">Memory usage per message</span></span>|<span data-ttu-id="60fcd-184">低，而不管訊息大小</span><span class="sxs-lookup"><span data-stu-id="60fcd-184">Low, regardless of message size</span></span>|<span data-ttu-id="60fcd-185">高 （訊息大小而有所不同）</span><span class="sxs-lookup"><span data-stu-id="60fcd-185">High (varies depending on message size)</span></span>|  
|<span data-ttu-id="60fcd-186">用來處理 XML 資料的一般類別</span><span class="sxs-lookup"><span data-stu-id="60fcd-186">Common classes used to process XML data</span></span>|<span data-ttu-id="60fcd-187">內建和自訂中的衍生：</span><span class="sxs-lookup"><span data-stu-id="60fcd-187">Built in and custom derivations of:</span></span><br /><br /> <span data-ttu-id="60fcd-188">XmlTranslatorStream、 XmlReader 和 XmlWriter</span><span class="sxs-lookup"><span data-stu-id="60fcd-188">XmlTranslatorStream, XmlReader and XmlWriter</span></span>|<span data-ttu-id="60fcd-189">XmlDocument、 XPathDocument、 MemoryStream 和 VirtualStream</span><span class="sxs-lookup"><span data-stu-id="60fcd-189">XmlDocument, XPathDocument, MemoryStream and VirtualStream</span></span>|  
|<span data-ttu-id="60fcd-190">文件集</span><span class="sxs-lookup"><span data-stu-id="60fcd-190">Documentation</span></span>|<span data-ttu-id="60fcd-191">不良 – 許多未支援和未記載的 BizTalk 類別</span><span class="sxs-lookup"><span data-stu-id="60fcd-191">Poor – many un-supported and un-documented BizTalk classes</span></span>|<span data-ttu-id="60fcd-192">很好的.NET Framework 類別</span><span class="sxs-lookup"><span data-stu-id="60fcd-192">Very good - .NET Framework classes</span></span>|  
|<span data-ttu-id="60fcd-193">「 處理邏輯 」 程式碼的位置</span><span class="sxs-lookup"><span data-stu-id="60fcd-193">Location of “Processing Logic” code</span></span>|<span data-ttu-id="60fcd-194">-「 連接 」 讀取器和透過 Execute 方法中的資料流。</span><span class="sxs-lookup"><span data-stu-id="60fcd-194">-   “Wire up” readers and streams via Execute method.</span></span><br /><span data-ttu-id="60fcd-195">-實際的執行會發生問題的讀取器和資料流中讀取資料。</span><span class="sxs-lookup"><span data-stu-id="60fcd-195">-   Actual execution occurs in the readers and streams as the data is read.</span></span>|<span data-ttu-id="60fcd-196">直接從管線元件的執行方法。</span><span class="sxs-lookup"><span data-stu-id="60fcd-196">Directly from the Execute method of the pipeline component.</span></span>|  
|<span data-ttu-id="60fcd-197">data</span><span class="sxs-lookup"><span data-stu-id="60fcd-197">Data</span></span>|<span data-ttu-id="60fcd-198">透過其讀取資料時，重新建立每個文繞圖層級。</span><span class="sxs-lookup"><span data-stu-id="60fcd-198">Re-created at each wrapping layer as data is read through it.</span></span>|<span data-ttu-id="60fcd-199">讀取、 修改並寫出每個元件在下一個元件呼叫之前。</span><span class="sxs-lookup"><span data-stu-id="60fcd-199">Read in, modified and written out at each component prior to next component being called.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60fcd-200">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60fcd-200">See Also</span></span>  
 [<span data-ttu-id="60fcd-201">最佳化 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="60fcd-201">Optimizing BizTalk Server Applications</span></span>](../technical-guides/optimizing-biztalk-server-applications.md)