---
title: "建立使用 SQL 配接器的通道 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e86398f6-c835-46f8-814f-31e43b18970e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c31146310b8c8b559fcd93d19362679b060cb42
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="create-a-channel-using-the-sql-adapter"></a>建立使用 SQL 配接器的通道
在 WCF 通道模型中，叫用 SQL Server 資料庫上的作業，藉由交換的 SOAP 訊息接收結果[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]透過 WCF 通道。  
  
-   您藉由使用叫用傳出作業**IRequestChannel**或**IOutputChannel**將訊息傳送至配接器。  
  
-   您透過接收訊息來接收訊息的輸入操作**IInputChannel**如**輪詢**， **TypedPolling**，或**通知**作業。  
  
 本主題中的程序會提供有關如何建立及設定可用於輸入和輸出作業的通道形狀的資訊。  
  
## <a name="creating-outbound-client-channels"></a>建立輸出 （用戶端） 通道  
 您可以使用**IRequestChannel**或**IOutputChannel**叫用 SQL Server 資料庫上的作業。 在任一情況下，您先建立**System.ServiceModel.ChannelFactory**使用適當的介面。 然後，您會使用處理站建立通道。 在建立通道之後，您可以使用它來叫用的介面卡上的作業。  
  
#### <a name="to-create-and-open-an-outbound-channel"></a>若要建立並開啟傳出的通道  
  
1.  建立和初始化的執行個體**ChannelFactory**為使用端點與繫結所需的通道圖案。 端點指定的 SQL Server 連接 URI，而且繫結的執行個體**sqlBinding**。  
  
2.  使用通道處理站提供 SQL Server 認證**認證**屬性。  
  
3.  開啟通道處理站。  
  
4.  取得通道的執行個體叫用**CreateChannel**通道處理站上的方法。  
  
5.  開啟通道。  
  
 在您的程式碼或組態中，您可以指定的繫結與端點位址。  
  
### <a name="specifying-the-binding-and-endpoint-address-in-code"></a>在程式碼中指定的繫結和端點位址  
 下列程式碼範例示範如何建立**IRequestChannel**藉由在程式碼中指定的繫結與端點位址。 若要建立的程式碼**IOutputChannel**也相同，只不過您必須指定**IOutputChannel**介面**ChannelFactory**和通道類型。  
  
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
  
### <a name="specifying-the-binding-and-endpoint-address-in-configuration"></a>在組態中指定的繫結和端點位址  
 下列程式碼範例示範如何從組態中指定的用戶端端點建立通道處理站。  
  
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
  
#### <a name="the-configuration-settings"></a>組態設定  
 下列程式碼示範使用上述範例的組態設定。 用戶端端點的合約必須是"System.ServiceModel.Channels.IRequestChannel"或"System.ServiceModel.Channels.IOutputChannel 」，您想要建立的通道類型的類型而定。  
  
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
  
## <a name="creating-inbound-service-channels"></a>建立輸入 （服務） 通道  
 您設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢屬性來設定繫結的執行個體的 SQL Server 資料庫資料表和檢視表**sqlBinding**。 然後使用這個繫結來建置通道接聽程式，您可以從中取得**IInputChannel**通道以接收**輪詢**， **TypedPolling**，或**通知**從配接器的作業。  
  
#### <a name="to-create-and-open-an-iinputchannel-to-receive-inbound-operations"></a>建立與開啟 IInputChannel 接收輸入的作業  
  
1.  建立的執行個體**SQLBinding**。  
  
2.  設定輸入作業所需的繫結屬性。 例如，對於**輪詢**作業，您必須設定至少**InboundOperationType**， **PolledDataAvailableStatement**，和**PollingStatement**繫結內容來設定[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]輪詢 SQL Server 資料庫。  
  
3.  叫用來建立通道接聽程式**BuildChannelListener\<IInputChannel\>** 方法**SQLBinding**。 您可以指定 SQL Server 連接 URI 為其中一個參數，這個方法。  
  
4.  開啟接聽程式。  
  
5.  取得**IInputChannel**叫用的通道**AcceptChannel**接聽程式上的方法。  
  
6.  開啟通道。  
  
 下列程式碼示範如何建立通道接聽程式，並取得**IInputChannel**從配接器接收的資料變更的訊息。  
  
> [!IMPORTANT]
>  [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]僅支援單向接收。 因此，您必須使用**IInputChannel**以接收來自 SQL Server 的輸入作業的訊息。  
  
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
  
## <a name="see-also"></a>請參閱  
[使用 WCF 通道模型開發應用程式](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)