---
title: "向外擴充接收主控件 |Microsoft 文件"
ms.custom: 
ms.date: 2016-03-17
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, receive adapters
- high availability
- HTTP adapters, scaling
- receive adapters, scaling
- POP3 adapters, scaling
- MSMQ adapters, scaling
- EDI adapters, scaling
- Web services, scaling
- hosts, multiple
- MQSeries adapters, scaling
- adapters, Windows SharePoint Services
- scaling, hosts
- scaling, adapters
- SAP adapters
- FTP adapters
- scaling, receive adapters
- hosts, receiving
- adapters, Web services
- hosts, scaling
- SOAP adapters, scaling
- adapters, scaling
- SQL adapters, scaling
- Web services, adapters
- File adapters, scaling
- clustering
ms.assetid: 94f35426-37fa-4ad2-8e35-d82fdca02262
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9bc048de978a6dfd7c28505c54cdaaaef64064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-receiving-hosts"></a>向外擴充的接收主控件
當主控件包含接收項目時 (例如接收位置或管線)，它將做為安全範圍，而訊息解碼和解密都發生在主控件的管線中。 若要讓接收主控件變成高度可用，您必須有兩部或以上的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦執行每個接收主控件的執行個體。 透過向外擴充接收主控件，您可以確保需要大量傳訊的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署的可用性。 雖然這些部署有可能執行最少的協調流程處理，不過它們仍可以最快的速度並提供最大的可靠性來路由許多不同類型的訊息。  
  
 您可以將接收主控件與處理協調流程和傳送訊息的主控件分開，藉此個別保護和擴充其他主控件的每個主控件，提升環境的安全性與擴充性。 例如，您可以將兩部電腦 (主控件執行個體) 新增至接收主控件，而不需將任何電腦新增至處理或傳送主控件。  
  
## <a name="multiple-hosts-for-receiving-messages"></a>接收訊息的多個主控件  
 下圖顯示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 部署，此部署具有兩台執行接收主控件執行個體的電腦，可為接收主控件提供高可用性。 請注意，在此圖中處理和傳送主控件不是高度可用。  
  
 ![多個主控件接收訊息](../core/media/tdi-ha-scalereceive.gif "TDI_HA_ScaleReceive")  
  
 在大型部署、處理多個交易夥伴的實例，以及使用不同通訊協定的實例方面，您可以在多個接收主控件之間分佈接收功能。 例如，您可以為每個配接器建立接收訊息的主控件，或是建立不同的主控件以接收不同夥伴的訊息。 當您建立多個接收主控件時，您可以建立安全範圍並讓環境更容易管理和擴充，不過，它並不會使環境變得高度可用。  
  
 為了使環境變得高度可用，您必須為每個建立的接收主控件建立兩個或以上的主控件執行個體。 例如，您可以建立三個不同的接收主控件 (A、B 和 C) 以接收三個不同公司的訊息。 若要讓每個主控件高度可用，您需要在兩部或以上的電腦中為每個主控件建立主控件執行個體。 請注意，您可以在一部電腦上擁有每個主控件的執行個體，而不會損失安全範圍、管理性或擴充性。  
  
 下圖顯示高度可用的三部電腦之 BizTalk Server 環境，包含專用以接受不同公司訊息的主控件。  
  
 ![接收執行個體](../core/media/tdi-ha-receiveinstances2.gif "TDI_HA_ReceiveInstances2")  
  
 若要以此組態提供高可用性，每部電腦都需執行三個主控件執行個體：三家公司的每一家各有一個執行個體。 每家公司的主控件執行個體都包含接收位置和管線以便和該公司通訊。 在一般作業期間，只要您在接收配接器前為向外擴充做了必要工作 (例如，若您設定 HTTP 的網路負載平衡)，傳訊負載將分散於每個主控件的三個主控件執行個體之間。 若一部電腦上的主控件執行個體失敗，在另外兩部電腦上執行的主控件執行個體會提供備援並維護服務的可用性。  
  
## <a name="scaling-the-biztalk-server-receive-adapters"></a>擴充 BizTalk Server 接收配接器  
 除了主控件執行個體之外，為接收主控件擴充和提供高可用性的程序也取決於您在部署中實作的特定配接器而定。 每個配接器都有通訊協定特有的特性，使得每個案例中的規劃和部署均不同。 不過，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 讓您可為所有配接器套用相同的高可用性方案，主要是透過其他電腦和主控件執行個體。  
  
 視要使用的特定通訊協定之不同，某些接收配接器需要其他機制，以便在多個主機電腦之間分散內送訊息以提供高可用性。 例如，使用 HTTP 或 SOAP 配接器 (又稱為 Web 服務配接器) 的 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 解決方案，需要像「網路負載平衡」(NLB) 等負載平衡器來分散接收工作負載。 下表摘要了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中最常用之配接器的高可用性指導方針。  
  
