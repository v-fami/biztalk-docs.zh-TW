---
title: "發行服務中繼資料之 wcf 接收配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- publishing, WCF services
- WCF services, publishing
ms.assetid: 4df09e8f-e0c9-41c5-bd71-13bb0e96cd97
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b8a15ab9258c9212c2fa6fdd6557227f534a86c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="publishing-service-metadata-for-the-wcf-receive-adapters"></a>發佈 WCF 接收配接器的服務中繼資料
您可以使用「BizTalk WCF 服務發佈精靈」建立 WCF 服務，以發佈現有 WCF 接收位置的服務中繼資料。 若要從已發行中繼資料文件產生用戶端服務模型程式碼中，您可以使用隨附的 Service Model Metadata Utility 工具 (SvcUtil.exe) [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]軟體開發套件 (SDK) for[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]和[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]執行階段元件。  
  
> [!NOTE]
>  發佈 WCF 配接器的服務中繼資料之前，您必須建立 WCF 接收位置使用 BizTalk 管理主控台或 BTSTask 命令列工具隨附[!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。 如需有關如何建立 WCF 接收位置，請參閱中的每個 WCF 配接器的適當主題[WCF 配接器](../core/wcf-adapters.md)。  
  
 **IIS 版本**  
  
 發佈服務中繼資料的 WCF 服務可以在以下作業系統的下列 Internet Information Services (IIS) 版本上執行：  
  
-   **Windows Vista、 Windows Server 2008 SP2 和 Windows Server 2008 R2 上的 IIS 7.0/7.5。** IIS 7.0/7.5 提供與 IIS 6.0 相同的進階的處理模型。 已發佈的 BizTalk WCF 服務必須執行在 ASP.NET 相容性模式的 IIS 7.0/7.5。 WCF 接收配接器發佈的 Web 應用程式在 IIS 7.0/7.5 中的服務中繼資料可透過 HTTP 傳輸存取。  
  
 **發行服務中繼資料的 WCF 接收位置**  
  
 若要發佈 WCF 接收位置的服務中繼資料，您必須使用「BizTalk WCF 服務發佈精靈」建立 Web 應用程式，以裝載提供服務中繼資料的 WCF 服務。 這樣可允許以 WCF 服務的形式呼叫接收位置。  「BizTalk WCF 服務發佈精靈」會在所建立 Web 應用程式的根資料夾中產生下列檔案：  
  
|檔案|資料夾|Description|  
|----------|------------|-----------------|  
|WCF 服務 (.svc 檔案)|\|發佈 WCF 接收位置之服務中繼資料的 WCF 服務。 WCF 服務會使用 HTTP/GET 要求發佈服務中繼資料以供擷取。|  
|Web.config|\|ASP.NET 組態檔，其中包含 ASP.NET Web 應用程式行為、已發佈的 WCF 服務行為、中繼資料端點以及 BizTalk 相關設定的資訊。 精靈會產生 Web.config 時**httpGetEnabled**屬性 **\<serviceMetadata\>** 元素設定為**true**。 您可以在開發環境中使用中繼資料匯入工具 (例如 SvcUtil.exe) 產生呼叫此服務所需的用戶端程式碼。 中繼資料發行的位址是 WCF 服務的端點位址加上一個**？ wsdl**查詢字串。 **注意：** BizTalk WCF 發佈精靈所產生的預設中繼資料繫結並不安全，它允許匿名存取中繼資料。 服務中繼資料包含關於服務的詳細描述，因此可能會在有意或無意之間包含機密資訊。 若要防止未經授權存取服務中繼資料，您可以修改 Web.config，為中繼資料結束點使用安全繫結。|  
|ServiceDescription.xml|\|描述已發佈之 WCF 服務合約 (包括訊息類型) 的 XML 檔案。|  
|BizTalk 結構描述 (.xsd 檔案)|\App_Data|定義 XML 執行個體訊息結構的 XML 結構描述，在 WCF 接收位置中使用。|  
|SchemaIndex.xml|\App_Data|表示在 WCF 接收位置中使用之 XML 結構描述檔案的 XML 檔案。|  
|Serialization.xsd|\App_Data|XML 結構描述所匯出[DataContractSerializer](http://go.microsoft.com/fwlink/?LinkId=81722)類型、 項目和命名空間中，屬性 http://schemas.microsoft.com/2003/10/Serialization/。|  
|BindingInfo.xml|\App_Data\Temp|可由開發命令列工具或精靈匯入的 BizTalk 繫結檔案，以設定接收位置。 已發佈的 WCF 服務不會在執行階段使用此檔案和 Temp 資料夾。|  
|WcfServiceDescription.xml|\App_Data\Temp|摘要描述您搭配「BizTalk WCF 服務發佈精靈」來建立此 Web 應用程式之設定的 XML 檔案。 已發佈的 WCF 服務不會在執行階段使用此檔案和 Temp 資料夾。|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何使用 BizTalk WCF 服務發佈精靈來發佈 WCF 接收位置的內容為基礎的路由服務中繼資料](../core/publish-service-metadata-for-a-wcf-receive-location-for-content-based-routing.md)  
  
-   [如何使用 BizTalk WCF 服務發佈精靈發佈之 WCF 接收位置的服務中繼資料繫結至協調流程連接埠](../core/publish-receive-location-service-metadata-biztalk-wcf-service-publishing-wizard.md)  
  
## <a name="see-also"></a>請參閱  
 [逐步解說：使用 WCF-NetMsmq 配接器發佈 WCF 服務](../core/walkthrough-publishing-wcf-services-with-the-wcf-netmsmq-adapter.md)