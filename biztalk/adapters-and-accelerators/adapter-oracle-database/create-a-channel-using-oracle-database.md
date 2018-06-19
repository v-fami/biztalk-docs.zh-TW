---
title: 建立通道使用 Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- creating a channel
- WCF channel model, creating a channel
- how to, create a channel
- channel programming, creating a channel
ms.assetid: a30156a0-5a5a-4418-be17-2e23c3716fc1
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 413f62a679c0510be34289900b92188554e622c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25963676"
---
# <a name="create-a-channel-using-oracle-database"></a><span data-ttu-id="e897a-102">建立通道使用 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="e897a-102">Create a channel using Oracle Database</span></span>
<span data-ttu-id="e897a-103">在 WCF 通道模型中，叫用 Oracle 資料庫上的作業，接收交換的 SOAP 訊息來輪詢查詢的結果[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]透過 WCF 通道。</span><span class="sxs-lookup"><span data-stu-id="e897a-103">In the WCF channel model, you invoke operations on the Oracle database and receive the results of a polling query by exchanging SOAP messages with the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="e897a-104">您使用叫用作業 （輸出作業） **IRequestChannel**或**IOutputChannel**將訊息傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="e897a-104">You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter.</span></span>  
  
-   <span data-ttu-id="e897a-105">透過接收 POLLINGSTMT 訊息接收輪詢基礎資料變更的訊息**IInputChannel**。</span><span class="sxs-lookup"><span data-stu-id="e897a-105">You receive polling-based data-changed messages by receiving POLLINGSTMT messages over an **IInputChannel**.</span></span>  
  
 <span data-ttu-id="e897a-106">本節中的主題提供有關如何建立及設定可用於輸入和輸出作業的通道形狀的資訊。</span><span class="sxs-lookup"><span data-stu-id="e897a-106">The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="e897a-107">建立輸出 （用戶端） 通道</span><span class="sxs-lookup"><span data-stu-id="e897a-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="e897a-108">您可以使用**IRequestChannel**或**IOutputChannel**叫用的 Oracle 資料庫上的作業。</span><span class="sxs-lookup"><span data-stu-id="e897a-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the Oracle database.</span></span> <span data-ttu-id="e897a-109">在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。</span><span class="sxs-lookup"><span data-stu-id="e897a-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="e897a-110">然後，您會使用處理站建立通道。</span><span class="sxs-lookup"><span data-stu-id="e897a-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="e897a-111">在建立通道之後，您可以使用它來叫用的介面卡上的作業。</span><span class="sxs-lookup"><span data-stu-id="e897a-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="e897a-112">若要建立並開啟傳出的通道</span><span class="sxs-lookup"><span data-stu-id="e897a-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="e897a-113">建立和初始化的執行個體**ChannelFactory**為使用端點與繫結所需的通道圖案。</span><span class="sxs-lookup"><span data-stu-id="e897a-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="e897a-114">端點指定的 Oracle 連接 URI，而且繫結的執行個體**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="e897a-114">The endpoint specifies an Oracle connection URI and the binding is an instance of **OracleDBBinding**.</span></span>  
  
2.  <span data-ttu-id="e897a-115">使用提供的通道處理站的 Oracle 認證**認證**屬性。</span><span class="sxs-lookup"><span data-stu-id="e897a-115">Provide Oracle credentials for the channel factory by using the **Credentials** property.</span></span>  
  
3.  <span data-ttu-id="e897a-116">開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="e897a-116">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="e897a-117">取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。</span><span class="sxs-lookup"><span data-stu-id="e897a-117">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="e897a-118">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="e897a-118">Open the channel.</span></span>  
  
 <span data-ttu-id="e897a-119">在您的程式碼或組態中，您可以指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="e897a-119">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="e897a-120">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="e897a-120">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="e897a-121">下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="e897a-121">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="e897a-122">若要建立的程式碼**IOutputChannel**也相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。</span><span class="sxs-lookup"><span data-stu-id="e897a-122">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
OracleDBBinding odbBinding = new OracleDBBinding();  
  
