---
title: 最佳化管線效能 |Microsoft 文件
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
ms.openlocfilehash: 4311efd0d23e29b63f02fc34b1650a894d29d335
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299550"
---
# <a name="optimizing-pipeline-performance"></a>將管線效能最佳化
本主題描述的管線中的效能最佳化的指導方針[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]方案。  
  
## <a name="best-practices-for-optimizing-performance-of-biztalk-server-pipelines"></a>最佳化效能的 BizTalk Server 管線的最佳作法  
  
1.  因為管線元件對效能有顯著的影響 （例如，通過管線元件會執行 XML 組合器/解譯器管線元件優於最多 30%），請務必執行任何自訂管線元件以最佳方式，才能在您的部署中執行。 如果您想要最大化 BizTalk 應用程式的整體效能，最小化您的自訂管線中的管線元件的數目。  
  
2.  您也可以改善整體效能降低管線元件中的訊息持續性頻率和透過編碼自己的元件備援性降到最低。 每個自訂組件和特別的成品，可能會中斷與自訂追蹤元件，相同的效能，應該測試個別狀況負載過重，系統會使用完整的容量時，觀察其行為並找出任何可能的瓶頸。  
  
3.  如果您要讀取的輸入的訊息內的管線元件，請避免整個文件載入記憶體使用**XmlDocument**物件。 執行個體所需的空間數量**XmlDocument**類別來載入及建立記憶體中表示的 XML 文件是實際的訊息大小的 10 倍。 若要讀取訊息，您應該使用**XmlTextReader**以及下列類別的執行個體的物件：  
  
    -   **VirtualStream (Microsoft.BizTalk.Streaming.dll)** -這個類別的原始程式碼位於管線 SDK 下的兩個位置，如下所示： SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。  
  
    -   **ReadOnlySeekableStream (Microsoft.BizTalk.Streaming.dll)**。  
  
    -   **SeekAbleReadOnlyStream** -這個類別的原始程式碼位於管線 SDK 下的兩個位置，如下所示： SDK\Samples\Pipelines\ArbitraryXPathPropertyHandler 和 SDK\Samples\Pipelines\SchemaResolverComponent\SchemaResolverFlatFileDasm。  
  
4.  使用 PassThruReceive 管線和 PassThruTransmit 標準管線盡可能。 它們不包含任何管線元件，且不會執行任何處理的訊息。 基於這個理由，他們可以確保在接收或傳送訊息的最大效能。 如果您要將二進位文件發佈到 BizTalk MessageBox 和 PassThruTransmit 管線的傳送埠上，如果您需要傳送出二進位訊息，您可以使用 PassThruReceive 管線的接收位置上。 您也可以在繫結至協調流程，如果訊息已格式化，並已準備好要傳送的實體傳送埠上使用 PassThruTransmit 管線。 您必須使用不同的方式，如果您需要完成下列動作之一：  
  
    -   升級屬性輸入的 XML 或一般檔案訊息的內容。  
  
    -   適用於接收位置內的對應。  
  
    -   適用於訂閱的訊息的協調流程中的對應。  
  
    -   套用訂閱了訊息的傳送埠上的對應。  
  
     若要完成其中一個動作，您必須探查和探索文件類型的接收管線內並指派 MessageType 內容屬性 （命名空間 #root 名稱） 值。 這項作業通常被透過解譯器元件，例如 Xml 解譯器元件 (XmlDasmComp) 或一般檔案解譯器元件 (FFDasmComp)。 在此情況下，您需要使用標準 （比方說，XmlReceive 管線） 或自訂管線，其中包含標準或自訂解譯器元件。  
  
5.  取得資源越好並發行這些儘早越好。 比方說，如果您要在資料庫上存取資料，請開啟連接晚盡可能並儘快將它關閉。 使用 C# using 陳述式隱含地發行可處置的物件或 finally 區塊的 catch-try-finally 陳述式來明確處置物件。 檢測您的原始程式碼，以便輕鬆地偵錯您的元件。  
  
6.  排除任何您並非絕對必要，以加速處理訊息的管線元件。  
  
7.  內接收管線中，您應該在只有在訊息路由 （協調流程、 傳送埠） 或降級的訊息內容屬性 （傳送埠） 必須升級至訊息內容的項目。  
  
