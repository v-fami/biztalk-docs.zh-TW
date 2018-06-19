---
title: 資料流中使用 WCF 通道模型的 SAP 的一般檔案 Idoc |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF channel model, streaming flat-file IDOCs
ms.assetid: 5010e215-d8d0-47c8-93a6-20cfdeff2951
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8de850022a03a3be0310da3022a2cf496c94f30
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25966036"
---
# <a name="stream-flat-file-idocs-in-sap-using-the-wcf-channel-model"></a>使用 WCF 通道模型的 SAP 中的資料流一般檔案 Idoc
[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]支援節點值的 SendIdoc 和 ReceiveIdoc 作業的串流。 這些作業用來傳送和接收一般檔案 （字串） 的 Idoc 與配接器。 在這兩種作業中，整個 IDOC 的資料包含在單一節點下的字串 (\<idocData\>)。 對於大型的 Idoc，串流 IDOC 資料配接器與您的程式碼之間可能節省大量記憶體資源。  
  
 如需配接器支援資料流處理的背景資訊，請參閱[資料流與 SAP 配接器](../../adapters-and-accelerators/adapter-sap/streaming-and-the-sap-adapter.md)。 您應該閱讀本主題後再繼續。  
  
 本主題中的各節說明如何實作資料流 SendIdoc 和 ReceiveIdoc 作業，當您使用 WCF 通道模型的節點值。  
  
## <a name="streaming-outbound-flat-file-idocs-to-the-adapter"></a>資料流的輸出一般檔案 Idoc，配接器  
 配接器支援的節點值的資料流處理 SendIdoc 作業的要求訊息。  
  
 若要支援的節點值的資料流處理 SendIdoc WCF 通道模型中的作業，您必須：  
  
1.  實作**System.ServiceModel.Channels.BodyWriter**能夠串流 IDOC 資料 （執行節點值的資料流處理的 IDOC 資料）。  
  
2.  建立**System.ServiceModel.Message**用來叫用作業，藉由提供與此訊息本文**BodyWriter**使用的適當多載**Message.Create**方法。  
  
### <a name="implementing-a-bodywriter"></a>實作 BodyWriter  
 下列範例示範實作**BodyWriter**執行節點值的資料流。  
  
```  
/// <summary>  
/// This class overrides the OnWriteBodyContents function to do node-value streaming  
/// </summary>  
class StreamingBodyWriter : BodyWriter, IDisposable  
{  
    XmlReader m_reader = null;  
  
    int m_chunkSize;  
    /// <summary>  
    /// Initializes the body writer  
    /// </summary>  
    /// <param name="reader">Reader for input</param>  
    /// <param name="chunkSize">The chunksize in which the data is passed to adapter</param>  
    public StreamingBodyWriter(XmlReader reader, int chunkSize)  
        : base(false)  
    {  
        m_reader = reader;  
        if (chunkSize <= 0)  
            throw new ApplicationException("ChunkSize should be a positive value");  
        m_chunkSize = chunkSize;  
    }  
  
    protected override void OnWriteBodyContents(XmlDictionaryWriter writer)  
    {  
        if (m_reader == null)  
            throw new ApplicationException("Reader cannot be null");  
  
        while (m_reader.Read())  
        {  
            switch (m_reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    writer.WriteStartElement(m_reader.LocalName, m_reader.NamespaceURI);  
                    break;  
                case XmlNodeType.Text:  
                    #region Streaming Code  
                    char[] tempBuffer = new char[m_chunkSize];  
                    int length = 0;  
                    while ((length = m_reader.ReadValueChunk(tempBuffer, 0, m_chunkSize)) > 0)  
                    {  
                        writer.WriteString(new String(tempBuffer, 0, length));  
                    }  
                    #endregion  
                    break;  
                case XmlNodeType.EndElement:  
                    writer.WriteEndElement();  
                    break;  
            }  
        }  
  
    }  
  
    #region IDisposable Members  
  
    public void Dispose()  
    {  
        if (m_reader != null)  
        {  
            m_reader.Close();  
            m_reader = null;  
        }  
    }  
  
    #endregion  
}  
```  
  
### <a name="creating-a-message-by-using-a-bodywriter"></a>使用 BodyWriter 建立訊息  
 下列範例示範如何建立 SendIdoc 要求訊息使用**BodyWriter**在上述範例中。 從檔案讀取訊息資料。  
  
```  
XmlReader readerIn = XmlReader.Create ("sendidoc.xml");  
// StreamingBodyWrtier class is responsible for streaming  
StreamingBodyWriter stBW = new StreamingBodyWriter(readerIn, chunkSize);  
  
Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.SAP/2007/03/Idoc/SendIdoc",   
    stBW);  
  
```  
  
## <a name="streaming-inbound-flat-file-idocs-from-the-adapter"></a>從配接器的資料流輸入的一般檔案 Idoc  
 您輸入的 ReceiveIdoc 作業中接收一般檔案 Idoc。 配接器支援的節點值的資料流處理 ReceiveIdoc 作業的要求訊息。  
  
 若要支援的節點值的資料流處理 ReceiveIdoc WCF 通道模型中的作業，您必須：  
  
