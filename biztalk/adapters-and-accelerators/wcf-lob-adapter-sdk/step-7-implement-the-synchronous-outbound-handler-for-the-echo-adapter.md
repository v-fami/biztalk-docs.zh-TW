---
title: 步驟 7： 實作 Echo 配接器同步輸出的處理常式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4da4d987-03c4-4817-850b-4c5ca2ba7e62
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e44c26c1708f54cceeb979cf20e5c43a95528a54
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979463"
---
# <a name="step-7-implement-the-synchronous-outbound-handler-for-the-echo-adapter"></a><span data-ttu-id="5c8b3-102">步驟 7： 實作 Echo 配接器同步輸出的處理常式</span><span class="sxs-lookup"><span data-stu-id="5c8b3-102">Step 7: Implement the Synchronous Outbound Handler for the Echo Adapter</span></span>
<span data-ttu-id="5c8b3-103">![步驟 9 的 7](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")</span><span class="sxs-lookup"><span data-stu-id="5c8b3-103">![Step 7 of 9](../../adapters-and-accelerators/wcf-lob-adapter-sdk/media/step-7of9.gif "Step_7of9")</span></span>  
  
 <span data-ttu-id="5c8b3-104">**若要完成的時間：** 30 分鐘</span><span class="sxs-lookup"><span data-stu-id="5c8b3-104">**Time to complete:** 30 minutes</span></span>  
  
 <span data-ttu-id="5c8b3-105">在此步驟中，您可以實作 Echo 配接器的同步輸出的功能。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-105">In this step, you implement the synchronous outbound capability of the Echo adapter.</span></span> <span data-ttu-id="5c8b3-106">根據[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]，以支援同步輸出的功能，您必須實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`介面。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-106">According to the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], to support the synchronous outbound capability, you must implement the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` interface.</span></span> <span data-ttu-id="5c8b3-107">Echo 配接器，[!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)]會自動產生一個衍生的類別，稱為 EchoAdapterOutboundHandler。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-107">For the Echo adapter, the [!INCLUDE[afdevwizardnameshort](../../includes/afdevwizardnameshort-md.md)] automatically generates one derived class called EchoAdapterOutboundHandler.</span></span>  
  
 <span data-ttu-id="5c8b3-108">在下列章節中，您會更新 EchoAdapterOutboundHandler 類別，以取得進一步了解如何實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`、 如何剖析連入的 WCF 要求訊息，以及如何產生外寄 WCF 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-108">In the following sections, you update the EchoAdapterOutboundHandler class to get a better understanding of how to implement the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`, how to parse the incoming WCF request message, and how to generate outgoing WCF response messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5c8b3-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="5c8b3-109">Prerequisites</span></span>  
 <span data-ttu-id="5c8b3-110">在開始此步驟之前，您必須先成功完成[步驟 6： 實作 Echo 配接器的中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-110">Before you begin this step, you must have successfully completed [Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md).</span></span> <span data-ttu-id="5c8b3-111">基本的熟悉`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`也很有用。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-111">A basic familiarity with `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` is also helpful.</span></span>  
  
## <a name="the-ioutboundhandler-interface"></a><span data-ttu-id="5c8b3-112">IOutboundHandler 介面</span><span class="sxs-lookup"><span data-stu-id="5c8b3-112">The IOutboundHandler Interface</span></span>  
 <span data-ttu-id="5c8b3-113">`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`定義為：</span><span class="sxs-lookup"><span data-stu-id="5c8b3-113">The `Microsoft.ServiceModel.Channels.Common.IOutboundHandler` is defined as:</span></span>  
  
```  
public interface IOutboundHandler : IConnectionHandler, IDisposable  
{  
    Message Execute(Message message, TimeSpan timeout);  
}  
```  
  
 <span data-ttu-id="5c8b3-114">`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`方法叫用對應的方法，在目標系統上執行內送 WCF 要求訊息，然後傳回 外寄的 WCF 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-114">The `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` method executes the incoming WCF request message by invoking the corresponding method on the target system and then returns an outgoing WCF response message.</span></span> <span data-ttu-id="5c8b3-115">下表中列出其參數的定義：</span><span class="sxs-lookup"><span data-stu-id="5c8b3-115">The definitions of its parameters are listed in the following table:</span></span>  
  
|<span data-ttu-id="5c8b3-116">**參數**</span><span class="sxs-lookup"><span data-stu-id="5c8b3-116">**Parameter**</span></span>|<span data-ttu-id="5c8b3-117">**定義**</span><span class="sxs-lookup"><span data-stu-id="5c8b3-117">**Definition**</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="5c8b3-118">message</span><span class="sxs-lookup"><span data-stu-id="5c8b3-118">message</span></span>|<span data-ttu-id="5c8b3-119">內送 WCF 要求訊息。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-119">Incoming WCF request message.</span></span>|  
|<span data-ttu-id="5c8b3-120">timeout</span><span class="sxs-lookup"><span data-stu-id="5c8b3-120">timeout</span></span>|<span data-ttu-id="5c8b3-121">應該在其中完成這項作業的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-121">Time interval within which this operation should be completed.</span></span> <span data-ttu-id="5c8b3-122">此作業應該擲回`System.TimeoutException`如果在作業完成之前，超出指定的逾時。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-122">The operation should throw a `System.TimeoutException` if the specified timeout is exceeded before the operation is completed.</span></span>|  
  
 <span data-ttu-id="5c8b3-123">如果您的配接器正在執行 （沒有您的配接器所預期的回應訊息） 的單向傳送，這個方法應該傳回 null。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-123">If your adapter is performing a one-way send (there is no response message expected by your adapter), this method should return null.</span></span> <span data-ttu-id="5c8b3-124">如果您的配接器正在執行雙向作業中的搭配`Microsoft.ServiceModel.Channels.Common.OperationResult`等於`Microsoft.ServiceModel.Channels.Common.OperationResult.Empty%2A`，這個方法會傳回空的內文的 WCF 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-124">If your adapter is performing a two-way operation with `Microsoft.ServiceModel.Channels.Common.OperationResult` equal to `Microsoft.ServiceModel.Channels.Common.OperationResult.Empty%2A`, this method returns a WCF response message with an empty body.</span></span> <span data-ttu-id="5c8b3-125">否則，它應該傳回 WCF 回應訊息內文，內含值`Microsoft.ServiceModel.Channels.Common.OperationResult`物件。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-125">Otherwise, it should return the WCF response message with a body that contains the values in the `Microsoft.ServiceModel.Channels.Common.OperationResult` object.</span></span> <span data-ttu-id="5c8b3-126">若要建構回應的動作字串，請使用`Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-126">To construct the response action string, use `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`.</span></span>  
  
## <a name="echo-adapter-synchronous-outbound"></a><span data-ttu-id="5c8b3-127">Echo 配接器同步輸出</span><span class="sxs-lookup"><span data-stu-id="5c8b3-127">Echo Adapter Synchronous Outbound</span></span>  
 <span data-ttu-id="5c8b3-128">根據目標系統的作業中，有許多方式可實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`方法。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-128">Depending on your target system's operations, there are many ways to implement the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` method.</span></span> <span data-ttu-id="5c8b3-129">Echo 配接器中，有三個輸出的作業，而其指派的節點識別碼和顯示名稱是：</span><span class="sxs-lookup"><span data-stu-id="5c8b3-129">For the Echo adapter, there are three outbound operations, and their assigned node IDs and display names are:</span></span>  
  
- <span data-ttu-id="5c8b3-130">string [] EchoStrings （字串資料），節點識別碼 = Echo/EchoString，顯示名稱 = EchoString</span><span class="sxs-lookup"><span data-stu-id="5c8b3-130">string[] EchoStrings(string data), node ID = Echo/EchoString, display name=EchoString</span></span>  
  
- <span data-ttu-id="5c8b3-131">[] EchoGreetings(Greeting greeting)，節點識別碼的問候語 = Echo/EchoGreetings，顯示名稱 = EchoGreetings</span><span class="sxs-lookup"><span data-stu-id="5c8b3-131">Greeting[] EchoGreetings(Greeting greeting), node ID=Echo/EchoGreetings, display name=EchoGreetings</span></span>  
  
- <span data-ttu-id="5c8b3-132">CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath)，nodeID = Echo/EchoCustomGreetingFromFile，顯示名稱 = EchoGreetings</span><span class="sxs-lookup"><span data-stu-id="5c8b3-132">CustomGreeting EchoCustomGreetingFromFile(Uri greetingInstancePath), nodeID=Echo/EchoCustomGreetingFromFile, display name=EchoGreetings</span></span>  
  
  <span data-ttu-id="5c8b3-133">若要正確地剖析內送 WCF 要求訊息，並產生外寄的 WCF 回應訊息，您必須熟悉下列的項目所使用的 SOAP 訊息內[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="5c8b3-133">To correctly parse the incoming WCF request message and generate the outgoing WCF response message, you must be familiar with the following elements within the SOAP message used by the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]:</span></span>  
  
  <span data-ttu-id="5c8b3-134">內送 WCF 要求訊息：</span><span class="sxs-lookup"><span data-stu-id="5c8b3-134">For the incoming WCF request message:</span></span>  
  
