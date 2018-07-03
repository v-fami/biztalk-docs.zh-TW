---
title: 最佳化管道效能 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b5137747-0dcf-4c96-90a7-01afb92f56a6
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7102eb3fc0f6f7b1ef16a319e5e04daff6d544d1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007871"
---
# <a name="optimizing-pipeline-performance"></a>最佳化管道效能
本主題說明管線中的效能達到最佳化的指導方針[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]解決方案。  
  
## <a name="best-practices-for-optimizing-performance-of-biztalk-server-pipelines"></a>BizTalk Server 管線的效能達到最佳化的最佳作法  
  
1. 因為管線元件對效能有重大影響 （例如，通過管線元件會執行優於 XML 組合器/解譯器管線元件最多 30%），請務必執行任何自訂管線元件最佳化之前在您的部署中執行。 如果您想要最大化您的 BizTalk 應用程式的整體效能，最小化您的自訂管線中的管線元件的數目。  
  
2. 您也可以改善整體效能降低您的管線元件中的訊息持續性頻率和透過編碼自己的元件最小化備援性。 每個自訂組件，特別是效能，例如自訂追蹤元件，可能就會中斷服務的成品應個別測試狀況負載過重時，系統會在容量全滿，觀察其行為，並尋找任何可能的瓶頸。  
  
3. 如果您要讀取的輸入的訊息內的管線元件，請避免使用記憶體時，載入整份文件**XmlDocument**物件。 執行個體所需的空間數量**XmlDocument**類別來載入及建立 XML 文件的記憶體中表示法是實際的訊息大小的最多 10 倍。 若要讀取的訊息，您應該使用**XmlTextReader**下列類別的執行個體的物件：  
  
   -   **VirtualStream (Microsoft.BizTalk.Streaming.dll)** -此類別的原始程式碼位於下管線 SDK 的兩個位置，如下所示： SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。  
  
   -   **ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**。  
  
   -   **SeekAbleReadOnlyStream** -此類別的原始程式碼位於下管線 SDK 的兩個位置，如下所示： SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。  
  
4. 使用 PassThruReceive 管線和 PassThruTransmit 標準管線盡可能。 它們不包含任何管線元件，因此不會執行任何處理訊息。 基於這個理由，它們可確保在接收或傳送訊息的最大效能。 如果您要將二進位文件發佈到 BizTalk MessageBox 和 PassThruTransmit 管線的傳送埠，如果您需要傳送二進位訊息，您可以使用 PassThruReceive 管線接收位置上。 您也可以使用實體傳送埠至協調流程繫結，如果訊息已經格式化，且已準備好要傳送的 PassThruTransmit 管線。 您必須使用不同的方式，如果您需要完成下列動作之一：  
  
   - 升級傳入 XML 或一般檔案訊息的內容上的屬性。  
  
   - 套用對應的接收位置內。  
  
   - 適用於訂閱了訊息的協調流程中的對應。  
  
   - 套用訂閱了訊息的傳送埠上的對應。  
  
     若要完成其中一個動作，您必須探查探索接收管線內的文件類型和 （命名空間 #root 名稱） 值指派為 MessageType 內容屬性。 這項作業，通常是由解譯器元件，例如 Xml 解譯器元件 (XmlDasmComp) 或一般檔案解譯器元件 (FFDasmComp) 來完成。 在此情況下，您需要使用 （比方說，XmlReceive 管線） 的標準或自訂管線，其中包含標準或自訂解譯器元件。  
  
5. 資源越慢取得並將它們早發行越好。 比方說，如果您需要存取資料庫的資料，則開啟盡可能越慢的連線，並儘速關閉它。 使用 C# using 陳述式會隱含地釋放可處置的物件或 finally 區塊的 catch 的 try-finally 陳述式來明確處置物件。 檢測您的原始程式碼，讓您的元件輕鬆地偵錯。  
  
6. 排除任何您不是絕對必要，以加速訊息處理的管線元件。  
  
7. 接收管線，您應該在只有在訊息路由 （協調流程、 傳送埠） 或降級的訊息內容屬性 （傳送埠） 必須升級至訊息內容的項目。  
  
