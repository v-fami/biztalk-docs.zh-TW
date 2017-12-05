---
title: "步驟 7： 實作同步輸出的處理常式回應配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4da4d987-03c4-4817-850b-4c5ca2ba7e62
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a2e2679edafd72dc0d64510e7a8566180818f8c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter"></a>步驟 7： 回應配接器實作同步輸出的處理常式
![步驟 7 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")  
  
 **若要完成的時間：** 30 分鐘  
  
 在此步驟中，您可以實作回應配接器的同步輸出的功能。 根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，以支援同步輸出的功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`介面。 回應配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]自動產生一個稱為 EchoAdapterOutboundHandler 的衍生的類別。  
  
 您可以在下列章節中，更新 EchoAdapterOutboundHandler 類別，以取得更深入了解如何實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`、 如何剖析連入的 WCF 要求訊息，以及如何產生外寄 WCF 回應訊息。  
  
## <a name="prerequisites"></a>必要條件  
 在開始此步驟之前，您必須已順利完成[步驟 6： 實作回應配接器中繼資料解析的處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。 基本的認識`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`也很有用。  
  
## <a name="the-ioutboundhandler-interface"></a>IOutboundHandler 介面  
 `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`定義為：  
  
```  
public interface IOutboundHandler : IConnectionHandler, IDisposable  
{  
    Message Execute(Message message, TimeSpan timeout);  
}  
```  
  
 `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`方法會叫用對應的方法，在目標系統上執行內送 WCF 要求訊息，然後再傳回外寄 WCF 回應訊息。 下表中列出的參數定義：  
  
|**參數**|**定義**|  
|-------------------|--------------------|  
|message|內送 WCF 要求訊息。|  
|timeout|應該在其中完成這項作業的時間間隔。 此作業應該擲回`System.TimeoutException`如果在作業完成之前，超出指定的逾時。|  
  
 如果您的配接器正在執行 （沒有任何您的配接器所預期的回應訊息） 的單向傳送，這個方法應該傳回 null。 如果您的配接器正在執行的雙向作業`Microsoft.ServiceModel.Channels.Common.OperationResult`等於`Microsoft.ServiceModel.Channels.Common.OperationResult.Empty%2A`，這個方法會傳回空的內文的 WCF 回應訊息。 否則，它應該傳回 WCF 回應訊息中包含值的主體`Microsoft.ServiceModel.Channels.Common.OperationResult`物件。 若要建構回應動作字串，請使用`Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`。  
  
## <a name="echo-adapter-synchronous-outbound"></a>回應配接器同步輸出  
 根據目標系統的作業，會有許多方式來實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`方法。 回應配接器有三個輸出的作業，並有其指派的節點識別碼和顯示名稱：  
  
-   string [] EchoStrings （字串資料），節點識別碼 = Echo/EchoString，顯示名稱 = EchoString  
  
-   問候語 [] EchoGreetings(Greeting greeting)，節點識別碼 = Echo/EchoGreetings，顯示名稱 = EchoGreetings  
  
-   CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath)，nodeID = Echo/EchoCustomGreetingFromFile，顯示名稱 = EchoGreetings  
  
 若要正確地剖析內送 WCF 要求訊息，並產生外寄 WCF 回應訊息，您必須熟悉下列項目所使用的 SOAP 訊息內[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:  
  
 內送 WCF 要求訊息：  
  
-   WCF 輸入訊息動作 = 作業的節點識別碼  
  
-   內送訊息本文 = 開始本文的元素是\<displayname\>\<參數名稱\>{資料}\</parameter 名稱\>\</displayname\>  
  
 外寄 WCF 回應訊息：  
  
-   WCF 輸出訊息動作 = 作業的節點識別碼 +"/ 回應 」  
  
-   外寄訊息本文 = 開始本文的元素是\<displayname +"Response"\>，後面接著\<displayname +"Result"\>，，後面接著\<datatype\>資料\</datatype\>\</displayname+ 」 結果\>\</displayname +"Response"\>  
  
 例如，作業**string [] （字串資料） EchoStrings**，節點識別碼 = Echo/EchoStrings，和顯示名稱 = EchoStrings:  
  
 WCF 輸入訊息動作 ="Echo/EchoStrings";輸入的主體看起來像這樣，因為參數名稱和`data`。  
  
```  
<EchoStrings>  
<data>{data}  
</data>  
</EchoStrings>  
```  
  
 WCF 輸出訊息動作 ="Echo/EchoStrings/回應 」。與輸出主體看起來像這樣，因為資料類型是**字串**。  
  
```  
<EchoStringsResponse>  
<EchoStringsResult>  
<string>{data}</string>  
</EchoStringsResult>  
</EchoStringsResponse>  
```  
  
 當剖析內送 WCF 要求訊息，您可以使用`System.Xml.XmlDictionaryReader`撰寫 WCF 回應訊息時，請擷取 WCF 訊息; 內的內容，您可以使用`System.Xml.XmlWriter`若要這樣做。  
  
## <a name="implementing-the-ioutboundhandler"></a>實作 IOutboundHandler  
 實作的 Execute 方法`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`。 首先，取得`Microsoft.ServiceModel.Channels.Common.OperationMetadata`物件會根據輸入的訊息動作。 然後，會剖析內送 WCF 訊息，並執行根據每個作業的相關聯的回應功能。 最後，建立外寄 WCF 回應訊息使用的外寄訊息本文格式。  
  
#### <a name="to-implement-the-execute-method-of-the-echoadapteroutboundhandler-class"></a>若要實作 EchoAdapterOutboundHandler 類別的 Execute 方法  
  
1.  在 [方案總管] 中，按兩下**EchoAdapterOutboundHandler.cs**檔案。  
  
2.  在 Visual Studio 編輯器中，加入下面兩個 using 指示詞至一組現有的 using 指示詞。  
  
    ```csharp  
    using System.Xml;  
    using System.IO;  
    ```  
  
3.  內部**Execute**方法時，現有的邏輯取代為下列：  
  
    1.  此邏輯會驗證要求的作業。  
  
    2.  它會取得`Microsoft.ServiceModel.Channels.Common.OperationMetadata`物件是根據 SOAP 輸入的訊息動作。  
  
    3.  根據動作類型，它會剖析 WCF 要求訊息，並叫用適當的作業。  
  
    ```csharp  
    // Trace input message  
    EchoAdapterUtilities.Trace.Trace(System.Diagnostics.TraceEventType.Verbose, "http://Microsoft.Adapters.Samples.Sql/TraceCode/InputWcfMessage", "Input WCF Message", this, new MessageTraceRecord(message));  
    // Timeout is not supported in this sample  
    OperationMetadata om = this.MetadataLookup.GetOperationDefinitionFromInputMessageAction(message.Headers.Action, timeout);  
    if (om == null)  
    {  
        throw new AdapterException("Invalid operation metadata for " + message.Headers.Action);  
    }  
    if (timeout.Equals(TimeSpan.Zero))  
    {  
        throw new AdapterException("time out is zero");  
    }  
  
    switch (message.Headers.Action)  
    {  
        case "Echo/EchoStrings":  
            return ExecuteEchoStrings(om as ParameterizedOperationMetadata, message, timeout);  
  
        case "Echo/EchoGreetings":  
            return ExecuteEchoGreetings(om as ParameterizedOperationMetadata, message, timeout);  
  
        case "Echo/EchoCustomGreetingFromFile":  
            return ExecuteEchoCustomGreetingFromFile(om, message, timeout);  
    }  
    return null;              
    ```  
  
4.  現在，加入**ExecuteEchoStrings**方法以處理 string [] EchoStrings （字串資料） 作業。 這個 helper 函式會讀取 WCF 要求訊息，會檢查以 echoInUpperCase URI 項目是否設定為 true。如果是的話，它會將輸入的字串轉換為大寫，計數變數會指出的次數中。 接著，它會 WCF 回應訊息產生的格式： \<EchoStringsResponse\>\<EchoStringResult\>\<字串\>{資料}\</string\> \</EchoStringResult\>\</EchoStringsResponse\>。  
  
    ```csharp  
    private Message ExecuteEchoStrings(ParameterizedOperationMetadata om, Message message, TimeSpan timeout)  
    {  
        // ** Read the WCF request  
        // ** <EchoStrings><name>{text}</name></EchoStrings>  
        XmlDictionaryReader inputReader = message.GetReaderAtBodyContents();  
        while (inputReader.Read())  
        {  
            if ((String.IsNullOrEmpty(inputReader.Prefix) && inputReader.Name.Equals("data"))  
                || inputReader.Name.Equals(inputReader.Prefix + ":" + "data")) break;  
        }  
        inputReader.Read();  
        // if the connection property "echoInUpperCase" is set to true, it echoes the data in upper case  
        bool echoInUpperCase = this.Connection.ConnectionFactory.ConnectionUri.EchoInUpperCase;  
        string inputValue = echoInUpperCase ? inputReader.Value.ToUpper() : inputReader.Value;  
        int arrayCount = this.Connection.ConnectionFactory.Adapter.Count;  
  
        // ** Generate the WCF response  
        // ** <EchoStringsResponse><EchoStringResult>{Name}</EchoStringResult></EchoStringsResponse >  
        StringBuilder outputString = new StringBuilder();  
        XmlWriterSettings settings = new XmlWriterSettings();  
        settings.OmitXmlDeclaration = true;  
        XmlWriter replywriter = XmlWriter.Create(outputString, settings);  
        replywriter.WriteStartElement(om.DisplayName + "Response", EchoAdapter.SERVICENAMESPACE);  
        replywriter.WriteStartElement(om.DisplayName + "Result", EchoAdapter.SERVICENAMESPACE);  
        if (om.OperationResult.IsArray)  
        {  
            for (int count = 0; count < arrayCount; count++)  
            {  
                replywriter.WriteElementString("string", "http://schemas.microsoft.com/2003/10/Serialization/Arrays", inputValue);  
            }  
        }  
        replywriter.WriteEndElement();  
        replywriter.WriteEndElement();  
        replywriter.Close();  
        XmlReader replyReader = XmlReader.Create(new StringReader(outputString.ToString()));  
        return Message.CreateMessage(message.Version, om.OutputMessageAction, replyReader);  
    }  
    ```  
  
5.  繼續加入**ExecuteEchoGreetings**方法以處理 EchoGreetings 作業。 這個 helper 函式會讀取 WCF 要求訊息、 作業和型別解析`ResolveOperationMetadata`和`ResolveTypeMetadata`方法`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`介面，並接著會產生 WCF 回應訊息使用的格式： \<EchoGreetingsResponse\>\<EchoGreetingsResult\>...訊息...\</EchoGreetingsResult\>\</EchoGreetingsResponse\>。  
  
    ```csharp  
    private Message ExecuteEchoGreetings(ParameterizedOperationMetadata om, Message message, TimeSpan timeout)  
    {  
        // NOTE this method doesn't return response in upper case based on   
        // connection property echoInUpperCase  
  
        // ** Read the WCF request  
        String inputValue = String.Empty;  
        using (XmlDictionaryReader inputReader = message.GetReaderAtBodyContents())  
        {  
  
            bool foundGreeting = inputReader.ReadToDescendant("greeting");  
            if (foundGreeting)  
            {  
                inputValue = inputReader.ReadInnerXml();  
            }  
        }  
  
        int arrayCount = this.Connection.ConnectionFactory.Adapter.Count;  
  
        // ** Generate the WCF response  
        StringBuilder outputString = new StringBuilder();  
        XmlWriterSettings settings = new XmlWriterSettings();  
        settings.OmitXmlDeclaration = true;  
        XmlWriter replywriter = XmlWriter.Create(outputString, settings);  
        replywriter.WriteStartElement(om.DisplayName + "Response", EchoAdapter.SERVICENAMESPACE);  
        replywriter.WriteStartElement(om.DisplayName + "Result", EchoAdapter.SERVICENAMESPACE);  
        for(int i = 0; i < arrayCount; i++ )  
        {  
            ComplexQualifiedType cqtResult = om.OperationResult.QualifiedType as ComplexQualifiedType;  
            StructuredTypeMetadata tmResult = MetadataLookup.GetTypeDefinition(cqtResult.TypeId, timeout) as StructuredTypeMetadata;  
            replywriter.WriteStartElement(tmResult.TypeName, tmResult.TypeNamespace);  
            replywriter.WriteRaw(inputValue);  
            replywriter.WriteEndElement();  
        }  
        replywriter.WriteEndElement();  
        replywriter.WriteEndElement();  
        replywriter.Close();  
        XmlReader replyReader = XmlReader.Create(new StringReader(outputString.ToString()));  
        return Message.CreateMessage(message.Version, om.OutputMessageAction, replyReader);  
    }  
    ```  
  
6.  現在，加入**ExecuteEchoCustomGreetingFromFile**方法以處理 EchoCustomGreetingFromFile 作業。 這個 helper 函式會讀取 WCF 要求訊息中，從指定的檔案讀取訊息，然後再產生 WCF 回應訊息使用的格式： \<EchoGreetingsFromFileResponse\> \<EchoGreetingsFromFileResult\>...訊息...\</EchoGreetingsFromFileResult\>\</EchoGreetingsFromFileResponse\>。  
  
    ```csharp  
    private Message ExecuteEchoCustomGreetingFromFile(OperationMetadata om, Message message, TimeSpan timeout)  
    {  
        // NOTE this method doesn't return response in upper case based on   
        // connection property echoInUpperCase  
  
        // ** Read the WCF request  
        Uri path;  
        using (XmlDictionaryReader inputReader = message.GetReaderAtBodyContents())  
        {  
            inputReader.MoveToContent();  
            inputReader.ReadStartElement(om.DisplayName);  
            inputReader.MoveToContent();  
            // The path contains the location of the XML file that contains the instance of Greeting object to read   
            path = new Uri(inputReader.ReadElementContentAsString());  
            inputReader.ReadEndElement();  
        }  
  
        // ** Generate the WCF response  
        StringBuilder outputString = new StringBuilder();  
        XmlWriterSettings settings = new XmlWriterSettings();  
        settings.OmitXmlDeclaration = true;  
        XmlWriter replywriter = XmlWriter.Create(outputString, settings);  
        replywriter.WriteStartElement(om.DisplayName + "Response", EchoAdapter.SERVICENAMESPACE);  
        replywriter.WriteStartElement(om.DisplayName + "Result", EchoAdapter.SERVICENAMESPACE);  
        // Read the XML file and set it to the reply writer here  
        FileStream stream = new FileStream(path.AbsolutePath, FileMode.Open);  
        XmlDictionaryReader xdr = XmlDictionaryReader.CreateTextReader(stream, new XmlDictionaryReaderQuotas());  
        xdr.MoveToContent();  
        string rawGreeting = xdr.ReadInnerXml();  
        replywriter.WriteRaw(rawGreeting);  
        replywriter.WriteEndElement();  
        replywriter.WriteEndElement();  
        replywriter.Close();  
        XmlReader replyReader = XmlReader.Create(new StringReader(outputString.ToString()));  
        return Message.CreateMessage(message.Version, om.OutputMessageAction, replyReader);  
    }  
    ```  
  
7.  在 Visual Studio 中，在**檔案**功能表上，按一下 **全部儲存**。  
  
8.  按一下 [ **建置** ] 功能表上的 [ **建置方案**]。 它應該編譯無誤。 如果沒有，請確定您已依照上述每個步驟。 現在，您可以安全地關閉 Visual Studio 或繼續前往[步驟 8： 為回應配接器實作同步的輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)。  
  
## <a name="what-did-i-just-do"></a>我剛剛做什麼？  
 在此步驟中，您將學會如何實作回應配接器同步輸出訊息的功能。 若要這樣做，您實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`方法`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`。 這個方法會剖析內送 WCF 要求訊息、 執行必要的動作，然後產生外寄 WCF 回應訊息。  
  
 具體來說，如內送 WCF 要求訊息，您可以使用 WCF`System.ServiceModel.Channels.Message.Headers.Action%2A`來進一步了解基本結構的內送的訊息主體擷取輸入的訊息動作。 外寄 WCF 回應訊息使用`Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`來進一步了解基本結構的外寄訊息主體擷取輸出訊息動作。 當剖析與撰寫 WCF 訊息，您會使用`System.Xml.XmlDictionaryReader`來讀取內送 WCF 要求訊息和使用`System.Xml.XmlWriter`寫入外寄 WCF 回應訊息。  
  
## <a name="next-steps"></a>後續步驟  
建置和部署回應配接器。  
  
## <a name="see-also"></a>請參閱  
 [步驟 6： 實作回應配接器中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)   
 [步驟 8：實作 Echo 配接器的同步輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)