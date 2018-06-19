---
title: 串流處理 Oracle 資料庫 LOB 資料類型使用 WCF 通道模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- streaming, Oracle LOB data types
- WCF channel model, streaming Oracle LOB data types
ms.assetid: 513a7cb8-495d-4019-bce1-b5babca3629f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0ee2f8d1c90f69a206a3006398d52e67f819e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22215790"
---
# <a name="streaming-oracle-database-lob-data-types-using-the-wcf-channel-model"></a><span data-ttu-id="be62b-102">資料流處理的 Oracle 資料庫 LOB 資料類型使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="be62b-102">Streaming Oracle Database LOB Data Types Using the WCF Channel Model</span></span>
<span data-ttu-id="be62b-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]支援端對端的資料流的特定作業的 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="be62b-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] supports end-to-end streaming of LOB data for certain operations.</span></span> <span data-ttu-id="be62b-104">本主題中的各節說明如何實作 LOB 資料的資料流，當您使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="be62b-104">The sections in this topic describe how to implement streaming for LOB data when you use the WCF channel model.</span></span>  
  
 <span data-ttu-id="be62b-105">如需配接器支援 LOB 資料類型的資料流的背景資訊，請參閱[串流處理大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="be62b-105">For background information about how the adapter supports streaming of LOB data types, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span> <span data-ttu-id="be62b-106">您應該閱讀本主題後再繼續。</span><span class="sxs-lookup"><span data-stu-id="be62b-106">You should read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="be62b-107">位於 SDK 範例隨附的範例示範 LOB 資料流[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="be62b-107">A sample that demonstrates LOB data streaming is available in the SDK samples included with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="be62b-108">如需詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="be62b-108">For more information, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="streaming-outbound-messages-to-the-adapter"></a><span data-ttu-id="be62b-109">資料流的輸出訊息，配接器</span><span class="sxs-lookup"><span data-stu-id="be62b-109">Streaming Outbound Messages to the Adapter</span></span>  
 <span data-ttu-id="be62b-110">配接器支援 UpdateLOB 作業的要求訊息的串流的端對端 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="be62b-110">The adapter supports end-to-end LOB data streaming for the request message for the UpdateLOB operation.</span></span>  
  
 <span data-ttu-id="be62b-111">若要支援端對端的資料流上 UpdateLOB WCF 通道模型中的作業，您必須：</span><span class="sxs-lookup"><span data-stu-id="be62b-111">To support end-to-end streaming on UpdateLOB operations in the WCF channel model, you must:</span></span>  
  
1.  <span data-ttu-id="be62b-112">設定**UseAmbientTransaction**繫結屬性為 true。</span><span class="sxs-lookup"><span data-stu-id="be62b-112">Set the **UseAmbientTransaction** binding property to true.</span></span>  
  
2.  <span data-ttu-id="be62b-113">實作**System.ServiceModel.Channels.BodyWriter**能夠串流處理 LOB 資料 （執行 LOB 資料資料流處理的節點值）。</span><span class="sxs-lookup"><span data-stu-id="be62b-113">Implement a **System.ServiceModel.Channels.BodyWriter** that is capable of streaming the LOB data (performing node-value streaming on the LOB data).</span></span>  
  
3.  <span data-ttu-id="be62b-114">執行 UpdateLOB 作業在交易範圍內。</span><span class="sxs-lookup"><span data-stu-id="be62b-114">Perform the UpdateLOB operation within a transaction scope.</span></span>  
  
4.  <span data-ttu-id="be62b-115">建立**System.ServiceModel.Message**用來叫用作業，藉由提供與此訊息本文**BodyWriter**使用的適當多載**Message.Create**方法。</span><span class="sxs-lookup"><span data-stu-id="be62b-115">Create the **System.ServiceModel.Message** used to invoke the operation by supplying the message body with this **BodyWriter** using an appropriate overload of the **Message.Create** method.</span></span>  
  
### <a name="setting-the-useambienttransaction-binding-property"></a><span data-ttu-id="be62b-116">設定繫結屬性 UseAmbientTransaction</span><span class="sxs-lookup"><span data-stu-id="be62b-116">Setting the UseAmbientTransaction Binding Property</span></span>  
 <span data-ttu-id="be62b-117">下列範例示範如何建立的繫結[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]並設定**UseAmbientTransaction**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="be62b-117">The following example shows how to create a binding for the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and set the **UseAmbientTransaction** binding property.</span></span>  
  
```  
// Create binding  
OracleDBBinding odbBinding = new OracleDBBinding();  
  
//set the binding property  
binding.UseAmbientTransaction = true;  
  
```  
  
### <a name="implementing-a-bodywriter"></a><span data-ttu-id="be62b-118">實作 BodyWriter</span><span class="sxs-lookup"><span data-stu-id="be62b-118">Implementing a BodyWriter</span></span>  
 <span data-ttu-id="be62b-119">下列範例示範實作**BodyWriter**執行節點值的資料流。</span><span class="sxs-lookup"><span data-stu-id="be62b-119">The following example shows an implementation of a **BodyWriter** that performs node-value streaming.</span></span>  
  
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
        if (chunkSize \<= 0)  
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
  
### <a name="perform-the-operations-within-a-transaction-scope"></a><span data-ttu-id="be62b-120">執行的作業在交易範圍內</span><span class="sxs-lookup"><span data-stu-id="be62b-120">Perform the Operations Within a Transaction Scope</span></span>  
 <span data-ttu-id="be62b-121">下列範例會示範如何在交易範圍內執行作業。</span><span class="sxs-lookup"><span data-stu-id="be62b-121">The following example shows how to perform operations within a transaction scope.</span></span>  
  
```  
// Create a transaction scope  
using(TransactionScope tx = new TransactionScope())  
{  
  // perform operations within the transaction  
  // ...  
  // ...  
  
  //Complete the transaction  
  tx.Complete()  
}  
  
```  
  
### <a name="creating-a-message-by-using-a-bodywriter"></a><span data-ttu-id="be62b-122">使用 BodyWriter 建立訊息</span><span class="sxs-lookup"><span data-stu-id="be62b-122">Creating a Message by using a BodyWriter</span></span>  
 <span data-ttu-id="be62b-123">下列範例示範如何建立 UpdateLOB 要求訊息使用**BodyWriter**在上述範例中。</span><span class="sxs-lookup"><span data-stu-id="be62b-123">The following example shows how to create an UpdateLOB request message using the **BodyWriter** in the preceding example.</span></span> <span data-ttu-id="be62b-124">從檔案讀取訊息資料。</span><span class="sxs-lookup"><span data-stu-id="be62b-124">The message data is read from a file.</span></span>  
  
```  
// Create a transaction scope  
using(TransactionScope tx = new TransactionScope())  
{  
    XmlReader readerIn = XmlReader.Create ("updatelob.xml");  
    // StreamingBodyWrtier class is responsible for streaming  
    StreamingBodyWriter stBW = new StreamingBodyWriter(readerIn, chunkSize);  
  
    Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB",   
    stBW);  
  
    //Send the request message and get the output message  
    OutputMsg = channel.Request(InputMsg);  
  
    tx.Complete();  
}  
  
```  
  
## <a name="streaming-inbound-messages-from-the-adapter"></a><span data-ttu-id="be62b-125">資料流的輸入的訊息從配接器</span><span class="sxs-lookup"><span data-stu-id="be62b-125">Streaming Inbound Messages from the Adapter</span></span>  
 <span data-ttu-id="be62b-126">配接器支援下列的內送訊息的串流的端對端 LOB 資料：</span><span class="sxs-lookup"><span data-stu-id="be62b-126">The adapter supports end-to-end LOB data streaming for the following inbound messages:</span></span>  
  
-   <span data-ttu-id="be62b-127">具有跨函式的回應訊息，或在 OUT 參數包含 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="be62b-127">Response message for functions with OUT or IN OUT parameters that contain LOB data.</span></span> <span data-ttu-id="be62b-128">請注意，記錄型別參數可以包含 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="be62b-128">Note that RECORD TYPE parameters can contain LOB data columns.</span></span>  
  
-   <span data-ttu-id="be62b-129">使用 OUT REF CURSOR 參數 （或傳回值） 包含 LOB 資料的函式的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="be62b-129">Response message for functions with OUT REF CURSOR parameters (or return values) that contain LOB data.</span></span> <span data-ttu-id="be62b-130">這包括在 OUT REF CURSOR 參數的輸出端。</span><span class="sxs-lookup"><span data-stu-id="be62b-130">This includes the output side of IN OUT REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="be62b-131">回應訊息中的程序或在 OUT 參數包含 LOB 資料。</span><span class="sxs-lookup"><span data-stu-id="be62b-131">Response message for procedures with IN or IN OUT parameters that contain LOB data.</span></span> <span data-ttu-id="be62b-132">請注意，記錄型別參數可以包含 LOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="be62b-132">Note that RECORD TYPE parameters can contain LOB data columns.</span></span>  
  
-   <span data-ttu-id="be62b-133">具有包含 LOB 資料的 OUT REF CURSOR 參數的程序的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="be62b-133">Response message for procedures with OUT REF CURSOR parameters that contain LOB data.</span></span> <span data-ttu-id="be62b-134">這包括在 OUT REF CURSOR 參數的輸出端</span><span class="sxs-lookup"><span data-stu-id="be62b-134">This includes the output side of IN OUT REF CURSOR parameters</span></span>  
  
-   <span data-ttu-id="be62b-135">傳回包含 LOB 資料的結果集的 SQLEXECUTE 作業的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="be62b-135">Response message for SQLEXECUTE operations that return result sets that contain LOB data.</span></span>  
  
-   <span data-ttu-id="be62b-136">設定資料表或檢視表傳回結果中的 LOB 資料的 Select 作業的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="be62b-136">Response message for Table or view Select operations that return LOB data in the result set.</span></span>  
  
-   <span data-ttu-id="be62b-137">（輸入） 的 POLLINGSTMT 作業的要求訊息</span><span class="sxs-lookup"><span data-stu-id="be62b-137">Request message for the (inbound) POLLINGSTMT operation</span></span>  
  
 <span data-ttu-id="be62b-138">若要支援端對端的資料流中的 WCF 通道模型的輸入訊息上，您必須：</span><span class="sxs-lookup"><span data-stu-id="be62b-138">To support end-to-end streaming on an inbound message in the WCF channel model, you must:</span></span>  
  
1.  <span data-ttu-id="be62b-139">實作**System.Xml.XmlDictionaryWriter**能夠串流處理 LOB 資料 （執行 LOB 資料資料流處理的節點值）。</span><span class="sxs-lookup"><span data-stu-id="be62b-139">Implement a **System.Xml.XmlDictionaryWriter** that is capable of streaming the LOB data (performing node-value streaming on the LOB data).</span></span>  
  
2.  <span data-ttu-id="be62b-140">取用**訊息**叫用**WriteBodyContents**方法與這個**XmlDictionaryWriter**。</span><span class="sxs-lookup"><span data-stu-id="be62b-140">Consume the **Message** by invoking **WriteBodyContents** method with this **XmlDictionaryWriter**.</span></span>  
  
### <a name="implementing-an-xmldictionarywriter"></a><span data-ttu-id="be62b-141">實作 XmlDictionaryWriter</span><span class="sxs-lookup"><span data-stu-id="be62b-141">Implementing an XmlDictionaryWriter</span></span>  
 <span data-ttu-id="be62b-142">下列範例示範實作**XmlDictionaryWriter**執行節點值的資料流。</span><span class="sxs-lookup"><span data-stu-id="be62b-142">The following example shows an implementation of an **XmlDictionaryWriter** that performs node-value streaming.</span></span>  
  
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
  
### <a name="consuming-a-message-by-using-an-xmldictionarywriter"></a><span data-ttu-id="be62b-143">使用 XmlDictionaryWriter 取用訊息</span><span class="sxs-lookup"><span data-stu-id="be62b-143">Consuming a Message by using an XmlDictionaryWriter</span></span>  
 <span data-ttu-id="be62b-144">下列範例示範如何使用 資料表選取回應訊息使用**FileXmlWriter**上述範例中實作。</span><span class="sxs-lookup"><span data-stu-id="be62b-144">The following example shows how to consume a table Select response message using the **FileXmlWriter** implemented in the preceding example.</span></span> <span data-ttu-id="be62b-145">( **FileWriter**類別已由分為子類別建立**XmlDictionaryWriter**。)此範例會使用**IRequestChannel**通道來叫用選取的作業。</span><span class="sxs-lookup"><span data-stu-id="be62b-145">(The **FileWriter** class was created by sub-classing **XmlDictionaryWriter**.) The example uses an **IRequestChannel** channel to invoke the Select operation.</span></span> <span data-ttu-id="be62b-146">已省略的通道建立詳細資料。</span><span class="sxs-lookup"><span data-stu-id="be62b-146">The details of the channel creation have been omitted.</span></span> <span data-ttu-id="be62b-147">選取要求訊息會從檔案讀取，並選取回應訊息寫入至檔案。</span><span class="sxs-lookup"><span data-stu-id="be62b-147">The Select request message is read from a file and the Select response message is written to a file.</span></span>  
  
```  
// Read Select message body from a file  
XmlReader readerIn = XmlReader.Create("select.xml");  
Message InputMsg = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/Select", readerIn);  
  
Message OutputMsg = channel.Request(InputMsg);  
  
// Streaming response message to select_output.xml using the custom XmlDictionaryWriter;  
FileXmlWriter fileXmlWriter = new FileXmlWriter("select_output.xml");  
OutputMsg.WriteBodyContents(fileXmlWriter);  
fileXmlWriter.Flush();  
fileXmlWriter.Close();  
  
// Streaming complete close output message;  
OutputMsg.Close();  
```  
  
 <span data-ttu-id="be62b-148">下列 XML 會說明在 Select 作業的要求訊息 （select.xml 檔案的內容）。</span><span class="sxs-lookup"><span data-stu-id="be62b-148">The following XML shows the request message (contents of the select.xml file) for the Select operation.</span></span> <span data-ttu-id="be62b-149">CUSTOMER 資料表中包含名為相片的 BLOB 資料行。</span><span class="sxs-lookup"><span data-stu-id="be62b-149">The CUSTOMER table contains a BLOB column named PHOTO.</span></span>  
  
```  
<Select xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <COLUMN_NAMES>*</COLUMN_NAMES>  
  <FILTER>NAME='Kim Ralls'</FILTER>  
</Select>  
```  
  
## <a name="see-also"></a><span data-ttu-id="be62b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="be62b-150">See Also</span></span>  
 [<span data-ttu-id="be62b-151">開發 Oracle 資料庫應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="be62b-151">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)