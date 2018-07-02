---
title: 建立通道，使用 SAP |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- channel programming, creating a channel
- how to, create a channel
- creating a channel
- WCF channel model, creating a channel
ms.assetid: 24af1465-bb60-41d7-98bd-e501a981f82a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8f42d21fe70a3058a9d92384c6a2853b0e35c84
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981407"
---
# <a name="create-a-channel-using-sap"></a><span data-ttu-id="c544d-102">建立通道，使用 SAP</span><span class="sxs-lookup"><span data-stu-id="c544d-102">Create a channel using SAP</span></span>
<span data-ttu-id="c544d-103">在 WCF 通道模型中，SAP 系統上叫用作業，或從 SAP 系統接收訊息，藉由交換的 SOAP 訊息[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]透過 WCF 通道。</span><span class="sxs-lookup"><span data-stu-id="c544d-103">In the WCF channel model, you invoke operations on the SAP system or receive messages from the SAP system by exchanging SOAP messages with the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] over a WCF channel.</span></span>  
  
- <span data-ttu-id="c544d-104">您使用其中一種叫用 （輸出作業） 的作業**IRequestChannel**該**IOutputChannel**將訊息傳送至配接器</span><span class="sxs-lookup"><span data-stu-id="c544d-104">You invoke operations (outbound operations) by using either an **IRequestChannel** or an **IOutputChannel** to send messages to the adapter</span></span>  
  
- <span data-ttu-id="c544d-105">您會收到訊息 （觸發從 SAP 系統） 透過**IReplyChannel**。</span><span class="sxs-lookup"><span data-stu-id="c544d-105">You receive messages (triggered from the SAP system) over an **IReplyChannel**.</span></span>  
  
  <span data-ttu-id="c544d-106">在本節中的主題提供有關如何建立和設定用於輸入和輸出作業的通道形狀的資訊。</span><span class="sxs-lookup"><span data-stu-id="c544d-106">The topics in this section provide information about how to create and configure channel shapes that are used for inbound and outbound operations.</span></span>  
  
## <a name="creating-outbound-client-channels"></a><span data-ttu-id="c544d-107">建立輸出 （用戶端） 通道</span><span class="sxs-lookup"><span data-stu-id="c544d-107">Creating Outbound (Client) Channels</span></span>  
 <span data-ttu-id="c544d-108">您可以使用**IRequestChannel**該**IOutputChannel**叫用 SAP 系統上的作業。</span><span class="sxs-lookup"><span data-stu-id="c544d-108">You can use either an **IRequestChannel** or an **IOutputChannel** to invoke operations on the SAP system.</span></span> <span data-ttu-id="c544d-109">在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。</span><span class="sxs-lookup"><span data-stu-id="c544d-109">In either case, you first create a **System.ServiceModel.ChannelFactory** using the appropriate interface.</span></span> <span data-ttu-id="c544d-110">然後，您會使用 factory 來建立通道。</span><span class="sxs-lookup"><span data-stu-id="c544d-110">You then use the factory to create the channel.</span></span> <span data-ttu-id="c544d-111">您已建立通道之後，您可以使用它來叫用的介面卡上的作業。</span><span class="sxs-lookup"><span data-stu-id="c544d-111">After you have created the channel you can use it to invoke operations on the adapter.</span></span>  
  
#### <a name="to-create-and-open-an-outbound-channel"></a><span data-ttu-id="c544d-112">若要建立並開啟一個傳出通道</span><span class="sxs-lookup"><span data-stu-id="c544d-112">To create and open an outbound channel</span></span>  
  
1. <span data-ttu-id="c544d-113">建立和初始化的執行個體**ChannelFactory**端點和繫結所使用的所需的通道形狀。</span><span class="sxs-lookup"><span data-stu-id="c544d-113">Create and initialize an instance of **ChannelFactory** for the desired channel shape by using an endpoint and a binding.</span></span> <span data-ttu-id="c544d-114">端點指定 SAP 連線 URI，而且繫結的執行個體**SAPDBBinding**。</span><span class="sxs-lookup"><span data-stu-id="c544d-114">The endpoint specifies an SAP connection URI and the binding is an instance of **SAPDBBinding**.</span></span> <span data-ttu-id="c544d-115">（設定之前開啟通道處理站所需的任何繫結屬性）。</span><span class="sxs-lookup"><span data-stu-id="c544d-115">(Set any binding properties required before you open the channel factory.)</span></span>  
  