8.  如果您需要以納入中繼資料訊息，而且您不使用中繼資料的輸入路由或降級的目的，使用**IBaseMessageContext.Write**方法，而非**IBaseMessageContext.Promote**方法。  
  
9. 如果您要使用 XPath 運算式的訊息中擷取資訊，請避免整個文件載入記憶體使用**XmlDocument**物件只是為了使用**SelectNodes**或**SelectSingleNode**方法。 或者，使用中所述的技巧[最佳化記憶體使用量與 Streaming](../technical-guides/optimizing-memory-usage-with-streaming.md)。  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-pipelines"></a>使用資料流載入在管線中的訊息時所需的記憶體使用量降到最低  
 下列技術會描述如何載入在管線中的訊息時，將訊息的記憶體使用量降到最低。  
  
### <a name="use-readonlyseekablestream-and-virtualstream-to-process-a-message-from-a-pipeline-component"></a>使用 ReadOnlySeekableStream 和 VirtualStream 來處理來自管線元件的訊息  
 公認的最佳做法是避免將整個訊息載入記憶體內的管線元件。 最好的方法是將使用自訂資料流實作，然後再為已讀取要求的輸入資料流、 自訂資料流實作會包裝基礎資料流讀取和處理資料讀取時 （以純粹的串流處理方式）。 這可以是很難實作，而且不可能，根據所需的資料流處理。 在此情況下，使用**ReadOnlySeekableStream**和**VirtualStream** Microsoft.BizTalk.Streaming.dll 所公開的類別。 中也會提供這些實作[任意 XPath 屬性處理常式 （BizTalk Server 範例）](http://go.microsoft.com/fwlink/?LinkId=160069) (http://go.microsoft.com/fwlink/?LinkId=160069) BizTalk SDK 中。**ReadOnlySeekableStream**可確保資料指標可以重新定位到資料流的開頭。 **VirtualStream**會使用 MemoryStream 就內部而言，除非大小已超過指定臨界值，在此情況下則會寫入資料流至檔案系統。 使用下列兩個資料流中組合 (使用**VirtualStream**為永續性儲存體**ReadOnlySeekableStream**) 提供 「 seekability 」 和 「 檔案系統的溢位 」 功能。 這適合處理大型訊息而不將整個訊息載入記憶體。 下列程式碼可用於管線元件中實作這項功能。  
  
```  
int bufferSize = 0x280;  
int thresholdSize = 0x100000;  
Stream vStream = new VirtualStream(bufferSize, thresholdSize);  
Stream seekStream = new ReadOnlySeekableStream(inboundStream, vStream, bufferSize);  
```  
  
 此程式碼藉由公開 bufferSize 提供 「 溢位閾值 」，而且 thresholdSize 變數在每個接收位置或傳送埠組態。 然後可以由開發人員或系統管理員針對不同的訊息類型和不同的組態 （例如 32 位元與調整此溢位臨界值64 位元)。  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-given-ibasemessage-object-from-within-a-custom-pipeline-component"></a>使用 XPathReader 和 XPathCollection 擷取給定的 IBaseMessage 物件，從自訂管線元件中。  
 如果需要從 XML 文件，而不是使用特定值**SelectNodes**和**SelectSingleNode** XmlDocument 類別所公開的方法使用 XPathReader 類別的執行個體Microsoft.BizTalk.XPathReader.dll 組件所提供，如下列程式碼範例所示。  
  
> [!NOTE]  
>  特別是，使用 SelectNodes 或 SelectSingleNode XmlDocument 可能會提供更佳的效能比使用 XPathReader，但是 XPathReader 可讓您將您的應用程式的一般記憶體設定檔較小的訊息。  
  
 這個範例示範如何使用 XPathReader 和 XPathCollection 擷取給定**IBaseMessage**物件內的自訂管線元件。  
  
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
  