// Create address.  
EndpointAddress odbAddress = new EndpointAddress("oracledb://ADAPTER/");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(odbBinding, odbAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open factory  
factory.Open();  
  
// Get channel and open it  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="e897a-123">在組態中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="e897a-123">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="e897a-124">下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。</span><span class="sxs-lookup"><span data-stu-id="e897a-124">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="e897a-125">組態設定</span><span class="sxs-lookup"><span data-stu-id="e897a-125">The Configuration Settings</span></span>  
 <span data-ttu-id="e897a-126">下列程式碼示範使用上述範例的組態設定。</span><span class="sxs-lookup"><span data-stu-id="e897a-126">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="e897a-127">用戶端端點的合約必須是"System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IRequestChannel 」，您想要建立的通道類型的類型而定。</span><span class="sxs-lookup"><span data-stu-id="e897a-127">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IRequestChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <oracleDBBinding>  
                <binding name="OracleDBBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" metadataPooling="true"  
                    statementCachePurge="false" statementCacheSize="10" pollingInterval="500"  
                    useOracleConnectionPool="true" minPoolSize="1" maxPoolSize="100"  
                    incrPoolSize="5" decrPoolSize="1" connectionLifetime="0" acceptCredentialsInUri="false"  
                    useAmbientTransaction="true" polledDataAvailableStatement="SELECT 1 FROM DUAL"  
                    pollWhileDataFound="false" notifyOnListenerStart="true" notificationPort="-1"  
                    inboundOperationType="Polling" dataFetchSize="65536" longDatatypeColumnSize="0"  
                    skipNilNodes="true" maxOutputAssociativeArrayElements="32"  
                    enableSafeTyping="false" insertBatchSize="1" useSchemaInNameSpace="true"  
                    enableBizTalkCompatibilityMode="false" enablePerformanceCounters="false" />  
            </oracleDBBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracledb://adapter/" binding="oracleDBBinding"  
                bindingConfiguration="OracleDBBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a><span data-ttu-id="e897a-128">建立輸入 （服務） 通道</span><span class="sxs-lookup"><span data-stu-id="e897a-128">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="e897a-129">您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢的 Oracle 資料庫資料表和檢視所設定的執行個體上的繫結屬性**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="e897a-129">You configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll the Oracle database tables and views by setting binding properties on an instance of **OracleDBBinding**.</span></span> <span data-ttu-id="e897a-130">然後使用這個繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收來自配接器的輸入作業的訊息。</span><span class="sxs-lookup"><span data-stu-id="e897a-130">You then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive message for inbound operations from the adapter.</span></span>  
  
##### <a name="to-create-and-open-an-iinputchannel-to-receive-messages-for-inbound-operations"></a><span data-ttu-id="e897a-131">建立與開啟 IInputChannel 來接收訊息的輸入作業</span><span class="sxs-lookup"><span data-stu-id="e897a-131">To create and open an IInputChannel to receive messages for inbound operations</span></span>  
  
1.  <span data-ttu-id="e897a-132">建立的執行個體**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="e897a-132">Create an instance of **OracleDBBinding**.</span></span>  
  
2.  <span data-ttu-id="e897a-133">設定輸入作業所需的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="e897a-133">Set the binding properties required for the inbound operation.</span></span> <span data-ttu-id="e897a-134">例如，POLLINGSTMT 作業中，至少您必須設定**InboundOperationType**， **PollingStatement**，和**PollingInterval**繫結至屬性設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e897a-134">For example, for the POLLINGSTMT operation, at a minimum you must set the **InboundOperationType**, **PollingStatement**, and **PollingInterval** binding properties to configure the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] to poll the Oracle database.</span></span>  
  
3.  <span data-ttu-id="e897a-135">建立繫結參數集合使用**BindingParameterCollection**類別，並設定認證。</span><span class="sxs-lookup"><span data-stu-id="e897a-135">Create a binding parameter collection using the **BindingParameterCollection** class and set the credentials.</span></span>  
  
4.  <span data-ttu-id="e897a-136">叫用來建立通道接聽程式**BuildChannelListener\<IInputChannel\>** 方法**OracleDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="e897a-136">Create a channel listener by invoking **BuildChannelListener\<IInputChannel\>** method on the **OracleDBBinding**.</span></span> <span data-ttu-id="e897a-137">您可以指定 Oracle 連線 URI 為其中一個參數，這個方法。</span><span class="sxs-lookup"><span data-stu-id="e897a-137">You specify the Oracle connection URI as one of the parameters to this method.</span></span> <span data-ttu-id="e897a-138">如需 Oracle 連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="e897a-138">For more information about the Oracle connection URI, see [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md).</span></span>  
  
5.  <span data-ttu-id="e897a-139">開啟接聽程式。</span><span class="sxs-lookup"><span data-stu-id="e897a-139">Open the listener.</span></span>  
  
6.  <span data-ttu-id="e897a-140">取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法。</span><span class="sxs-lookup"><span data-stu-id="e897a-140">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
7.  <span data-ttu-id="e897a-141">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="e897a-141">Open the channel.</span></span>  
  
 <span data-ttu-id="e897a-142">下列程式碼示範如何建立通道接聽程式，並取得**IInputChannel**來輸入訊息從配接器使用 POLLINGSTMT 作業。</span><span class="sxs-lookup"><span data-stu-id="e897a-142">The following code shows how to create a channel listener and get an **IInputChannel** to inbound messages from the adapter using the POLLINGSTMT operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e897a-143">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]僅支援單向接收。</span><span class="sxs-lookup"><span data-stu-id="e897a-143">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] only supports one-way receive.</span></span> <span data-ttu-id="e897a-144">因此，您必須使用 IInputChannel 從 Oracle 資料庫接收訊息的輸入操作。</span><span class="sxs-lookup"><span data-stu-id="e897a-144">So, you must use IInputChannel to receive messages for inbound operations from Oracle database.</span></span>  
  
```  
// Create a binding: specify the InboundOperationType, PollingInterval (in seconds), the PollingStatement, and  
// the PostPollStatement.  
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
  
// Get a listener from the binding and open it.  
Uri connectionUri = new Uri("oracleDB://ADAPTER");  
IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
listener.Open();  
  
// Get a channel from the listener and open it.  
channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="e897a-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="e897a-145">See Also</span></span>  
 [<span data-ttu-id="e897a-146">開發 Oracle 資料庫應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="e897a-146">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)