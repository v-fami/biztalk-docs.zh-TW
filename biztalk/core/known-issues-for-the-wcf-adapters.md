---
title: "WCF 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 423c6021-5fb7-48c9-9319-11e7a18c775c
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ccdc0c0f36f2dca474b962d3f108e4f287e378f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-for-the-wcf-adapters"></a>WCF 配接器的已知問題
本主題描述 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 所附 WCF 配接器的已知問題。  
  
## <a name="a-message-that-fails-in-the-inbound-soap-marshaling-processing-is-not-suspended-in-wcf-receive-adapters"></a>在輸入 SOAP 封送處理中失敗的訊息未在 WCF 接收配接器中遭擱置  
 當訊息抵達 WCF 接收配接器時，WCF 配接器會從內送 SOAP 訊息建立 BizTalk 訊息，然後將 BizTalk 訊息傳遞給結束點管理員管理的傳輸 Proxy。 如果配接器在建立 BizTalk 訊息時無法讀取 SOAP 信封和內文，訊息不會遭擱置，因為配接器使用快速、非快取的順向讀取器來存取 SOAP 訊息。  
  
 請查看事件日誌中的失敗訊息。 例如，您可以使用內文路徑運算式上**訊息**WCF 配接器傳輸屬性對話方塊來指定如何從 SOAP 訊息內送 WCF 配接器透過建立輸入的 BizTalk 訊息內文中的索引標籤。 當內送 SOAP 訊息無效的內文路徑運算式所提供的**訊息**索引標籤上，配接器就無法建立 BizTalk 訊息的工作，也無法擱置內送訊息。 如需有關如何使用內文路徑運算式上**訊息**索引標籤上，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。  
  
 下圖顯示**訊息** 索引標籤，您可以指定如何從內送 SOAP 訊息建立輸入的 BizTalk 訊息。  
  
## <a name="a-message-that-fails-in-the-inbound-soap-marshaling-processing-is-not-suspended-in-wcf-send-adapters"></a>在輸入 SOAP 封送處理中失敗的訊息未在 WCF 傳送配接器中遭擱置  
 請求-回應 WCF 傳送埠可接收 WCF 訊息做為回應訊息。 當訊息抵達 WCF 傳送配接器時，WCF 配接器會從內送 SOAP 訊息建立 BizTalk 訊息，然後將 BizTalk 訊息傳遞給結束點管理員管理的傳輸 Proxy。 如果配接器在建立 BizTalk 訊息時無法讀取 SOAP 信封和內文，訊息不會遭擱置，因為配接器使用快速、非快取的順向讀取器來存取 SOAP 訊息。  
  
 請查看事件日誌中的失敗訊息。 例如，您可以使用 XPath 運算式上**訊息**WCF 配接器傳輸屬性對話方塊來指定如何從 SOAP 訊息內送 WCF 配接器透過建立輸入的 BizTalk 訊息內文中的索引標籤。 當無效的 XPath 運算式內送 SOAP 訊息所提供的**訊息**索引標籤上，配接器就無法建立 BizTalk 訊息的工作，也無法擱置內送訊息。 如需有關如何使用 XPath 運算式，在**訊息**索引標籤上，請參閱[指定 WCF 配接器的訊息本文](../core/specifying-the-message-body-for-the-wcf-adapters.md)。  
  
 下圖顯示**訊息**Wcf-netnamedpipe 傳送配接器做為範例 索引標籤。  
  
 ![[訊息] 索引標籤，在 WCF 傳送配接器](../core/media/54623ccf-49a9-4b6a-9487-da0d94bab64d.gif "54623ccf-49a9-4b6a-9487-da0d94bab64d")  
  
