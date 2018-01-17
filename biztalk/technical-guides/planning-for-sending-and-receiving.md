---
title: "規劃傳送和接收 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d67e5f7-5127-4c1d-be20-8d8dbb538286
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca2b87964266b77629f7fa1d1156ace3cd048e7f
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="planning-for-sending-and-receiving"></a>規劃傳送和接收
幾乎所有由處理的文件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]收到[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]接收配接器，與寄件者[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]傳送配接器。 因為[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器，以突顯的方式圖中任何[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，請務必預先規劃，以判斷哪些配接器或加速器您將使用及如何正確地設定這些介面卡和/或加速器。  
  
## <a name="determining-which-adapters-and-accelerators-you-will-use"></a>判斷哪些配接器和您將使用的快速鍵  
 與交易夥伴事先來判斷哪一個配接器和您將需要執行傳送和接收文件，您的組織與交易夥伴，以及您的 BizTalk 應用程式與您的內部之間的快速鍵商務應用程式。 設計您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]架構是有足夠的彈性，以容納新增其他配接器或加速器，建立關聯性與其他交易夥伴在未來。  
  
## <a name="functionality-supported-by-biztalk-adapters"></a>BizTalk 配接器支援的功能  
 本節的表格會列出每個原生配接器和配接器是否提供下列功能的主要優點：  
  
-   **交易支援**傳送和接收文件的分散式的交易協調器 (DTC) 交易內容下的能力。 此為維護已排序之訊息傳遞所需的必要功能，並用以保證文件並未重複或遺失。  
  
    > [!NOTE]  
    >  如果您遇到與 msdtc 進行通訊的問題，請檢閱主題[疑難排解 MSDTC 問題的](http://go.microsoft.com/fwlink/?LinkID=154693)(http://go.microsoft.com/fwlink/?LinkID=154693)。  
  
-   **雙向通訊支援 （要求/回應或請求/回應）**能夠傳送文件，並處理來自目的地的回應訊息或接收文件和傳送回應訊息的來源。  
  
-   **依序接收支援。** 能夠接收文件發佈至 MessageBox 資料庫已接收的文件的正確順序。  
  
    > [!NOTE]  
    >  特定配接器可以強制在接收位置層級的已排序的文件傳遞，而其他配接器不能。 排序的傳遞仍會在傳送埠層級，這些介面卡不支援排序傳遞文件接收位置層級強制執行，但這樣做可能會對效能帶來負面影響。 如需排序的傳遞的訊息，請參閱本主題[排序訊息傳遞](http://go.microsoft.com/fwlink/?LinkId=155751)(http://go.microsoft.com/fwlink/?LinkId=155751)。  
  
-   **已啟用 SSO。** 以配接器傳送或接收文件時，使用 SSO 驗證的功能。  
  
|配接器|主要優點|交易支援|雙向通訊支援|依序接收支援|已啟用 SSO|  
|-------------|---------------------|-------------------------|------------------------------------|-------------------------------|-----------------|  
|檔案|容易使用|否|否|否|否|  
|FTP|廣泛用於企業對企業通訊|否|否|否|是|  
|HTTP(S)|廣泛用於企業對企業通訊|否|要求/回應和請求/回應|否|是|  
|SOAP|支援使用 Web 服務|否|要求/回應和請求/回應|否|是|  
|MSMQ|支援保證僅一次傳遞，BizTalk Server 和 Microsoft Message Queuing 之間的訊息|是|否|是|否|  
|MQ 系列|保證僅一次傳遞的 BizTalk Server 與 IBM WebSphere MQ 之間的訊息用於 Windows 平台支援|是|否|是|是|  
|SQL|支援直接 BizTalk Server 與 SQL Server 資料庫之間的通訊|是|僅請求/回應|否|否|  
|Windows SharePoint Services|可讓 XML 和二進位訊息，BizTalk Server 與 SharePoint 文件庫之間的交換|否|否|否|否|  
|POP3|接收文件，透過電子郵件支援|否|否|否|否|  
|SMTP|支援傳送電子郵件的文件|否|否|否|否|  
|EDI|支援處理符合 EDI 標準的商務文件|否|否|否|否|  
|Custom|支援舊版系統|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|  
|WCF-WSHttp|支援 WS-* 標準，透過 HTTP 傳輸|是，WsHTTP 支援交易 (僅限 WS-Transaction)|要求/回應和請求/回應|否|是|  
|WCF-BasicHttp|與 ASMX 架構 Web 服務和用戶端和其他符合 WS-I 通訊-Basic Profile 1.1 使用 HTTP 或 HTTPS|否|要求/回應和請求/回應|否|是|  
|WCF-NetTcp|支援 WS-* 標準，透過 TCP 傳輸|是|要求/回應和請求/回應|否|是|  
|WCF-NetMsmq|支援佇列，利用 Microsoft Message Queuing (MSMQ) 做為傳輸|是|否|是|是|  
|WCF-NetNamedPipe|提供的快速傳輸 （僅適用於 WCF 應用程式） 在相同電腦上的跨處理序通訊|是|要求/回應和請求/回應|否|是|  
|WCF-Custom|可讓您使用 WCF 擴充性功能|是的。|是的。|是，只要繫結支援它即可。|是的。|  
|WCF-CustomIsolated|透過 HTTP 傳輸啟用 WCF 擴充性功能|是的。|是的。|資料分割|是的。|  
  
## <a name="line-of-business-adapters"></a>商務營運系統配接器  
 以下是 Microsoft 提供的「主要商務」(LOB) 配接器清單。  
  
> [!NOTE]  
>  除了 Microsoft BizTalk Adapter v2.0 for mySAP™ Business Suite （配接器），無商務 」 配接器支援在 Windows Vista 上。  
  
|配接器|Description|支援的版本|  
|-------------|-----------------|------------------------|  
|SAP （也稱為 「 配接器 」）|允許的中繼文件 (IDOC)、 BAPI 和 BizTalk Server 和 SAP R/3® 系統之間的遠端函式呼叫 (RFC) 訊息交換。|SAP R/3 4.x 和 R/3 6.20 (Enterprise)|  
|PeopleSoft Enterprise|允許在 BizTalk Server 和 PeopleSoft 系統之間的元件介面 (CI) 訊息交換。|PeopleTools 8.17.02、8.43、8.45、8.46 和 8.48 版|  
|JD Edwards OneWorld XE|允許在 BizTalk Server 和 JD Edwards OneWorld 系統之間的商務功能訊息交換。|B7.3.3.3 SP23 和 JDE 8.0 (B7.3.3.4)|  
|JD Edwards EnterpriseOne|允許在 BizTalk Server 和 JD Edwards EnterpriseOne 系統之間的商務功能訊息交換。|8.10 & 8.11 with Tools 版本 8.93、 8.94、 8.95 和 8.96|  
|Oracle 資料庫的 ODBC 配接器|允許從 Oracle Server 資料庫讀取和寫入資訊。|Oracle 8i (8.1.6.0)、 9i (9.2.0.1) 或 10g|  
|Siebel eBusiness 應用程式|允許在 BizTalk Server 和 Siebel eBusiness 應用程式之間的商務元件和商務服務訊息交換。|7.0、 7.5。 *、 7.7。\*，及 7.8。\*|  
|TIBCO Rendezvous|允許在 BizTalk Server 和 TIBCO Rendezvous 之間的 XML 和二進位資料格式訊息交換。|7.3|  
|TIBCO Enterprise Message Service|允許在 BizTalk Server 和提供緊密整合及可靠應用程式基礎結構之 TIBCO EMS 伺服器之間的 XML 及二進位資料格式訊息交換。|4.2|  
|WebSphere MQ|允許在 BizTalk Server 和 IBM WebSphere MQ 之間的訊息交換。|5.3 搭配 Fix Pack 10 或更新版本和 6.0 修正組件 1.1 或更新版本|  
  
 如需 BizTalk Server 上提供的 LOB 配接器的詳細資訊，請參閱[配接器隨附於 BizTalk Server 2010](http://go.microsoft.com/fwlink/?LinkId=152664) (http://go.microsoft.com/fwlink/?LinkId=152664)。  
  
## <a name="biztalk-adapter-pack"></a>BizTalk 配接器封包  
 Microsoft[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]包含 wcf 配接器能夠提供連線至 LOB 應用程式，例如 Oracle 資料庫、 Oracle E-business Suite、 SAP、 Siebel 和 SQL Server。 如需可用的配接器的清單[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱[BizTalk Adapter Pack](http://go.microsoft.com/fwlink/?LinkId=152665) (http://go.microsoft.com/fwlink/?LinkId=152665)。  
  
> [!IMPORTANT]  
>  您可以使用[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]移轉工具，以將 LOB 配接器的 BizTalk 專案移轉至 wcf LOB 配接器隨附的 BizTalk 專案[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。 您可以下載[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]移轉工具從[BizTalk Adapter Pack 移轉工具](http://go.microsoft.com/fwlink/?LinkID=153328)(http://go.microsoft.com/fwlink/?LinkID=153328)。 若要深入了解移轉至 wcf LOB 配接器隨附的 LOB 配接器[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱[Microsoft BizTalk Adapter 2.0 移轉詘躩裛](http://go.microsoft.com/fwlink/?LinkId=158848)(http://go.microsoft.com/fwlink/?LinkId=158848)。  
  
## <a name="biztalk-accelerators"></a>BizTalk 加速器  
 BizTalk 配接器會配合特定的通訊協定傳送和接收的文件，而 BizTalk 加速器專門設計來容納根據特定的業界標準的文件的交換。 如需可用的 BizTalk 快速鍵的清單，請參閱[Microsoft BizTalk Server 加速器](http://go.microsoft.com/fwlink/?LinkId=103609)(http://go.microsoft.com/fwlink/?LinkId=103609)。  
  
##  <a name="BKMK_InternetTrans"></a>公開到網際網路傳輸時，設定您的網域  
 為簡化傳送和接收的文件，您的組織和外部交易夥伴之間，可能需要公開可從網際網路存取的公用對向站台上的傳輸。 在這些情況下，建議使用下列網域的設定：  
  
-   **周邊網路網域，（也稱為非軍事區域 (DMZ) 或過濾的子網路），採用到屋伺服器以提供網際網路相關服務，為您的組織**  
  
     周邊網路網域應該包含伺服器的存放位置網際網路對向傳輸文件路由傳送執行的電腦之間的實體位置[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與交易夥伴。 周邊網路防火牆只應該開啟允許網際網路對向傳輸的通訊所需的連接埠。 不應該執行的任何電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]周邊網路網域中接收位置或企業單一登入伺服器電腦。 文件傳送/接收至 azure 或從周邊網路網域中的傳輸應從網際網路對向防火牆路由至防火牆保護處理網域中使用 Internet Security and Acceleration Server (ISA) Server 網頁發佈和伺服器發佈。 如需使用 ISA Server Web 和伺服器發佈的詳細資訊，請參閱[ISA Server 2006 中的發行概念](http://go.microsoft.com/fwlink/?LinkID=86359)(http://go.microsoft.com/fwlink/?LinkID=86359)。  
  
    > [!NOTE]  
    >  新增量值的安全性，請考慮使用公開金鑰基礎結構 (PKI) 數位憑證用於文件加密和解密，文件簽署和驗證 （不可否認性） 的文件傳送或接收來自交易夥伴透過網際網路對向此網域中的傳輸。  
  
     下列傳輸通常是可從網際網路存取周邊網路網域上使用：  
  
    -   FTP 接收使用 FTP 通訊協定文件  
  
    -   SMTP-將使用 SMTP 通訊協定的文件傳送  
  
    -   HTTP-接收使用 HTTP 通訊協定文件  
  
    -   SOAP-接收使用 SOAP 的文件  
  
    -   POP3-接收使用 POP3 通訊協定文件  
  
-   **使用處理網域中所包含 BizTalk Server 的伺服器接收和傳送處理常式和 BAM 入口網站伺服器**  
  
     透過這些網域之間有防火牆，應該進行路由周邊網域中的外部對向傳輸和處理網域中的 BizTalk 配接器之間的文件流程。 處理網域中應該包含[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]連接埠、 接收位置、 管線、 對應、 結構描述，以及用來接收，組件路由傳送，並將訊息傳送。 處理網域，也應該包含 BAM 入口網站的伺服器。 執行的電腦數目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]處理網域中將主機數目而定，主控件執行個體需要符合您組織的效能需求。  
  
    > [!IMPORTANT]  
    >  請確定在處理網域中，以容納流量流入周邊網域中的 HTTP 與 SOAP 傳輸和處理網域中的 HTTP 與 SOAP 配接器之間建立足夠的外掛式主控的件執行個體。 如果大部分的組織與交易夥伴之間的文件流量流經 HTTP 與 SOAP 傳輸，以處理文件流程處理網域中必須有足夠處理頻寬。  
  
-   **運用您的環境提供進一步的隔離和安全性層級的其他網域**  
  
     應該包含這些網域：  
  
    -   服務網域的信任處理網域，而且這需要成功處理訊息。 服務網域中的伺服器通常會執行 BizTalk 協調流程、 管線、 企業單一登入 (SSO) 服務、 商務規則引擎，而且可能包括其他商務程序。  
  
    -   執行所使用的 SQL Server 之電腦的資料網域[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。  
  
    -   伺服器和桌面的電腦，提供給您組織中的資訊工作者服務的公司網域。  
  
     如需有關網域拓樸建議用於各種[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]架構，請參閱[範例 BizTalk Server 架構](http://go.microsoft.com/fwlink/?LinkId=155750)(http://go.microsoft.com/fwlink/?LinkId=155750)。  
  
## <a name="high-availability-considerations"></a>高可用性考量  
 可以在 BizTalk 群組中的多部 BizTalk 伺服器上執行配接器處理常式主控件執行個體，針對大部分的配接器提供高可用性。 這樣一來，如果一個配接器處理常式主控件執行個體失敗，另一個配接器處理常式主控件執行個體就可繼續處理。 有，不過，這樣的例外狀況。 在某些情況下執行多個配接器處理常式主控件執行個體可能會造成競爭問題。 例如執行 POP3 和 FTP 配接器的多個執行個體時，就會發生競爭問題。 在這些情況下，提供高可用性可以配接器藉由在叢集 BizTalk 主控件執行配接器處理常式主控件執行個體。  
  
 如需主機叢集透過配接器處理常式主控件執行個體提供高可用性的詳細資訊，請參閱[叢集主控件中執行配接器處理常式的考量](http://go.microsoft.com/fwlink/?LinkID=151284)(http://go.microsoft.com/fwlink/?LinkID=151284)。 如需有關如何為 BizTalk 主控件提供高可用性的詳細資訊，請參閱[高可用性的 BizTalk 主控件](../technical-guides/high-availability-for-biztalk-hosts.md)。  
  
## <a name="performance-considerations"></a>效能考量  
 **SOAP 配接器效能的考量**  
  
 最佳化效能，SOAP 配接器的相關資訊，請參閱[組態參數會影響配接器效能](http://go.microsoft.com/fwlink/?LinkID=154200)(http://go.microsoft.com/fwlink/?LinkID=154200)。  
  
 **MQSeries 配接器效能的考量**  
  
 **停用交易支援和排序的傳遞，如果沒有所需的 MQSeries 配接器接收位置**當 MQSeries 配接器接收位置會設定與**交易支援**選項設為**[是]**，或**Ordered**選項設定為**含有停止的順序**，則將會由接收位置挑選每個訊息處理的 Microsoft Distributed 內容中交易協調器 (MSDTC) 交易。 因為沒有其他配接器負擔時所產生處理 MSDTC 交易的內容中的訊息，這些選項不應啟用如果排序的傳遞，或交易支援就不需要為 MQSeries 接收位置。  
  
## <a name="planning-for-ordered-message-delivery"></a>規劃訊息的排序的傳遞  
 訊息的排序的傳遞可確保會發佈到 MessageBox 資料庫，依指定順序的訊息會傳遞至每個相符的訂閱者以相同的順序。 實作依序的傳遞訊息時，就會適用下列考量：  
  
 **設定訊息的排序的傳遞**  
  
 순차적 메시지 전달은 다음 위치에서 구성할 수 있습니다.  
  
-   在協調流程接收圖形  
  
-   接收位置的特定介面卡  
  
-   송신 포트  
  
 **排序的傳遞具備現有傳輸**  
  
 FILE 및 HTTP와 같은 특정 전송에서는 순차적 전달 개념과 일치하지 않는 프로토콜을 사용합니다. 그러나 이러한 전송을 사용하는 경우에도 전송에 바인딩된 포트가 순차적 전달용으로 표시되어 있으면 BizTalk Server에서는 현재 아웃바운드 메시지가 성공적으로 송신될 때까지 다음 메시지가 전송되지 않도록 하여 순차적 전달을 적용합니다. 若要達成此目的，BizTalk Server 會將每個訊息傳遞至傳輸的配接器，在單一批次並等待配接器已成功刪除之前訊息從 MessageBox 資料庫另一個批次中的下一個訊息，傳遞至配接器之前。  
  
 **自訂配接器的排序傳遞**  
  
 自訂接收配接器提交訊息至 BizTalk Server 時，保留訊息順序，配接器必須開發具有下列功能：  
  
-   在提交訊息批次之後, 您的自訂接收配接器應該等候 BatchComplete 呼叫從 BizTalk Server，再提交下一個批次。 如需詳細資訊，請參閱[Batch-Supported 接收配接器的介面](http://go.microsoft.com/fwlink/?LinkId=155752)(http://go.microsoft.com/fwlink/?LinkId=155752)。  
  
-   如果訊息在管線中，它應該被擱置，最好是為不可繼續。 使用 BTS。SuspendAsNonResumable 訊息內容屬性中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]適當地加上旗標的訊息。  
  
    > [!NOTE]  
    >  일시 중단된 메시지가 나중에 다시 시작되면 메시지 순서가 잘못될 수 있습니다. 若不想使用此行為，擱置失敗的訊息為不可繼續。  
  
 **條件的端對端排序的訊息處理**  
  
 종단 간 순차적 전달을 제공하려면 다음 조건을 충족해야 합니다.  
  
-   BizTalk Server로 메시지를 전송할 때 메시지 순서를 유지하는 어댑터를 사용하여 메시지를 수신해야 합니다. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，這類配接器的範例包括 MSMQ 和 MQSeries。 또한 HTTP 또는 SOAP 어댑터를 사용하여 메시지를 순서대로 전송할 수도 있지만 이러한 경우 HTTP 또는 SOAP 클라이언트에서 메시지를 한 번에 하나씩 전송하여 메시지 순서를 유지해야 합니다.  
  
-   您必須訂閱這些訊息的傳送埠**排序的傳遞**選項設定為**True**。  
  
-   協調流程的訊息，協調流程中的單一執行個體應該使用的程序來協調流程，如果應該設定為使用循序群組，而 **排序的傳遞** 屬性的協調流程的接收連接埠應該設定為 **True**。  
  
## <a name="see-also"></a>另請參閱  
 [規劃 BizTalk Server 的環境](../technical-guides/planning-the-environment-for-biztalk-server.md)