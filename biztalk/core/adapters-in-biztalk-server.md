---
title: "在 BizTalk Server 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters
- adapters, about adapters
- adapters, list of BizTalk adapters
- adapters, features
ms.assetid: 8fd279fb-2c68-4de4-a586-5a8e42a685ff
caps.latest.revision: "48"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d65d7304547df50ac14128717526fa7d55880775
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="adapters-in-biztalk-server"></a>BizTalk Server 中的配接器
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的其中一個主要目標是用以協助交易夥伴之間的商業文件交換。 為了協助符合此目標，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含數個配接器，使用普遍認可的資料通訊協定和文件格式，來提供 BizTalk Server 與交易夥伴之間的連繫。 本主題將討論何謂配接器，以及您為何要使用配接器。  
  
## <a name="what-is-an-adapter"></a>何謂配接器？  
 配接器是一種軟體元件，可讓您在 BizTalk Server 上透過傳遞機制輕易地將訊息傳送出去或接收進來，這個傳遞機制符合普遍認可的標準，例如 SMTP、POP3、FTP 或是 Microsoft Message Queuing (MSMQ)。 由於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的開發，對於可快速連接常用應用程式與技術的配接器需求也隨之提高。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]包含下列配接器，稱為 「 原生 」 或 「 整合式 」 配接器： 檔案、 FTP、 HTTP、 MQSeries、 MSMQ、 POP3、 SMTP、 SOAP、 Windows Sharepoint Services 和七個 WCF 配接器 （Wcf-wshttp、 Wcf-basichttp、 Wcf-nettcp、 Wcf-netmsmq，WCF-NetNamedPipe、 Wcf-custom 和 Wcf-customisolated)。 原生配接器會隨 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一起安裝。 您也可以使用 BizTalk 配接器架構，為特定解決方案建立自訂配接器。  
  
 每個原生配接器都會與一個接收位置關聯，這個接收位置是設計來聆聽來自某個位址之某個傳輸的訊息。 在接收位置收到訊息後，它會傳遞給配接器。 配接器會將資料流附加到訊息 (通常是在訊息的內文部分)、新增任何與接收資料之結束點相關的中繼資料，然後將該訊息提交至「BizTalk 傳訊引擎」。  
  
 依照預設，當您執行「BizTalk 組態精靈」時，精靈會安裝原生配接器，並以預設組態為每個配接器建立配接器處理常式。  
  
 使用 BizTalk Server 管理主控台，您可以修改配接器處理常式的預設組態，以及新增、移除和修改配接器的傳送埠和接收位置。 如需有關這些程序的詳細資訊，請參閱＜另請參閱＞中的適當主題。  
  
## <a name="why-use-an-adapter"></a>為何要使用配接器？  
 使用配接器可大幅簡化在 BizTalk Server 上傳送和接收訊息的傳輸。 若您現有基礎結構所使用的傳輸有對應的 BizTalk 配接器，則在 BizTalk Server 上傳送或接收訊息的程序，會與設定適當的配接器以使用對應的傳輸機制來傳送或接收訊息一樣簡單。  
  
## <a name="summary-of-functionality-supported-by-biztalk-native-adapters"></a>BizTalk 原生配接器支援的功能摘要  
 下表列出每個原生配接器的主要優點，以及配接器是否提供下列功能：  
  
-   **交易支援。** 在分散式交易協調器 (DTC) 交易環境下傳送及接收文件的功能。 此為維護已排序之訊息傳遞所需的必要功能，並用以保證文件並未重複或遺失。  
  
-   **雙向通訊支援 （要求/回應或請求/回應）。** 傳送文件和處理來自目的地之回應訊息，或是接收文件與傳送回應訊息至來源的功能。  
  
-   **依序接收支援。** 將接收的文件按照接收文件的相同順序發佈到 BizTalk MessageBox 資料庫。  
  
-   **已啟用 SSO。** 以配接器傳送或接收文件時，使用 SSO 驗證的功能。  
  
-   **裝載處理序**執行配接器的程序。 *BizTalk IP* BTSNTSvc.exe 處理序內執行時*IIS OOP*在 Internet Information Server (IIS) 處理序中的 BizTalk Server 處理序之外執行。  
  