2. <span data-ttu-id="c544d-116">使用提供 SAP 認證之通道處理站**ClientCredentials**屬性。</span><span class="sxs-lookup"><span data-stu-id="c544d-116">Provide SAP credentials for the channel factory by using the **ClientCredentials** property.</span></span>  
  
3. <span data-ttu-id="c544d-117">開啟通道處理站。</span><span class="sxs-lookup"><span data-stu-id="c544d-117">Open the channel factory.</span></span>  
  
4. <span data-ttu-id="c544d-118">取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。</span><span class="sxs-lookup"><span data-stu-id="c544d-118">Get an instance of the channel by invoking the **CreateChannel** method on the channel factory.</span></span>  
  
5. <span data-ttu-id="c544d-119">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="c544d-119">Open the channel.</span></span>  
  
   <span data-ttu-id="c544d-120">在您的程式碼或組態，您可以指定繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="c544d-120">You can specify the binding and endpoint address in your code or from configuration.</span></span>  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a><span data-ttu-id="c544d-121">在程式碼中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="c544d-121">Specifying the Binding and Endpoint Address in Code</span></span>  
 <span data-ttu-id="c544d-122">下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。</span><span class="sxs-lookup"><span data-stu-id="c544d-122">The following code example shows how to create an **IRequestChannel** by specifying the binding and endpoint address in code.</span></span> <span data-ttu-id="c544d-123">若要建立的程式碼**IOutputChannel**與其相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。</span><span class="sxs-lookup"><span data-stu-id="c544d-123">The code to create an **IOutputChannel** is the same except that you must specify an **IOutputChannel** interface for the **ChannelFactory** and channel type.</span></span>  
  
```  
// Create binding -- set binding properties before you open the factory.  
SAPBinding sapBinding = new SAPBinding();  
  
// Create address.  
EndpointAddress sapAddress = new EndpointAddress("sap://Client=800;lang=EN@A/YourSAPHost/00");  
  
// Create channel factory from binding and address.  
ChannelFactory<IRequestChannel> factory =   
    new ChannelFactory<IRequestChannel>(sapBinding, sapAddress);  
  
// Specify credentials.   
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the factory  
factory.Open();  
  
// Get channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a><span data-ttu-id="c544d-124">在組態中指定的繫結和端點位址</span><span class="sxs-lookup"><span data-stu-id="c544d-124">Specifying the Binding and Endpoint Address in Configuration</span></span>  
 <span data-ttu-id="c544d-125">下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。</span><span class="sxs-lookup"><span data-stu-id="c544d-125">The following code example shows how to create a channel factory from a client endpoint specified in configuration.</span></span>  
  
```  
// Create channel factory from configuration.  
ChannelFactory<IRequestChannel> factory =  
new ChannelFactory<IRequestChannel>("MyRequestChannel");  
  
// Specify credentials.  
factory.Credentials.UserName.UserName = "YourUserName";  
factory.Credentials.UserName.Password = "YourPassword";  
  
// Open the factory.  
factory.Open();  
  