- <span data-ttu-id="5c8b3-135">WCF 輸入訊息動作 = 作業的節點識別碼</span><span class="sxs-lookup"><span data-stu-id="5c8b3-135">The WCF input message action = operation's node ID</span></span>  
  
- <span data-ttu-id="5c8b3-136">內送的訊息內文 = 開始本文的元素是\<displayname\>\<參數名稱\>{資料}\</parameter 名稱\>\</displayname\></span><span class="sxs-lookup"><span data-stu-id="5c8b3-136">Incoming message body = The start element of the body is \<displayname\>\<parameter name\>{data}\</parameter name\>\</displayname\></span></span>  
  
  <span data-ttu-id="5c8b3-137">外寄的 WCF 回應訊息：</span><span class="sxs-lookup"><span data-stu-id="5c8b3-137">For the outgoing WCF response message:</span></span>  
  
- <span data-ttu-id="5c8b3-138">WCF 輸出訊息動作 = 作業的節點識別碼 +"/ 回應 」</span><span class="sxs-lookup"><span data-stu-id="5c8b3-138">The WCF output message action = operation's node ID + "/response"</span></span>  
  
- <span data-ttu-id="5c8b3-139">外寄訊息內文 = 開始本文的元素是\<displayname + 「 回應 」\>，後面接著\<displayname +"Result"\>，且後面接著\<datatype\>資料\</datatype\>\</displayname+ 」 結果\>\</displayname + 「 回應 」\></span><span class="sxs-lookup"><span data-stu-id="5c8b3-139">Outgoing message body = The start element of the body is \<displayname + "Response"\>, followed by \<displayname + "Result"\>, and followed by the \<datatype\>data\</datatype\>\</displayname+"Result\>\</displayname + "Response"\></span></span>  
  
  <span data-ttu-id="5c8b3-140">例如，作業**string [] （字串資料） EchoStrings**，節點識別碼 = Echo/EchoStrings，和顯示名稱 = EchoStrings:</span><span class="sxs-lookup"><span data-stu-id="5c8b3-140">For example, operation **string[] EchoStrings(string data)**, node ID = Echo/EchoStrings, and display name= EchoStrings:</span></span>  
  
  <span data-ttu-id="5c8b3-141">WCF 輸入訊息動作 ="Echo/EchoStrings";輸入的主體看起來像這樣，因為參數名稱和`data`。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-141">The WCF input message action = "Echo/EchoStrings"; and the input body looks as follows, since the parameter name is `data`.</span></span>  
  