|配接器|主要優點|交易支援|雙向通訊支援|依序接收支援|已啟用 SSO|主控處理序|  
|-------------|---------------------|-------------------------|------------------------------------|-------------------------------|-----------------|---------------------|  
|檔案|易於使用。|否|否|否|否|BizTalk IP|  
|FTP|廣泛應用於 B2B 通訊。|否|否|否|是|BizTalk IP|  
|HTTP(S)|廣泛應用於 B2B 通訊。|否|要求/回應和請求/回應|否|是|IIS OOP|  
|SOAP|支援 Web 服務的使用。|否|要求/回應和請求/回應|否|是|IIS OOP|  
|MSMQ|支援 BizTalk Server 與 Microsoft Message Queuing 之間保證僅一次的訊息傳遞。|是|否|是|否|BizTalk IP|  
|MQ 系列|支援 BizTalk Server 與 IBM WebSphere MQ for Windows 平台之間保證僅一次的訊息傳遞。|是|否|是|是|BizTalk IP|  
|Windows SharePoint Services|允許 BizTalk Server 與 SharePoint 文件庫之間彼此交換 XML 和二進位訊息。|否|否|否|否|BizTalk IP|  
|POP3|支援透過電子郵件接收文件。|否|否|否|否|BizTalk IP|  
|SMTP|支援透過電子郵件傳送文件。|否|否|否|否|BizTalk IP|  
|Custom|支援您的系統。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|BizTalk IP|  
|WCF-WSHttp|支援透過 HTTP 傳輸的 WS-* 標準。|是，WsHTTP 支援交易 (僅限 WS-Transaction)|要求/回應和請求/回應|否|是|IIS OOP|  
|WCF-BasicHttp|與 ASMX 架構的 Web 服務和用戶端，以及與其他符合使用 HTTP 或 HTTPS 之 WS-I 基本設定檔 1.1 的服務進行通訊。|否|要求/回應和請求/回應|否|是|IIS OOP|  
|WCF-NetTcp|支援透過 TCP 傳輸的 WS-* 標準。|是|要求/回應和請求/回應|否|是|BizTalk IP|  
|WCF-NetMsmq|支援佇列，利用 Microsoft Message Queuing (MSMQ) 做為傳輸。|是|否|是|是|BizTalk IP|  
|WCF-NetNamedPipe|在同一部機器上提供跨處理序通訊的快速傳輸 (僅適用 WCF 應用程式)。|是|要求/回應和請求/回應|否|是|BizTalk IP|  
|WCF-Custom|啟用使用 WCF 擴充性功能。|是的。|是的。|是，只要繫結支援它即可。|是的。|BizTalk IP|  
|WCF-CustomIsolated|啟用透過 HTTP 傳輸使用 WCF 擴充性功能。|是的。|是的。|資料分割|是的。|IIS OOP|  
  
## <a name="line-of-business-adapters"></a>商務營運系統配接器  
 以下是 Microsoft 提供的「主要商務」(LOB) 配接器清單。  
  
|配接器|Description|支援的版本|  
|-------------|-----------------|------------------------|  
|PeopleSoft Enterprise|允許在 BizTalk Server 和 PeopleSoft 系統之間的元件介面 (CI) 訊息交換。|[支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards OneWorld XE|允許在 BizTalk Server 和 JD Edwards OneWorld 系統之間的商務功能訊息交換。|[支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards EnterpriseOne|允許在 BizTalk Server 和 JD Edwards EnterpriseOne 系統之間的商務功能訊息交換。|[支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Rendezvous|允許在 BizTalk Server 和 TIBCO Rendezvous 之間的 XML 和二進位資料格式訊息交換。|[支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Enterprise Message Service|允許在 BizTalk Server 和提供緊密整合及可靠應用程式基礎結構之 TIBCO EMS 伺服器之間的 XML 及二進位資料格式訊息交換。|[支援的特定業務 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
  
 您也可以使用 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] 隨附的配接器連接至各種企業營運系統。 如需有關[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱[http://go.microsoft.com/fwlink/p/?LinkID=188849](http://go.microsoft.com/fwlink/p/?LinkID=188849)  
  
## <a name="see-also"></a>另請參閱  
 [保護配接器的最佳作法](../core/best-practices-for-securing-adapters.md)   
 [建立和刪除配接器處理常式](../core/creating-and-deleting-adapter-handlers.md)   
 [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)