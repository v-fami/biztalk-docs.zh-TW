---
title: BizTalk Server WCF 配接器效能最佳化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2900c845-15be-4466-8fa0-b51b2486842f
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ce620e7d9da984081b0f0874985bfe762eeae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299670"
---
# <a name="optimizing-biztalk-server-wcf-adapter-performance"></a>BizTalk Server WCF 配接器效能最佳化
本主題提供選取適當的 WCF 配接器或繫結型別和指導方針套用不同的 WCF 配接器組態選項的建議。  
  
## <a name="considerations-when-choosing-which-wcf-adapter-to-use-or-which-wcf-customwcf-customisolated-binding-type-to-use"></a>選擇要使用的 WCF 配接器或要使用的 WCF 自訂/WCF CustomIsolated 繫結類型時的考量  
  
-   如果並非絕對必要的因為它會增加訊息大小，請勿使用訊息層級安全性。 這又可以降低解決方案的整體輸送量。  
  
-   當您選擇要使用的 WCF 配接器或哪些自訂/WCF-Wcf-customisolated 時**繫結類型**若要使用，請仔細考慮任何應用程式需求，例如相容性、 效能、 裝載平台、 安全性和支援傳輸。 下面所列的指導方針適用於 WCF 一般情況下，而且不屬於 BizTalk Server:  
  
    -   **BasicHttpBinding**如果 WCF 服務必須支援舊版的用戶端，例如 WebSphere Web 服務或.NET 1.1 應用程式所預期的 ASMX Web 服務應該使用。 BasicHttpBinding 未實作任何安全性依預設，如果您需要訊息或傳輸安全性，因為應該在這個繫結上明確地設定它。 若要公開能夠與 ASMX 架構 Web 服務和用戶端和其他符合 WS-I 通訊之端點使用 BasicHttpBinding-Basic Profile 1.1。 當設定傳輸安全性，BasicHttpBinding，則預設為只使用無認證就像傳統的 ASMX Web 服務。 BasicHttpBinding，可讓您裝載在 IIS 7.5 或 IIS 7.0 中的 WCF 服務。  
  
    -   **WsHttpBinding**應該用於網際網路的 WCF 用戶端會呼叫 WCF 服務時。 WsHttpBinding 是網際網路案例中沒有支援預期的 ASMX Web 服務的舊版用戶端 WsHttpBinding 可讓您裝載 WCF 服務，IIS 7.5 或 IIS 7.0 中的理想選擇。 如果您需要支援的舊版用戶端，請考慮改為使用 BasicHttpBinding。   
        應該使用 WsHttpBinding，當您需要公開 WCF 接收位置，或採用傳送埠支援 WS-* 通訊協定，例如 WS-安全性 」 或 「 WS AtomicTransactions。  
  
    -   **NetTcpBinding**是很好的選擇，如果您需要支援內部網路中的用戶端。 NetTcpBinding 是適合內部網路案例，如果傳輸效能對您很重要，而且是可接受在 Windows 服務而不是在 IIS 中裝載服務。 當您想要提供安全、 可靠的繫結的環境時，請使用此繫結。NET-.NET 跨電腦通訊。 請注意，NetTcpBinding 必須裝載在 Windows 服務或 IIS 7.5/7.0。  
  
    -   **NetNamedPipeBinding**如果您需要為您的服務在相同電腦上支援 WCF 用戶端應該使用。 這個繫結會提供跨處理序的同一部電腦通訊的安全而可靠的繫結環境。 使用此繫結，當您想要使用具名管道通訊協定。 請注意，NetNamedPipeBinding 必須裝載在 Windows 服務或 IIS 7.5/7.0。  
  
    -   **NetMsmqBinding**應該使用，如果您需要支援中斷連線的佇列。 佇列是由使用 Message Queuing (也稱為 MSMQ) 提供做為傳輸，可支援中斷連接的作業、 失敗隔離、 和負載均衡。 當用戶端和服務不需要同時在線上時，您可以使用 NetMsmqBinding。 您也可以使用 負載均衡管理任何數目的內送訊息。 訊息佇列支援失敗隔離、 可能不會影響其他訊息的處理會失敗的訊息。 請注意，NetMsmqBinding 必須裝載在 Windows 服務或 IIS 7.5/7.0。  
  
    -   **WsDualHttpBinding**如果您需要支援雙工服務應該使用。 雙工服務會使用雙工訊息模式，因此，讓服務的通訊透過回呼用戶端的服務。 請注意，WsDualHttpBinding 必須裝載在 Windows 服務或 IIS 7.5/7.0。  
  