## <a name="messages-can-be-lost-when-using-onewaybindingelement-in-a-two-way-transport-with-custom-binding-in-non-transactional-wcf-receive-locations"></a>在非交易式 WCF 接受位置使用自訂繫結的雙向傳輸中若使用 OneWayBindingElement 時，訊息可能會遺失  
 在雙向通訊中，WCF 配接器會傳回回應，直到訊息保存在 MessageBox 資料庫中。 不過，使用**OneWayBindingElement**分派到 WCF 配接器接收的訊息之前，立即產生虛擬回應。 因此，如果您設定的自訂繫結**OneWayBindingElement**通道堆疊中針對雙向傳輸中非交易式接收位置，因為 WCF 配接器處理接收的訊息可能會遺失以單向方式訊息。  
  
## <a name="default-values-of-the-readerquotas-attributes-in-the-wcf-custom-and-wcf-customisolated-transport-properties-dialog-boxes-are-used-when-constructing-the-bindings"></a>建構繫結時，會使用 WCF-Custom 和 WCF-CustomIsolated 傳輸屬性對話方塊中的 ReaderQuotas 屬性預設值  
 在 Wcf-custom 和 Wcf-customisolated 傳輸屬性 對話方塊中， **ReaderQuotas**屬性值會顯示為零。 不過，當建構繫結時，會使用下列值：  
  
|Attribute|Description|值|  
|---------------|-----------------|-----------|  
|maxArrayLength|指定陣列長度上限的正整數。|16384|  
|maxBytesPerRead|指定每次讀取作業傳回的位元組上限的正整數。|4096|  
|maxDepth|指定每次讀取的巢狀節點深度上限的正整數。|32|  
|maxNameTableCharCount|指定資料表名稱的字元數上限的正整數。|16384|  
|maxStringContentLength|指定 XML 項目內容的字元數上限的正整數。|8192|  
  
## <a name="the-wcf-receive-locations-may-be-disabled-if-you-change-the-wcf-adapter-type-and-keep-the-same-address"></a>如果變更 WCF 配接器類型但位址保持不變，則 WCF 接收位置可能會停用  
 如果您變更配接器類型，例如，將 WCF 配接器類型從 WCF-NetTcp 變更為包含 NetTcp 繫結的 WCF-Custom，而位址保持不變，則接收位置可能會停用，因為結束點管理員會發生快取問題。 若要解決這個問題，您可以執行下列任一種方法：  
  
-   重新啟動 BTSNTSvc 服務。  
  
-   將 URI 變更為不同的位址並儲存，然後將 URI 變更回原來的位址，再儲存一次。  
  
## <a name="the-wcf-action-set-in-the-orchestration-does-not-override-the-action-setting-in-the-static-send-port"></a>協調流程中設定的 WCF 動作不會覆寫靜態傳送埠中的動作設定  
 如果您設定**WCF。動作**協調流程中的內容屬性，您需要讓**動作**WCF 配接器傳輸屬性對話方塊中的空白欄位。 如果您也在靜態傳送埠中，指定動作**WCF。動作**您設定靜態傳送埠中的值將會覆寫您在協調流程中設定的內容屬性。  
  
## <a name="propagating-a-fault-message-is-not-supported-in-the-transactional-send"></a>交易式傳送中不支援傳播錯誤訊息  
 **傳播錯誤訊息**請求-回應傳送埠中的選項可讓您將路由至訂閱應用程式的輸出處理失敗的訊息。 不過，如果**啟用交易**傳輸屬性對話方塊中也會選取核取方塊，交易已中止或錯誤回應抵達配接器時，則無法使用，您將無法傳播訂閱的任何應用程式的錯誤訊息  
  
## <a name="the-msmq-cluster-resource-group-needs-to-be-restarted-before-restarting-the-biztalk-host-cluster-resource-group-during-the-cluster-failover"></a>叢集容錯移轉期間，需要先重新啟動 MSMQ 叢集資源群組，才能重新啟動 BizTalk 主控件叢集資源群組  
 在容錯移轉叢集的情況中，如果發生容錯移轉，需要先重新啟動 MSMQ 叢集資源群組，才能重新啟動 BizTalk 主控件叢集資源群組。 如果未能這麼做，MSMQ 接收位置可能會停用。 若要解決這個問題，您可以設定 BizTalk 主控件叢集資源群組相依於 MSMQ 叢集資源群組，以確保 MSMQ 叢集資源群組會在 BizTalk 主控件叢集資源群組之前先行啟動。 或者，您也可以重新啟動 BizTalk 主控件叢集資源群組來解決這個問題。  
  