// Get a channel and open it.  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
```  
  
#### <a name="the-configuration-settings"></a><span data-ttu-id="c544d-126">組態設定</span><span class="sxs-lookup"><span data-stu-id="c544d-126">The Configuration Settings</span></span>  
 <span data-ttu-id="c544d-127">下列程式碼顯示上述範例中所使用的組態設定。</span><span class="sxs-lookup"><span data-stu-id="c544d-127">The following code shows the configuration settings used for the preceding example.</span></span> <span data-ttu-id="c544d-128">用戶端端點的合約必須是 「 System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IRequestChannel 」，根據您想要建立的通道類型的類型。</span><span class="sxs-lookup"><span data-stu-id="c544d-128">The contract for the client endpoint must be "System.ServiceModel.Channels.IRequestChannel" or "System.ServiceModel.Channels.IRequestChannel" depending on the kind of channel shape that you want to create.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    <system.serviceModel>  
        <bindings>  
            <sapBinding>  
                <binding name="SAPBinding" closeTimeout="00:01:00" openTimeout="00:01:00"  
                    receiveTimeout="00:10:00" sendTimeout="00:01:00" enableBizTalkCompatibilityMode="false"  
                    receiveIdocFormat="Typed" enableSafeTyping="false" generateFlatFileCompatibleIdocSchema="true"  
                    maxConnectionsPerSystem="50" enableConnectionPooling="true"  
                    idleConnectionTimeout="00:15:00" flatFileSegmentIndicator="SegmentDefinition"  
                    enablePerformanceCounters="false" autoConfirmSentIdocs="false"  
                    acceptCredentialsInUri="false"  
                    padReceivedIdocWithSpaces="false" sncLibrary="" sncPartnerName="" />  
            </sapBinding>  
        </bindings>  
        <client>  
            <endpoint address="sap://CLIENT=800;LANG=EN;@a/ADAPSAP47/00?RfcSdkTrace=False&AbapDebug=False"  
                binding="sapBinding" bindingConfiguration="SAPBinding" contract="System.ServiceModel.Channels.IRequestChannel"  
                name="MyRequestChannel" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a><span data-ttu-id="c544d-129">建立輸入 （服務） 通道</span><span class="sxs-lookup"><span data-stu-id="c544d-129">Creating Inbound (Service) Channels</span></span>  
 <span data-ttu-id="c544d-130">設定要從 SAP 系統接收輸入的訊息，方法是執行個體上設定繫結屬性的介面卡**SAPBinding**。</span><span class="sxs-lookup"><span data-stu-id="c544d-130">You configure the adapter to receive inbound messages from an SAP system by setting binding properties on an instance of **SAPBinding**.</span></span> <span data-ttu-id="c544d-131">您接著使用此繫結來建置通道接聽程式，您可以從中取得**IReplyChannel**通道以接收來自配接器的作業。</span><span class="sxs-lookup"><span data-stu-id="c544d-131">You then use this binding to build a channel listener from which you can get an **IReplyChannel** channel to receive operations from the adapter.</span></span>  
  
##### <a name="to-create-and-open-an-ireplychannel-to-receive-data-changed-notifications"></a><span data-ttu-id="c544d-132">建立及開啟 IReplyChannel 接收的資料變更的通知</span><span class="sxs-lookup"><span data-stu-id="c544d-132">To create and open an IReplyChannel to Receive Data-changed Notifications</span></span>  
  
1. <span data-ttu-id="c544d-133">建立的執行個體**SAPBinding**。</span><span class="sxs-lookup"><span data-stu-id="c544d-133">Create an instance of **SAPBinding**.</span></span>  
  
2. <span data-ttu-id="c544d-134">設定您想要接收的作業所需的任何繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="c544d-134">Set any binding properties required for the operations you want to receive.</span></span> <span data-ttu-id="c544d-135">請務必設定**AcceptCredentialsInUri**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="c544d-135">Be sure to set the **AcceptCredentialsInUri** binding property.</span></span>  
  
3. <span data-ttu-id="c544d-136">建立**BindingParameterCollection**並加入**InboundActionCollection** ，其中包含您想要接收作業的動作。</span><span class="sxs-lookup"><span data-stu-id="c544d-136">Create a **BindingParameterCollection** and add an **InboundActionCollection** that contains the actions of the operations that you want to receive.</span></span> <span data-ttu-id="c544d-137">配接器會傳回例外狀況至 SAP 系統的所有其他作業。</span><span class="sxs-lookup"><span data-stu-id="c544d-137">The adapter will return an exception to the SAP system for all other operations.</span></span> <span data-ttu-id="c544d-138">此步驟是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c544d-138">This step is optional.</span></span> <span data-ttu-id="c544d-139">如需詳細資訊，請參閱 <<c0> [ 接收輸入作業使用 WCF 通道模型的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。</span><span class="sxs-lookup"><span data-stu-id="c544d-139">For more information, see [Receiving Inbound Operations from the SAP System by Using the WCF Channel Model](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md).</span></span>  
  
4. <span data-ttu-id="c544d-140">建立通道接聽程式，藉由叫用**BuildChannelListener\<IReplyChannel\>** 方法**SAPBinding**。</span><span class="sxs-lookup"><span data-stu-id="c544d-140">Create a channel listener by invoking **BuildChannelListener\<IReplyChannel\>** method on the **SAPBinding**.</span></span> <span data-ttu-id="c544d-141">您可以指定 SAP 連線 URI 做為其中一個此方法的參數。</span><span class="sxs-lookup"><span data-stu-id="c544d-141">You specify the SAP connection URI as one of the parameters to this method.</span></span> <span data-ttu-id="c544d-142">連線 URI 必須包含在 SAP 系統的 RFC 目的地的參數。</span><span class="sxs-lookup"><span data-stu-id="c544d-142">The connection URI must contain parameters for an RFC Destination on the SAP system.</span></span> <span data-ttu-id="c544d-143">如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。</span><span class="sxs-lookup"><span data-stu-id="c544d-143">For more information about the SAP connection URI, see The [Create the SAP System Connection URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md).</span></span> <span data-ttu-id="c544d-144">如果您建立**BindingParameterCollection**在步驟 3 中，您也指定這當您建立通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c544d-144">If you created a **BindingParameterCollection** in step 3, you also specify this when you create the channel listener.</span></span>  
  
5. <span data-ttu-id="c544d-145">開啟接聽程式。</span><span class="sxs-lookup"><span data-stu-id="c544d-145">Open the listener.</span></span>  
  
6. <span data-ttu-id="c544d-146">取得**IReplyChannel**藉由叫用的通道**AcceptChannel**接聽程式上的方法。</span><span class="sxs-lookup"><span data-stu-id="c544d-146">Get an **IReplyChannel** channel by invoking the **AcceptChannel** method on listener.</span></span>  
  
7. <span data-ttu-id="c544d-147">開啟通道。</span><span class="sxs-lookup"><span data-stu-id="c544d-147">Open the channel.</span></span>  
  
   <span data-ttu-id="c544d-148">下列程式碼示範如何建立通道接聽程式，並取得**IReplyChannel**從配接器接收作業。</span><span class="sxs-lookup"><span data-stu-id="c544d-148">The following code shows how to create a channel listener and get an **IReplyChannel** to receive operations from the adapter.</span></span>  
  
```  
// Create a binding and specify any binding properties required  
// for the opreations you want to receive  
SAPBinding binding = new SAPBinding();  
  