8. 如果您需要包含中繼資料的訊息，而且您不使用中繼資料的輸入路由或降級的目的，使用**IBaseMessageContext.Write**方法，而非**IBaseMessageContext.Promote**方法。  
  
9. 如果您要使用 XPath 運算式的訊息中擷取資訊，請避免使用記憶體時，載入整份文件**XmlDocument**只是為了使用的物件**SelectNodes**或**SelectSingleNode**方法。 或者，使用中所述的技巧[最佳化資料流的記憶體使用量](../technical-guides/optimizing-memory-usage-with-streaming.md)。  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-pipelines"></a>使用資料流載入在管線中的訊息時所需的記憶體使用量降到最低  
 下列技術說明如何將訊息載入管線時，將一則訊息的記憶體使用量降至最低。  
  
### <a name="use-readonlyseekablestream-and-virtualstream-to-process-a-message-from-a-pipeline-component"></a>使用 ReadOnlySeekableStream 和 VirtualStream 來處理來自管線元件的訊息  
 它會被視為最好避免將整個訊息載入記憶體內的管線元件。 比較理想的方法是將包裝輸入資料流的自訂資料流實作，然後為已讀取要求都是，自訂資料流實作讀取基礎、 包裝資料流，並處理資料，因為它讀取 （以單純的資料流處理方式）。 這可以是很難實作，而且可能不可行的視需要透過資料流。 在此案例中，使用**ReadOnlySeekableStream**並**VirtualStream** Microsoft.BizTalk.Streaming.dll 所公開的類別。 中也會提供這些項目的實作[任意 XPath 屬性處理常式 （BizTalk Server 範例）](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) BizTalk SDK 中。**ReadOnlySeekableStream**可確保資料指標，可以重新定位到資料流開頭。 **VirtualStream**會使用一個 MemoryStream，就內部而言，除非大小為超過指定的臨界值，在此情況下將資料流寫入至檔案系統。 使用這些組合中的兩個資料流 (使用**VirtualStream**為永續性儲存體**ReadOnlySeekableStream**) 提供 「 seekability 」 和 「 檔案系統的溢位 」 功能。 這可以容納大型訊息的處理而不需要整個訊息載入記憶體。 下列程式碼可用的管線元件中實作這項功能。  
  
```  
int bufferSize = 0x280;  
int thresholdSize = 0x100000;  
Stream vStream = new VirtualStream(bufferSize, thresholdSize);  
Stream seekStream = new ReadOnlySeekableStream(inboundStream, vStream, bufferSize);  
```  
  
 此程式碼提供 「 溢位閾值 」，藉由公開 bufferSize 和 thresholdSize 變數在每個接收位置或傳送埠組態。 然後可以藉由開發人員或系統管理員針對不同的訊息類型和不同的設定 （例如，32 位元與調整此溢位臨界值64 位元)。  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-given-ibasemessage-object-from-within-a-custom-pipeline-component"></a>擷取給定的 IBaseMessage 物件，從自訂管線元件中使用 XPathReader 和 XPathCollection。  
 如果特定的值必須是 XML 文件，而不是使用從提取**SelectNodes**並**SelectSingleNode** XmlDocument 類別所公開的方法使用 XPathReader 類別的執行個體Microsoft.BizTalk.XPathReader.dll 組件所提供，如下列程式碼範例所示。  
  
> [!NOTE]  
>  尤其是使用 SelectNodes 或 SelectSingleNode 的 XmlDocument，可能會提供更佳的效能比使用 XPathReader，但 XPathReader 可讓您保留您的應用程式的一般記憶體設定檔較小的訊息。  
  
 此範例示範如何使用 XPathReader 和 XPathCollection 擷取給定**IBaseMessage**物件內的自訂管線元件。  
  
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
  