## <a name="you-receive-an-error-when-sending-messages-to-a-wcf-service-that-uses-wsfederationhttpbinding-in-the-endpoint"></a>將訊息傳送到在結束點中使用 wsFederationHttpBinding 的 WCF 服務時，收到錯誤  
 您收到類似下面的錯誤：  
  
```  
The adapter failed to transmit message going to send port "MySendPort" with URL "http://localohost/MywsFedHttp". It will be retransmitted after the retry interval specified for this Send Port. Details:"The channel is configured to use interactive initializer 'System.ServiceModel.Security.InfocardInteractiveChannelInitializer', but the channel was Opened without calling DisplayInitializationUI.  Call DisplayInitializationUI before calling Open or other methods on this channel.".  
```  
  
 這是依據設計的行為。 WCF 配接器無法傳送訊息至 WCF 服務使用**wsFederationHttpBinding**在其端點。  
  
## <a name="the-biztalk-wcf-service-consuming-wizard-does-not-enable-you-to-select-message-types-or-port-types-from-the-wsdl"></a>BizTalk WCF 服務使用精靈無法讓您從 WSDL 選取訊息類型或連接埠類型  
 匯入 WCF 服務時，BizTalk WCF 服務使用精靈無法讓您從 WSDL 選取訊息類型或連接埠類型。 若要解除此限制，您可以使用下列程式碼取得結構描述，然後將所需的結構描述加入到您的 BizTalk 專案：  
  
```  
svcutil.exe /t:metadata http://service/metadataendpoint  
```  
  
## <a name="the-biztalk-wcf-service-consuming-wizard-does-not-allow-the-combination-of-one-way-and-request-response-operations"></a>BizTalk WCF 服務使用精靈不允許單向與要求-回應的組合作業  
 BizTalk WCF 服務使用精靈不允許您匯入有單向與要求-回應組合作業的連接埠類型。 若要解決這個問題，您可以使用 ServiceModel 中繼資料公用程式工具來產生連接埠類型。  
  
## <a name="the-biztalk-wcf-service-consuming-wizard-does-not-allow-you-to-set-certificate-credentials-when-retrieving-the-wsdl"></a>擷取 WSDL 時，BizTalk WCF 服務使用精靈不允許您設定憑證認證  
 擷取 WSDL 時，BizTalk WCF 服務使用精靈不允許您設定憑證認證。 若要解決這個問題，您可以使用 ServiceModel 中繼資料公用程式工具產生的 WSDL 與 XSD 檔案，您想要使用的憑證認證的 WCF 服務集合中的其他 svcutil.exe.config 檔，然後再匯入 BizTalk WCF 服務使用精靈選擇**中繼資料檔案 （WSDL 和 XSD）**選項**中繼資料來源**頁面。  
  
## <a name="wcf-adapters-do-not-support-one-way-operations"></a>WCF 配接器不支援單向作業  
 您會收到類似下面的錯誤訊息使用 WCF 服務發佈 WCF 配接器 （除了 Wcf-netmsmq 接收配接器） 時如果**IsOneWay**屬性設定為**true**在用戶端。 這是因為**System.ServiceModel.OperationContractAttribute.IsOneWay** （除非服務發行使用 Wcf-netmsmq 接收配接器） 的 WCF 配接器發佈之 WCF 服務的屬性設定為**false**即使是單向接收位置。  
  
```  
The channel received an unexpected input message while closing. Your Channel.Close() calls are not synchronized.  
```  
  
 使用指定的 WCF 服務時，您會收到類似下面的錯誤訊息**IsOneWay**屬性設定為**true**。 您從 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送的訊息將會擱置但可繼續。  
  