// Set AcceptCredentialsInUri because the URI must contain credentials.  
binding.AcceptCredentialsInUri = true;  
  
// Create an InboundActionCollection and add the message actions to listen for,  
// only the actions added to the InboundActionCollection are received on the channel.  
// In this case a single action is specified: http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD  
InboundActionCollection actions = new InboundActionCollection(listeneraddress);  
actions.Add("http://Microsoft.LobServices.Sap/2007/03/Rfc/Z_RFC_MKD_ADD");  
  
// Create a BindingParameterCollection and add the InboundActionCollection  
BindingParameterCollection bpcol = new BindingParameterCollection();  
bpcol.Add(actions);  
  
// Create the channel listener by specifying  
// the binding parameter collection (to filter for the Z_RFC_MKD_ADD action) and   
// a connection URI that contains listener parameters.  
Uri listeneraddress =  
new Uri("sap://User=YourUserName;Passwd=YourPassword;Client=800;Lang=EN;@a/YourSAPHost/00?ListenerGwServ=SAPGATEWAY&ListenerGwHost=YourSAPHost&ListenerProgramId=SAPAdapter");  
listener = binding.BuildChannelListener<IReplyChannel>(connectionUri, new BindingParameterCollection());  
listener.Open();  
  
// Get a channel from the listener and open it.  
channel = listener.AcceptChannel();  
channel.Open();  
```  
  
## <a name="see-also"></a><span data-ttu-id="c544d-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c544d-149">See Also</span></span>  
[<span data-ttu-id="c544d-150">使用 WCF 通道模型開發應用程式</span><span class="sxs-lookup"><span data-stu-id="c544d-150">Develop applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)