```  
<EchoStrings>  
<data>{data}  
</data>  
</EchoStrings>  
```  
  
 <span data-ttu-id="5c8b3-142">WCF 輸出訊息動作 = 「 Echo/EchoStrings/回應 」;與輸出主體看起來像這樣，因為資料類型是**字串**。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-142">The WCF output message action = "Echo/EchoStrings/response"; and the output body looks as follows, since the data type is **string**.</span></span>  
  
```  
<EchoStringsResponse>  
<EchoStringsResult>  
<string>{data}</string>  
</EchoStringsResult>  
</EchoStringsResponse>  
```  
  
 <span data-ttu-id="5c8b3-143">當剖析內送 WCF 要求訊息，您可以使用`System.Xml.XmlDictionaryReader`若要撰寫的 WCF 回應訊息時，請擷取內容 WCF 訊息內，您可以使用`System.Xml.XmlWriter`若要這樣做。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-143">When parsing the incoming WCF request message, you can use the `System.Xml.XmlDictionaryReader` to retrieve content within the WCF message; when composing the WCF response message, you can use the `System.Xml.XmlWriter` to do so.</span></span>  
  
## <a name="implementing-the-ioutboundhandler"></a><span data-ttu-id="5c8b3-144">實作 IOutboundHandler</span><span class="sxs-lookup"><span data-stu-id="5c8b3-144">Implementing the IOutboundHandler</span></span>  
 <span data-ttu-id="5c8b3-145">您實作的 Execute 方法`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-145">You implement the Execute method of the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`.</span></span> <span data-ttu-id="5c8b3-146">首先，取得`Microsoft.ServiceModel.Channels.Common.OperationMetadata`物件會根據輸入的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-146">First, gets a `Microsoft.ServiceModel.Channels.Common.OperationMetadata` object based on the input message action.</span></span> <span data-ttu-id="5c8b3-147">然後，剖析內送 WCF 訊息，並執行根據每個作業的相關聯的回應功能。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-147">Then, parses the incoming WCF message and executes the associated echo functionality based on each operation.</span></span> <span data-ttu-id="5c8b3-148">最後，建立外寄的 WCF 回應訊息所使用的外寄訊息內文格式。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-148">Finally, creates an outgoing WCF response message by using the format of outgoing message body.</span></span>  
  
