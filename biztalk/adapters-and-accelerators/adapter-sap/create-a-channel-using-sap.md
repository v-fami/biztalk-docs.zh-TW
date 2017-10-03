---
title: "建立通道使用 SAP |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel programming, creating a channel
- how to, create a channel
- creating a channel
- WCF channel model, creating a channel
ms.assetid: 24af1465-bb60-41d7-98bd-e501a981f82a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f69fbeb86cf63485591f048ef75cdcfd3d5056d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-channel-using-sap"></a>建立使用 SAP 的通道
在 WCF 通道模型中，SAP 系統上叫用作業，或從 SAP 系統接收訊息，藉由交換的 SOAP 訊息[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]透過 WCF 通道。  
  
-   您使用叫用作業 （輸出作業） **IRequestChannel**或**IOutputChannel**將訊息傳送至配接器  
  
-   接收訊息 （觸發從 SAP 系統） 透過**IReplyChannel**。  
  
 本節中的主題提供有關如何建立及設定可用於輸入和輸出作業的通道形狀的資訊。  
  
## <a name="creating-outbound-client-channels"></a>建立輸出 （用戶端） 通道  
 您可以使用**IRequestChannel**或**IOutputChannel**叫用 SAP 系統上的作業。 在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。 然後，您會使用處理站建立通道。 在建立通道之後，您可以使用它來叫用的介面卡上的作業。  
  
#### <a name="to-create-and-open-an-outbound-channel"></a>若要建立並開啟傳出的通道  
  
1.  建立和初始化的執行個體**ChannelFactory**為使用端點與繫結所需的通道圖案。 端點指定 SAP 連線 URI，而且繫結的執行個體**SAPDBBinding**。 （設定之前開啟通道處理站所需的任何繫結屬性）。  
  
2.  使用提供的通道處理站的 SAP 認證**ClientCredentials**屬性。  
  
3.  開啟通道處理站。  
  
4.  取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。  
  
5.  開啟通道。  
  
 在您的程式碼或組態中，您可以指定的繫結與端點位址。  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a>在程式碼中指定的繫結和端點位址  
 下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。 若要建立的程式碼**IOutputChannel**也相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。  
  
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
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a>在組態中指定的繫結和端點位址  
 下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。  
  
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
  
#### <a name="the-configuration-settings"></a>組態設定  
 下列程式碼示範使用上述範例的組態設定。 用戶端端點的合約必須是"System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IRequestChannel 」，您想要建立的通道類型的類型而定。  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<configuration xmlns="http://schemas.microsoft.com/.NetConfiguration/v2.0">  
    \<system.serviceModel>  
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
    \</system.serviceModel>  
</configuration>  
```  
  
### <a name="creating-inbound-service-channels"></a>建立輸入 （服務） 通道  
 設定要從 SAP 系統接收內送的訊息，藉由設定繫結屬性的執行個體上的介面卡**SAPBinding**。 然後使用這個繫結來建置通道接聽程式，您可以從中取得**IReplyChannel**通道以接收來自配接器的作業。  
  
##### <a name="to-create-and-open-an-ireplychannel-to-receive-data-changed-notifications"></a>若要建立並開啟 IReplyChannel 接收的資料變更通知  
  
1.  建立的執行個體**SAPBinding**。  
  
2.  設定您想要接收的作業所需的任何繫結屬性。 請務必設定**AcceptCredentialsInUri**繫結屬性。  
  
3.  建立**BindingParameterCollection**並加入**InboundActionCollection** ，其中包含您想要接收的作業動作。 配接器會將例外狀況傳回至 SAP 系統的所有其他作業。 此步驟是選擇性的。 如需詳細資訊，請參閱[接收輸入作業使用的 WCF 通道模型的 SAP 系統從](../../adapters-and-accelerators/adapter-sap/receive-inbound-operations-from-the-sap-system-using-the-wcf-channel-model.md)。  
  
4.  叫用來建立通道接聽程式**BuildChannelListener\<IReplyChannel >**方法**SAPBinding**。 您可以指定 SAP 連線 URI 為其中一個參數，這個方法。 連線 URI 必須包含參數的 RFC 目的地 SAP 系統上。 如需有關 SAP 連線 URI 的詳細資訊，請參閱[建立 SAP 系統連接 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。 如果您建立**BindingParameterCollection**在步驟 3 中，您也指定這當建立通道接聽程式。  
  
5.  開啟接聽程式。  
  
6.  取得**IReplyChannel**叫用的通道**AcceptChannel**接聽程式上的方法。  
  
7.  開啟通道。  
  
 下列程式碼示範如何建立通道接聽程式，並取得**IReplyChannel**配接器從接收作業。  
  
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
  
## <a name="see-also"></a>另請參閱  
[開發應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)