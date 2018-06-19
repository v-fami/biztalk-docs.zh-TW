---
title: 建立使用 SQL 配接器的通道 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e86398f6-c835-46f8-814f-31e43b18970e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c31146310b8c8b559fcd93d19362679b060cb42
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25962804"
---
# <a name="create-a-channel-using-the-sql-adapter"></a><span data-ttu-id="3298e-102">建立使用 SQL 配接器的通道</span><span class="sxs-lookup"><span data-stu-id="3298e-102">Create a channel using the SQL adapter</span></span>
<span data-ttu-id="3298e-103">在 WCF 通道模型中，叫用 SQL Server 資料庫上的作業，藉由交換的 SOAP 訊息接收結果[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]透過 WCF 通道。</span><span class="sxs-lookup"><span data-stu-id="3298e-103">In the WCF channel model, you invoke operations on the SQL Server database and receive the results by exchanging SOAP messages with the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="3298e-104">您藉由使用叫用傳出作業**IRequestChannel**或**IOutputChannel**將訊息傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="3298e-104">You invoke outbound operations by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter.</span></span>  
  
-   <span data-ttu-id="3298e-105">您透過接收訊息來接收訊息的輸入操作**IInputChannel**如**輪詢**， **TypedPolling**，或**通知**作業。</span><span class="sxs-lookup"><span data-stu-id="3298e-105">You receive messages for inbound operations by receiving messages over an **IInputChannel** for **Polling**, **TypedPolling**, or **Notification** operations.</span></span>  
  
 <span data-ttu-id="3298e-106">本主題中的程序會提供有關如何建立及設定可用於輸入和輸出作業的通道形狀的資訊。</span><span class="sxs-lookup"><span data-stu-id="3298e-106">The procedures in this topic provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="3298e-107">建立輸出 （用戶端） 通道</span><span class="sxs-lookup"><span data-stu-id="3298e-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="3298e-108">您可以使用**IRequestChannel**或**IOutputChannel**叫用 SQL Server 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="3298e-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the SQL Server database.</span></span> <span data-ttu-id="3298e-109">在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。</span><span class="sxs-lookup"><span data-stu-id="3298e-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="3298e-110">然後，您會使用處理站建立通道。</span><span class="sxs-lookup"><span data-stu-id="3298e-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="3298e-111">在建立通道之後，您可以使用它來叫用的介面卡上的作業。</span><span class="sxs-lookup"><span data-stu-id="3298e-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="3298e-112">若要建立並開啟傳出的通道</span><span class="sxs-lookup"><span data-stu-id="3298e-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="3298e-113">建立和初始化的執行個體**ChannelFactory**為使用端點與繫結所需的通道圖案。</span><span class="sxs-lookup"><span data-stu-id="3298e-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="3298e-114">端點指定的 SQL Server 連接 URI，而且繫結的執行個體**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="3298e-114">The endpoint specifies a SQL Server connection URI and the binding is an instance of **sqlBinding**.</span></span>  
  
2.  <span data-ttu-id="3298e-115">使用通道處理站提供 SQL Server 認證**認證**屬性。</span><span class="sxs-lookup"><span data-stu-id="3298e-115">Provide SQL Server credentials for the channel factory by using the **Credentials** property.</span></span>  
  
3.  <span data-ttu-id="3298e-116">開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="3298e-116">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="3298e-117">取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。</span><span class="sxs-lookup"><span data-stu-id="3298e-117">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="3298e-118">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="3298e-118">Open the channel.</span></span>  
  
 <span data-ttu-id="3298e-119">在您的程式碼或組態中，您可以指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="3298e-119">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="3298e-120">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="3298e-120">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="3298e-121">下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="3298e-121">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="3298e-122">若要建立的程式碼**IOutputChannel**也相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。</span><span class="sxs-lookup"><span data-stu-id="3298e-122">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
SqlAdapterBinding sdbBinding = new SqlAdapterBinding();  
  