#### <a name="to-implement-the-execute-method-of-the-echoadapteroutboundhandler-class"></a><span data-ttu-id="5c8b3-149">若要實作 EchoAdapterOutboundHandler 類別的 Execute 方法</span><span class="sxs-lookup"><span data-stu-id="5c8b3-149">To implement the Execute method of the EchoAdapterOutboundHandler class</span></span>  
  
1.  <span data-ttu-id="5c8b3-150">在 [方案總管] 中，按兩下**EchoAdapterOutboundHandler.cs**檔案。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-150">In Solution Explorer, double-click the **EchoAdapterOutboundHandler.cs** file.</span></span>  
  
2.  <span data-ttu-id="5c8b3-151">在 Visual Studio 編輯器中，新增下列兩個 using 指示詞至一組現有的 using 指示詞。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-151">In the Visual Studio editor, add the following two using directives to the existing set of using directives.</span></span>  
  
    ```csharp  
    using System.Xml;  
    using System.IO;  
    ```  
  
3.  <span data-ttu-id="5c8b3-152">內部**Execute**方法，以下列內容取代現有的邏輯：</span><span class="sxs-lookup"><span data-stu-id="5c8b3-152">Inside the **Execute** method, replace the existing logic with the following:</span></span>  
  
    1.  <span data-ttu-id="5c8b3-153">此邏輯會驗證要求的作業。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-153">This logic verifies the requested operation.</span></span>  
  
    2.  <span data-ttu-id="5c8b3-154">它會取得`Microsoft.ServiceModel.Channels.Common.OperationMetadata`物件根據 SOAP 輸入的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-154">It gets the `Microsoft.ServiceModel.Channels.Common.OperationMetadata` object based on the SOAP input message action.</span></span>  
  
    3.  <span data-ttu-id="5c8b3-155">根據動作類型，它會剖析 WCF 要求訊息，並叫用適當的作業。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-155">Based on the action type, it parses the WCF request message and invokes the appropriate operation.</span></span>  
  
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
  