```  
The request operation at net.tcp://localhost:8088/MyService/tcp did not receive a reply within timeout 00:01:00.  
```  
  
## <a name="a-memory-leak-may-occur-when-sending-messages-to-non-transactional-msmq-queues-using-wcf-netmsmq-binding"></a>使用 WCF-NetMsmq 繫結傳送訊息到非交易式 MSMQ 佇列時，可能會發生記憶體遺漏  
 使用 WCF-NetMsmq 繫結傳送訊息到非交易式 MSMQ 佇列時，BizTalk NT 服務可能會發生記憶體遺漏。 當您使用 WCF-NetMsmq 傳輸傳送訊息到非交易式 MSMQ 佇列，或使用包含 WCF-Custom 傳輸的 netMsmqBinding 傳送訊息到非交易式 MSMQ 佇列時，就可能會發生這種情況。  
  
 若要解決此問題，您必須安裝在知識庫文章 936512 所述的.NET Framework 3.0 hotfix [http://go.microsoft.com/fwlink/?LinkId=92962](http://go.microsoft.com/fwlink/?LinkId=92962)。 Hotfix 不需要系統重新開機，但需要重新啟動裝載使用 WCF-NetMsmq 繫結之傳送埠的 BizTalk NT 服務。  
  
## <a name="you-may-receive-exception-when-communicating-with-apache-web-servers-using-wcf-basichttp-adapter"></a>使用 WCF-BasicHttp 配接器與 Apache Web 伺服器通訊時，可能會收到例外狀況  
 當您使用包含傳輸安全性的 WCF-BasicHttp 配接器與 Apache Web 伺服器通訊時，可能會收到類似下面的例外狀況：  
  
```  
System.Net.WebException: The underlying connection was closed: An unexpected error occurred on a send.  
System.IO.IOException: Unable to write data to the transport connection: An established connection was aborted by the software in your host machine. System.Net.Sockets.SocketException: An established connection was aborted by the software in your host machine  
```  
  
 若要解決這個問題，您需要使用 WCF-Custom 配接器 (而非 WCF-BasicHttp 配接器) 來與 Apache Web 伺服器通訊，如下所示：  
  
1.  建立傳送埠和傳輸類型設定為**Wcf-custom**。  
  
2.  在**Wcf-custom 傳輸屬性**對話方塊**繫結**索引標籤上，選取**customBinding**從**繫結的型別**下拉式清單。  
  
3.  在下**customebindingelement**，以滑鼠右鍵按一下**httpTransport**，然後按一下 **移除延伸模組**。  
  
4.  以滑鼠右鍵按一下**customebindingelement**，然後按一下 **將延伸加入**。  
  
5.  在**選取繫結元素延伸模組**對話方塊中，選取**httpTransport** ，然後按一下 **確定**。  
  
6.  按一下**httpTransport**，然後在**組態** 窗格中，設定的值**keepaliveenabled**至**False**。  
  
7.  按一下**textMessageEncoding**，然後在**組態** 窗格中，設定的值**messageVersion**至`Soap11WSAddressing10`。  
  
8.  您可能需要視情況設定其他屬性。  
  
## <a name="biztalk-server-does-not-work-with-wcf-clients-that-using-clientviabehavior-for-multiple-hop-conversations"></a>BizTalk Server 無法與使用 ClientViaBehavior 進行多躍點交談的 WCF 用戶端搭配運作  
 當直接網路目的地不是訊息的預定處理器，WCF 用戶端會使用 ClientViaBehavior 來啟用多躍點交談，在這種情況下，呼叫應用程式不一定知道最終的目的地為何。 如果您指定 ClientViaBehavior 並將「收件人位址」設定為遠端服務，其中 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 將做為中介者，那麼就會收到如下錯誤訊息：  
  
```  
The message with To 'net.tcp://localhost:5555/test.svc' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher. Check that the sender and receiver's EndpointAddresses agree  
```