---
title: "使用 WCF 通道模型的 Oracle 資料庫中收到輪詢基礎資料變更的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, receiving polling-based messages
- how to, receive polling-based messages by using the WCF channel model
ms.assetid: 13f501e4-cff7-497c-a9da-fdd6382c779f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 01e1596c0b0676db916068ff9a33a8be9d6a9fa3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receive-polling-based-data-changed-messages-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="e7ae5-102">使用 WCF 通道模型的 Oracle 資料庫中收到輪詢基礎資料變更的訊息</span><span class="sxs-lookup"><span data-stu-id="e7ae5-102">Receive Polling-based Data-changed Messages in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="e7ae5-103">您可以設定[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]輪詢 Oracle 資料庫資料表或檢視之任何資料變更。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-103">You can configure the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to poll an Oracle database table or view for any data changes.</span></span> <span data-ttu-id="e7ae5-104">若要執行這類輪詢作業時，配接器會定期執行的 Oracle 資料表或檢視，後面接著選擇性的 PL/SQL 程式碼區塊的 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-104">To perform such a polling operation, the adapter periodically executes a SQL query against an Oracle table or view followed by an optional PL/SQL code block.</span></span> <span data-ttu-id="e7ae5-105">SQL 查詢的結果則會傳回由[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]為強類型的結果集，傳入的 POLLINGSTMT 作業程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-105">The results of the SQL query are then returned by the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to your code as a strongly-typed result set in an inbound POLLINGSTMT operation.</span></span> <span data-ttu-id="e7ae5-106">如需有關用來設定和執行 oracle 輪詢機制資料庫使用[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]，請參閱[在 Oracle 資料庫配接器收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-106">For more information about the mechanism used to configure and perform polling on an Oracle database using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)], see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span> <span data-ttu-id="e7ae5-107">強烈建議您先閱讀本主題後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-107">It is strongly recommended that you read this topic before proceeding.</span></span>  
  
 <span data-ttu-id="e7ae5-108">您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢和 Oracle 資料庫資料表或檢視的執行個體上設定繫結屬性**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-108">You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll and Oracle database table or view by setting binding properties on an instance of **OracleDBBinding**.</span></span> <span data-ttu-id="e7ae5-109">在 WCF 通道模型，然後您使用此繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收來自配接器 POLLINGSTMT 作業。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-109">In the WCF channel model, you then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive the POLLINGSTMT operation from the adapter.</span></span>  
  
 <span data-ttu-id="e7ae5-110">如需如何接收作業使用的概觀**IInputChannel**在 WCF 中，請參閱[服務通道層級程式設計](https://msdn.microsoft.com/library/ms789029.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-110">For an overview of how to receive operations using an **IInputChannel** in WCF, see [Service Channel-Level Programming](https://msdn.microsoft.com/library/ms789029.aspx).</span></span> 
  
 <span data-ttu-id="e7ae5-111">本主題中的章節提供可協助您執行輪詢 Oracle 資料庫資料表上的資訊，並檢視使用 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-111">The sections in this topic provide information to help you perform polling on Oracle database tables and views using the WCF channel model.</span></span>  
  
## <a name="consuming-the-pollingstmt-request-message"></a><span data-ttu-id="e7ae5-112">耗用 POLLINGSTMT 要求訊息</span><span class="sxs-lookup"><span data-stu-id="e7ae5-112">Consuming the POLLINGSTMT request message</span></span>  
 <span data-ttu-id="e7ae5-113">配接器會叫用 POLLINGSTMT 上的作業程式碼，以輪詢 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-113">The adapter invokes the POLLINGSTMT operation on your code to poll the Oracle database.</span></span> <span data-ttu-id="e7ae5-114">也就是說，配接器傳送 POLLINGSTMT 要求訊息，您透過接收**IInputChannel**通道圖案。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-114">That is, the adapter sends a POLLINGSTMT request message that you receive over an **IInputChannel** channel shape.</span></span> <span data-ttu-id="e7ae5-115">POLLINGSTMT 要求訊息包含所指定的查詢的結果集**PollingStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-115">The POLLINGSTMT request message contains the result set of the query specified by the **PollingStatement** binding property.</span></span> <span data-ttu-id="e7ae5-116">您可以使用 POLLINGSTMT 訊息中有兩種：</span><span class="sxs-lookup"><span data-stu-id="e7ae5-116">You can consume the POLLINGSTMT message in one of two ways:</span></span>  
  
-   <span data-ttu-id="e7ae5-117">若要使用訊息使用的節點值的資料流您必須呼叫**WriteBodyContents**方法回應訊息，並將它傳遞**XmlDictionaryWriter**實作節點值的資料流。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-117">To consume the message using node-value streaming you must call the **WriteBodyContents** method on the response message and pass it an **XmlDictionaryWriter** that implements node-value streaming.</span></span>  
  
-   <span data-ttu-id="e7ae5-118">若要使用訊息使用節點資料流處理，您可以呼叫**GetReaderAtBodyContents**要取得的回應訊息上**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-118">To consume the message using node streaming you can call **GetReaderAtBodyContents** on the response message to get an **XmlReader**.</span></span>  
  
 <span data-ttu-id="e7ae5-119">您通常使用的節點值的資料流來取用包含 Oracle LOB 資料行的結果集。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-119">You typically use node-value streaming to consume result sets that contain Oracle LOB data columns.</span></span>  
  
 <span data-ttu-id="e7ae5-120">如需 POLLINGSTMT 作業的訊息結構的詳細資訊，請參閱[輪詢作業的訊息結構描述](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-120">For more information about the message structure of the POLLINGSTMT operation, see [Message Schemas for the Polling Operations](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-polling-operations2.md).</span></span>  
  
 <span data-ttu-id="e7ae5-121">如需有關如何[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援資料流處理 LOB 資料，請參閱[串流處理大型物件資料類型在 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-121">For more information about how the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports streaming on LOB data, see [Streaming large object data types in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).</span></span>  
  
 <span data-ttu-id="e7ae5-122">如需實作串流處理您的程式碼，以支援端對端 LOB 資料的資料流中的節點值的詳細資訊，請參閱[串流處理 Oracle 資料庫的 LOB 資料類型使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-122">For more information about implementing node-value streaming in your code to support end-to-end streaming of LOB data, see [Streaming Oracle Database LOB Data Types Using the WCF Channel Model](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).</span></span>  
  
## <a name="about-the-examples-used-in-this-topic"></a><span data-ttu-id="e7ae5-123">關於本主題中使用的範例</span><span class="sxs-lookup"><span data-stu-id="e7ae5-123">About the Examples Used in this Topic</span></span>  
 <span data-ttu-id="e7ae5-124">本主題中的範例使用 SCOTT。ACCOUNTACTIVITY 資料表與 SCOTT。ACCOUNT_PKG。PROCESS_ACTIVITY 函式。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-124">The example in this topic uses the SCOTT.ACCOUNTACTIVITY table and the SCOTT.ACCOUNT_PKG.PROCESS_ACTIVITY function.</span></span> <span data-ttu-id="e7ae5-125">指令碼來產生這些成品隨附的範例。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-125">A script to generate these artifacts is supplied with the samples.</span></span> <span data-ttu-id="e7ae5-126">這個範例會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e7ae5-126">The example performs the following operations:</span></span>  
  
-   <span data-ttu-id="e7ae5-127">輪詢陳述式的一部分，請從 ACCOUNTACTIVITY 資料表並在主控台上的顯示選取的所有記錄。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-127">As part of the polling statement, selects all the records from the ACCOUNTACTIVITY table and displays on the console.</span></span>  
  
-   <span data-ttu-id="e7ae5-128">後輪詢陳述式的一部分，此範例會叫用 ACCOUNTACTIVITY 資料表中的所有記錄都移到 ACTIVITYHISTORY 資料表 PROCESS_ACTIVITY 函式。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-128">As part of the post poll statement, the example invokes the PROCESS_ACTIVITY function that moves all the records from ACCOUNTACTIVITY table to ACTIVITYHISTORY table.</span></span>  
  
-   <span data-ttu-id="e7ae5-129">後續輪詢 ACCOUNTACTIVITY 資料表上的不會傳回任何記錄。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-129">Subsequent polls on the ACCOUNTACTIVITY table do not return any records.</span></span> <span data-ttu-id="e7ae5-130">不過，如果您想要輪詢作業會傳回更多筆記錄的範例，您就必須 ACCOUNTACTIVITY 資料表中插入一些記錄。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-130">However, if you want the example to return more records as part of the polling operation, you must insert some records in the ACCOUNTACTIVITY table.</span></span> <span data-ttu-id="e7ae5-131">您可以藉由執行範例所提供的 more_activity_data.sql 指令碼。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-131">You can do so by running the more_activity_data.sql script provided with the samples.</span></span>  
  
 <span data-ttu-id="e7ae5-132">如需這些範例的詳細資訊，請參閱[配接器範例](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-132">For more information about the samples, see [Adapter Samples](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).</span></span>  
  
## <a name="how-do-i-poll-an-oracle-database-using-an-iinputchannel"></a><span data-ttu-id="e7ae5-133">我要如何輪詢 Oracle 資料庫使用 IInputChannel？</span><span class="sxs-lookup"><span data-stu-id="e7ae5-133">How Do I Poll an Oracle Database Using an IInputChannel?</span></span>  
 <span data-ttu-id="e7ae5-134">若要輪詢的 Oracle 資料庫資料表或檢視，以接收使用 WCF 通道模型的資料變更訊息，執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-134">To poll an Oracle database table or view to receive data-change messages using the WCF channel model, perform the following steps.</span></span>  
  
#### <a name="to-receive-data-changed-messages-using-an-iinputchannel"></a><span data-ttu-id="e7ae5-135">若要接收的資料變更的訊息使用 IInputChannel</span><span class="sxs-lookup"><span data-stu-id="e7ae5-135">To receive data-changed messages using an IInputChannel</span></span>  
  
1.  <span data-ttu-id="e7ae5-136">Visual C# 中建立專案[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-136">Create a Visual C# project in [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="e7ae5-137">本主題中，建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-137">For this topic, create a console application.</span></span>  
  
2.  <span data-ttu-id="e7ae5-138">在 [方案總管] 中，加入參考`Microsoft.Adapters.OracleDB`， `Microsoft.ServiceModel.Channels`， `System.ServiceModel`，和`System.Runtime.Serialization`。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-138">In the Solution Explorer, add reference to `Microsoft.Adapters.OracleDB`, `Microsoft.ServiceModel.Channels`, `System.ServiceModel`, and `System.Runtime.Serialization`.</span></span>  
  
3.  <span data-ttu-id="e7ae5-139">開啟 Program.cs 檔案並加入下列命名空間：</span><span class="sxs-lookup"><span data-stu-id="e7ae5-139">Open the Program.cs file and add the following namespaces:</span></span>  
  
    -   `Microsoft.Adapters.OracleDB`  
  
    -   `Microsoft.ServiceModel.Channels`  
  
    -   `System.ServiceModel`  
  
    -   `System.ServiceModel.Description`  
  
    -   `System.ServiceModel.Channels`  
  
    -   `System.Xml`  
  
    -   `System.Runtime.Serialization`  
  
    -   `System.IO`  
  
    -   `Microsoft.ServiceModel.Channels.Common`  
  
4.  <span data-ttu-id="e7ae5-140">建立的執行個體**OracleDBBinding**並設定繫結屬性才能設定輪詢。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-140">Create an instance of **OracleDBBinding** and set the binding properties required to configure polling.</span></span> <span data-ttu-id="e7ae5-141">您必須設定至少**InboundOperationType**， **PollingStatement**，和**PollingInterval**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-141">At a minimum you must set the **InboundOperationType**, **PollingStatement**, and **PollingInterval** binding properties.</span></span> <span data-ttu-id="e7ae5-142">為此範例中，您也可以設定**PostPollStatement**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-142">For this example, you also set the **PostPollStatement** binding property.</span></span> <span data-ttu-id="e7ae5-143">如需繫結屬性用來設定輪詢的詳細資訊，請參閱[在 Oracle 資料庫配接器收到輪詢基礎資料變更的訊息](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-143">For more information about binding properties used to configure polling, see [Receive polling-based data-changed messages in Oracle Database adapter](../../adapters-and-accelerators/adapter-oracle-database/receive-polling-based-data-changed-messages-in-oracle-database-adapter.md).</span></span>  
  
    ```  
    OracleDBBinding binding = new OracleDBBinding();  
    binding.InboundOperationType = InboundOperation.Polling;  
    binding.PollingInterval = 30;  
    binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
    binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;"  
    ```  
  
5.  <span data-ttu-id="e7ae5-144">建立繫結參數集合，並設定認證。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-144">Create a binding parameter collection and set the credentials.</span></span>  
  
    ```  
    ClientCredentials credentials = new ClientCredentials();  
    credentials.UserName.UserName = "SCOTT";  
    credentials.UserName.Password = "TIGER";  
  
    BindingParameterCollection bindingParams = new BindingParameterCollection();  
    bindingParams.Add(credentials);  
    ```  
  
6.  <span data-ttu-id="e7ae5-145">建立通道接聽程式，並將它開啟。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-145">Create a channel listener and open it.</span></span> <span data-ttu-id="e7ae5-146">您建立的接聽程式叫用**BuildChannelListener < IInputChannel\>** 方法**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-146">You create the listener by invoking **BuildChannelListener<IInputChannel\>** method on the **OracleDBBinding**.</span></span> <span data-ttu-id="e7ae5-147">您可以修改 POLLINGSTMT 作業的目標命名空間中的連線 URI 設定 PollingId 屬性。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-147">You can modify the target namespace for the POLLINGSTMT operation by setting the PollingId property in the connection URI.</span></span> <span data-ttu-id="e7ae5-148">如需配接器的連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-148">For more information about the adapter connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
    ```  
    IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
    listener.Open();  
    ```  
  
7.  <span data-ttu-id="e7ae5-149">取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法，並開啟它。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-149">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on the listener and open it.</span></span>  
  
    ```  
    IInputChannel channel = listener.AcceptChannel();  
    channel.Open();  
    ```  
  
8.  <span data-ttu-id="e7ae5-150">叫用**接收**從配接器取得下一個 POLLINGSTMT 訊息之通道上。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-150">Invoke **Receive** on the channel to get the next POLLINGSTMT message from the adapter.</span></span>  
  
    ```  
    Message message = channel.Receive();  
    ```  
  
9. <span data-ttu-id="e7ae5-151">耗用 POLLINGSTMT 作業所傳回的結果集。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-151">Consume the result set returned by the POLLINGSTMT operation.</span></span> <span data-ttu-id="e7ae5-152">您可以使用訊息使用**XmlReader**或**XmlDictionaryWriter**。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-152">You can consume the message using either an **XmlReader** or an **XmlDictionaryWriter**.</span></span>  
  
    ```  
    XmlReader reader = message.GetReaderAtBodyContents();  
    ```  
  
10. <span data-ttu-id="e7ae5-153">當您完成處理要求，請關閉通道。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-153">Close the channel when you have completed processing the request.</span></span>  
  
    ```  
    channel.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e7ae5-154">處理 POLLINGSTMT 作業完成之後，您必須關閉通道。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-154">You must close the channel after you have finished processing the POLLINGSTMT operation.</span></span> <span data-ttu-id="e7ae5-155">無法關閉通道可能會影響您的程式碼的行為。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-155">Failure to close the channel may affect the behavior of your code.</span></span>  
  
11. <span data-ttu-id="e7ae5-156">當您完成接收的資料變更的訊息時，請關閉接聽程式。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-156">Close the listener when you are finished receiving data-changed messages.</span></span>  
  
    ```  
    listener.Close()  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e7ae5-157">關閉接聽程式不會關閉建立使用接聽程式通道。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-157">Closing the listener does not close channels created using the listener.</span></span> <span data-ttu-id="e7ae5-158">您必須明確地關閉使用接聽程式所建立的每個通道。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-158">You must explicitly close each channel created using the listener.</span></span>  
  
### <a name="example"></a><span data-ttu-id="e7ae5-159">範例</span><span class="sxs-lookup"><span data-stu-id="e7ae5-159">Example</span></span>  
 <span data-ttu-id="e7ae5-160">下列範例示範如何設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢 Oracle 資料庫資料表和檢視表和接收 POLLLINGSTMT 作業使用的 WCF 通道模型。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-160">The following example shows how to configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll Oracle database tables and views and receive the POLLLINGSTMT operation using the WCF channel model.</span></span> <span data-ttu-id="e7ae5-161">POLLINGSTMT 作業中傳回的結果集透過使用撰寫主控台**XmlReader**。</span><span class="sxs-lookup"><span data-stu-id="e7ae5-161">The result set returned in the POLLINGSTMT operation is written to the console by using an **XmlReader**.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
// Add WCF, WCF LOB Adapter SDK, and Oracle Database adapter namepaces  
using System.ServiceModel;  
using System.ServiceModel.Description;  
using Microsoft.ServiceModel.Channels;  
using Microsoft.Adapters.OracleDB;  
  
// Add this namespace for channel model  
using System.ServiceModel.Channels;  
  
using System.Xml;  
using System.Runtime.Serialization;  
using System.IO;  
  
// Include this namespace for the WCF LOB Adapter SDK and Oracle exceptions  
using Microsoft.ServiceModel.Channels.Common;  
  
namespace OraclePollingCM  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            Uri connectionUri = new Uri("oracleDB://ADAPTER/");  
  
            IChannelListener<IInputChannel> listener = null;  
            IInputChannel channel = null;  
  
            // set timeout to receive POLLINGSTMT message  
            TimeSpan messageTimeout = new TimeSpan(0, 0, 30);  
  
            Console.WriteLine("Sample Started");  
  
            try  
            {  
                // Create a binding: specify the InboundOperationType, PollingInterval (in seconds), the           
                // PollingStatement,and the PostPollStatement.  
                OracleDBBinding binding = new OracleDBBinding();  
                binding.InboundOperationType = InboundOperation.Polling;  
                binding.PollingInterval = 30;  
                binding.PollingStatement = "SELECT * FROM ACCOUNTACTIVITY FOR UPDATE";  
                binding.PostPollStatement = "BEGIN ACCOUNT_PKG.PROCESS_ACTIVITY(); END;";  
  
                // Create a binding parameter collection and set the credentials  
                ClientCredentials credentials = new ClientCredentials();  
                credentials.UserName.UserName = "SCOTT";  
                credentials.UserName.Password = "TIGER";  
  
                BindingParameterCollection bindingParams = new BindingParameterCollection();  
                bindingParams.Add(credentials);  
  
                Console.WriteLine("Opening listener");  
                // get a listener  from the binding  
                listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
                listener.Open();  
  
                Console.WriteLine("Opening channel");  
                // get a channel from the listener  
                channel = listener.AcceptChannel();  
                channel.Open();  
  
                Console.WriteLine("Channel opened -- waiting for polled data");  
                Console.WriteLine("Receive request timeout is {0}", messageTimeout);  
  
                // Poll five times with the specified message timeout   
                // If a timeout occurs polling will be aborted  
                for (int i = 0; i < 5; i++)  
                {  
                    Console.WriteLine("Polling: " + i);  
                    Message message = null;  
                    XmlReader reader = null;  
                    try  
                    {  
                        //Message is received so process the results  
                        message = channel.Receive(messageTimeout);  
                    }  
                    catch (System.TimeoutException toEx)  
                    {  
                        Console.WriteLine("\nNo data for request number {0}: {1}", i + 1, toEx.Message);  
                        continue;  
                    }  
  
                    // Get the query results using an XML reader  
                    try  
                    {  
                        reader = message.GetReaderAtBodyContents();  
                    }  
                    catch (Exception ex)  
                    {  
                        Console.WriteLine("Exception :" + ex);  
                        throw;  
                    }  
  
                    // Write the TID, ACCOUNT, AMOUNT, and TRANSDATE for each record to the Console  
                    Console.WriteLine("\nPolling data received for request number {0}", i+1);  
                    Console.WriteLine("Tx ID\tACCOUNT\tAMOUNT\tTx DATE");  
  
                    while (reader.Read())  
                    {  
                        if (reader.IsStartElement())  
                        {  
                            switch (reader.Name)  
                            {  
                                case "POLLINGSTMTRECORD":  
                                    Console.Write("\n");  
                                    break;  
  
                                case "TID":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "ACCOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
                                case "AMOUNT":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                case "TRANSDATE":  
                                    reader.Read();  
                                    Console.Write(reader.ReadString() + "\t");  
                                    break;  
  
                                default:  
                                    break;  
                            }  
                        }  
                    }  
  
                    // return the cursor  
                    Console.WriteLine();  
  
                    // close the reader  
                    reader.Close();  
  
                    //            To save the polling data to a file you can REPLACE the code above with the following  
                    //  
                    //            XmlDocument doc = new XmlDocument();  
                    //            doc.Load(reader);  
                    //            using (XmlWriter writer = XmlWriter.Create("PollingOutput.xml"))  
                    //            {  
                    //                doc.WriteTo(writer);  
                    //            }  
                    message.Close();  
                }  
  
                Console.WriteLine("\nPolling done -- hit <RETURN> to finish");  
                Console.ReadLine();  
            }  
            catch (TargetSystemException tex)  
            {  
                Console.WriteLine("Exception occurred on the Oracle Database");  
                Console.WriteLine(tex.InnerException.Message);  
            }  
            catch (ConnectionException cex)  
            {  
                Console.WriteLine("Exception occurred connecting to the Oracle Database");  
                Console.WriteLine(cex.InnerException.Message);  
            }  
            catch (Exception ex)  
            {  
                Console.WriteLine("Exception is: " + ex.Message);  
                if (ex.InnerException != null)  
                {  
                    Console.WriteLine("Inner Exception is: " + ex.InnerException.Message);  
                }  
            }  
            finally  
            {  
                // IMPORTANT: close the channel and listener to stop polling  
                if (channel != null)  
                {  
                    if (channel.State == CommunicationState.Opened)  
                        channel.Close();  
                    else  
                        channel.Abort();  
                }  
  
                if (listener != null)  
                {  
                    if (listener.State == CommunicationState.Opened)  
                        listener.Close();  
                    else  
                        listener.Abort();  
                }  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7ae5-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7ae5-162">See Also</span></span>  
 [<span data-ttu-id="e7ae5-163">開發 Oracle 資料庫應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="e7ae5-163">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)