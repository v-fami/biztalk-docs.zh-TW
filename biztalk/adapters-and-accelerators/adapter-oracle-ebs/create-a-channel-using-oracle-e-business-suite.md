---
title: "建立通道，使用 Oracle E-business Suite |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d18b7c2f-a43e-4499-ba94-4955dd5fe641
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0f06a8f1e8b622574f20f331069d7ca280fc45c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-channel-using-oracle-e-business-suite"></a><span data-ttu-id="a8f06-102">建立使用 Oracle E-business Suite 的通道</span><span class="sxs-lookup"><span data-stu-id="a8f06-102">Create a channel using Oracle E-Business Suite</span></span>
<span data-ttu-id="a8f06-103">在 WCF 通道模型中，叫用 Oracle E-business suite 作業，並藉由交換的 SOAP 訊息接收結果[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]透過 WCF 通道。</span><span class="sxs-lookup"><span data-stu-id="a8f06-103">In the WCF channel model, you invoke operations on the Oracle E-Business Suite and receive the results by exchanging SOAP messages with the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] over a WCF channel.</span></span>  
  
-   <span data-ttu-id="a8f06-104">您使用叫用作業 （輸出作業） **IRequestChannel**或**IOutputChannel**將訊息傳送至配接器。</span><span class="sxs-lookup"><span data-stu-id="a8f06-104">You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter.</span></span>  
  
-   <span data-ttu-id="a8f06-105">您透過接收訊息的輸入操作**IInputChannel**。</span><span class="sxs-lookup"><span data-stu-id="a8f06-105">You receive messages for inbound operations over an **IInputChannel**.</span></span>  
  
 <span data-ttu-id="a8f06-106">本節中的主題提供有關如何建立及設定可用於輸入和輸出作業的通道形狀的資訊。</span><span class="sxs-lookup"><span data-stu-id="a8f06-106">The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="a8f06-107">建立輸出 （用戶端） 通道</span><span class="sxs-lookup"><span data-stu-id="a8f06-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="a8f06-108">您可以使用**IRequestChannel**或**IOutputChannel**叫用 Oracle E-business suite 作業。</span><span class="sxs-lookup"><span data-stu-id="a8f06-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the Oracle E-Business Suite.</span></span> <span data-ttu-id="a8f06-109">在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。</span><span class="sxs-lookup"><span data-stu-id="a8f06-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="a8f06-110">然後，您會使用處理站建立通道。</span><span class="sxs-lookup"><span data-stu-id="a8f06-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="a8f06-111">在建立通道之後，您可以使用它來叫用的介面卡上的作業。</span><span class="sxs-lookup"><span data-stu-id="a8f06-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="a8f06-112">若要建立並開啟傳出的通道</span><span class="sxs-lookup"><span data-stu-id="a8f06-112">To create and open an outbound channel</span></span>  
  
1.  <span data-ttu-id="a8f06-113">建立和初始化的執行個體**ChannelFactory**為使用端點與繫結所需的通道圖案。</span><span class="sxs-lookup"><span data-stu-id="a8f06-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="a8f06-114">端點指定 Oracle E-business Suite 連線 URI，而且繫結的執行個體**OracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="a8f06-114">The endpoint specifies an Oracle E-Business Suite connection URI and the binding is an instance of **OracleEBSBinding**.</span></span>  
  
2.  <span data-ttu-id="a8f06-115">使用通道處理站提供 Oracle E-business Suite 認證**認證**屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f06-115">Provide Oracle E-Business Suite credentials for the channel factory by using the **Credentials** property.</span></span>  
  
3.  <span data-ttu-id="a8f06-116">開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="a8f06-116">Open the channel factory.</span></span>  
  
4.  <span data-ttu-id="a8f06-117">取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。</span><span class="sxs-lookup"><span data-stu-id="a8f06-117">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5.  <span data-ttu-id="a8f06-118">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="a8f06-118">Open the channel.</span></span>  
  
 <span data-ttu-id="a8f06-119">在您的程式碼或組態中，您可以指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="a8f06-119">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="a8f06-120">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="a8f06-120">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="a8f06-121">下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="a8f06-121">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="a8f06-122">若要建立的程式碼**IOutputChannel**也相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。</span><span class="sxs-lookup"><span data-stu-id="a8f06-122">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