## <a name="wcf-binding-comparison"></a>WCF 繫結的比較  
 繫結會提供用來設定通道堆疊的機制。 繫結會建立處理程序來建立使用傳輸通道、 訊息編碼器，以及一組通訊協定通道的通道堆疊。 Windows Communication Foundation 隨附有預先設定，若要解決最常見的通訊案例的許多內建繫結。  
  
|繫結的類別名稱|傳輸|訊息編碼|安全性模式|可信賴傳訊|異動流程 （預設為停用）|  
|------------------------|---------------|----------------------|-------------------|------------------------|----------------------------------------------|  
|BasicHttpBinding|HTTP|Text|無|不支援|不支援|  
|WSHttpBinding|HTTP|Text|訊息|已停用|WS AtomicTransactions|  
|NetTcpBinding|TCP|二進位|傳輸|已停用|OleTransactions|  
|NetNamedPipesBinding|具名管道|二進位|傳輸|不支援|OleTransactions|  
|NetMsmqBinding|MSMQ|二進位|訊息|不支援|不支援|  
|CustomBinding|您決定|您決定|您決定|您決定|您決定|  
  
 您可以選取特定的繫結，根據您通訊需求。 例如：  
  
-   **BasicHttpBinding**設計簡單的 Web 服務互通性。 BasicHttpBinding 使用 HTTP 傳輸和訊息編碼的文字。  
  
-   **WSHttpBinding**設計的互通性與更進階的 Web 服務，可能會利用不同的 WS-* 通訊協定。  WSHttpBinding 也會使用 HTTP 傳輸和訊息編碼的文字。  
  
-   **NetTcpBinding**和**NetNamedPipeBinding**專為有效率以及跨電腦或在相同電腦上分別執行 ant 通訊與其他 WCF 應用程式。  
  
-   如果您需要在執行階段使用一個或多個自訂通訊協定通道的最大的彈性，您可以使用**CustomBinding** ，讓您決定哪一個繫結項目撰寫您的繫結。  
  
> [!NOTE]  
>  繫結會有不同的回應時間與輸送量的特性。 因此，以提升效能的一般建議使用 NetTcpBindind 和 NetNamesPipeBinding 盡可能。  
  
## <a name="use-the-tcp-transport-and-binary-message-encoding-to-maximize-wcf-adapter-throughput-and-minimize-wcf-adapter-latency"></a>使用 TCP 傳輸和二進位訊息編碼 WCF 配接器輸送量最大化和 WCF 配接器延遲降至最低  
 使用 Wcf-nettcp 配接器時能夠發揮最大輸送量。 Wcf-nettcp 配接器會使用 TCP/IP 傳輸通訊協定和二進位訊息編碼的結合，提供更佳的效能相較於其他 WCF-* 配接器。  
  
 或者，您可以設定 WCF 自訂 （或 Wcf-customisolated 配接器的接收位置） 與**customBinding**繫結類型。 接著，新增**binaryMessageEncoding**繫結延伸模組來實作二進位訊息編碼和**tcpTransport**繫結延伸模組來實作訊息傳輸通訊協定的 TCP/IP。 這個方法相當富彈性，因為它可讓您選取及設定只需要繫結元素，並建立自訂通道，以便擴充 「 BizTalk 傳訊引擎的預設行為。 如果您實作使用 Wcf-custom 配接器**customBinding**繫結類型，指定這些參數的值繫結延伸組態發揮最大輸送量和延遲降至最低。  
  
 **傳送埠組態值：**  
  