|**配接器**|**高可用性指導方針**|  
|-----------------|---------------------------------------|  
|HTTP|將多部電腦新增至接收主控件並將 NLB 設定為在多部主機電腦之間分散內送訊息。|  
|SOAP|將多部電腦新增至接收主控件並將 NLB 設定為在多部主機電腦之間分散內送訊息。|  
|檔案|將多部電腦新增至在每部主機電腦上含有接收位置的接收主控件，這些電腦參考相同的檔案資料夾或是「通用命名慣例」(UNC) 路徑。 在完整高度可用的方案方面，您必須確定 UNC 路徑所指向的檔案位置是高度可用的 (或至少是可靠的)。|  
|FTP|設定 FTP 接收配接器以便在叢集 BizTalk 主控件中執行。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。|  
|POP3|設定 POP3 接收配接器以便在叢集 BizTalk 主控件中執行。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。|  
|MSMQ|設定 MSMQ 接收配接器，Windows 叢集 BizTalk 主控件中執行。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。 如果 MSMQ 接收位置會使用遠端 MSMQ 伺服器上的佇列，您不需要在叢集 BizTalk 主控件。  在此案例中，執行 MSMQ 接收多個 BizTalk 群組中的電腦上的主機。|  
|MQSeries|將多部電腦新增至此配接器的接收主控件、使用 MQSeries for Windows 中的叢集佇列管理員，並叢集 MQSeries Server for Windows。|  
|Windows SharePoint Services|將多部電腦新增至接收主控件並將 NLB 設定為在多部主機電腦之間分散內送訊息。|  
|WCF-NetTcp<br />-WCF 自訂|將多部電腦新增至接收主控件並將 NLB 設定為在這些主機電腦之間分散內送訊息。<br /><br /> -或者-<br /><br /> 將配接器接收處理常式所使用的主控件進行叢集處理。|  
|-Wcf-netnamedpipe<br />-Wcf-basichttp<br />-Wcf-wshttp<br />-Wcf-customisolated|將多部電腦新增至接收主控件並將 NLB 設定為在這些主機電腦之間分散內送訊息。|  
|WCF-NetMsmq|將配接器接收處理常式所使用的主控件進行叢集處理。|  
  
### <a name="http-adapter"></a>HTTP 配接器  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中的 HTTP 接收配接器是網際網路伺服器 API (ISAPI) 延伸模組 (BTSHTTPReceive.dll)，此延伸模組以主控件執行個體的方式在每部接收主機電腦上執行。 當夥伴透過 HTTP 通訊協定傳送訊息至 BizTalk Server 時，此訊息通常會到達安裝 Internet Information Services (IIS) 的 BizTalk Server 電腦上的特定 URL。 您可以在 BizTalk Server 中建立主控件執行個體，並包含訂閱此 URL 的接收位置。 當訊息到達 URL 時，BizTalk Server 會擷取它們並將它們保存在 MessageBox 資料庫中。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您建立相同接收主控件的多個主控件執行個體，為 HTTP 接收配接器提供高可用性。 若您使用 NLB 在多個接收主控件之間分散內送訊息，這些主控件執行個體就會訂閱可能是共用或叢集 IP 位址的特定 URL。 這些主控件全部都可以做為叢集的虛擬 IP 位址，因此，若一個叢集成員失敗，其他成員仍然可以服務此 IP 位址。  
  
### <a name="soap-adapter-web-services-adapter"></a>SOAP 配接器 (Web 服務配接器)  
 不像 HTTP 接收配接器，Web 服務的接收配接器並不包含 ISAPI 延伸模組。 它會經由您利用「BizTalk Web 服務發佈精靈」所指定的 URL 來接收內送訊息。 此精靈會匯出 Web 服務並建立可做為接收位置的虛擬目錄。  
  
 若要為 Web 服務配接器提供高可用性，請將多部電腦新增至接收主控件並使用 NLB 來分散內送訊息。 當用戶端透過 Web 服務配接器傳送訊息至 BizTalk Server 時，NLB 負載會將訊息平衡至其中一個接收主控件，而在主控件上執行的適當主控件執行個體會保存訊息在 MessageBox 資料庫中。  
  
### <a name="file-adapter"></a>FILE 配接器  
 FILE 接收配接器會擷取檔案資料夾或 UNC 路徑的訊息。 因為雙方都需要路徑的權限，而不同的公司通常不會共用檔案系統，所以此配接器通常是用在公司內，而不是 B2B 的實例。 您可以設定檔案接收處理常式來訂閱路徑，這樣 BizTalk Server 就會在訊息到達接收位置時擷取它。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您在訂閱相同 UNC 路徑的多個主機電腦上建立主控件執行個體，為 FILE 接收配接器提供高可用性。 若在一部主機電腦上執行的主控件執行個體發生錯誤或失敗，在另一部主機電腦上執行的相同主控件執行個體就會擷取訊息，並將它保存在 MessageBox 資料庫中。  
  
