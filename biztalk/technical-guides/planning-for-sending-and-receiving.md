---
title: 規劃傳送與接收 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d67e5f7-5127-4c1d-be20-8d8dbb538286
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a96c75ceadfeaf06dde2c3661dd00f435529dcc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009519"
---
# <a name="planning-for-sending-and-receiving"></a>規劃傳送與接收
幾乎每個處理的文件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收配接器，並從傳送[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送配接器。 因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器圖因此以醒目方式在任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境，請務必預先規劃，以判斷哪一個配接器或加速器您將使用，以及如何正確地設定這些介面卡和/或加速器。  
  
## <a name="determining-which-adapters-and-accelerators-you-will-use"></a>判斷哪些您將使用的加速器和配接器  
 授與對交易夥伴，以判斷哪一個您必須以利於進行傳送和接收文件，您的組織與交易夥伴，以及您的 BizTalk 應用程式與您的內部的加速器和配接器商務應用程式。 設計您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]具備足夠的彈性，以容納新增其他配接器或加速器，建立與其他交易的關聯性的架構未來合作夥伴。  
  
## <a name="functionality-supported-by-biztalk-adapters"></a>BizTalk 配接器所支援的功能  
 本章節中的表格列出每個原生配接器和配接器是否提供下列功能的主要優點：  
  