1.  實作**System.Xml.XmlDictionaryWriter**能夠串流 IDOC 資料 （執行節點值的資料流處理的 IDOC 資料）。  
  
2.  取用**訊息**叫用其**WriteBodyContents**方法與這個**XmlDictionaryWriter**。  
  
### <a name="implementing-an-xmldictionarywriter"></a>實作 XmlDictionaryWriter  
 下列範例示範實作**XmlDictionaryWriter**執行節點值的資料流。  
  
```  
using System;  
using System.Xml;  
using System.Text;  
  
class FileXmlWriter : XmlDictionaryWriter  
{  
    XmlTextWriter xts;  
  
    public FileXmlWriter(string file)  
    {  
        xts = new XmlTextWriter(file, Encoding.UTF8);  
    }  
  
    public override void WriteBase64(byte[] buffer, int index, int count)  
    {  
        xts.WriteBase64(buffer, index, count);  
    }  
  
    public override void WriteCData(string text)  
    {  
        xts.WriteCData(text);  
    }  
  
    public override void WriteCharEntity(char ch)  
    {  
        xts.WriteCharEntity(ch);  
    }  
  
    public override void WriteChars(char[] buffer, int index, int count)  
    {  
        xts.WriteChars(buffer, index, count);  
    }  
  
    public override void WriteComment(string text)  
    {  
        xts.WriteComment(text);  
    }  
  
    public override void WriteDocType(string name, string pubid, string sysid, string subset)  
    {  
        xts.WriteDocType(name, pubid, sysid, subset);  
    }  
  
    public override void WriteEndAttribute()  
    {  
        xts.WriteEndAttribute();  
    }  
  
    public override void WriteEndDocument()  
    {  
        xts.WriteEndDocument();  
    }  
  
    public override void WriteEndElement()  
    {  
        xts.WriteEndElement();  
    }  
  
    public override void WriteEntityRef(string name)  
    {  
        xts.WriteEntityRef(name);  
    }  
  
    public override void WriteFullEndElement()  
    {  
        xts.WriteFullEndElement();  
    }  
  
    public override void WriteProcessingInstruction(string name, string text)  
    {  
        xts.WriteProcessingInstruction(name, text);  
    }  
  
    public override void WriteRaw(string data)  
    {  
        xts.WriteRaw(data);  
    }  
  
    public override void WriteRaw(char[] buffer, int index, int count)  
    {  
        xts.WriteRaw(buffer, index, count);  
    }  
  
    public override void WriteStartAttribute(string prefix, string localName, string ns)  
    {  
        xts.WriteStartAttribute(prefix, localName, ns);  
    }  
  
    public override void WriteStartDocument(bool standalone)  
    {  
        xts.WriteStartDocument(standalone);  
    }  
  
    public override void WriteStartDocument()  
    {  
        xts.WriteStartDocument();  
    }  
  
    public override void WriteStartElement(string prefix, string localName, string ns)  
    {  
        xts.WriteStartElement(localName);  
    }  
  
    public override void WriteString(string text)  
    {  
        xts.WriteString(text);  
    }  
  
    public override void WriteSurrogateCharEntity(char lowChar, char highChar)  
    {  
        xts.WriteSurrogateCharEntity(lowChar, highChar);  
    }  
  
    public override void WriteWhitespace(string ws)  
    {  
        xts.WriteWhitespace(ws);  
    }  
  
    public override void Close()  
    {  
        xts.Close();  
    }  
  
    public override void Flush()  
    {  
        xts.Flush();  
    }  
  
    public override string LookupPrefix(string ns)  
    {  
        return xts.LookupPrefix(ns);  
    }  
  
    public override WriteState WriteState  
    {  
        get { return xts.WriteState; }  
    }  
  
}  
```  
  
### <a name="consuming-a-message-by-using-an-xmldictionarywriter"></a>使用 XmlDictionaryWriter 取用訊息  
 下列範例示範如何使用 ReceiveIdoc 要求訊息使用**FileXmlWriter**上述範例中實作。 ( **FileWriter**類別已由分為子類別建立**XmlDictionaryWriter**。)此範例會使用**IReplyChannel**通道以接收 ReceiveIdoc 作業。 已省略的通道建立詳細資料。 ReceiveIdoc 要求訊息會寫入至檔案。  
  
```  
// Receive the ReceiveIdoc request message from the adapter.  
RequestContext rc = channel.ReceiveRequest();  
Message inputMsg = rc.RequestMessage;  
  
// Stream the request message to received_idoc.xml using the custom XmlDictionaryWriter.  
FileXmlWriter fileXmlWriter = new FileXmlWriter("received_idoc.xml");  
inputMsg.WriteBodyContents(fileXmlWriter);  
fileXmlWriter.Flush();  
fileXmlWriter.Close();  
  
```  
  
## <a name="see-also"></a>請參閱  
[使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)