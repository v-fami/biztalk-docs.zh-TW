---
title: 在 BizTalk Server 中的配接器 |Microsoft Docs
description: 在 BizTalk Server，包括內建配接器、 企業配接器，以及 BizTalk Adapter Pack 中所有可用的配接器的完整清單
ms.custom: ''
ms.date: 06/22/2018
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8fd279fb-2c68-4de4-a586-5a8e42a685ff
caps.latest.revision: 48
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f19ecce5c7068f7218d9189a6dffd19e76d6211
ms.sourcegitcommit: e7609c319b64ec20bf215d17aa5ac4f9dcae52ec
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36945537"
---
# <a name="adapters-in-biztalk-server"></a>BizTalk Server 中的配接器
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的其中一個主要目標是用以協助交易夥伴之間的商業文件交換。 為了協助符合此目標，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含數個配接器，使用普遍認可的資料通訊協定和文件格式，來提供 BizTalk Server 與交易夥伴之間的連繫。 本主題將討論何謂配接器，以及您為何要使用配接器。  
  
## <a name="what-is-an-adapter"></a>何謂配接器？  
 配接器是一種軟體元件，可讓您在 BizTalk Server 上透過傳遞機制輕易地將訊息傳送出去或接收進來，這個傳遞機制符合普遍認可的標準，例如 SMTP、POP3、FTP 或是 Microsoft Message Queuing (MSMQ)。 由於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的開發，對於可快速連接常用應用程式與技術的配接器需求也隨之提高。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 包含下列配接器，稱為 「 原生 」 或 「 整合式 」 配接器： 檔案、 FTP、 HTTP、 MQSeries、 MSMQ、 POP3、 SMTP、 SOAP、 Windows Sharepoint Services 和七個 WCF 配接器 （Wcf-wshttp、 Wcf-basichttp、 Wcf-nettcp、 Wcf-netmsmq，WCF-NetNamedPipe、 Wcf-custom 和 Wcf-customisolated)。 原生配接器會隨 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 一起安裝。 您也可以使用 BizTalk 配接器架構，為特定解決方案建立自訂配接器。  
  
 每個原生配接器都會與一個接收位置關聯，這個接收位置是設計來聆聽來自某個位址之某個傳輸的訊息。 在接收位置收到訊息後，它會傳遞給配接器。 配接器會將資料流附加到訊息 (通常是在訊息的內文部分)、新增任何與接收資料之結束點相關的中繼資料，然後將該訊息提交至「BizTalk 傳訊引擎」。  
  
 依照預設，當您執行「BizTalk 組態精靈」時，精靈會安裝原生配接器，並以預設組態為每個配接器建立配接器處理常式。  
  
 使用 BizTalk Server 管理主控台，您可以修改配接器處理常式的預設組態，以及新增、移除和修改配接器的傳送埠和接收位置。 如需有關這些程序的詳細資訊，請參閱＜另請參閱＞中的適當主題。  
  
## <a name="why-use-an-adapter"></a>為何要使用配接器？  
 使用配接器可大幅簡化在 BizTalk Server 上傳送和接收訊息的傳輸。 若您現有基礎結構所使用的傳輸有對應的 BizTalk 配接器，則在 BizTalk Server 上傳送或接收訊息的程序，會與設定適當的配接器以使用對應的傳輸機制來傳送或接收訊息一樣簡單。  
  
## <a name="functionality-support-in-built-in-adapters"></a>內建配接器中的功能支援  
 下表列出每個原生配接器的主要優點，以及配接器是否提供下列功能：  
  
-   **交易支援**： 能夠傳送和接收的分散式的交易協調器 (DTC) 交易內容下的文件。 此為維護已排序之訊息傳遞所需的必要功能，並用以保證文件並未重複或遺失。  
  
-   **雙向通訊支援 （要求/回應或請求/回應）** ： 能夠傳送文件，並處理來自目的地的回應訊息或接收文件，並將回應訊息傳送至來源。  
  
-   **依序接收支援**： 能夠將收到的文件發佈到 BizTalk MessageBox 資料庫所接收的文件的正確順序。  
  
-   **已啟用 SSO** ： 使用 SSO 驗證傳送或接收配接器的文件時的能力。  
  
-   **裝載處理序**： 執行配接器的程序。 *BizTalk IP*執行在 BTSNTSvc.exe 處理序中，雖然*IIS OOP* Internet Information Server (IIS) 處理序中的 BizTalk Server 程序之外執行。  
  