OracleEBSBinding binding = new OracleEBSBinding();  
  
// Create address  
EndpointAddress address = new EndpointAddress("oracleebs://<oracleebs_instance_name>/");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(binding, address);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="a8f06-123">在組態中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="a8f06-123">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="a8f06-124">下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。</span><span class="sxs-lookup"><span data-stu-id="a8f06-124">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
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
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="a8f06-125">組態設定</span><span class="sxs-lookup"><span data-stu-id="a8f06-125">The Configuration Settings</span></span>  
 <span data-ttu-id="a8f06-126">下列程式碼示範使用上述範例的組態設定。</span><span class="sxs-lookup"><span data-stu-id="a8f06-126">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="a8f06-127">用戶端端點的合約必須是"System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IOutputChannel 」，您想要建立的通道類型的類型而定。</span><span class="sxs-lookup"><span data-stu-id="a8f06-127">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IOutputChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <oracleEBSBinding>  
                <binding openTimeout="00:05:00" name="OracleEBSBinding" closeTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" clientCredentialType="Database"  
                    inboundOperationType="Polling" metadataPooling="true" statementCachePurge="false"  
                    statementCacheSize="10" pollWhileDataFound="false" pollingInterval="30"  
                    useOracleConnectionPool="true" minPoolSize="1" maxPoolSize="100"  
                    incrPoolSize="5" decrPoolSize="1" connectionLifetime="0" acceptCredentialsInUri="false"  
                    useAmbientTransaction="true" notifyOnListenerStart="true"  
                    notificationPort="-1" dataFetchSize="65536" longDatatypeColumnSize="0"  
                    skipNilNodes="true" maxOutputAssociativeArrayElements="32"  
                    enableSafeTyping="false" insertBatchSize="20" useSchemaInNameSpace="true"  
                    enableBizTalkCompatibilityMode="true" enablePerformanceCounters="false">  
                    <mlsSettings language="" dateFormat="" dateLanguage="" numericCharacters=""  
                        sort="" territory="" comparison="" currency="" dualCurrency=""  
                        iSOCurrency="" calendar="" lengthSemantics="" nCharConversionException="true"  
                        timeStampFormat="" timeStampTZFormat="" timeZone="" />  
                </binding>  
            </oracleEBSBinding>  
        </bindings>  
        <client>  
            <endpoint address="oracleebs://oracle_ebs_instance/" binding="oracleEBSBinding"  
                bindingConfiguration="OracleEBSBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a><span data-ttu-id="a8f06-128">建立輸入 （服務） 通道</span><span class="sxs-lookup"><span data-stu-id="a8f06-128">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="a8f06-129">您設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢的 Oracle 資料庫資料表和檢視所設定的執行個體上的繫結屬性**OracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="a8f06-129">You configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database tables and views by setting binding properties on an instance of **OracleEBSBinding**.</span></span> <span data-ttu-id="a8f06-130">然後使用這個繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收來自配接器的輸入的操作。</span><span class="sxs-lookup"><span data-stu-id="a8f06-130">You then use this binding to build a channel listener from which you can get an **IInputChannel** channel to receive inbound operations from the adapter.</span></span>  
  
##### <a name="to-create-and-open-an-iinputchannel-to-receive-messages-for-inbound-operations"></a><span data-ttu-id="a8f06-131">建立與開啟 IInputChannel 來接收訊息的輸入作業</span><span class="sxs-lookup"><span data-stu-id="a8f06-131">To create and open an IInputChannel to receive messages for inbound operations</span></span>  
  
1.  <span data-ttu-id="a8f06-132">建立的執行個體**OracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="a8f06-132">Create an instance of **OracleEBSBinding**.</span></span>  
  
2.  <span data-ttu-id="a8f06-133">設定輸入作業所需的繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="a8f06-133">Set the binding properties required for the inbound operation.</span></span> <span data-ttu-id="a8f06-134">例如，輪詢作業中，至少您必須設定**InboundOperationType**， **PolledDataAvailableStatement**， **PollingAction**，和**PollingInput**繫結內容來設定[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]輪詢 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="a8f06-134">For example, for a polling operation, at a minimum you must set the **InboundOperationType**, **PolledDataAvailableStatement**, **PollingAction**, and the **PollingInput** binding properties to configure the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] to poll the Oracle database.</span></span>  
  
