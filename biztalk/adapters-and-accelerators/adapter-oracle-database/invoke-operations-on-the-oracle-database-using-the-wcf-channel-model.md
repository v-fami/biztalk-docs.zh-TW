---
title: 叫用使用 WCF 通道模型的 Oracle 資料庫上的作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- invoking operations, using the WCF channel model
- WCF channel model, invoking operations
- invoking operations
- operations, invoking
ms.assetid: 6dd95c18-8f78-46d0-8845-b74890614c33
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1ff19d925ac8892fdaed62204f4da742d1e86ef
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37007415"
---
# <a name="invoke-operations-on-the-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="e8996-102">使用 WCF 通道模型之 Oracle 資料庫上叫用作業</span><span class="sxs-lookup"><span data-stu-id="e8996-102">Invoke Operations on the Oracle Database Using the WCF Channel Model</span></span>
<span data-ttu-id="e8996-103">您可以在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]利用**IRequestChannel**或是**IOutputChannel**圖形以將訊息傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="e8996-103">You can invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using an **IRequestChannel** or **IOutputChannel** shape to send messages to the adapter.</span></span> <span data-ttu-id="e8996-104">基本的模式是使用繫結建立通道處理站所需的通道形狀 (**OracleDBBinding**) 和建立的連線 URI 的端點。</span><span class="sxs-lookup"><span data-stu-id="e8996-104">The basic pattern is to create a channel factory for the required channel shape by using a binding (**OracleDBBinding**) and an endpoint created from a connection URI.</span></span> <span data-ttu-id="e8996-105">接著，您建立**訊息**表示 SOAP 訊息，以符合您目標的作業的訊息結構描述執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8996-105">You then create a **Message** instance that represents a SOAP message that conforms to the message schema for your target operation.</span></span> <span data-ttu-id="e8996-106">您可以接著將傳送這**訊息**到[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用從通道處理站建立通道。</span><span class="sxs-lookup"><span data-stu-id="e8996-106">You can then send this **Message** to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] by using a channel created from the channel factory.</span></span> <span data-ttu-id="e8996-107">如果您使用**IRequestChannel**，您會收到回應。</span><span class="sxs-lookup"><span data-stu-id="e8996-107">If you are using an **IRequestChannel**, you receive a response.</span></span> <span data-ttu-id="e8996-108">如果沒有執行 Oracle 資料庫時，作業的問題[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]會擲回**Microsoft.ServiceModel.Channels.Common.TargetSystemException**。</span><span class="sxs-lookup"><span data-stu-id="e8996-108">If there is a problem executing the operation on the Oracle database, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] throws a **Microsoft.ServiceModel.Channels.Common.TargetSystemException**.</span></span>  
  
 <span data-ttu-id="e8996-109">如需如何傳送作業使用的概觀**IRequestChannel**在 WCF 中，請參閱 < 用戶端通道層級程式設計 >，網址[ http://go.microsoft.com/fwlink/?LinkId=106081 ](http://go.microsoft.com/fwlink/?LinkId=106081)。</span><span class="sxs-lookup"><span data-stu-id="e8996-109">For an overview of how to send operations using an **IRequestChannel** in WCF, see "Client Channel-Level Programming" at [http://go.microsoft.com/fwlink/?LinkId=106081](http://go.microsoft.com/fwlink/?LinkId=106081).</span></span>  
  
 <span data-ttu-id="e8996-110">本主題中的各節提供的資訊可協助您在上叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="e8996-110">The sections in this topic provide information to help you invoke operations on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] using the WCF channel model.</span></span>  
  
