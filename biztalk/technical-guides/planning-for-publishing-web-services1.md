---
title: "發佈 Web Services1 規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b571c3aa-874b-43f7-af2e-5a71113a93dd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f5b2b5daa3c8e91c603b2bd410acb7edc624413
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-publishing-web-services"></a>規劃發佈 Web 服務
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]為 Web 服務提供內建支援。 它可讓您重複使用和彙總協調流程內現有的 Web 服務。  
  
 您也可以發佈 （公開） 您的協調流程為 Web 服務以區隔 Web 服務邏輯與商務程序邏輯，可讓您更新或取代，但沒有碰觸用於 Web 服務邏輯的程式碼所需的商務邏輯。 這項功能稱為 「 實作 」 模組化程式碼 」。 一般公認的最佳作法是盡可能實作模組化的程式碼。 發佈 Web 服務需要您啟用 Web 服務，以及將協調流程或結構描述發佈為 Web 服務，使用 BizTalk Web 服務發佈精靈。  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實作支援透過 SOAP 配接器使用 Web 服務中的原生配接器。 原生配接器支援提供 Web 服務的擴充性、容錯和追蹤功能，且無須撰寫任何程式碼。 如需有關 SOAP 配接器的詳細資訊，請參閱[SOAP 配接器](http://go.microsoft.com/fwlink/?LinkId=155754)(http://go.microsoft.com/fwlink/?LinkId=155754)。  
  
 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]提供 Windows Azure AppFabric 服務匯流排端點為 WCF 服務發佈的 BizTalk 應用程式的支援。 如需詳細資訊，請參閱[使用 AppFabric Connect 服務](../technical-guides/planning-for-publishing-web-services1.md#BKMK_AFCS)。  
  
 Web 服務的規劃可以分成兩個類別，規劃發佈 Web 服務，以及規劃使用 Web 服務。 本主題說明發佈 Web 服務所應遵循的步驟。  
  
## <a name="enabling-web-services"></a>啟用 Web 服務  
 若要發佈 Web 服務，您必須設定 Internet Information Services (IIS)、BizTalk 外掛式主控件，以及 Windows 使用者和群組帳戶。 本節提供有關啟用 web 服務的概觀。 如需有關啟用 Web 服務的詳細資訊，請參閱 IIS 文件。  
  
### <a name="internet-information-services-70"></a>Internet Information Services 7.0  
 您可以發佈 Web 服務來安裝 IIS 7.0 或更高版本使用 ASP.NET 2.0 設定的 Windows 系統。 IIS 7.0 的所有 Web 服務都執行 ASP.NET 工作者處理序內。  
  
 IIS 7.0 使用 IIS 應用程式集區處理 Web 服務要求。 IIS 7.0 支援多個應用程式集區和每個應用程式集區處理序可以在不同的使用者內容下執行。  
  
### <a name="biztalk-isolated-hosts"></a>BizTalk 外掛式主控件  
 若要啟用 Web 服務，您必須建立至少一個外掛式主控的件，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 外掛式主控的件代表外部處理序，例如 ISAPI 擴充程式及 BizTalk Server 不會建立或控制 ASP.NET 處理序。 這些類型的外部處理序必須裝載特定配接器，例如 HTTP/S 和 SOAP。  
  
 BizTalk Server 組態管理員會建立 BizTalkServerIsolatedHost[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用做為預設外掛式主控件。 BizTalk 外掛式主控件使用者群組是與這個主控件相關的 Windows 群組預設名稱。 如需主控件和主控件執行個體的詳細資訊，請參閱[管理 BizTalk 主控件和主控件執行個體](http://go.microsoft.com/fwlink/?LinkID=154191)(http://go.microsoft.com/fwlink/?LinkID=154191)。  
  
 外掛式主控件執行個體只能執行一個配接器。 如果您使用單一外掛式主控件設定 HTTP 和 SOAP 配接器的接收處理常式，則必須建立兩個應用程式集區，讓每個配接器使用一個應用程式集區。  
  
 例如，如果您計劃設定兩個的外掛式主控的件，如下所示：  
  
|外掛式主控的件名稱|接收位置|  
|------------------------|-----------------------|  
|外掛式主控的件 1|HTTP_ReceiveLocation1A<br /><br /> HTTP_ReceiveLocation1B<br /><br /> SOAP_ReceiveLocation1**附註：** **外掛式主控件 1**用於接收 SOAP 和 HTTP 配接器處理常式。|  
|外掛式主控件 2|HTTP_ReceiveLocation2|  
  
 您可以建立四個虛擬目錄，其中每個接收位置，如下所示：  
  
|接收位置|虛擬目錄|  
|----------------------|-----------------------|  
|HTTP_ReceiveLocation1A|IIS_Virtual_Directory1A|  
|HTTP_ReceiveLocation1B|IIS_Virtual_Directory1B|  
|SOAP_ReceiveLocation1|IIS_Virtual_Directory1C|  
|HTTP_ReceiveLocation2|IIS_Virtual_Directory2|  
  
 則必須建立至少三個虛擬目錄的應用程式集區，如下所示：  
  
> [!NOTE]  
>  您必須至少為每一個外掛式主控件建立一個應用程式集區。  
  
|虛擬目錄|應用程式集區|Description|  
|-------------------------|----------------------|-----------------|  
|IIS_Virtual_Directory1A<br /><br /> IIS_Virtual_Directory1B|AppPool_Host1_HTTP|您不需要其他應用程式集區，因為所有接收位置都有相同的外掛式主控件 (外掛式主控件 1)，和相同的通訊協定。|  
|IIS_Virtual_Directory1C|AppPool_Host1_SOAP|您不需要其他應用程式集區，因為接收位置使用的通訊協定 (SOAP) 與同一主控件 (外掛式主控件 1) 中其他接收位置不同。|  
|IIS_Virtual_Directory2|AppPool_Host2_HTTP|您需要另一個應用程式集區，因為接收位置不是在外掛式主控件 1 下執行。|  
  
 當您建立您的應用程式集區，請牢記下列要點：  
  
-   您必須將應用程式集區的使用者帳戶加入適當的本機或網域群組的外掛式主控件。 如需詳細資訊，請參閱[Windows 群組和 BizTalk Server 中的使用者帳戶](http://go.microsoft.com/fwlink/?LinkId=155755)(http://go.microsoft.com/fwlink/?LinkId=155755)。  
  
-   您必須根據上表，在外掛式主控件執行個體與對應的應用程式集區之間對應使用者帳戶。 如需外掛式主控的件執行個體和應用程式集區的使用者帳戶之間的關聯性的詳細資訊，請參閱[如何變更服務帳戶和密碼](http://go.microsoft.com/fwlink/?LinkId=155756)(http://go.microsoft.com/fwlink/?LinkId=155756)。  
  
-   IIS 5.0 和 Windows 2000 Server 或 Windows XP 中的 IIS 5.1 沒有應用程式集區。 如果您使用 IIS 5.0 和 5.1，設定 IIS 虛擬目錄的隔離等級**高**。 這樣做將會為每一個虛擬目錄建立不同的 COM+ 應用程式。 每個 COM+ 應用程式將會使用自己的 dllhost.exe 執行。  
  
### <a name="database-access-for-single-server-installations"></a>單一伺服器安裝的資料庫存取  
 如果 BizTalk Server 和 BizTalk 管理資料庫位於相同的伺服器，您應該將 ASP.NET 工作者處理序或 IIS 應用程式集區的使用者內容設定本機 ASPNET 使用者帳戶，或擁有最低權限的本機或網域使用者帳戶。  
  
### <a name="database-access-for-multiple-server-installations"></a>多個伺服器安裝的資料庫存取  
 如果 BizTalk Server 和 BizTalk 管理資料庫位於不同的伺服器上，您應該為網域使用者帳戶變更 ASP.NET 工作者處理序或 IIS 應用程式集區的使用者內容。  
  
 實作多重伺服器部署時，外掛式主控件 Windows 群組必須存在於 BizTalk 資料庫伺服器所屬的網域。  
  
### <a name="minimizing-account-privileges-and-user-rights"></a>最小化帳戶權限和使用者權限  
 請使用外掛式主控件，將與 BizTalk Server 互動時所需最低限度資源的存取權限，賦予給在外部處理序中執行的配接器。 更安全的部署，您應該給予使用者內容外部處理序最小權限。  
  
### <a name="security-recommendations-for-biztalk-web-services-publishing-wizard"></a>BizTalk Web 服務發佈精靈的安全性建議  
 BizTalk Web 服務發佈精靈建立的虛擬目錄將繼承父系虛擬目錄或網站的存取控制清單 (ACL) 和驗證需求。 如果父系虛擬目錄或網站允許匿名存取，則 BizTalk Web 服務發佈精靈將在建立虛擬目錄時移除該功能。  
  
### <a name="enabling-aspnet-40-for-published-web-services"></a>啟用 ASP.NET 4.0 的已發佈的 Web 服務  
 若要啟用 ASP.NET 4.0 已發佈的 Web 服務，請參閱[如何發佈 Web 服務啟用 ASP.NET 4.0](http://go.microsoft.com/fwlink/?LinkId=155758) (http://go.microsoft.com/fwlink/?LinkId=155758)。  
  
## <a name="using-the-biztalk-web-services-publishing-wizard"></a>使用 BizTalk Web 服務發佈精靈  
 如需協調流程發佈為 Web 服務的詳細資訊，請參閱[協調流程發佈為 Web 服務](http://go.microsoft.com/fwlink/?LinkId=155761)(http://go.microsoft.com/fwlink/?LinkId=155761)。  
  
 為 Web 服務發佈結構描述的相關資訊，請參閱[發佈為 Web 服務的結構描述](http://go.microsoft.com/fwlink/?LinkId=155762)(http://go.microsoft.com/fwlink/?LinkId=155762)。  
  
##  <a name="BKMK_AFCS"></a>使用 AppFabric Connect 服務  
 如需有關 BizTalk 應用程式發佈為 WCF 服務與 Windows Azure AppFabric 服務匯流排端點請參閱[使用 AppFabric Connect 服務在雲端上的 BizTalk 應用程式公開](http://go.microsoft.com/fwlink/?LinkID=204700)(http://go.microsoft.com/fwlink/ 嗎？LinkID = 204700)。  
  
## <a name="planning-for-publishing-wcf-services"></a>規劃發佈 WCF 服務  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]導入了內建支援的 Windows Communication Foundation (WCF)。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]可讓您重複使用和彙總所有現有的 WCF 服務協調流程中。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]也實作 WCF 服務中原生配接器的支援。 原生配接器支援為 WCF 服務提供擴充性、容錯和追蹤功能，您無須撰寫任何程式碼。 WCF 配接器的相關資訊，請參閱[WCF 配接器](http://go.microsoft.com/fwlink/?LinkId=155763)(http://go.microsoft.com/fwlink/?LinkId=155763)。  
  
 如需有關規劃中的 WCF 服務[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[發佈 WCF 服務](http://go.microsoft.com/fwlink/?LinkId=155764)(http://go.microsoft.com/fwlink/?LinkId=155764)。  
  
## <a name="see-also"></a>另請參閱  
 [規劃使用 Web 服務](../technical-guides/planning-for-consuming-web-services.md)