3.  <span data-ttu-id="a8f06-135">建立繫結參數集合使用**BindingParameterCollection**類別，並設定認證。</span><span class="sxs-lookup"><span data-stu-id="a8f06-135">Create a binding parameter collection using the **BindingParameterCollection** class and set the credentials.</span></span>  
  
4.  <span data-ttu-id="a8f06-136">叫用來建立通道接聽程式**BuildChannelListener\<IInputChannel\>** 方法**OracleEBSBinding**。</span><span class="sxs-lookup"><span data-stu-id="a8f06-136">Create a channel listener by invoking **BuildChannelListener\<IInputChannel\>** method on the **OracleEBSBinding**.</span></span> <span data-ttu-id="a8f06-137">您可以指定 Oracle 連線 URI 為其中一個參數，這個方法。</span><span class="sxs-lookup"><span data-stu-id="a8f06-137">You specify the Oracle connection URI as one of the parameters to this method.</span></span>  
  
5.  <span data-ttu-id="a8f06-138">開啟接聽程式。</span><span class="sxs-lookup"><span data-stu-id="a8f06-138">Open the listener.</span></span>  
  
6.  <span data-ttu-id="a8f06-139">取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法。</span><span class="sxs-lookup"><span data-stu-id="a8f06-139">Get an **IInputChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
7.  <span data-ttu-id="a8f06-140">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="a8f06-140">Open the channel.</span></span>  
  
 <span data-ttu-id="a8f06-141">下列程式碼示範如何建立通道接聽程式，並取得**IInputChannel**以接收來自配接器的輸入作業的訊息。</span><span class="sxs-lookup"><span data-stu-id="a8f06-141">The following code shows how to create a channel listener and get an **IInputChannel** to receive messages for inbound operations from the adapter.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a8f06-142">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]僅支援單向接收。</span><span class="sxs-lookup"><span data-stu-id="a8f06-142">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] only supports one-way receive.</span></span> <span data-ttu-id="a8f06-143">因此，您必須使用**IInputChannel**從 Oracle E-business Suite 接收輸入作業的訊息。</span><span class="sxs-lookup"><span data-stu-id="a8f06-143">So, you must use **IInputChannel** to receive messages for inbound operations from Oracle E-Business Suite.</span></span>  
  
```  
// Create a binding: specify the InboundOperationType, the PolledDataAvailableStatement, the PollingAction, and   
// the PollingInput binding properties.  
OracleEBSBinding binding = new OracleEBSBinding();  
binding.InboundOperationType = InboundOperation.Polling;  
binding.PolledDataAvailableStatement = "SELECT COUNT (*) FROM MS_SAMPLE_EMPLOYEE";  
binding.PollingAction = "InterfaceTables/Poll/FND/APPS/MS_SAMPLE_EMPLOYEE";  
binding.PollingInput = "SELECT * FROM MS_SAMPLE_EMPLOYEE FOR UPDATE";  
  
// Create a binding parameter collection and set the credentials  
ClientCredentials credentials = new ClientCredentials();  
credentials.UserName.UserName = "myuser";  
credentials.UserName.Password = "mypassword";  
  
BindingParameterCollection bindingParams = new BindingParameterCollection();  
bindingParams.Add(credentials);  
  
// Get a listener from the binding and open it.  
Uri connectionUri = new Uri("oracleebs://oracle_ebs_instance/");  
IChannelListener<IInputChannel> listener = binding.BuildChannelListener<IInputChannel>(connectionUri, bindingParams);  
listener.Open();  
  
// Get a channel from the listener and open it.  
IInputChannel channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8f06-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="a8f06-144">See Also</span></span>  
 [<span data-ttu-id="a8f06-145">開發 Oracle E-business Suite 應用程式使用 WCF 通道模型</span><span class="sxs-lookup"><span data-stu-id="a8f06-145">Develop Oracle E-Business Suite applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)