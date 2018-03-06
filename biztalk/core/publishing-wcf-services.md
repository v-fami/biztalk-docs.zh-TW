---
title: "發佈 WCF 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70b7851b-77c1-4ab3-a61f-e7165ceb56fb
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00136b64d5feaf552f77b92b3ad4442da4e447cc
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="publish-wcf-services"></a>發佈 WCF 服務
協調流程可以發佈為 WCF 服務會由 WCF 用戶端所呼叫的 BizTalk Server 中。  
  
## <a name="publish-wcf-services-with-the-isolated-wcf-adapters"></a>發佈 WCF 服務與外掛式 WCF 配接器 
  
 您要使用「BizTalk WCF 服務發佈精靈」，針對 WCF-BasicHttp 配接器、WCF-WSHttp 配接器和 WCF-CustomIsolated 配接器等外掛式 WCF 配接器來建立和發佈其 WCF 服務。 這樣會建立做為 IIS 中的跨處理序應用程式的接收位置。  
  
 在使用外掛式 WCF 配接器來發佈 WCF 服務之前，您應該要先清楚如何在 Internet Information Services (IIS) 中裝載 WCF 服務。  
  
## <a name="publish-service-metadata-for-the-wcf-receive-locations"></a>WCF 接收位置發佈服務中繼資料
  
 您要使用「BizTalk WCF 服務發佈精靈」，針對已發佈的 WCF 接收位置建立其服務中繼資料。 若要從已發行中繼資料文件產生服務模型用戶端程式碼中，您可以使用隨附的 Windows 軟體開發套件 (SDK) 和.NET Framework 執行階段元件中的 Service Model Metadata Utility 工具 (SvcUtil.exe)。  
  
> [!IMPORTANT]
>  在執行「BizTalk WCF 服務發佈精靈」之前，您必須先啟用 WCF 服務。 如需啟用您的系統的 WCF 服務的詳細資訊，請參閱[外掛式 WCF 接收配接器設定的 IIS](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)。  
  
## <a name="next-steps"></a>後續的步驟
  
-   [利用外掛式 WCF 接收配接器發佈 WCF 服務](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [發佈 WCF 接收配接器的服務中繼資料](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [利用 WCF 接收配接器發佈 WCF 服務時的考量](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [SOAP 標頭與已發佈的 WCF 服務](../core/soap-headers-with-published-wcf-services.md)  
  
-   [從發佈為 WCF 服務的協調流程擲回錯誤例外狀況](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)