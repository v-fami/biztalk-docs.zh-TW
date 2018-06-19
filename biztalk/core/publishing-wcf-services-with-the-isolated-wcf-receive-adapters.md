---
title: 發佈 WCF 服務，利用外掛式 WCF 接收配接器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- receive adapters, WCF services
- publishing, WCF services
- WCF services, receive adapters
- WCF services, publishing
ms.assetid: 62ebf373-075c-4c98-8130-ac2cf06e4a70
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c5305560713771e7279eb013d26ff267aa21a74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271630"
---
# <a name="publishing-wcf-services-with-the-isolated-wcf-receive-adapters"></a>利用外掛式 WCF 接收配接器發佈 WCF 服務
BizTalk Windows Communication Foundation (WCF) 配接器允許[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與 WCF 架構的應用程式通訊。 BizTalk WCF 配接器包含七個實體配接器。 除了 WCF-CustomIsolated 配接器之外，每個配接器均包含傳送與接收配接器。  
  
 WCF 接收配接器會提供兩種類型的配接器： 隔離 WCF 配接器和內含式 WCF 配接器。 雖然內含式配接器是由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理，但外掛式配接器不會由 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 具現化， 而是在另一個處理序中具現化及裝載。 外掛式 WCF 配接器裝載於 Internet Information Services (IIS) 中執行的 Web 應用程式。  
  
> [!NOTE]
>  在使用外掛式 WCF 配接器來發佈 WCF 服務之前，您應該要先清楚如何在 Internet Information Services (IIS) 中裝載 WCF 服務。 在 IIS 中裝載 WCF 服務的詳細資訊，請參閱 < 裝載於 IIS >，網址[http://go.microsoft.com/fwlink/?LinkID=75700](http://go.microsoft.com/fwlink/?LinkID=75700)。  
  
 **IIS 版本**  
  
 有三種外掛式 WCF 配接器 (WCF-CustomIsolated、WCF-BasicHttp 與 WCF-WSHttp) 可裝載於以下作業系統的下列 IIS 版本：  
  
-   **在 Windows Vista 和 Windows Server 2008 上的 IIS 7.0/7.5。** IIS 7.0/7.5 提供與 IIS 6.0 相同的進階的處理模型。 已發佈的 BizTalk WCF 服務必須執行在 ASP.NET 相容性模式的 IIS 7.0/7.5。  
  
> [!NOTE]
>  雖然 IIS 7.0/7.5 中的 Windows 處理序啟用服務 (WAS) 允許透過 HTTP 以外的通訊協定進行啟用和網路通訊，但外掛式 WCF 配接器只支援 HTTP 傳輸。  
  
 **外掛式的 WCF 配接器**  
  
 以下是外掛式 WCF 配接器的清單：  
  
-   **Wcf-wshttp 配接器**。 提供透過 HTTP 傳輸的 WS-* 標準支援。 WCF-WSHttp 配接器會實作下列規格：外部應用程式和 MessageBox 資料庫之間的交易式互動適用的 WS-Transaction，以及訊息安全性和驗證適用的 WS-Security。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是「文字」或「訊息傳輸最佳化機制」(Message Transmission Optimization Mechanism，MTOM) 編碼。  
  
-   **Wcf-basichttp 配接器**。 與 ASMX 架構 Web 服務和用戶端，以及其他符合 WS-I 基本設定檔 1.1 的服務進行通訊。 傳輸方式是 HTTP 或 HTTPS，訊息編碼方式則是「文字」或 MTOM 編碼。  
  
-   **Wcf-customisolated 配接器**。 啟用透過 HTTP 傳輸使用 WCF 擴充性功能。 這個配接器讓您能夠針對在外掛式主控件中執行的接收位置，選取和設定 WCF 繫結和行為資訊。  
  
 **使用外掛式 WCF 配接器發佈 WCF 服務**  
  
 若要使用外掛式 WCF 接收配接器發佈 WCF 服務，您必須使用「BizTalk WCF 服務發佈精靈」建立 Web 應用程式，以裝載外掛式 WCF 配接器。 此外，「BizTalk WCF 服務發佈精靈」會在所建立 Web 應用程式的根資料夾中產生下列檔案：  
  
|檔案|資料夾|Description|  
|----------|------------|-----------------|  
|WCF 服務 (.svc 檔案)|\|使用外掛式 WCF 配接器發佈之 WCF 接收位置的 WCF 服務。|  
|Web.config|\|ASP.NET 組態檔，其中包含 ASP.NET Web 應用程式行為、已發佈的 WCF 服務行為、中繼資料端點以及 BizTalk 相關設定的資訊。 「BizTalk WCF 發佈精靈」產生的預設中繼資料繫結並不安全，它允許匿名存取中繼資料。 服務中繼資料包含關於服務的詳細描述，因此可能會在有意或無意之間包含機密資訊。 若要防止未經授權存取服務中繼資料，您可以修改 Web.config，為中繼資料結束點使用安全繫結。 **注意：** 並非所有的中繼資料端點繫結和服務端點繫結的組合都有效。 在某些狀況下，中繼資料端點的繫結組態必須與其服務端點的繫結組態一致。 例如，當服務端點的安全性模式依賴 HTTPS 時，中繼資料端點就無法使用需要 HTTP 傳輸的安全性模式設定。|  
|ServiceDescription.xml|\|描述已發佈之 WCF 服務合約 (包括訊息類型) 的 XML 檔案。|  
|BizTalk 結構描述 (.xsd 檔案)|\App_Data|定義 XML 執行個體訊息結構的 XML 結構描述，這會使用外接式 WCF 配接器發佈。|  
|SchemaIndex.xml|\App_Data|表示在發佈的 WCF 服務中使用之 XML 結構描述檔案的 XML 檔案。|  
|Serialization.xsd|\App_Data|XML 結構描述所匯出[DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722)類型、 項目和命名空間中，屬性 http://schemas.microsoft.com/2003/10/Serialization/。|  
|BindingInfo.xml|\App_Data\Temp|建立對應到已發佈 Web 服務之 WCF 接收位置的 BizTalk 繫結檔案。 可由開發指令行工具或精靈匯入 BindingInfo.xml 檔案，以建立必要的接收位置。 已發佈的 WCF 服務不會在執行階段使用此檔案和 Temp 資料夾。|  
|WcfServiceDescription.xml|\App_Data\Temp|摘要描述您搭配「BizTalk WCF 服務發佈精靈」來建立此 Web 應用程式之設定的 XML 檔案。 已發佈的 WCF 服務不會在執行階段使用此檔案和 Temp 資料夾。|  
  
 您也可以使用「BizTalk WCF 服務發佈精靈」，為執行外掛式 WCF 配接器的接收位置建立 WCF 接收位置和服務中繼資料。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何使用 BizTalk WCF 服務發佈精靈協調流程發佈為 WCF 服務](../core/publish-orchestrations-as-wcf-services--biztalk-wcf-service-publishing-wizard.md)  
  
-   [如何使用 BizTalk WCF 服務發佈精靈結構描述發佈為 WCF 服務](../core/publish-schemas-as-wcf-services--use-the-biztalk-wcf-service-publishing-wizard.md)  
  
-   [設定 IIS 的外掛式 WCF 接收配接器](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)  
  
-   [如何設定使用 BizTalk WCF 服務發佈精靈發佈的 WCF 服務](../core/configure-wcf-services-published-with-the-biztalk-wcf-service-publishing-wizard.md)  
  
-   [如何建立.NET 應用程式來測試使用 BizTalk WCF 服務發佈精靈發佈 WCF 服務](../core/use-net-application-to-test-wcf-service-published-with-wcf-service-publishing.md)  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說： 使用發佈 WCF 服務 Wcf-basichttp 配接器](../core/walkthrough-publishing-wcf-services-with-the-wcf-basichttp-adapter.md)