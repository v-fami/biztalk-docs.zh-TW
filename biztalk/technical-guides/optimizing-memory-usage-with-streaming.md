---
title: 將資料流的記憶體使用最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f8ba8820-65b4-4161-9f7a-3ae3d39e3d11
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55c86fafdab538dcf60f52265e10711b1a43340a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024148"
---
# <a name="optimizing-memory-usage-with-streaming"></a><span data-ttu-id="b7f6f-102">將資料流的記憶體使用最佳化</span><span class="sxs-lookup"><span data-stu-id="b7f6f-102">Optimizing Memory Usage with Streaming</span></span>
<span data-ttu-id="b7f6f-103">本主題提供使用資料流模式時傳送或接收大型訊息的 WCF 傳輸，或載入協調流程中的訊息時，訊息的記憶體使用量降到最低的建議。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-103">This topic provides recommendations for using streaming patterns to minimize message memory footprints when sending or receiving large messages with a WCF transport or when loading messages in orchestrations.</span></span>   
<span data-ttu-id="b7f6f-104">當使用協調流程中的程式碼，來讀取訊息的內容，請避免使用 XmlDocument 變數。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-104">When using code in an orchestration to read the contents of a message, avoid using XmlDocument variables.</span></span> <span data-ttu-id="b7f6f-105">載入 XmlDocument 變數中的訊息時，會產生明顯的負擔，特別是針對大型訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-105">Loading a message into an XmlDocument variable incurs significant overhead, especially for large messages.</span></span> <span data-ttu-id="b7f6f-106">這個額外的記憶體使用量和處理，以建置記憶體中的結構。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-106">This overhead is in terms of memory usage and processing to build the in-memory structures.</span></span> <span data-ttu-id="b7f6f-107">使用 XmlDocument 執行個體強制要載入到記憶體才能建立物件圖形的文件物件模組 (DOM) 的整個訊息內容。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-107">The use of an XmlDocument instance forces the entire message contents to be loaded into memory in order to build the object graph for the Document Object Module (DOM).</span></span> <span data-ttu-id="b7f6f-108">此類別的執行個體所使用總數量可能是記憶體的大約 10 倍的實際的訊息大小。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-108">The total amount of memory used by an instance of this class can be around 10 times the actual message size.</span></span> <span data-ttu-id="b7f6f-109">如需有關載入 XmlDocument 變數中的訊息時所需的記憶體使用量的詳細資訊，請參閱[第 9 章-改善 XML 效能](http://go.microsoft.com/fwlink/?LinkId=139772)(http://go.microsoft.com/fwlink/?LinkId=139772) MSDN 上。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-109">For more information about the memory footprint required when loading a message into an XmlDocument variable, see [Chapter 9 – Improving XML Performance](http://go.microsoft.com/fwlink/?LinkId=139772) (http://go.microsoft.com/fwlink/?LinkId=139772) on MSDN.</span></span>   
<span data-ttu-id="b7f6f-110">本主題的其餘部分提供替代的方法，來讀取訊息的內容，不需要載入 XmlDocument 變數中的訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-110">The remainder of this topic provides alternative methods for reading message contents that do not require loading a message into an XmlDocument variable.</span></span>  
  
## <a name="use-streaming-when-sending-or-receiving-large-messages-with-a-wcf-transport"></a><span data-ttu-id="b7f6f-111">使用資料流傳送或接收與 WCF 傳輸大型訊息時</span><span class="sxs-lookup"><span data-stu-id="b7f6f-111">Use streaming when sending or receiving large messages with a WCF transport</span></span>  
 <span data-ttu-id="b7f6f-112">在傳送或接收大型訊息的 WCF 傳輸，使用 Wcf-custom 或 Wcf-customisolated 配接器，並設定與繫結型別支援**transferMode = Streamed**選項，例如下列繫結：</span><span class="sxs-lookup"><span data-stu-id="b7f6f-112">When sending or receiving large messages with a WCF transport, use the WCF-Custom or WCF-CustomIsolated adapter and configure with a binding type that supports the **transferMode = Streamed** option, such as the following bindings:</span></span>  
  
- <span data-ttu-id="b7f6f-113">**basicHttpBinding + BasicHttpBindingElement，傳輸模式 = Streamed**</span><span class="sxs-lookup"><span data-stu-id="b7f6f-113">**basicHttpBinding + BasicHttpBindingElement, transferMode = Streamed**</span></span>  
  
- <span data-ttu-id="b7f6f-114">**netTcpBinding + NetTcpBindingElement，傳輸模式 = Streamed**</span><span class="sxs-lookup"><span data-stu-id="b7f6f-114">**netTcpBinding + NetTcpBindingElement, transferMode = Streamed**</span></span>  
  
- <span data-ttu-id="b7f6f-115">**customBinding + HttpTransportElement，傳輸模式 = Streamed**</span><span class="sxs-lookup"><span data-stu-id="b7f6f-115">**customBinding + HttpTransportElement, transferMode = Streamed**</span></span>  
  
- <span data-ttu-id="b7f6f-116">**customBinding + ConnectionOrientedTransportElement，傳輸模式 = Streamed**</span><span class="sxs-lookup"><span data-stu-id="b7f6f-116">**customBinding +ConnectionOrientedTransportElement, transferMode = Streamed**</span></span>  
  
  <span data-ttu-id="b7f6f-117">選擇以及支援的繫結的 Wcf-custom 或 Wcf-customisolated 配接器**transferMode = Streamed**選項將會實作的檔案系統的大型訊息資料流，如有需要並會減少可能記憶體不足的問題。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-117">Choosing a WCF-Custom or WCF-CustomIsolated adapter along with a binding that supports the **transferMode = Streamed** option will implement streaming of large messages to the file system as needed, and will mitigate potential out-of-memory issues.</span></span>  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-orchestrations"></a><span data-ttu-id="b7f6f-118">使用資料流載入協調流程中的訊息時所需的記憶體使用量降到最低</span><span class="sxs-lookup"><span data-stu-id="b7f6f-118">Use streaming to minimize the memory footprint required when loading messages in orchestrations</span></span>  
 <span data-ttu-id="b7f6f-119">下列技術說明如何將訊息載入協調流程時，將一則訊息的記憶體使用量降至最低。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-119">The following techniques describe how to minimize the memory footprint of a message when loading the message into an orchestration.</span></span>  
  
### <a name="use-an-xlangmessage-variable-to-process-the-contents-of-a-message-or-message-part"></a><span data-ttu-id="b7f6f-120">使用 XLANGMessage 變數來處理訊息或訊息部分的內容</span><span class="sxs-lookup"><span data-stu-id="b7f6f-120">Use an XLANGMessage variable to process the contents of a message or message part</span></span>  
 <span data-ttu-id="b7f6f-121">當從協調流程的訊息傳遞.NET 類別庫中，不將它們傳遞為 XmlDocument 變數，如本主題中，稍早所述的原因請改用 XLANGMessage 變數。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-121">When passing a message from an orchestration to .NET class libraries, do not pass them as XmlDocument variables, for reasons mentioned earlier in this topic; use XLANGMessage variables instead.</span></span> <span data-ttu-id="b7f6f-122">下列技術說明用於讀取的訊息或訊息部分使用 XLANGMessage 變數的方法。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-122">The following techniques illustrate methods for reading a message or message part using an XLANGMessage variable.</span></span>  
  
-   <span data-ttu-id="b7f6f-123">**處理訊息與 XMLReader** -若要處理的訊息與 XmlReader 執行個體、 將訊息傳遞給.NET 程式碼，為 XLANGMessage，以及擷取使用 XmlReader 的組件內容。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-123">**Process messages with XMLReader** - To process a message with an XmlReader instance, pass the message to .NET code as an XLANGMessage, and retrieve the Part content using XmlReader.</span></span>  
  
    ```  
    public void ProcessMessage(XLANGMessage message)  
    {  
        try  
        {  
            using (XmlReader reader = message[0].RetrieveAs(typeof(XmlReader)) as XmlReader)  
            if (reader != null)  
            {  
                ...  
            }  
        }  
        finally  
        {  
            message.Dispose();  
        }  
    }  
    ```  
  
-   <span data-ttu-id="b7f6f-124">**擷取訊息的內容轉換為字串 streamreader** -XmlDocument 協調流程中的常見用途之一是使用 XmlDocument.OuterXml() XML 字串形式擷取的訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-124">**Retrieve the contents of a message into a string with StreamReader** - One of the common uses of XmlDocument in orchestrations is to retrieve the message as an XML string using XmlDocument.OuterXml().</span></span> <span data-ttu-id="b7f6f-125">下列程式碼範例說明了替代方法，以使用 XLANGMessage 變數字串擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-125">The following code example illustrates an alternative method which retrieves the message as a string using an XLANGMessage variable.</span></span>  
  
    ```  
    public static string MessageToString(XLANGMessage message)  
    {  
        string strResults;  
        try  
        {  
            using (Stream stream = message[0].RetrieveAs(typeof(Stream)) as Stream)  
            {  
                using (StreamReader reader = new StreamReader(stream))  
                {  
                    strResults = reader.ReadToEnd();  
                }  
            }  
        }  
        finally  
        {  
            message.Dispose();  
        }  
        return strResults;  
    }  
    ```  
  
-   <span data-ttu-id="b7f6f-126">**轉換為字串中擷取的簡單.NET 訊息內容**-如果訊息的類型是簡單的.NET 型別，您可以擷取與該類型的訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-126">**Retrieve the contents of simple .NET messages into a string** - If the type of the message is a simple .NET type, you can retrieve the message as that type.</span></span> <span data-ttu-id="b7f6f-127">比方說，若要為字串的訊息，傳遞給.NET 程式碼，為 XLANGMessage 的訊息，並擷取為字串的部分內容。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-127">For example, to get the message as a string, pass the message to the .NET code as an XLANGMessage and retrieve the Part content as a string.</span></span>  
  
    ```  
    public void ProcessMessage(XLANGMessage message)  
    {  
        try  
        {  
            string content = message[0].RetrieveAs(typeof(string)) as string;  
            if (!string.IsNullOrEmpty(content))  
            {  
                ...  
            }  
        }  
        finally  
        {  
            message.Dispose();  
        }  
    }  
    ```  
  
-   <span data-ttu-id="b7f6f-128">**擷取訊息的內容資料流**-若要取得做為資料流的訊息、 將訊息傳遞給.NET 程式碼，為 XLANGMessage 和擷取組件內容，做為資料流。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-128">**Retrieve the contents of a message into a stream** - To get the message as a stream, pass the message to the .NET code as an XLANGMessage and retrieve the Part content as a stream.</span></span>  
  
    ```  
    public Stream ProcessRequestReturnStream(XLANGMessage message, int bufferSize, int thresholdSize)  
    {  
       ...  
       try  
       {  
          using (VirtualStream virtualStream = new VirtualStream(bufferSize, thresholdSize))  
          {  
             using (Stream partStream = (Stream)message[0].RetrieveAs(typeof(Stream)))  
             //Note that when calling this code, if the XmlDocument is quite large, keeping it in a memory with a MemoryStream may have an adverse effect on performance.   
             //In this case, it may be worthwhile to consider an approach that uses a VirtualStream + ReadonlySeekableStream to buffer it to the file system, if its size is bigger than the thresholdSize parameter.  
             //Keep in mind that:  
             // - If the message size is smaller than the threshold size, the VirtualStream class buffers the stream to a MemoryStream.  
             // - If the message size is bigger than the threshold size, the VirtualStream class buffers the stream to a temporary file.  
                using (ReadOnlySeekableStream readOnlySeekableStream = new ReadOnlySeekableStream(partStream, virtualStream, bufferSize))  
                {  
                   using (XmlReader reader = XmlReader.Create(readOnlySeekableStream))  
                   {  
  
                   }  
                }  
             }  
          }  
       }  
       catch (Exception ex)  
       {  
  
       }  
       finally  
       {  
          message.Dispose();  
       }  
       return stream;  
    }  
    ```  
  
-   <span data-ttu-id="b7f6f-129">**成.NET 物件中擷取訊息的內容**-若要取得的訊息為.NET 物件、 將訊息傳遞給.NET 程式碼，為 XLANGMessage 和擷取組件內容與.NET 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-129">**Retrieve the contents of a message into a .NET object** - To get the message as a .NET object, pass the message to the .NET code as an XLANGMessage and retrieve the Part content as an instance of a .NET class.</span></span> <span data-ttu-id="b7f6f-130">建立這第二個 Xml 結構描述使用 Visual Studio 2010 所提供的 XML 結構描述定義工具 (Xsd.exe) 工具的訊息。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-130">Create this latter from the Xml Schema of the message using the XML Schema Definition Tool (Xsd.exe) tool provided by Visual Studio 2010.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b7f6f-131">只有當訊息很小，這個技術非常有效。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-131">This technique is valid only when messages are small.</span></span> <span data-ttu-id="b7f6f-132">否則，這種方法可能會相當大的負擔，若要將實際的訊息還原序列化成.NET 物件中。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-132">Otherwise, this approach could incur in a significant overhead to de-serialize the actual message into a .NET object.</span></span>  
  
    ```  
    public void ProcessMessage(XLANGMessage message)  
    {  
        try  
          {  
          Request request = message[0].RetrieveAs(typeof(Request)) as Request;  
          if (request != null)  
          {  
             ...  
          }  
       }  
       finally  
       {  
          message.Dispose();  
       }  
  
    }  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="b7f6f-133">利用**dispose （)** XLANGMessage 參數所公開的.NET 程式碼，返回之前的方法是特別重要，在迴圈案例和長時間執行的協調流程可以累積的執行個體XLANGMessage 物件，而不釋出一段時間。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-133">Use of the **Dispose()** method exposed by the XLANGMessage parameter before returning from the .NET code is particularly important in looping scenarios and long-running orchestrations that can accumulate instances of the XLANGMessage object without releasing them over time.</span></span> <span data-ttu-id="b7f6f-134">如需呼叫訊息的詳細資訊。Dispose （） 這種方式，請參閱[訊息表示為 XLANGMessage](http://go.microsoft.com/fwlink/?LinkId=139775) (http://go.microsoft.com/fwlink/?LinkId=139775) BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-134">For more information about calling message.Dispose() in this manner, see [Messages Represented as XLANGMessage](http://go.microsoft.com/fwlink/?LinkId=139775) (http://go.microsoft.com/fwlink/?LinkId=139775) in the BizTalk Server documentation.</span></span> <span data-ttu-id="b7f6f-135">本主題也提供使用 IStreamFactory 建構 XLANGMessage 變數中使用資料流為基礎的方法的使用者程式碼的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-135">This topic also provides best practices for using IStreamFactory to construct XLANGMessage variables in user code using a stream-based approach.</span></span>  
  
 <span data-ttu-id="b7f6f-136">如需有關處理 XLANGMessage 內叫用的協調流程的協助程式元件的不同方式的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="b7f6f-136">For more information about the different ways to process an XLANGMessage within an helper component invoked by an orchestration, see the following topics:</span></span>  
  
-   <span data-ttu-id="b7f6f-137">[4 個不同的方式來處理第 1 部分協調流程叫用協助程式元件內 XLANGMessage](http://go.microsoft.com/fwlink/?LinkID=210420) (http://go.microsoft.com/fwlink/?LinkID=210420)。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-137">[4 Different ways to process an XLANGMessage within an helper component invoked by an orchestration Part 1](http://go.microsoft.com/fwlink/?LinkID=210420) (http://go.microsoft.com/fwlink/?LinkID=210420).</span></span>  
  
-   <span data-ttu-id="b7f6f-138">[4 個不同的方式來處理第 2 部分協調流程叫用協助程式元件內 XLANGMessage](http://go.microsoft.com/fwlink/?LinkID=210421) (http://go.microsoft.com/fwlink/?LinkID=210421)。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-138">[4 Different ways to process an XLANGMessage within an helper component invoked by an orchestration Part 2](http://go.microsoft.com/fwlink/?LinkID=210421) (http://go.microsoft.com/fwlink/?LinkID=210421).</span></span>  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-value-from-an-xlangmessage-object-from-a-method-invoked-by-an-orchestration"></a><span data-ttu-id="b7f6f-139">使用 XPathReader 和 XPathCollection XLANGMessage 從物件的方法叫用的協調流程中擷取值</span><span class="sxs-lookup"><span data-stu-id="b7f6f-139">Using XPathReader and XPathCollection to extract a value from an XLANGMessage object from a method invoked by an orchestration</span></span>  
 <span data-ttu-id="b7f6f-140">避免使用 XMLDocument 類別讀取 XML 訊息的內容從自訂程式碼，例如自訂管線元件或協調流程所叫用的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-140">Avoid using the XMLDocument class to read the contents of XML messages from custom code, such as custom pipeline components or helper classes invoked by orchestrations.</span></span> <span data-ttu-id="b7f6f-141">當您可以使用 XMLDocument 執行個體來載入 XML 訊息，會將整個訊息載入記憶體，這是效率不佳，而且可能需要最多 10 倍的實際大小的訊息的記憶體。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-141">When using an XMLDocument instance to load an XML message, the entire message is loaded into memory, which is inefficient and may require memory up to 10 times the actual size of the message.</span></span> <span data-ttu-id="b7f6f-142">讀取 XML 訊息的內容更有效率的方式是使用資料流技術之一 Microsoft.BizTalk.Streaming.dll 組件所提供的資料流類別包裝原始資料流。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-142">A more efficient way of reading the contents of XML messages is to use a streaming technique to wrap the original stream with one of the stream classes provided by the Microsoft.BizTalk.Streaming.dll assembly.</span></span> <span data-ttu-id="b7f6f-143">載入大型訊息時，這項技術會特別有用。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-143">This technique is particularly useful when loading large messages.</span></span>  
  
 <span data-ttu-id="b7f6f-144">如果特定的值必須是 XML 文件，而不是使用 SelectNodes 與 SelectSingleNode 方法公開為 XmlDocument 類別，從使用 Microsoft.BizTalk.XPathReader.dll 組件所提供的 XPathReader 類別的執行個體下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-144">If specific values need to be pulled from an XML document, instead of using the SelectNodes and SelectSingleNode methods exposed by the XmlDocument class, use an instance of the XPathReader class provided by the Microsoft.BizTalk.XPathReader.dll assembly as illustrated in the following code example.</span></span>  
  
-   <span data-ttu-id="b7f6f-145">此範例說明使用 XPathReader 和 XPathCollection 從 XLANGMessage 物件方法，叫用的協調流程內擷取指定的值。</span><span class="sxs-lookup"><span data-stu-id="b7f6f-145">This example illustrates using the XPathReader and XPathCollection to extract a given value from an XLANGMessage object inside a method invoked by an orchestration.</span></span>  
  
    ```  
    public static string SelectSingleNode(XLANGMessage message, string xPath)   
    {  
        try  
        {  
            if (message == null || string.IsNullOrEmpty(xPath))  
            {  
                return string.Empty;  
            }  
            using (XmlReader reader = (XmlReader)message[0].RetrieveAs(typeof(XmlReader)))  
            {  
                XPathCollection xPathCollection = new XPathCollection();  
                XPathReader xPathReader = new XPathReader(reader, xPathCollection);  
                xPathCollection.Add(xPath);  
                while (xPathReader.ReadUntilMatch())  
                {  
                    if (xPathReader.Match(0))  
                    {  
                        return xPathReader.ReadString();  
                    }  
                }  
            }  
        }  
        catch (Exception ex)  
        {  
            ...  
        }  
        finally  
        {  
            message.Dispose();  
        }  
        return string.Empty;  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="b7f6f-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7f6f-146">See Also</span></span>  
 [<span data-ttu-id="b7f6f-147">最佳化 BizTalk Server 應用程式</span><span class="sxs-lookup"><span data-stu-id="b7f6f-147">Optimizing BizTalk Server Applications</span></span>](../technical-guides/optimizing-biztalk-server-applications.md)