## <a name="creating-and-consuming-messages-for-outbound-operations"></a><span data-ttu-id="e8996-111">建立和輸出作業取用訊息</span><span class="sxs-lookup"><span data-stu-id="e8996-111">Creating and Consuming Messages for Outbound Operations</span></span>  
 <span data-ttu-id="e8996-112">若要在叫用作業[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，您將使用目標作業的要求訊息的傳送**IRequestChannel**或**IOutputChannel**。</span><span class="sxs-lookup"><span data-stu-id="e8996-112">To invoke an operation on the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], you send the request message for the target operation using either an **IRequestChannel** or an **IOutputChannel**.</span></span> <span data-ttu-id="e8996-113">如果您使用**IRequestChannel**配接器會傳回作業結果的回應訊息中。</span><span class="sxs-lookup"><span data-stu-id="e8996-113">If you use an **IRequestChannel** the adapter returns the results of the operation in the response message.</span></span>  
  
 <span data-ttu-id="e8996-114">如需詳細的要求和回應訊息結構描述和每個作業的訊息動作相關資訊，請參閱[訊息和訊息結構描述，BizTalk adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="e8996-114">For more detailed information about the request and response message schemas and the message actions for each operation, see [Messages and Message Schemas for BizTalk Adapter for Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).</span></span>  
  
 <span data-ttu-id="e8996-115">如何建立要求訊息及取用回應訊息會決定配接器會執行節點資料流或資料流處理的節點值。</span><span class="sxs-lookup"><span data-stu-id="e8996-115">How you create the request message and consume the response message determines whether node streaming or node-value streaming is performed by the adapter.</span></span> <span data-ttu-id="e8996-116">這接著會決定是否執行受支援的作業的端對端 LOB 資料的資料流。</span><span class="sxs-lookup"><span data-stu-id="e8996-116">This in turn determines whether end-to-end streaming of LOB data is performed for supported operations.</span></span>  
  
### <a name="creating-the-request-message"></a><span data-ttu-id="e8996-117">建立要求訊息</span><span class="sxs-lookup"><span data-stu-id="e8996-117">Creating the request message</span></span>  
 <span data-ttu-id="e8996-118">您可以使用兩種方式之一來建立要求訊息：</span><span class="sxs-lookup"><span data-stu-id="e8996-118">You can create the request message in one of two ways:</span></span>  
  
- <span data-ttu-id="e8996-119">若要建立可以用於節點值的訊息在串流，您必須傳遞的訊息本文的**XmlBodyWriter**實作資料流處理的節點值。</span><span class="sxs-lookup"><span data-stu-id="e8996-119">To create a message that can be used for node-value streaming you must pass the message body in an **XmlBodyWriter** that implements node-value streaming.</span></span>  
  
- <span data-ttu-id="e8996-120">若要建立的訊息，可以用於節點在串流，您可以傳遞的訊息本文的**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="e8996-120">To create a message that can be used for node streaming you can pass the message body in an **XmlReader**.</span></span>  
  
  <span data-ttu-id="e8996-121">通常，您會使用可支援端對端資料流的要求訊息中的 Oracle LOB 資料串流處理的節點值。</span><span class="sxs-lookup"><span data-stu-id="e8996-121">You typically use node-value streaming to support end-to-end streaming of Oracle LOB data in the request message.</span></span> <span data-ttu-id="e8996-122">支援此功能的唯一作業是 UpdateLOB。</span><span class="sxs-lookup"><span data-stu-id="e8996-122">The only operation that supports this feature is UpdateLOB.</span></span>  
  
### <a name="consuming-the-response-message"></a><span data-ttu-id="e8996-123">取用回應訊息</span><span class="sxs-lookup"><span data-stu-id="e8996-123">Consuming the response message</span></span>  
 <span data-ttu-id="e8996-124">您可以取用回應訊息中有兩種：</span><span class="sxs-lookup"><span data-stu-id="e8996-124">You can consume the response message in one of two ways:</span></span>  
  
- <span data-ttu-id="e8996-125">若要使用訊息使用節點值串流，您必須呼叫**WriteBodyContents**方法的回應訊息，並將它傳遞**XmlDictionaryWriter**實作資料流處理的節點值。</span><span class="sxs-lookup"><span data-stu-id="e8996-125">To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
- <span data-ttu-id="e8996-126">若要取用使用節點資料流處理的訊息，您可以呼叫**GetReaderAtBodyContents**回應訊息，可取得**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="e8996-126">To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
  <span data-ttu-id="e8996-127">通常，您會使用可支援端對端資料流的回應訊息中的 Oracle LOB 資料串流處理的節點值。</span><span class="sxs-lookup"><span data-stu-id="e8996-127">You typically use node-value streaming to support end-to-end streaming of Oracle LOB data in the response message.</span></span> <span data-ttu-id="e8996-128">有許多作業都支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="e8996-128">There are many operations that support this feature.</span></span>  
  
### <a name="lob-data-and-message-streaming-support"></a><span data-ttu-id="e8996-129">LOB 資料和訊息資料流支援</span><span class="sxs-lookup"><span data-stu-id="e8996-129">LOB Data and Message Streaming Support</span></span>  
 <span data-ttu-id="e8996-130">如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援串流 LOB 資料，請參閱[串流大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e8996-130">For more information about how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports streaming on LOB data, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="e8996-131">如需實作串流您的程式碼，以支援端對端 LOB 資料的資料流中的節點值的詳細資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用的 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e8996-131">For more information about implementing node-value streaming in your code to support end-to-end streaming of LOB data, see [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="transaction-support-on-outbound-operations-in-the-wcf-channel-model"></a><span data-ttu-id="e8996-132">WCF 通道模型中的輸出作業的交易支援。</span><span class="sxs-lookup"><span data-stu-id="e8996-132">Transaction Support on Outbound Operations in the WCF Channel Model.</span></span>  
 <span data-ttu-id="e8996-133">您可以在專用的 Oracle 資料庫上交易內叫用每個作業執行配接器。</span><span class="sxs-lookup"><span data-stu-id="e8996-133">The adapter executes each operation you invoke inside a dedicated transaction on the Oracle database.</span></span> <span data-ttu-id="e8996-134">您可以設定來控制這些交易的隔離等級**TransactionIsolationLevel**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e8996-134">You can control the isolation level of these transactions by setting the **TransactionIsolationLevel** binding property.</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="e8996-135">有關使用本主題中的範例</span><span class="sxs-lookup"><span data-stu-id="e8996-135">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="e8996-136">本主題中的範例會使用 SCOTT。ACCOUNTACTIVITY 資料表。</span><span class="sxs-lookup"><span data-stu-id="e8996-136">The example in this topic uses the SCOTT.ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="e8996-137">指令碼來產生這些成品隨附於 SDK 範例。</span><span class="sxs-lookup"><span data-stu-id="e8996-137">A script to generate these artifacts is supplied with the SDK samples.</span></span> <span data-ttu-id="e8996-138">如需有關 SDK 範例的詳細資訊，請參閱[SDK 中的範例](../../core/samples-in-the-sdk.md)。</span><span class="sxs-lookup"><span data-stu-id="e8996-138">For more information about the SDK samples, see [Samples in the SDK](../../core/samples-in-the-sdk.md).</span></span>  
  
## <a name="how-do-i-invoke-an-operation-by-using-a-channel"></a><span data-ttu-id="e8996-139">如何使用通道叫用的作業？</span><span class="sxs-lookup"><span data-stu-id="e8996-139">How Do I Invoke an Operation by Using a Channel?</span></span>  
 <span data-ttu-id="e8996-140">使用叫用作業**IRequestChannel**，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="e8996-140">To invoke an operation by using an **IRequestChannel**, perform the following steps.</span></span>  
  
#### <a name="how-to-invoke-an-operation-by-using-an-instance-of-irequestchannel"></a><span data-ttu-id="e8996-141">如何使用 IRequestChannel 的執行個體叫用作業</span><span class="sxs-lookup"><span data-stu-id="e8996-141">How to invoke an operation by using an instance of IRequestChannel</span></span>  
  
1. <span data-ttu-id="e8996-142">建置通道處理站 (**ChannelFactory\<IRequestChannel\>**)。</span><span class="sxs-lookup"><span data-stu-id="e8996-142">Build a channel factory (**ChannelFactory\<IRequestChannel\>**).</span></span> <span data-ttu-id="e8996-143">若要這樣做，您必須指定繫結 (**OracleDBBinding**) 和端點位址。</span><span class="sxs-lookup"><span data-stu-id="e8996-143">To do this, you must specify a binding (**OracleDBBinding**) and an endpoint address.</span></span> <span data-ttu-id="e8996-144">以命令方式在您的程式碼或是宣告式組態中，您可以指定繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="e8996-144">You can specify the binding and endpoint address either imperatively in your code or declaratively in configuration.</span></span> <span data-ttu-id="e8996-145">如需如何在組態中指定的繫結和端點位址的詳細資訊，請參閱[建立通道，使用 Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)。</span><span class="sxs-lookup"><span data-stu-id="e8996-145">For more information about how to specify the binding and endpoint address in configuration, see [Create a channel using Oracle Database](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md).</span></span>  
  
   ```  
   // Create a binding  
   OracleDBBinding binding = new OracleDBBinding();  
   // Create an endpoint address by using the connection URI  
   EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
   // Create the channel factory  
   ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
   ```  
  
2. <span data-ttu-id="e8996-146">使用設定的使用者名稱密碼認證之通道處理站**ClientCredentials**屬性。</span><span class="sxs-lookup"><span data-stu-id="e8996-146">Set the user name password credentials for the channel factory by using the **ClientCredentials** property.</span></span>  
  
   ```  
   factory.Credentials.UserName.UserName = "SCOTT";  
   factory.Credentials.UserName.Password = "TIGER";  
   ```  
  
3. <span data-ttu-id="e8996-147">開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="e8996-147">Open the channel factory.</span></span>  
  
   ```  
   factory.Open();  
   ```  
  
4. <span data-ttu-id="e8996-148">從 factory 取得的通道，然後開啟它。</span><span class="sxs-lookup"><span data-stu-id="e8996-148">Get a channel from the factory and open it.</span></span>  
  
   ```  
   IRequestChannel channel = factory.CreateChannel();  
   channel.Open();  
   ```  
  
5. <span data-ttu-id="e8996-149">建立**訊息**目標作業的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8996-149">Create a **Message** instance for the target operation.</span></span> <span data-ttu-id="e8996-150">請務必確認已指定目標作業的訊息動作。</span><span class="sxs-lookup"><span data-stu-id="e8996-150">Be sure that the message action for the target operation is specified.</span></span> <span data-ttu-id="e8996-151">在此範例中，藉由傳遞訊息內文**XmlReader**透過 file。</span><span class="sxs-lookup"><span data-stu-id="e8996-151">In this example, the message body is passed by creating an **XmlReader** over a file.</span></span> <span data-ttu-id="e8996-152">目標作業是 SCOTT/EMP 資料表上的選取作業。</span><span class="sxs-lookup"><span data-stu-id="e8996-152">The target operation is a Select operation on the SCOTT/EMP table.</span></span>  
  
   ```  
   XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
   Message messageIn = Message.CreateMessage(MessageVersion.Default,  
       "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
       readerIn);  
   ```  
  
6. <span data-ttu-id="e8996-153">叫用**要求**方法來傳送訊息給在通道上的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]和接收回覆。</span><span class="sxs-lookup"><span data-stu-id="e8996-153">Invoke the **Request** method on the channel to send the message to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and receive the reply.</span></span> <span data-ttu-id="e8996-154">如果 Oracle 資料庫中發生例外狀況，配接器會擲回**TargetSystemException**。</span><span class="sxs-lookup"><span data-stu-id="e8996-154">If the Oracle database encounters an exception, the adapter throws a **TargetSystemException**.</span></span> <span data-ttu-id="e8996-155">（其他例外狀況是可能的非 Oracle 例外狀況）。您可以取得從 Oracle 錯誤的描述**InnerException.Message**屬性**TargetSystemException**。</span><span class="sxs-lookup"><span data-stu-id="e8996-155">(Other exceptions are possible for non Oracle exceptions.) You can get a description of the Oracle error from the **InnerException.Message** property of the **TargetSystemException**.</span></span>  
  
   ```  
   try  
   {  
       Message messageOut = channel.Request(messageIn);  
   }  
   catch (Exception ex)  
   {  
       // handle exception  
   }  
   ```  
  
7. <span data-ttu-id="e8996-156">處理回應。</span><span class="sxs-lookup"><span data-stu-id="e8996-156">Process the response.</span></span> <span data-ttu-id="e8996-157">在此範例中， **GetReaderAtBodyContents**来取得訊息內文的回應訊息上呼叫。</span><span class="sxs-lookup"><span data-stu-id="e8996-157">In this example, **GetReaderAtBodyContents** is called on the response message to get the message body.</span></span>  
  
   ```  
   XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
   ```  
  
8. <span data-ttu-id="e8996-158">當您完成處理回應訊息時，關閉讀取器和訊息。</span><span class="sxs-lookup"><span data-stu-id="e8996-158">When you are done processing the response message, close the reader and the message.</span></span>  
  
   ```  
   readerOut.Close();  
   messageOut.Close();  
   ```  
  
9. <span data-ttu-id="e8996-159">當您完成使用通道和通道處理站中，關閉它們。</span><span class="sxs-lookup"><span data-stu-id="e8996-159">When you are done using the channel and the channel factory, close them.</span></span> <span data-ttu-id="e8996-160">關閉處理站，將會關閉所有使用它所建立的通道。</span><span class="sxs-lookup"><span data-stu-id="e8996-160">Closing the factory will close all channels that were created with it.</span></span>  
  
    ```  
    channel.Close()  
    factory.Close();  
  
    ```  
  
   <span data-ttu-id="e8996-161">請遵循相同的步驟，以傳送訊息，使用**IOutputChannel**圖形除外：</span><span class="sxs-lookup"><span data-stu-id="e8996-161">You follow the same steps to send a message using the **IOutputChannel** shape except:</span></span>  
  
-   <span data-ttu-id="e8996-162">您建立**ChannelFactory\<IOutputChannel\>** 在步驟 1。</span><span class="sxs-lookup"><span data-stu-id="e8996-162">You create a **ChannelFactory\<IOutputChannel\>** in step 1.</span></span>  
  
-   <span data-ttu-id="e8996-163">您呼叫**傳送**步驟 6 中的通道上的方法。</span><span class="sxs-lookup"><span data-stu-id="e8996-163">You call the **Send** method on the channel in step 6.</span></span> <span data-ttu-id="e8996-164">`channel.Send(messageIn);`。</span><span class="sxs-lookup"><span data-stu-id="e8996-164">`channel.Send(messageIn);`.</span></span>  
  
-   <span data-ttu-id="e8996-165">不沒有傳回任何回應訊息**IOutputChannel**。</span><span class="sxs-lookup"><span data-stu-id="e8996-165">There is no response message returned for an **IOutputChannel**.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e8996-166">範例</span><span class="sxs-lookup"><span data-stu-id="e8996-166">Example</span></span>  
 <span data-ttu-id="e8996-167">下列範例示範如何使用叫用選取的作業**IRequestChannel**通道。</span><span class="sxs-lookup"><span data-stu-id="e8996-167">The following example shows how to invoke a Select operation by using an **IRequestChannel** channel.</span></span> <span data-ttu-id="e8996-168">選取回應訊息因使用而消耗**XmlReader**而傳回的記錄數目會寫入至主控台。</span><span class="sxs-lookup"><span data-stu-id="e8996-168">The Select response message is consumed by using an **XmlReader** and the number of records returned is written to the console.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
using System.Xml;  
using System.IO;  
using System.Runtime.Serialization;  
  
namespace RequestChanneSample  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The Select operation request message  
            const string selectRequestString =  
                "\<Select xmlns=\"http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY\"\>" +  
                    "<COLUMN_NAMES>*</COLUMN_NAMES>" +  
                    "<FILTER>ACCOUNT = 100002</FILTER>" +  
                "</Select>";  
            try  
            {  
                // Create binding -- specify binding properties before you open the factory.  
                OracleDBBinding odbBinding = new OracleDBBinding();  
  
                // Create address.  
                EndpointAddress odbAddress = new EndpointAddress("oracledb://ADAPTER/");  
  
                // Create channel factory from binding and address.  
                ChannelFactory<IRequestChannel> factory =   
                    new ChannelFactory<IRequestChannel>(odbBinding, odbAddress);  
  
                // Specify credentials   
                factory.Credentials.UserName.UserName = "SCOTT";  
                factory.Credentials.UserName.Password = "TIGER";  
  
                // Open the factory.  
                factory.Open();  
  
                // Get a channel.  
                IRequestChannel channel = factory.CreateChannel();  
  
                // Open the channel.  
                channel.Open();  
  
                // Create the request message from the string  
                StringReader strReader = new StringReader(selectRequestString);  
                XmlReader readerIn = XmlReader.Create(strReader);  
  
                Message requestMessage = Message.CreateMessage(MessageVersion.Default,  
                    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/ACCOUNTACTIVITY/Select",  
                    readerIn);  
  
                Send the message and get a respone  
                Message responseMessage = channel.Request(requestMessage);  
  
                // Get an XmlReader from the message  
                XmlReader readerOut = (XmlReader) responseMessage.GetReaderAtBodyContents();  
  
                // Count the number of records returned and write to the console.  
                readerOut.MoveToContent();  
                int numberOfRecordsReturned = 0;  
                while (readerOut.Read())  
                {  
                    if (readerOut.NodeType == XmlNodeType.Element && readerOut.Name == "ACCOUNTACTIVITYRECORDSELECT")  
                        numberOfRecordsReturned++;  
                }  
  
                Console.WriteLine("{0} records returned.", numberOfRecordsReturned);  
  
                // Close the output reader and message  
                readerOut.Close();  
                responseMessage.Close();  
  
                //Close channel  
                channel.Close();  
  
                //Close the factory  
                factory.Close();  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine(ex.Message);  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8996-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8996-169">See Also</span></span>  
 [<span data-ttu-id="e8996-170">開發使用 WCF 通道模型的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="e8996-170">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)