## <a name="use-xmlreader-and-xmlwriter-with-xmltranslatorstream-to-process-a-message-from-a-pipeline-component"></a>使用 XMLReader 和 XMLWriter 具有 XMLTranslatorStream 來處理來自管線元件的訊息  
 實作自訂管線元件會使用資料流的方法的另一個方法是使用.NET **XmlReader**並**XmlWriter**類別搭配**XmlTranslatorStream** BizTalk Server 所提供的類別。 例如， **NamespaceTranslatorStream** Microsoft.BizTalk.Pipeline.Components 組件所包含的類別繼承自**XmlTranslatorStream**而且可用來取代舊的命名空間以新資料流中包含的 XML 文件中。 若要使用這項功能的自訂管線元件內，您可以將原始資料流的新執行個體訊息內文部分的包裝**NamespaceTranslatorStream**類別，並傳回第二個。 以這種方式輸入的訊息未讀取或處理在管線元件中，但只有當資料流讀取相同的管線中的後續元件或最後由訊息代理程式再將文件發佈至 BizTalk Server 時MessageBox。  
  
 下列範例說明如何使用這項功能。  
  
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
  
## <a name="using-resourcetracker-in-custom-pipeline-components"></a>使用自訂管線元件中的 ResourceTracker  
 管線元件應該管理其建立之物件的存留期，並執行記憶體回收，因為這些物件已不再需要。  如果管線元件想直到管線執行時，結尾的最後一個物件的存留期，則您必須加入您的管線可以從管線內容擷取資源追蹤程式中的這類物件。  
  
 資源追蹤程式會使用下列類型的物件：  
  
- Stream 物件  
  
- COM 物件  
  
- IDisposable 物件  
  
  訊息引擎可確保在適當的時間，完全執行管線，而不論其是否成功或失敗之後會釋出會新增至資源追蹤程式的所有原生資源。 資源追蹤程式執行個體和它正在追蹤之物件的存留期是由管線內容物件管理。 管線內容可供所有類型的管線元件，透過實作 IPipelineContext 介面的物件。  
  
  比方說，下列程式碼片段會說明如何使用自訂管線元件中的 ResourceTracker 屬性的範例。 若要使用 ResourceTracker 屬性，程式碼片段會使用下列參數`IPipelineContext.ResourceTracker.AddResource`。 在此參數：  
  
- IPipelineContext 介面會定義用來存取所有的文件處理特定介面的方法。  
  
- ResourceTracker 屬性參考 IPipelineContext 並用來追蹤會在管線處理結尾明確處置的物件。  
  
- ResourceTracker.AddResource 方法用來追蹤的 COM 物件，可處置的物件和資料流，並應該一律使用自訂管線元件內明確關閉 （資料流）、 處置 （IDisposable 物件） 或這些釋放 （COM 物件）訊息發佈到 BizTalk MessageBox 時，資源的類型。  
  
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
  
## <a name="comparison-of-loading-messages-into-pipelines-using-an-in-memory-approach-and-using-a-streaming-approach"></a>正在載入訊息到管線中使用記憶體中的方法，並使用資料流的方法的比較  
 下列資訊取自 Nic Barden 部落格[ http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx ](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228)。 下表提供摘要的載入訊息比較到管線中使用記憶體中的方法，並使用資料流的方法。  
  
|比較...|串流處理|在記憶體中|  
|----------------------|---------------|---------------|  
|每個訊息的記憶體使用量|低，不論訊息大小|高 （依訊息大小而有所不同）|  
|用來處理 XML 資料的一般類別|內建的 in 和自訂衍生：<br /><br /> XmlTranslatorStream、 XmlReader 和 XmlWriter|XmlDocument、 XPathDocument、 MemoryStream 和 VirtualStream|  
|文件集|不是佳 – 許多未支援和未記載的 BizTalk 類別|非常好-.NET Framework 類別|  
|「 處理邏輯 」 程式碼的位置|-「 連接 」 的讀取器和透過 Execute 方法中的資料流。<br />-實際會以執行讀取器和資料流讀取資料時。|直接從管線元件的執行方法。|  
|data|透過它讀取資料時，重新建立每個換行層級。|讀取、 修改並寫出在之前所呼叫的下一個元件的每個元件。|  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)