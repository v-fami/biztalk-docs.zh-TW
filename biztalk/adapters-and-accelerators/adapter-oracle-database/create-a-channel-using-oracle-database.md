---
title: "建立通道使用 Oracle 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating a channel
- WCF channel model, creating a channel
- how to, create a channel
- channel programming, creating a channel
ms.assetid: a30156a0-5a5a-4418-be17-2e23c3716fc1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 413f62a679c0510be34289900b92188554e622c8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-channel-using-oracle-database"></a>建立通道使用 Oracle 資料庫
在 WCF 通道模型中，叫用 Oracle 資料庫上的作業，接收交換的 SOAP 訊息來輪詢查詢的結果[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]透過 WCF 通道。  
  
-   您使用叫用作業 （輸出作業） **IRequestChannel**或**IOutputChannel**將訊息傳送至配接器。  
  
-   透過接收 POLLINGSTMT 訊息接收輪詢基礎資料變更的訊息**IInputChannel**。  
  
 本節中的主題提供有關如何建立及設定可用於輸入和輸出作業的通道形狀的資訊。  
  
## <a name="creating-outbound-client-channels"></a>建立輸出 （用戶端） 通道  
 您可以使用**IRequestChannel**或**IOutputChannel**叫用的 Oracle 資料庫上的作業。 在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。 然後，您會使用處理站建立通道。 在建立通道之後，您可以使用它來叫用的介面卡上的作業。  
  
#### <a name="to-create-and-open-an-outbound-channel"></a>若要建立並開啟傳出的通道  
  
1.  建立和初始化的執行個體**ChannelFactory**為使用端點與繫結所需的通道圖案。 端點指定的 Oracle 連接 URI，而且繫結的執行個體**OracleDBBinding**。  
  
2.  使用提供的通道處理站的 Oracle 認證**認證**屬性。  
  
3.  開啟通道處理站。  
  
4.  取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。  
  
5.  開啟通道。  
  
 在您的程式碼或組態中，您可以指定的繫結與端點位址。  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a>在程式碼中指定的繫結和端點位址  
 下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。 若要建立的程式碼**IOutputChannel**也相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。  
  
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
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a>在組態中指定的繫結和端點位址  
 下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。  
  
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
  
#### <a name="the-configuration-settings"></a>組態設定  
 下列程式碼示範使用上述範例的組態設定。 用戶端端點的合約必須是"System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IRequestChannel 」，您想要建立的通道類型的類型而定。  
  
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
  
### <a name="creating-inbound-service-channels"></a>建立輸入 （服務） 通道  
 您設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢的 Oracle 資料庫資料表和檢視所設定的執行個體上的繫結屬性**OracleDBBinding**。 然後使用這個繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收來自配接器的輸入作業的訊息。  
  
##### <a name="to-create-and-open-an-iinputchannel-to-receive-messages-for-inbound-operations"></a>建立與開啟 IInputChannel 來接收訊息的輸入作業  
  
1.  建立的執行個體**OracleDBBinding**。  
  
2.  設定輸入作業所需的繫結屬性。 例如，POLLINGSTMT 作業中，至少您必須設定**InboundOperationType**， **PollingStatement**，和**PollingInterval**繫結至屬性設定[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]輪詢 Oracle 資料庫。  
  
3.  建立繫結參數集合使用**BindingParameterCollection**類別，並設定認證。  
  
4.  叫用來建立通道接聽程式**BuildChannelListener\<IInputChannel\>** 方法**OracleDBBinding**。 您可以指定 Oracle 連線 URI 為其中一個參數，這個方法。 如需 Oracle 連線 URI 的詳細資訊，請參閱[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)。  
  
5.  開啟接聽程式。  
  
6.  取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法。  
  
7.  開啟通道。  
  
 下列程式碼示範如何建立通道接聽程式，並取得**IInputChannel**來輸入訊息從配接器使用 POLLINGSTMT 作業。  
  
> [!NOTE]
>  [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]僅支援單向接收。 因此，您必須使用 IInputChannel 從 Oracle 資料庫接收訊息的輸入操作。  
  
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
  
## <a name="see-also"></a>請參閱  
 [開發 Oracle 資料庫應用程式使用 WCF 通道模型](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)