// Create address.  
EndpointAddress sdbAddress = new EndpointAddress("mssql://<sql_server_name>//<database_name>?");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(sdbBinding, sdbAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="3298e-123">在組態中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="3298e-123">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="3298e-124">下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。</span><span class="sxs-lookup"><span data-stu-id="3298e-124">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="3298e-125">組態設定</span><span class="sxs-lookup"><span data-stu-id="3298e-125">The Configuration Settings</span></span>  
 <span data-ttu-id="3298e-126">下列程式碼示範使用上述範例的組態設定。</span><span class="sxs-lookup"><span data-stu-id="3298e-126">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="3298e-127">用戶端端點的合約必須是"System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IOutputChannel 」，您想要建立的通道類型的類型而定。</span><span class="sxs-lookup"><span data-stu-id="3298e-127">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IOutputChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sqlBinding>  
                <binding name="SqlAdapterBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" maxConnectionPoolSize="100"  
                    encrypt="false" useAmbientTransaction="true" batchSize="20"  
                    polledDataAvailableStatement="" pollingStatement="" pollingIntervalInSeconds="30"  
                    pollWhileDataFound="false" notificationStatement="" notifyOnListenerStart="true"  
                    enableBizTalkCompatibilityMode="true" chunkSize="4194304"  
                    inboundOperationType="Polling" useDatabaseNameInXsdNamespace="false"  
                    allowIdentityInsert="false" enablePerformanceCounters="false"  
                    xmlStoredProcedureRootNodeName="" xmlStoredProcedureRootNodeNamespace="" />  
            </sqlBinding>  
        </bindings>  
        <client>  
            <endpoint address="mssql://mysqlserver//mydatabase?" binding="sqlBinding"  
                bindingConfiguration="SqlAdapterBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="creating-inbound-service-channels"></a><span data-ttu-id="3298e-128">建立輸入 （服務） 通道</span><span class="sxs-lookup"><span data-stu-id="3298e-128">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="3298e-129">您設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢屬性來設定繫結的執行個體的 SQL Server 資料庫資料表和檢視表**sqlBinding**。</span><span class="sxs-lookup"><span data-stu-id="3298e-129">You configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll the SQL Server database tables and views by setting binding properties on an instance of **sqlBinding**.</span></span> <span data-ttu-id="3298e-130">然後使用這個繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收**輪詢**， **TypedPolling**，或**通知**從配接器的作業。</span><span class="sxs-lookup"><span data-stu-id="3298e-130">You then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive the **Polling**, **TypedPolling**, or **Notification** operation from the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-iinputchannel-to-receive-inbound-operations"></a><span data-ttu-id="3298e-131">建立與開啟 IInputChannel 接收輸入的作業</span><span class="sxs-lookup"><span data-stu-id="3298e-131">To create and open an IInputChannel to receive inbound operations</span></span>  
  
1.  <span data-ttu-id="3298e-132">建立的執行個體**SQLBinding**。</span><span class="sxs-lookup"><span data-stu-id="3298e-132">Create an instance of **SQLBinding**.</span></span>  
  
2.  <span data-ttu-id="3298e-133">設定輸入作業所需的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="3298e-133">Set the binding properties required for inbound operation.</span></span> <span data-ttu-id="3298e-134">例如，對於**輪詢**作業，您必須設定至少**InboundOperationType**， **PolledDataAvailableStatement**，和**PollingStatement**繫結內容來設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3298e-134">For example, for a **Polling** operation, at a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, and **PollingStatement** binding properties to configure the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to poll the SQL Server database.</span></span>  
  
3.  <span data-ttu-id="3298e-135">叫用來建立通道接聽程式**BuildChannelListener\<IInputChannel\>** 方法**SQLBinding**。</span><span class="sxs-lookup"><span data-stu-id="3298e-135">Create a channel listener by invoking **BuildChannelListener\<IInputChannel\>** method on the **SQLBinding**.</span></span> <span data-ttu-id="3298e-136">您可以指定 SQL Server 連接 URI 為其中一個參數，這個方法。</span><span class="sxs-lookup"><span data-stu-id="3298e-136">You specify the SQL Server connection URI as one of the parameters to this method.</span></span>  
  
4.  <span data-ttu-id="3298e-137">開啟接聽程式。</span><span class="sxs-lookup"><span data-stu-id="3298e-137">Open the listener.</span></span>  
  
5.  <span data-ttu-id="3298e-138">取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法。</span><span class="sxs-lookup"><span data-stu-id="3298e-138">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
6.  <span data-ttu-id="3298e-139">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="3298e-139">Open the channel.</span></span>  
  
 <span data-ttu-id="3298e-140">下列程式碼示範如何建立通道接聽程式，並取得**IInputChannel**從配接器接收的資料變更的訊息。</span><span class="sxs-lookup"><span data-stu-id="3298e-140">The following code shows how to create a channel listener and get an **IInputChannel** to receive data-changed messages from the adapter.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3298e-141">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]僅支援單向接收。</span><span class="sxs-lookup"><span data-stu-id="3298e-141">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] only supports one-way receive.</span></span> <span data-ttu-id="3298e-142">因此，您必須使用**IInputChannel**以接收來自 SQL Server 的輸入作業的訊息。</span><span class="sxs-lookup"><span data-stu-id="3298e-142">So, you must use **IInputChannel** to receive messages for inbound operations from SQL Server.</span></span>  
  
```  
// Create a binding: specify the InboundOperationType, the PolledDataAvailableStatement, and   
// the PollingStatement binding properties.  
SqlAdapterBinding binding = new SqlAdapterBinding();  
binding.InboundOperationType = InboundOperation.Polling;  
binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM EMPLOYEE";  
binding.PollingStatement = "SELECT * FROM Employee;EXEC MOVE_EMP_DATA;EXEC ADD_EMP_DETAILS John, Tester, 100000";  
  
// Create a binding parameter collection and set the credentials  
ClientCredentials credentials = new ClientCredentials();  
credentials.UserName.UserName = "myuser";  
credentials.UserName.Password = "mypassword";  
  
BindingParameterCollection bindingParams = new BindingParameterCollection();  
bindingParams.Add(credentials);  
  
// Get a listener from the binding and open it.  
Uri connectionUri = new Uri("mssql://mysqlserver//mydatabase?");  
IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
listener.Open();  
  
// Get a channel from the listener and open it.  
IInputChannel channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="3298e-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="3298e-143">See Also</span></span>  
[<span data-ttu-id="3298e-144">使用 WCF 通道模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="3298e-144">Develop applications using the WCF Channel model</span></span>](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)