-   **交易支援**能夠傳送和接收的分散式的交易協調器 (DTC) 交易內容下的文件。 此為維護已排序之訊息傳遞所需的必要功能，並用以保證文件並未重複或遺失。  
  
    > [!NOTE]  
    >  如果您遇到 MSDTC 問題，請在檢閱主題[MSDTC 問題疑難排解](http://go.microsoft.com/fwlink/?LinkID=154693)(http://go.microsoft.com/fwlink/?LinkID=154693)。  
  
-   **雙向通訊支援 （要求/回應或請求/回應）** 能夠傳送文件，並處理來自目的地的回應訊息或接收文件，並將回應訊息傳送至來源。  
  
-   **依序接收支援。** 能夠將收到的文件發佈到 MessageBox 資料庫所接收的文件的正確順序。  
  
    > [!NOTE]  
    >  特定配接器可以強制執行在接收位置層級，傳遞已排序的文件，而其他配接器不能。 排序的傳遞仍會在這些介面卡不支援排序接收位置層級的文件傳遞傳送埠層級強制執行，但這樣做可能會產生對效能帶來負面影響。 如需排序的傳遞的訊息，請參閱主題[排序傳遞的訊息](http://go.microsoft.com/fwlink/?LinkId=155751)(http://go.microsoft.com/fwlink/?LinkId=155751)。  
  
-   **已啟用 SSO。** 以配接器傳送或接收文件時，使用 SSO 驗證的功能。  
  
|配接器|主要優點|交易支援|雙向通訊支援|依序接收支援|已啟用 SSO|  
|-------------|---------------------|-------------------------|------------------------------------|-------------------------------|-----------------|  
|檔案|容易使用|否|否|否|否|  
|FTP|廣泛用於企業對企業通訊|否|否|否|是|  
|HTTP(S)|廣泛用於企業對企業通訊|否|要求/回應和請求/回應|否|是|  
|SOAP|支援使用 Web 服務|否|要求/回應和請求/回應|否|是|  
|MSMQ|支援保證僅一次的傳遞，BizTalk Server 和 Microsoft Message Queuing 之間的訊息|是|否|是|否|  
|MQ 系列|支援保證僅一次傳遞適用於 Windows 平台 BizTalk Server 與 IBM WebSphere MQ 之間的訊息|是|否|是|是|  
|SQL|支援直接 BizTalk Server 與 SQL Server 資料庫之間的通訊|是|僅請求/回應|否|否|  
|Windows SharePoint Services|可讓 XML 和二進位訊息，BizTalk Server 與 SharePoint 文件庫之間的交換|否|否|否|否|  
|POP3|接收文件，透過電子郵件的支援|否|否|否|否|  
|SMTP|支援傳送電子郵件的文件|否|否|否|否|  
|EDI|支援處理符合 EDI 標準的商務文件|否|否|否|否|  
|Custom|支援舊版的系統|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|  
|WCF-WSHttp|支援 WS-* 標準，透過 HTTP 傳輸|是，WsHTTP 支援交易 (僅限 WS-Transaction)|要求/回應和請求/回應|否|是|  
|WCF-BasicHttp|與 ASMX 架構 Web 服務和用戶端和其他符合 WS-I 通訊-Basic Profile 1.1 中使用 HTTP 或 HTTPS|否|要求/回應和請求/回應|否|是|  
|WCF-NetTcp|支援 WS-* 標準，透過 TCP 傳輸|是|要求/回應和請求/回應|否|是|  
|WCF-NetMsmq|利用 Microsoft Message Queuing (MSMQ) 做為傳輸佇列的支援|是|否|是|是|  
|WCF-NetNamedPipe|（僅適用於 WCF 應用程式） 在同一部電腦上的跨處理序通訊，提供快速傳輸|是|要求/回應和請求/回應|否|是|  
|WCF-Custom|可讓您使用 WCF 擴充性功能|是的。|是的。|是，只要繫結支援它即可。|是的。|  
|WCF-CustomIsolated|透過 HTTP 傳輸啟用 WCF 擴充性功能|是的。|是的。|資料分割|是的。|  
  
## <a name="line-of-business-adapters"></a>商務營運系統配接器  
 以下是 Microsoft 提供的「主要商務」(LOB) 配接器清單。  
  
> [!NOTE]  
>  除了 Microsoft BizTalk Adapter v2.0 for mySAP™ Business Suite （配接器），沒有任何企業營運配接器支援在 Windows Vista 上。  
  
|配接器|描述|支援的版本|  
|-------------|-----------------|------------------------|  
|SAP （也稱為 「 配接器 」）|允許的中繼文件 (IDOC)、 BAPI 和 BizTalk Server 和 SAP R/3® 系統之間的遠端函式呼叫 (RFC) 訊息交換。|SAP R/3 4.x 和 R/3 6.20 (Enterprise)|  
|PeopleSoft Enterprise|允許在 BizTalk Server 和 PeopleSoft 系統之間的元件介面 (CI) 訊息交換。|PeopleTools 8.17.02、8.43、8.45、8.46 和 8.48 版|  
|JD Edwards OneWorld XE|允許在 BizTalk Server 和 JD Edwards OneWorld 系統之間的商務功能訊息交換。|B7.3.3.3 SP23 和 JDE 8.0 (B7.3.3.4)|  
|JD Edwards EnterpriseOne|允許在 BizTalk Server 和 JD Edwards EnterpriseOne 系統之間的商務功能訊息交換。|8.10 & 8.11 with Tools 版本 8.93、 8.94、 8.95 和 8.96|  
|Oracle 資料庫的 ODBC 配接器|允許從 Oracle Server 資料庫讀取和寫入資訊。|Oracle 8i (8.1.6.0)，9i (9.2.0.1)，或 10 g|  
|Siebel eBusiness 應用程式|允許在 BizTalk Server 和 Siebel eBusiness 應用程式之間的商務元件和商務服務訊息交換。|7.0、 7.5。 *、 7.7。\*，和 7.8。\*|  
|TIBCO Rendezvous|允許在 BizTalk Server 和 TIBCO Rendezvous 之間的 XML 和二進位資料格式訊息交換。|7.3|  
|TIBCO Enterprise Message Service|允許在 BizTalk Server 和提供緊密整合及可靠應用程式基礎結構之 TIBCO EMS 伺服器之間的 XML 及二進位資料格式訊息交換。|4.2|  
|WebSphere MQ|允許在 BizTalk Server 和 IBM WebSphere MQ 之間的訊息交換。|5.3 搭配 Fix Pack 10 或更新版本和 6.0 修正組件 1.1 或更新版本|  
  
 如需有關 BizTalk Server 上提供的 LOB 配接器的詳細資訊，請參閱[配接器隨附於 BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkId=152664) (http://go.microsoft.com/fwlink/?LinkId=152664)。  
  
## <a name="biztalk-adapter-pack"></a>BizTalk 配接器封包  
 Microsoft[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]包含 WCF 架構配接器可提供對 LOB 應用程式，例如 Oracle Database、 Oracle E-business Suite、 SAP、 Siebel 和 SQL Server 的連線。 如需可用與配接器的清單[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱 < [BizTalk Adapter Pack](http://go.microsoft.com/fwlink/?LinkId=152665) (<http://go.microsoft.com/fwlink/?LinkId=152665>)。  
  
> [!IMPORTANT]
>  您可以使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]LOB 配接器的 BizTalk 專案移轉至 wcf LOB 配接器隨附的 BizTalk 專案的移轉工具[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 您可以下載[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]移轉工具，從[BizTalk Adapter Pack 移轉工具](http://go.microsoft.com/fwlink/?LinkID=153328)(<http://go.microsoft.com/fwlink/?LinkID=153328>)。 若要深入了解移轉 LOB 配接器，以 WCF 為基礎的 LOB 配接器隨附[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱 < [Microsoft BizTalk Adapter 2.0 移轉詘躩裛](http://go.microsoft.com/fwlink/?LinkId=158848)(<http://go.microsoft.com/fwlink/?LinkId=158848>)。  
  
## <a name="biztalk-accelerators"></a>BizTalk 加速器  
 雖然 BizTalk 配接器會配合特定的通訊協定傳送和接收文件，BizTalk 加速器專門設計來容納根據特定的業界標準的文件的交換。 如需可用的 BizTalk 加速器，請參閱[Microsoft BizTalk Server 加速器](http://go.microsoft.com/fwlink/?LinkId=103609)(http://go.microsoft.com/fwlink/?LinkId=103609)。  
  
##  <a name="BKMK_InternetTrans"></a> 公開到網際網路傳輸時，設定您的網域  
 為簡化傳送和接收的文件，您的組織和外部交易夥伴之間，可能必須公開 （expose） 可從網際網路存取公用面向網站上的傳輸。 在這些情況下，建議使用下列網域設定：  
  
- **周邊網路網域，（也稱為 DMZ 或過濾的子網路），採用到屋伺服器以提供網際網路相關服務，為您的組織**  
  
   周邊網路網域應該包含裝載網際網路對向傳輸要路由傳送執行的電腦之間的文件中的實體位置的伺服器[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與交易夥伴。 周邊網路防火牆應該只會開啟，允許從網際網路對向傳輸來回的通訊所需的連接埠。 不應該執行的任何電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]周邊網路網域中接收位置或企業單一登入伺服器電腦。 應該從網際網路對向防火牆路由傳送/接收往返傳輸周邊網路網域中的文件，保護處理網域中使用 Internet Security and Acceleration Server (ISA) Server 網頁發佈的防火牆和伺服器發佈。 如需使用 ISA Server 網頁和伺服器發佈的詳細資訊，請參閱[ISA Server 2006 中發佈概念](http://go.microsoft.com/fwlink/?LinkID=86359)(<http://go.microsoft.com/fwlink/?LinkID=86359>)。  
  
  > [!NOTE]  
  >  已加入的量值的安全性，考慮進行文件加密和解密使用公開金鑰基礎結構 (PKI) 數位憑證時，文件簽署和驗證 （不可否認性） 的文件傳送或接收來自交易透過網際網路傳輸在這個網域中的合作夥伴。  
  
   下列傳輸通常會使用可從網際網路存取周邊網路網域上：  
  
  -   FTP-接收使用 FTP 通訊協定文件  
  
  -   SMTP-傳送使用 SMTP 通訊協定文件  
  
  -   HTTP-接收使用 HTTP 通訊協定文件  
  
  -   SOAP-接收使用 SOAP 文件  
  
  -   POP3-接收使用 POP3 通訊協定文件  
  
- **使用處理網域中，用於裝載伺服器，包含 BizTalk Server 接收和傳送處理常式和 BAM 入口網站的伺服器**  
  
   透過這些網域之間有防火牆，應該進行路由周邊網域中的外部對向傳輸和處理網域中的 BizTalk 配接器之間的文件流程。 處理網域應該客戶留言的場地[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]連接埠、 接收位置、 管線、 對應、 結構描述，以及用來接收，組件路由傳送，並將訊息傳送。 處理網域還應該包含 BAM 入口網站的伺服器。 執行的電腦數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理網域中將取決於主機的數目和主控件執行個體需要符合您組織的效能需求。  
  
  > [!IMPORTANT]  
  >  請確定您在可容納周邊網域中的 HTTP 與 SOAP 傳輸與處理網域中的 HTTP 與 SOAP 配接器之間流動的流量處理網域中建立足夠的外掛式主控件執行個體。 如果大部分的組織與交易夥伴之間的文件流量流經的 HTTP 與 SOAP 傳輸，來處理文件處理網域中必須有足夠的處理頻寬。  
  
- **運用您的環境提供進一步的隔離和安全性層級的其他網域**  
  
   這些網域應該包含：  
  
  - 服務網域的信任處理網域，而且這需要成功處理訊息。 服務網域中的伺服器通常會執行 BizTalk 協調流程、 管線、 企業單一登入 (SSO) 服務、 商務規則引擎，而且可能包含其他商務程序。  
  
  - 所使用的 SQL Server 電腦的資料網域[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
  - 伺服器和桌面的電腦，提供給您組織中的資訊工作者服務的公司網域。  
  
    如需各種建議網域拓樸[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]架構，請參閱[BizTalk Server 架構範例](http://go.microsoft.com/fwlink/?LinkId=155750)(<http://go.microsoft.com/fwlink/?LinkId=155750>)。  
  
## <a name="high-availability-considerations"></a>高可用性考量  
 可以在 BizTalk 群組中的多個 BizTalk 伺服器上執行配接器處理常式主控件執行個體，大部分的配接器提供高可用性。 如此一來，如果一個配接器處理常式主控件執行個體失敗，另一個配接器處理常式主控件執行個體可繼續處理。 有，不過，若要執行此動作的例外狀況。 在某些情況下執行多個配接器處理常式主控件執行個體可能會造成競爭問題。 例如執行多個 POP3 和 FTP 配接器執行個體時，就會發生競爭問題。 在這些情況下，提供高可用性可以是配接器在叢集 BizTalk 主控件執行配接器處理常式主控件執行個體。  
  
 如需有關如何為主機叢集透過配接器處理常式主控件執行個體提供高可用性的詳細資訊，請參閱[在叢集主控件執行配接器處理常式的考量](http://go.microsoft.com/fwlink/?LinkID=151284)(http://go.microsoft.com/fwlink/?LinkID=151284)。 如需有關如何為 BizTalk 主控件提供高可用性的詳細資訊，請參閱 <<c0> [ 高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。  
  
## <a name="performance-considerations"></a>效能考量  
 **SOAP 配接器效能考量**  
  
 如需最佳化 SOAP 配接器的效能資訊，請參閱[組態參數，會影響配接器效能](http://go.microsoft.com/fwlink/?LinkID=154200)(http://go.microsoft.com/fwlink/?LinkID=154200)。  
  
 **MQSeries 配接器效能考量**  
  
 **停用交易支援和排序的傳遞，如果沒有所需的 MQSeries 配接器接收位置**時為 MQSeries 配接器接收位置已設有**交易支援**選項設為 **[是]**，或有**Ordered**選項設定為**含有停止的順序**，然後由接收位置挑選每個訊息會被處理內容中的 Microsoft Distributed交易協調器 (MSDTC) 交易。 因為沒有其他配接器負擔時產生處理在 MSDTC 交易的內容中的訊息，這些選項不應啟用如果排序的傳遞或交易支援不需要為 MQSeries 接收位置。  
  
## <a name="planning-for-ordered-message-delivery"></a>規劃訊息的排序的傳遞  
 訊息的排序的傳遞可確保會發佈至 MessageBox 資料庫，依指定順序的訊息，傳遞給每個相符的訂閱者，以相同的順序。 實作依序的傳遞訊息時，就會適用下列考量：  
  
 **設定訊息的排序的傳遞**  
  
 可在下列位置設定訊息的排序傳遞：  
  
- 在 協調流程接收圖形  
  
- 某些配接器的接收位置  
  
- 傳送埠  
  
  **排序的傳遞和現有的傳輸**  
  
  在特定傳輸之下的通訊協定，像是 FILE 和 HTTP，與排序傳遞的概念並不一致。 不過，即使具備這類傳輸，若與傳輸繫結的連接埠標示為排序的傳遞，則 BizTalk Server 會藉由保證除非已成功傳送目前的輸出訊息，否則傳輸不會取得下一個輸出訊息，以強制排序的傳遞。 若要這麼做，BizTalk Server 會將每個訊息傳遞至傳輸的配接器，在單一批次並等待配接器已成功刪除之前將訊息從 MessageBox 資料庫另一部的批次中的下一個訊息，傳遞至配接器之前。  
  
  **自訂配接器的排序傳遞**  
  
  自訂接收配接器來保留訊息的順序，將它們提交到 BizTalk Server 時，必須開發配接器具有下列功能：  
  
- 提交訊息批次之後, 您的自訂接收配接器應該再提交下一個批次時等候 BatchComplete 呼叫，從 BizTalk Server。 如需詳細資訊，請參閱 < [Batch-Supported 接收配接器介面](http://go.microsoft.com/fwlink/?LinkId=155752)(http://go.microsoft.com/fwlink/?LinkId=155752)。  
  
- 如果管線中失敗的訊息應該被擱置，最好是以不可繼續。 使用 BTS。SuspendAsNonResumable 訊息內容屬性中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]適當地加上旗標的訊息。  
  
  > [!NOTE]  
  >  若在稍後繼續擱置的訊息，則會中斷訊息順序。 如果不想使用這種行為，擱置失敗的訊息為不可繼續。  
  
  **條件的端對端排序的訊息處理**  
  
  若要提供端對端排序的傳遞，必須符合下列條件：  
  
- 必須以保留提交訊息給 BizTalk Server 的訊息順序之配接器接收訊息。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，這類配接器的範例包括 MSMQ 和 MQSeries。 此外，HTTP 或 SOAP 配接器可以用來提交訊息順序，但在此情況下 HTTP 或 SOAP 用戶端必須強制執行一次提交一個訊息的順序。  
  
- 您必須訂閱這些訊息與傳送埠具有**排序的傳遞**選項設定為 **，則為 True**。  
  
- 如果應該使用的訊息，協調流程中的單一執行個體的程序來協調流程，協調流程應該設定為使用循序群組中，而**排序的傳遞**屬性協調流程的接收埠應該設定為 **，則為 True**。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 的環境](../technical-guides/planning-the-environment-for-biztalk-server.md)