|設定|預設值|建議值|  
|-------------|-------------------|-----------------------|  
|**TcpTransportBindingElement.ConnectionPoolSettings.maxOutboundConnectionsPerEndpoint** -取得或設定在連線集區內快取每個端點的傳出連接的數目上限。 這會限制每個唯一遠端端點快取中的連線數目。 如果超過此值時擁有更多使用中的用戶端連線，此服務可能會沒有回應至用戶端，並應該調整這個值，以容納每個唯一遠端端點快取的預期連接數目上限。 如需有關這個屬性的詳細資訊，請參閱[TcpConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint 屬性](http://go.microsoft.com/fwlink/?LinkId=157737)(http://go.microsoft.com/fwlink/?LinkId=157737) MSDN 上。|10|再試一次 > = 20|  
  
 **接收埠組態值：**  
  
|設定|.NET Framework 4 的預設值|適用於.NET Framework 4 的建議的值|預設值，適用於.NET Framework 3.5|適用於.NET Framework 3.5 的建議的值|  
|-------------|----------------------------------------|--------------------------------------------|------------------------------------------|----------------------------------------------|  
|**TcpTransportBindingElement.MaxPendingAccepts** -取得或設定最大暫止非同步接受作業數目可供處理服務傳入連線。 具備高層級 initiations 同時連接的情況下，這個值可能並不夠，應該加以調整，連同**MaxPendingConnections**屬性以處理更高層級的並行用戶端連線嘗試。 它不能有必要，設定此屬性的值大於存在於裝載服務之電腦的處理器數目。 如需有關這個屬性的詳細資訊，請參閱[ConnectionOrientedTransportBindingElement.MaxPendingAccepts 屬性](http://go.microsoft.com/fwlink/?LinkId=157738)(http://go.microsoft.com/fwlink/?LinkId=157738) MSDN 上。|1|2 * ProcessorCount|1|再試一次 > = 20|  
|**TcpTransportBindingElement.MaxPendingConnections** -取得或設定的服務上等待分派的連線數目上限。 這會限制同時用戶端等待分派的連線數目。 如果此值就太低，用戶端連接嘗試可能會遭到拒絕服務。 如果太高，服務可能會變慢或沒有回應至用戶端負載過重的期間。 這個屬性應該設定的值，可讓服務在執行完整的容量，並不高。 當執行的呼叫堆疊中較高層**AcceptDispatch**，已從等待分派之連線的佇列中移除連線。 如需有關這個屬性的詳細資訊，請參閱[ConnectionOrientedTransportBindingElement.MaxPendingConnections 屬性](http://go.microsoft.com/fwlink/?LinkId=157735)(http://go.microsoft.com/fwlink/?LinkId=157735) MSDN 上。|10|16 * ProcessorCount|10|再試一次 > = 20|  
|**TcpTransportBindingElement.ListenBacklog** -取得或設定可以擱置之佇列的連線要求的最大數目。 **ListenBacklog**是通訊端層級的屬性，描述所使用的 「 暫停接受 」 要求排入佇列。 請確認最大並行連接數目未超過基礎通訊端佇列。 如需此屬性的詳細資訊，請參閱[TcpTransportBindingElement.ListenBacklog 屬性](http://go.microsoft.com/fwlink/?LinkId=157734)(http://go.microsoft.com/fwlink/?LinkId=157734) MSDN 上。|10|16 * ProcessorCount|10|再試一次 > = 20|  
  
 **新增服務行為 ServiceThrottlingBehavior Wcf-custom 或 Wcf-customisolated 接收位置，並使用下列設定：**  
  
> [!NOTE]  
>  可以修改行為 ServiceThrottlingBehavior 服務的任何項目之前，您必須先新增**serviceThrottling**行為延伸模組至**行為** 索引標籤**WCF 自訂\*傳輸屬性** 對話方塊。 若要新增 serviceThrottling 之行為的清單，選取**行為** 索引標籤**Wcf-custom\*傳輸屬性**對話方塊中，以滑鼠右鍵按一下**ServiceBehavior**下**行為**，按一下**加入擴充功能**，選取**serviceThrottling**，然後按一下**確定**。 然後按一下以選取底下可用的屬性**ServiceThrottlingElement**並視需要變更屬性的值。  
  
|設定|.NET Framework 4 的預設值|適用於.NET Framework 4 的建議的值|預設值，適用於.NET Framework 3.5|建議值適用於.Net Framework 3.5|  
|-------------|----------------------------------------|--------------------------------------------|------------------------------------------|----------------------------------------------|  
|**ServiceThrottlingBehavior.MaxConcurrentCalls** -取得或設定值，這個值會指定上主動處理的訊息數目上限**ServiceHost**。 **MaxConcurrentCalls**屬性會指定上主動處理的訊息數目上限**ServiceHost**物件。 每個通道可以有一個暫止的訊息不會計算的值， **MaxConcurrentCalls**直到 WCF 開始處理它。 如需有關這個屬性的詳細資訊，請參閱[ServiceThrottlingBehavior.MaxConcurrentCalls](http://go.microsoft.com/fwlink/?LinkId=157838) (http://go.microsoft.com/fwlink/?LinkId=157838) MSDN 上。 預設值為 BizTalk Wcf-custom 和 Wcf-customisolated 接收配接器**MaxConcurrentCalls**屬性是**16**每個 CPU。 **注意：** BizTalk Server WCF 接收配接器以外的 Wcf-custom 和 Wcf-customisolated 配接器公開**同時呼叫上限**屬性**繫結** 索引標籤**WCF-\*傳輸屬性**對話方塊，即可設定此行為。 預設值**同時呼叫上限**行為是**200**。|16 * ProcessorCount|16 * ProcessorCount|-16 個 BizTalk Wcf-custom 和 Wcf-customisolated 接收配接器。<br />-200 其他 wcf 接收配接器。|-請嘗試 > = 200，Wcf-custom 和 Wcf-customisolated 接收配接器。<br />-再次嘗試 > 為 200**同時呼叫上限**屬性**繫結** 索引標籤**WCF-\*傳輸屬性**BizTalk Server WCF 對話方塊接收 Wcf-custom 和 Wcf-customisolated 配接器以外的配接器。|  
|**ServiceThrottlingBehavior.maxConcurrentInstances** -取得或設定值，指定最大數目**InstanceContext**可以同時執行的服務中的物件。 **MaxConcurrentInstances**屬性指定的最大數目**InstanceContext**服務中的物件。 請務必記住之間的關聯性**MaxConcurrentInstances**屬性和**InstanceContextMode**屬性。 如果**InstanceContextMode**是 PerSession，產生的值是工作階段總數。 如果**InstanceContextMode**為 PerCall，產生的值是同時呼叫數目。 如果訊息抵達時的最大數目**InstanceContext**物件已經存在，會保留該訊息，直到**InstanceContext**物件關閉。 如需有關這個屬性的詳細資訊，請參閱[ServiceThrottlingBehavior.MaxConcurrentInstances 屬性](http://go.microsoft.com/fwlink/?LinkId=157897)(http://go.microsoft.com/fwlink/?LinkId=157897) MSDN 上。 個 Wcf-custom 和 Wcf-customisolated 接收配接器 MaxConcurrentInstances 屬性的預設值是**116**每個 CPU。 **注意：** 因為 WCF 接收位置會實作為包含 Microsoft.BizTalk.Adapter.Wcf.Runtime.dll 組件中，但是由於此類別標示為 ServiceBehavior (InstanceContextMode BizTalkServiceInstance 類別的執行個體= InstanceContextMode.Single，ConcurrencyMode=ConcurrencyMode.Multiple）。 所有連入要求都受相同的單一物件，這個參數已忽略。 因此 maxConcurrentInstances 屬性設定特定 Wcf-custom 接收位置會有任何作用，因為作用中的執行個體的數目會一律等於 1。|116 * ProcessorCount|116 * ProcessorCount|26|再試一次 > = 200|  
|**ServiceThrottlingBehavior.MaxConcurrentSessions** - **MaxConcurrentSessions**屬性取得或設定工作階段數目上限**ServiceHost**物件可以接受一次. 請務必了解工作階段在此情況下並不限於支援可靠工作階段的通道。 每個接聽程式物件只能有一個暫止通道工作階段，不會計算的值**MaxConcurrentSessions**直到 WCF 接受通道工作階段並開始處理通道工作階段訊息。 這個屬性是在最有用的工作階段所運用的案例。 當這個屬性設定為小於用戶端執行緒數目的值時，來自多個用戶端的要求可能會在相同的通訊端連線中形成佇列。 將會封鎖來自尚未以服務建立工作階段的用戶端的要求。 它們會保持封鎖，直到服務關閉其工作階段與其他用戶端，如果服務上的開啟工作階段數目已達到指定的值**MaxConcurrentSessions**。 不提供服務的用戶端要求會再逾時，並在服務關閉工作階段。 若要避免這種情況，請考慮執行用戶端執行緒從不同的應用程式定義域，以便接受要求訊息的不同通訊端連線。 如需有關這個屬性的詳細資訊，請參閱[ServiceThrottlingBehavior.MaxConcurrentSessions 屬性](http://go.microsoft.com/fwlink/?LinkID=157864)(http://go.microsoft.com/fwlink/?LinkId=157864) MSDN 上。|100 * ProcessorCount|100 * ProcessorCount|10|再試一次 > = 200|  
  
 當修改連接埠組態設定套用變更有條理地;個別修改每個參數，並測試效能和整體穩定性的變更影響。 要套用適當的值一定，取決於特定案例： 如果設定值太低，可以降低延展性。而如果值設得太高，應用程式的需求可能會超過電腦上的實體資源的容量。 此外，由於這些屬性在相關，他們應該設定一致且保持一致的方式。 如需使用 ServiceThrottlingBehavior 來控制 WCF 服務效能的詳細資訊，請參閱[使用 ServiceThrottlingBehavior 來控制 WCF 服務效能](http://go.microsoft.com/fwlink/?LinkId=157908)(http://go.microsoft.com/fwlink/?LinkId=157908) MSDN 上。  
  
## <a name="see-also"></a>另請參閱  
 [BizTalk Server 效能最佳化](../technical-guides/optimizing-biztalk-server-performance.md)