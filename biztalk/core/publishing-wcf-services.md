---
title: "發佈 WCF 服務 |Microsoft 文件"
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
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5f72f2b300738f2e9a1a643e152048b64cf8f55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-wcf-services"></a>發佈 WCF 服務
協調流程可以發佈為 WCF 服務中[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會由 WCF 用戶端所呼叫。  
  
 **使用外掛式 WCF 配接器發佈 WCF 服務**  
  
 您要使用「BizTalk WCF 服務發佈精靈」，針對 WCF-BasicHttp 配接器、WCF-WSHttp 配接器和 WCF-CustomIsolated 配接器等外掛式 WCF 配接器來建立和發佈其 WCF 服務。 這樣會建立做為 IIS 中的跨處理序應用程式的接收位置。  
  
 在使用外掛式 WCF 配接器來發佈 WCF 服務之前，您應該要先清楚如何在 Internet Information Services (IIS) 中裝載 WCF 服務。  
  
 **發行服務中繼資料的 WCF 接收位置**  
  
 您要使用「BizTalk WCF 服務發佈精靈」，針對已發佈的 WCF 接收位置建立其服務中繼資料。 若要從已發行中繼資料文件產生服務模型用戶端程式碼中，您可以使用隨附的 Service Model Metadata Utility 工具 (SvcUtil.exe) [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]軟體開發套件 (SDK) for[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]和[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]執行階段元件。  
  
> [!IMPORTANT]
>  在執行「BizTalk WCF 服務發佈精靈」之前，您必須先啟用 WCF 服務。 如需啟用您的系統的 WCF 服務的詳細資訊，請參閱[外掛式 WCF 接收配接器設定的 IIS](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [發佈 WCF 服務，利用外掛式 WCF 接收配接器](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [發行服務中繼資料之 wcf 接收配接器](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [考量發佈 WCF 服務使用 WCF 接收配接器](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [SOAP 標頭與已發佈的 WCF 服務](../core/soap-headers-with-published-wcf-services.md)  
  
-   [如何從協調流程發佈為 WCF 服務擲回錯誤例外狀況](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)