4.  <span data-ttu-id="5c8b3-156">現在，加入**ExecuteEchoStrings**方法以處理 string [] EchoStrings （字串資料） 作業。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-156">Now add the **ExecuteEchoStrings** method to handle the string[] EchoStrings(string data) operation.</span></span> <span data-ttu-id="5c8b3-157">此協助程式函式會讀取 WCF 要求訊息，檢查，以查看 echoInUpperCase URI 項目是否設定為 true;如果是的話，它會將輸入的字串轉換為大寫計數的變數會指出的次數中。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-157">This helper function reads the WCF request message, checks to see if the echoInUpperCase URI element is set to true; if so, it converts the input string to upper case as many times as the count variable indicates.</span></span> <span data-ttu-id="5c8b3-158">然後，它產生 WCF 回應訊息的格式： \<EchoStringsResponse\>\<EchoStringResult\>\<字串\>{資料}\</string\> \</EchoStringResult\>\</EchoStringsResponse\>。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-158">Then, it generates the WCF response message in the format of: \<EchoStringsResponse\>\<EchoStringResult\>\<string\>{data}\</string\>\</EchoStringResult\>\</EchoStringsResponse\>.</span></span>  
  
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
  
5.  <span data-ttu-id="5c8b3-159">藉由新增繼續**ExecuteEchoGreetings**方法以處理 EchoGreetings 作業。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-159">Continue by adding the **ExecuteEchoGreetings** method to handle the EchoGreetings operation.</span></span> <span data-ttu-id="5c8b3-160">此協助程式函式會讀取 WCF 要求訊息時，會解析作業和型別`ResolveOperationMetadata`並`ResolveTypeMetadata`種`Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler`介面，並接著會產生 WCF 回應訊息使用的格式： \<EchoGreetingsResponse\>\<EchoGreetingsResult\>...訊息...\</EchoGreetingsResult\>\</EchoGreetingsResponse\>。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-160">This helper function reads the WCF request message, resolves operation and type by the `ResolveOperationMetadata` and `ResolveTypeMetadata` methods of the `Microsoft.ServiceModel.Channels.Common.IMetadataResolverHandler` interface, and then generates the WCF response message using the format of: \<EchoGreetingsResponse\>\<EchoGreetingsResult\>…message…\</EchoGreetingsResult\>\</EchoGreetingsResponse\>.</span></span>  
  
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
  
6.  <span data-ttu-id="5c8b3-161">現在，加入**ExecuteEchoCustomGreetingFromFile**方法以處理 EchoCustomGreetingFromFile 作業。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-161">Now add the **ExecuteEchoCustomGreetingFromFile** method to handle the EchoCustomGreetingFromFile operation.</span></span> <span data-ttu-id="5c8b3-162">此協助程式函式會讀取 WCF 要求訊息中，從指定的檔案，讀取訊息，並接著會產生 WCF 回應訊息使用的格式： \<EchoGreetingsFromFileResponse\> \<EchoGreetingsFromFileResult\>...訊息...\</EchoGreetingsFromFileResult\>\</EchoGreetingsFromFileResponse\>。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-162">This helper function reads the WCF request message, reads the message from the specified file, and then generates the  WCF response message using the format of: \<EchoGreetingsFromFileResponse\>\<EchoGreetingsFromFileResult\>…message…\</EchoGreetingsFromFileResult\>\</EchoGreetingsFromFileResponse\>.</span></span>  
  
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
  
7.  <span data-ttu-id="5c8b3-163">在 Visual Studio 中，在**檔案**功能表上，按一下**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-163">In Visual Studio, on the **File** menu, click **Save All**.</span></span>  
  