|配接器|主要優點|交易支援|雙向通訊支援|依序接收支援|已啟用 SSO|主控處理序|  
|---|---|---|---|---|---|---|  
|Custom|支援您的系統。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|是的，需要自訂程式碼。|BizTalk IP|  
|檔案|易於使用。|否|否|否|否|BizTalk IP|  
|FTP|廣泛應用於 B2B 通訊。|否|否|否|是|BizTalk IP|  
|HTTP(S)|廣泛應用於 B2B 通訊。|否|要求/回應和請求/回應|否|是|IIS OOP|  
|MSMQ|支援 BizTalk Server 與 Microsoft Message Queuing 之間保證僅一次的訊息傳遞。|是|否|是|否|BizTalk IP|  
|邏輯應用程式| 接收和傳送至 Azure 邏輯應用程式。 在內部部署和雲端環境中，使用此配接器來存取許多 Azure 服務 | 是 | 取決於您的工作流程設計 | 否 | 否 |接收： BizTalk IP<br/>傳送： IIS OOP| 
|MQ 系列|支援 BizTalk Server 與 IBM WebSphere MQ for Windows 平台之間保證僅一次的訊息傳遞。|是|否|是|是|BizTalk IP|  
|Office 365 的郵件 | 接收和傳送電子郵件到 Office 365 | | 否 | 否，為了接收 | 否 | BizTalk IP| 
|Office 365 行事曆 | 接收和 Office 365 中建立事件 | | 否 | 否，為了接收 | 否 | BizTalk IP| 
|Office 365 連絡人 | 在 Office 365 中建立連絡人 | | 否 | 否，為了接收 | 否 | BizTalk IP| 
|POP3|支援透過電子郵件接收文件。|否|否|否|否|BizTalk IP|  
|SMTP|支援透過電子郵件傳送文件。|否|否|否|否|BizTalk IP|  
|SOAP|支援 Web 服務的使用。|否|要求/回應和請求/回應|否|是|IIS OOP|  
|Windows SharePoint Services|允許 BizTalk Server 與 SharePoint 文件庫之間彼此交換 XML 和二進位訊息。|否|否|否|否|BizTalk IP| 
|WCF-WSHttp|支援透過 HTTP 傳輸的 WS-* 標準。|是，WsHTTP 支援交易 (僅限 WS-Transaction)|要求/回應和請求/回應|否|是|IIS OOP|  
|WCF-BasicHttp|與 ASMX 架構的 Web 服務和用戶端，以及與其他符合使用 HTTP 或 HTTPS 之 WS-I 基本設定檔 1.1 的服務進行通訊。|否|要求/回應和請求/回應|否|是|IIS OOP|  
|WCF-NetTcp|支援透過 TCP 傳輸的 WS-* 標準。|是|要求/回應和請求/回應|否|是|BizTalk IP|  
|WCF-NetMsmq|支援佇列，利用 Microsoft Message Queuing (MSMQ) 做為傳輸。|是|否|是|是|BizTalk IP|  
|WCF-NetNamedPipe|在同一部機器上提供跨處理序通訊的快速傳輸 (僅適用 WCF 應用程式)。|是|要求/回應和請求/回應|否|是|BizTalk IP|  
|WCF-Custom|啟用使用 WCF 擴充性功能。|是|是|是，只要繫結支援它即可。|是|BizTalk IP|  
|WCF-CustomIsolated|啟用透過 HTTP 傳輸使用 WCF 擴充性功能。|是|是|否|是|IIS OOP|  
  
## <a name="enterprise-adapters"></a>企業配接器  
 以下是 Microsoft 提供的「主要商務」(LOB) 配接器清單。  
  
|配接器|描述|支援的版本|  
|---|---|---|  
|PeopleSoft Enterprise|允許在 BizTalk Server 和 PeopleSoft 系統之間的元件介面 (CI) 訊息交換。|[支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards OneWorld XE|允許在 BizTalk Server 和 JD Edwards OneWorld 系統之間的商務功能訊息交換。|[支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|JD Edwards EnterpriseOne|允許在 BizTalk Server 和 JD Edwards EnterpriseOne 系統之間的商務功能訊息交換。|[支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Rendezvous|允許在 BizTalk Server 和 TIBCO Rendezvous 之間的 XML 和二進位資料格式訊息交換。|[支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  
|TIBCO Enterprise Message Service|允許在 BizTalk Server 和提供緊密整合及可靠應用程式基礎結構之 TIBCO EMS 伺服器之間的 XML 及二進位資料格式訊息交換。|[支援的營運 (LOB) 和企業系統](http://social.technet.microsoft.com/wiki/contents/articles/17631.biztalk-server-supported-line-of-business-lob-and-enterprise-systems.aspx)|  

## <a name="biztalk-adapter-pack"></a>BizTalk 配接器封包  
 您也可以使用 [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)] 隨附的配接器連接至各種企業營運系統。 如需詳細資訊[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]，請參閱 < [BizTalk Adapter Pack](../adapters-and-accelerators/biztalk-adapter-pack.md)。
  
## <a name="see-also"></a>另請參閱  
 [保護配接器的最佳做法](../core/best-practices-for-securing-adapters.md)   
 [建立和刪除配接器處理常式](../core/creating-and-deleting-adapter-handlers.md)   
 [實作企業單一登入](../core/implementing-enterprise-single-sign-on.md)