### <a name="ftp-adapter"></a>FTP 配接器  
 FTP 接收配接器不應設定為在多個主控件中執行，因為 FTP 接收配接器使用 FTP 通訊協定擷取目標系統的檔案，而 FTP 通訊協定並沒有任何檔案鎖定的概念可確保執行 FTP 接收配接器的多個執行個體時不能同時擷取相同檔案的多個複本。 FTP 接收配接器應設定為在叢集 BizTalk 主控件中執行。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
### <a name="pop3-adapter"></a>POP3 配接器  
 POP3 接收配接器可以設定為在多個主控件中執行，除非配接器正在讀取的 POP3 伺服器允許多個並行連線同時連接到相同信箱。 若 POP3 配接器所連接的 POP3 伺服器允許多個連接至其信箱的並行連線，則必須透過設定 POP3 配接器接收處理常式在已叢集的 BizTalk 主控件執行個體中執行，以達成 POP3 配接器的高可用性。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
### <a name="msmq-adapter"></a>MSMQ 配接器  
 若要達到高可用性，執行 MSMQ 接收配接器，在 Windows 叢集 BizTalk 主控件叢集 MSMQ 資源相同叢集群組中。 如需詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)。  
  
 如果 MSMQ 接收位置是**只**接收來自遠端 MSMQ 伺服器上的 MSMQ 佇列，則可以透過執行 MSMQ 達成高可用性 BizTalk 群組中接收多個 BizTalk 電腦上的主機。  若要 MSMQ 提供高可用性，您必須確定遠端 MSMQ 伺服器正在使用容錯移轉叢集的 Windows。  遠端 MSMQ 伺服器使用交易式佇列，如果必須執行 MSMQ 4.0 (Windows Server 2008) 或更新版本。  
  
### <a name="mqseries-adapter"></a>MQSeries 配接器  
 Microsoft BizTalk Adapter for MQSeries 可做為 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 IBM MQSeries 伺服器之間的橋樑。 若要在使用此配接器時提供高度可用的方案，您必須有多個執行 MQSeries 配接器的主控件執行個體，且使用 MQSeries for Windows 中的叢集佇列管理員，並叢集 MQSeries Server for Windows。 如需叢集佇列管理員及叢集 MQSeries Server 的詳細資訊，請參閱 IBM WebSphere MQ 文件。 如需讓 MQSeries 配接器高度可用的詳細資訊，請參閱 Microsoft BizTalk Adapter for MQSeries 說明中的＜高可用性＞。  
  
### <a name="windows-sharepoint-services-adapter"></a>Windows SharePoint Services 配接器  
 Windows SharePoint Services 配接器透過呼叫由 SharePoint 電腦上的 BizTalk 所安裝的 Windows SharePoint Services Web 服務來擷取 SharePoint 的訊息。 配接器使用簽出機制，以確保不同的主控件執行個體將不會處理相同訊息。 這可讓接收配接器向外延展，藉由新增更多的主控件執行個體。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]提供高可用性 SharePoint 接收配接器，可讓您執行相同的接收訂閱指向 SharePoint NLB 安裝之相同 HTTP URL 的多個主控件執行個體上的位置。  
  
### <a name="wcf-nettcp-adapter"></a>WCF-NetTcp 配接器  
 NetTcpBinding 可以使用 IP 層負載平衡技術來進行負載平衡。 不過，NetTcpBinding 預設會使用 TCP 連線集區以減少連線延遲時間。 這是最佳化處理，但會干擾負載平衡的基本機制。 主要用於最佳化 NetTcpBinding 的組態值是租用逾時，此值屬於 [連線集區設定] 的一部分。 使用 連線集區會導致用戶端連線只會連到與伺服器陣列中的特定伺服器 。 如果這些連線的存留期增加 (由租用逾時設定控制的因素)，伺服器陣列中各伺服器之間的負載分配就會變得不均衡。 這樣平均呼叫時間就會增加。 因此，在負載平衡的實例中使用 NetTcpBinding 時，請考慮減少繫節所使用的預設租用逾時。 對於負載平衡實例，先使用 30 秒的租用逾時值還算適當，但最佳值仍應視應用程式而定。 如需 通道租用逾時和其他傳輸配額的詳細資訊，請參閱 「 傳輸配額 」。  
  
## <a name="see-also"></a>另請參閱  
 [為 BizTalk 主控件提供高可用性](../core/providing-high-availability-for-biztalk-hosts.md)