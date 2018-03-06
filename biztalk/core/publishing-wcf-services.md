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
# <a name="publish-wcf-services"></a><span data-ttu-id="377fe-102">發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="377fe-102">Publish WCF Services</span></span>
<span data-ttu-id="377fe-103">協調流程可以發佈為 WCF 服務會由 WCF 用戶端所呼叫的 BizTalk Server 中。</span><span class="sxs-lookup"><span data-stu-id="377fe-103">An orchestration can be published as a WCF service in BizTalk Server to be called by WCF clients.</span></span>  
  
## <a name="publish-wcf-services-with-the-isolated-wcf-adapters"></a><span data-ttu-id="377fe-104">發佈 WCF 服務與外掛式 WCF 配接器</span><span class="sxs-lookup"><span data-stu-id="377fe-104">Publish WCF services with the isolated WCF adapters</span></span> 
  
 <span data-ttu-id="377fe-105">您要使用「BizTalk WCF 服務發佈精靈」，針對 WCF-BasicHttp 配接器、WCF-WSHttp 配接器和 WCF-CustomIsolated 配接器等外掛式 WCF 配接器來建立和發佈其 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="377fe-105">You create and publish WCF services by using the BizTalk WCF Service Publishing Wizard for the isolated WCF adapters such as the WCF-BasicHttp adapter, the WCF-WSHttp adapter, and the WCF-CustomIsolated adapter.</span></span> <span data-ttu-id="377fe-106">這樣會建立做為 IIS 中的跨處理序應用程式的接收位置。</span><span class="sxs-lookup"><span data-stu-id="377fe-106">This creates a receive location which exists as an out of process application in IIS.</span></span>  
  
 <span data-ttu-id="377fe-107">在使用外掛式 WCF 配接器來發佈 WCF 服務之前，您應該要先清楚如何在 Internet Information Services (IIS) 中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="377fe-107">Before you publish a WCF service with the isolated WCF adapters, you should have an understanding of how to host WCF services in Internet Information Services (IIS).</span></span>  
  
## <a name="publish-service-metadata-for-the-wcf-receive-locations"></a><span data-ttu-id="377fe-108">WCF 接收位置發佈服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="377fe-108">Publish service metadata for the WCF receive locations</span></span>
  
 <span data-ttu-id="377fe-109">您要使用「BizTalk WCF 服務發佈精靈」，針對已發佈的 WCF 接收位置建立其服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="377fe-109">You create service metadata for published WCF receive locations by using the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="377fe-110">若要從已發行中繼資料文件產生服務模型用戶端程式碼中，您可以使用隨附的 Windows 軟體開發套件 (SDK) 和.NET Framework 執行階段元件中的 Service Model Metadata Utility 工具 (SvcUtil.exe)。</span><span class="sxs-lookup"><span data-stu-id="377fe-110">To generate service model client code from the published metadata documents you can use the Service Model Metadata Utility tool (SvcUtil.exe) included in the Windows Software Development Kit (SDK) and .NET Framework Runtime Components.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="377fe-111">在執行「BizTalk WCF 服務發佈精靈」之前，您必須先啟用 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="377fe-111">Before running the BizTalk WCF Service Publishing Wizard, you must enable WCF services.</span></span> <span data-ttu-id="377fe-112">如需啟用您的系統的 WCF 服務的詳細資訊，請參閱[外掛式 WCF 接收配接器設定的 IIS](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="377fe-112">For more information about enabling WCF services for your system, see [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="377fe-113">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="377fe-113">Next steps</span></span>
  
-   [<span data-ttu-id="377fe-114">利用外掛式 WCF 接收配接器發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="377fe-114">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="377fe-115">發佈 WCF 接收配接器的服務中繼資料</span><span class="sxs-lookup"><span data-stu-id="377fe-115">Publishing Service Metadata for the WCF Receive Adapters</span></span>](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="377fe-116">利用 WCF 接收配接器發佈 WCF 服務時的考量</span><span class="sxs-lookup"><span data-stu-id="377fe-116">Considerations When Publishing WCF Services with the WCF Receive Adapters</span></span>](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="377fe-117">SOAP 標頭與已發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="377fe-117">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)  
  
-   [<span data-ttu-id="377fe-118">從發佈為 WCF 服務的協調流程擲回錯誤例外狀況</span><span class="sxs-lookup"><span data-stu-id="377fe-118">Throw Fault Exceptions from Orchestrations Published as WCF Services</span></span>](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)