8.  <span data-ttu-id="5c8b3-164">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-164">On the **Build** menu, click **Build Solution**.</span></span> <span data-ttu-id="5c8b3-165">它應該編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-165">It should compile without errors.</span></span> <span data-ttu-id="5c8b3-166">如果沒有，請確定您已遵循上述每個步驟。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-166">If not, ensure that you have followed every step above.</span></span> <span data-ttu-id="5c8b3-167">現在，您可以安全地關閉 Visual Studio 或繼續[步驟 8： 實作 Echo 配接器的同步輸入處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-167">Now, you can safely close Visual Studio or continue on to [Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md).</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="5c8b3-168">我剛剛做了什麼？</span><span class="sxs-lookup"><span data-stu-id="5c8b3-168">What Did I Just Do?</span></span>  
 <span data-ttu-id="5c8b3-169">在此步驟中，您已了解如何實作 Echo 配接器的同步輸出訊息的功能。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-169">In this step, you learned how to implement the synchronous outbound messaging functionality of the Echo adapter.</span></span> <span data-ttu-id="5c8b3-170">若要這樣做，您實作`Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A`方法的`Microsoft.ServiceModel.Channels.Common.IOutboundHandler`。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-170">To do so, you implemented the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler.Execute%2A` method of the `Microsoft.ServiceModel.Channels.Common.IOutboundHandler`.</span></span> <span data-ttu-id="5c8b3-171">這個方法會剖析內送 WCF 要求訊息、 執行必要的動作，並產生外寄的 WCF 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-171">This method parsed the incoming WCF request message, performed the necessary actions, and then generated the outgoing WCF response message.</span></span>  
  
 <span data-ttu-id="5c8b3-172">具體來說，如內送 WCF 要求訊息中，您可以使用 WCF`System.ServiceModel.Channels.Message.Headers.Action%2A`擷取輸入的訊息的動作，藉由進一步了解傳入的訊息主體的基本結構。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-172">Specifically, for the incoming WCF request message, you used WCF `System.ServiceModel.Channels.Message.Headers.Action%2A` to retrieve the input message action by further understanding the basic structure of the incoming message body.</span></span> <span data-ttu-id="5c8b3-173">在您使用的外寄的 WCF 回應訊息，`Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A`擷取輸出訊息動作進一步了解外送的訊息主體的基本結構。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-173">For the outgoing WCF response message, you used `Microsoft.ServiceModel.Channels.Common.OperationMetadata.OutputMessageAction%2A` to retrieve the output message action by further understanding the basic structure of the outgoing message body.</span></span> <span data-ttu-id="5c8b3-174">剖析與撰寫 WCF 訊息，當您使用`System.Xml.XmlDictionaryReader`來讀取內送 WCF 要求訊息和使用`System.Xml.XmlWriter`將外寄的 WCF 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-174">When parsing and composing WCF messages, you used `System.Xml.XmlDictionaryReader` to read the incoming WCF request message and used `System.Xml.XmlWriter` to write an outgoing WCF response message.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5c8b3-175">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5c8b3-175">Next Steps</span></span>  
<span data-ttu-id="5c8b3-176">建置並部署 Echo 配接器。</span><span class="sxs-lookup"><span data-stu-id="5c8b3-176">Build and deploy the Echo adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c8b3-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c8b3-177">See Also</span></span>  
 <span data-ttu-id="5c8b3-178">[步驟 6： 實作 Echo 配接器中繼資料解析處理常式](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="5c8b3-178">[Step 6: Implement the Metadata Resolve Handler for the Echo Adapter](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-6-implement-the-metadata-resolve-handler-for-the-echo-adapter.md) </span></span>  
 [<span data-ttu-id="5c8b3-179">步驟 8：實作 Echo 配接器的同步輸入處理常式</span><span class="sxs-lookup"><span data-stu-id="5c8b3-179">Step 8: Implement the Synchronous Inbound Handler for the Echo Adapter</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/step-8-implement-the-synchronous-inbound-handler-for-the-echo-adapter.md)