## <a name="use-xmlreader-and-xmlwriter-with-xmltranslatorstream-to-process-a-message-from-a-pipeline-component"></a>使用 XMLReader 和 XMLWriter XMLTranslatorStream 來處理訊息的管線元件  
 實作自訂管線元件會使用以資料流的方法，另一個方法是使用.NET **XmlReader**和**XmlWriter**類別搭配**XmlTranslatorStream** BizTalk Server 所提供的類別。 例如， **NamespaceTranslatorStream** Microsoft.BizTalk.Pipeline.Components 組件所包含的類別繼承自**XmlTranslatorStream**而且可用來取代舊的命名空間以新資料流中包含的 XML 文件中。 若要使用這項功能內的自訂管線元件，您可以包裝原始資料流的新執行個體訊息內文部分的**NamespaceTranslatorStream**類別，並傳回第二個。 以這種方式將傳入的訊息未讀取或處理在管線元件，但在相同管線的後續元件所讀取的資料流，或最後取用文件發佈至 BizTalk Server 之前，訊息代理程式時，才MessageBox。  
  
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
  
## <a name="using-resourcetracker-in-custom-pipeline-components"></a>自訂管線元件中使用 ResourceTracker  
 管線元件應該管理其建立之物件的存留期和執行記憶體回收，因為已不再需要這些物件。  如果管線元件想到結束的管線執行時，最後一個物件的存留期，則您必須將這類物件加入您的管線可能會從管線內容擷取資源追蹤程式。  
  
 資源追蹤程式會使用下列類型的物件：  
  
-   資料流物件  
  
-   COM 物件  
  
-   IDisposable 物件  
  
 訊息引擎可確保在適當的時間之後完全執行管線，不論它是否成功或失敗,，並釋出所有原生資源加入至資源追蹤程式。 資源追蹤程式執行個體以及它會追蹤物件存留期是由管線內容物件來管理。 管線內容可供所有類型的管線元件，透過實作 IPipelineContext 介面的物件。  
  
 例如，下列程式碼片段會說明如何在自訂管線元件中使用 ResourceTracker 屬性的範例。 若要使用 ResourceTracker 屬性，程式碼片段會使用下列參數`IPipelineContext.ResourceTracker.AddResource`。 在此參數：  
  
-   IPipelineContext 介面會定義用來存取所有的文件處理特定介面的方法。  
  
-   ResourceTracker 屬性參考 IPipelineContext，而且用來追蹤會在管線處理結尾明確處置的物件。  
  
-   ResourceTracker.AddResource 方法用來追蹤 COM 物件、 可處置的物件和資料流，並應該一定可以用在自訂管線元件內來明確關閉 （資料流）、 dispose （IDisposable 物件） 或這些釋放 （COM 物件）訊息發佈到 BizTalk MessageBox 時，資源類型。  
  
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
  
## <a name="comparison-of-loading-messages-into-pipelines-using-an-in-memory-approach-and-using-a-streaming-approach"></a>載入訊息至管線，使用記憶體中的方法與使用資料流處理方式的比較  
 下列資訊取自 Nic Barden 部落格、 [http://blogs.objectsharp.com/cs/blogs/nbarden/archive/2008/04/14/developing-streaming-pipeline-components-part-1.aspx](http://go.microsoft.com/fwlink/?LinkId=160228) (http://go.microsoft.com/fwlink/?LinkId=160228)。 下表提供摘要的比較載入訊息至管線，使用記憶體中的方法與使用資料流的方式。  
  
|比較...|串流處理|在記憶體中|  
|----------------------|---------------|---------------|  
|每個訊息的記憶體使用量|低，而不管訊息大小|高 （訊息大小而有所不同）|  
|用來處理 XML 資料的一般類別|內建和自訂中的衍生：<br /><br /> XmlTranslatorStream、 XmlReader 和 XmlWriter|XmlDocument、 XPathDocument、 MemoryStream 和 VirtualStream|  
|文件集|不良 – 許多未支援和未記載的 BizTalk 類別|很好的.NET Framework 類別|  
|「 處理邏輯 」 程式碼的位置|-「 連接 」 讀取器和透過 Execute 方法中的資料流。<br />-實際的執行會發生問題的讀取器和資料流中讀取資料。|直接從管線元件的執行方法。|  
|data|透過其讀取資料時，重新建立每個文繞圖層級。|讀取、 修改並寫出每個元件在下一個元件呼叫之前。|  
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)