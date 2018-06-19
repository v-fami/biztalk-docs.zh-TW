---
title: 最佳化使用資料流的記憶體使用量 |Microsoft 文件
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
ms.openlocfilehash: 0e1707007eab19a86e4fabedfe9e16bfa9c8fc59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299342"
---
# <a name="optimizing-memory-usage-with-streaming"></a>最佳化使用資料流的記憶體使用量
本主題提供使用資料流處理模式時傳送或接收大型訊息使用 WCF 傳輸，或載入協調流程中的訊息時，訊息的記憶體使用量降到最低的建議。   
當協調流程中使用程式碼，以讀取訊息的內容，請避免使用 XmlDocument 變數。 載入 XmlDocument 變數中的訊息會帶來大量負擔，特別是針對大型訊息。 此額外負荷會依據記憶體使用量並處理以建置記憶體中的結構。 使用 XmlDocument 執行個體強制整個訊息內容以先載入到記憶體，才能建立物件圖形的文件物件模組 (DOM)。 這個類別的執行個體所使用總數量可以是記憶體的實際的訊息大小的 10 倍左右。 如需有關載入 XmlDocument 變數中的訊息時所需的記憶體使用量的詳細資訊，請參閱[第 9 章 – 改善 XML 效能](http://go.microsoft.com/fwlink/?LinkId=139772)(http://go.microsoft.com/fwlink/?LinkId=139772) MSDN 上。   
本主題的其餘部分提供替代方法來讀取訊息的內容，不需要載入 XmlDocument 變數中的訊息。  
  
## <a name="use-streaming-when-sending-or-receiving-large-messages-with-a-wcf-transport"></a>使用資料流傳送或接收與 WCF 傳輸大型訊息時  
 當傳送或接收與 WCF 傳輸大型訊息時，使用 Wcf-custom 或 Wcf-customisolated 配接器，並設定以支援繫結類型**傳輸模式 = Streamed**選項，例如下列繫結：  
  
-   **basicHttpBinding + BasicHttpBindingElement，傳輸模式 = Streamed**  
  
-   **netTcpBinding + NetTcpBindingElement，傳輸模式 = Streamed**  
  
-   **customBinding + HttpTransportElement，傳輸模式 = Streamed**  
  
-   **customBinding + ConnectionOrientedTransportElement，傳輸模式 = Streamed**  
  
 選擇以及支援的繫結的 Wcf-custom 或 Wcf-customisolated 配接器**傳輸模式 = Streamed**選項將會實作的檔案系統的大型訊息資料流，如有需要並會減少潛在記憶體不足的問題。  
  
## <a name="use-streaming-to-minimize-the-memory-footprint-required-when-loading-messages-in-orchestrations"></a>使用資料流載入協調流程中的訊息時所需的記憶體使用量降到最低  
 下列技術會描述如何將訊息載入協調流程時，將訊息的記憶體使用量降至最低。  
  
### <a name="use-an-xlangmessage-variable-to-process-the-contents-of-a-message-or-message-part"></a>使用 XLANGMessage 變數來處理訊息或訊息部分的內容  
 當從協調流程的訊息傳遞到.NET 類別庫中，不要傳遞它們做為 XmlDocument 變數，如本主題中; 稍早所述的原因請改用 XLANGMessage 變數。 下列技術說明方法來讀取訊息或訊息部分使用 XLANGMessage 變數。  
  
-   **處理訊息與 XMLReader** -若要處理的訊息與 XmlReader 執行個體、 將訊息傳遞給.NET 程式碼為 XLANGMessage，和擷取使用 XmlReader 用組件內容。  
  
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
  
-   **將訊息內容擷取成 streamreader 之類的字串**-XmlDocument 協調流程中的常見用途之一是使用 XmlDocument.OuterXml() XML 字串形式擷取的訊息。 下列程式碼範例說明的替代方法為使用 XLANGMessage 變數的字串擷取訊息。  
  
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
  
-   **簡單.NET 訊息的內容擷取成字串**-如果訊息的類型是簡單的.NET 類型，您可以擷取為該類型的訊息。 例如，若要取得訊息當成字串，將訊息傳遞至為 XLANGMessage 的.NET 程式碼並擷取為字串的部分內容。  
  
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
  
-   **將訊息內容擷取成資料流**-若要取得訊息資料流的形式，將訊息傳遞至為 XLANGMessage 的.NET 程式碼和擷取組件內容，做為資料流。  
  
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
  
-   **將訊息內容擷取成.NET 物件**-若要取得訊息的.NET 物件、 將訊息傳遞至為 XLANGMessage 的.NET 程式碼和.NET 類別的執行個體的形式擷取組件內容。 建立這第二個 Xml 結構描述使用 Visual Studio 2010 所提供的 XML 結構描述定義工具 (Xsd.exe) 工具的訊息。  
  
    > [!NOTE]  
    >  這個做法在只有小型訊息時，才會有效。 否則，這個方法可能會在還原序列化成.NET 物件的實際訊息的重大額外負荷。  
  
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
>  使用**dispose （)** XLANGMessage 參數所公開的.NET 程式碼在傳回前方法來說特別重要，在迴圈案例和長時間執行的協調流程可以累積的執行個體XLANGMessage 物件，但未釋放它們經過一段時間。 如需呼叫訊息的詳細資訊。Dispose （） 這種方式，請參閱[訊息表示為 XLANGMessage](http://go.microsoft.com/fwlink/?LinkId=139775) (http://go.microsoft.com/fwlink/?LinkId=139775) 中的 BizTalk Server 文件。 本主題也提供使用 IStreamFactory 建構 XLANGMessage 變數中使用資料流為基礎的方法的使用者程式碼的最佳作法。  
  
 如需不同的方式來處理 XLANGMessage 內叫用的協調流程的協助程式元件的詳細資訊，請參閱下列主題：  
  
-   [4 個不同的方式來處理 XLANGMessage 第 1 部分協調流程所叫用的協助程式元件內](http://go.microsoft.com/fwlink/?LinkID=210420)(http://go.microsoft.com/fwlink/?LinkID=210420)。  
  
-   [4 個不同的方式來處理協調流程第 2 部分所叫用的協助程式元件內 XLANGMessage](http://go.microsoft.com/fwlink/?LinkID=210421) (http://go.microsoft.com/fwlink/?LinkID=210421)。  
  
### <a name="using-xpathreader-and-xpathcollection-to-extract-a-value-from-an-xlangmessage-object-from-a-method-invoked-by-an-orchestration"></a>使用 XPathReader 和 XPathCollection 從協調流程叫用的方法從 XLANGMessage 物件中擷取值  
 避免使用 XMLDocument 類別讀取 XML 訊息的內容，從自訂程式碼，例如自訂管線元件或協調流程所叫用的 helper 類別。 當使用 XMLDocument 執行個體載入 XML 訊息時，整個訊息載入記憶體，也就是沒有效率，而且可能需要最多 10 倍的實際大小的訊息的記憶體。 讀取 XML 訊息的內容更有效率的方式是使用資料流技術之一 Microsoft.BizTalk.Streaming.dll 組件所提供的資料流類別包裝原始的資料流。 載入大型訊息時，這項技術就特別有用。  
  
 如果特定值要從 XML 文件，而不是使用 XmlDocument 類別所公開的 SelectNodes 和 SelectSingleNode 方法使用 Microsoft.BizTalk.XPathReader.dll 組件所提供的 XPathReader 類別的執行個體下列程式碼範例所示。  
  
-   此範例說明使用 XPathReader 和 XPathCollection 從協調流程叫用的方法內 XLANGMessage 物件擷取指定的值。  
  
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
  
## <a name="see-also"></a>另請參閱  
 [最佳化 BizTalk Server 應用程式](../technical-guides/optimizing-biztalk-server-applications.md)