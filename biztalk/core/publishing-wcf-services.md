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
# <a name="publishing-wcf-services"></a><span data-ttu-id="64108-102">發佈 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="64108-102">Publishing WCF Services</span></span>
<span data-ttu-id="64108-103">協調流程可以發佈為 WCF 服務中[!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會由 WCF 用戶端所呼叫。</span><span class="sxs-lookup"><span data-stu-id="64108-103">An orchestration can be published as a WCF service in [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to be called by WCF clients.</span></span>  
  
 <span data-ttu-id="64108-104">**使用外掛式 WCF 配接器發佈 WCF 服務**</span><span class="sxs-lookup"><span data-stu-id="64108-104">**Publishing WCF services with the isolated WCF adapters**</span></span>  
  
 <span data-ttu-id="64108-105">您要使用「BizTalk WCF 服務發佈精靈」，針對 WCF-BasicHttp 配接器、WCF-WSHttp 配接器和 WCF-CustomIsolated 配接器等外掛式 WCF 配接器來建立和發佈其 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="64108-105">You create and publish WCF services by using the BizTalk WCF Service Publishing Wizard for the isolated WCF adapters such as the WCF-BasicHttp adapter, the WCF-WSHttp adapter, and the WCF-CustomIsolated adapter.</span></span> <span data-ttu-id="64108-106">這樣會建立做為 IIS 中的跨處理序應用程式的接收位置。</span><span class="sxs-lookup"><span data-stu-id="64108-106">This creates a receive location which exists as an out of process application in IIS.</span></span>  
  
 <span data-ttu-id="64108-107">在使用外掛式 WCF 配接器來發佈 WCF 服務之前，您應該要先清楚如何在 Internet Information Services (IIS) 中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="64108-107">Before you publish a WCF service with the isolated WCF adapters, you should have an understanding of how to host WCF services in Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="64108-108">**發行服務中繼資料的 WCF 接收位置**</span><span class="sxs-lookup"><span data-stu-id="64108-108">**Publishing service metadata for the WCF receive locations**</span></span>  
  
 <span data-ttu-id="64108-109">您要使用「BizTalk WCF 服務發佈精靈」，針對已發佈的 WCF 接收位置建立其服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="64108-109">You create service metadata for published WCF receive locations by using the BizTalk WCF Service Publishing Wizard.</span></span> <span data-ttu-id="64108-110">若要從已發行中繼資料文件產生服務模型用戶端程式碼中，您可以使用隨附的 Service Model Metadata Utility 工具 (SvcUtil.exe) [!INCLUDE[btsCoName](../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]軟體開發套件 (SDK) for[!INCLUDE[btsWinVista](../includes/btswinvista-md.md)]和[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]執行階段元件。</span><span class="sxs-lookup"><span data-stu-id="64108-110">To generate service model client code from the published metadata documents you can use the Service Model Metadata Utility tool (SvcUtil.exe) included in the [!INCLUDE[btsCoName](../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] Software Development Kit (SDK) for [!INCLUDE[btsWinVista](../includes/btswinvista-md.md)] and [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Runtime Components.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64108-111">在執行「BizTalk WCF 服務發佈精靈」之前，您必須先啟用 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="64108-111">Before running the BizTalk WCF Service Publishing Wizard, you must enable WCF services.</span></span> <span data-ttu-id="64108-112">如需啟用您的系統的 WCF 服務的詳細資訊，請參閱[外掛式 WCF 接收配接器設定的 IIS](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md)。</span><span class="sxs-lookup"><span data-stu-id="64108-112">For more information about enabling WCF services for your system, see [Configuring IIS for the Isolated WCF Receive Adapters](../core/configuring-iis-for-the-isolated-wcf-receive-adapters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="64108-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="64108-113">In This Section</span></span>  
  
-   [<span data-ttu-id="64108-114">發佈 WCF 服務，利用外掛式 WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="64108-114">Publishing WCF Services with the Isolated WCF Receive Adapters</span></span>](../core/publishing-wcf-services-with-the-isolated-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="64108-115">發行服務中繼資料之 wcf 接收配接器</span><span class="sxs-lookup"><span data-stu-id="64108-115">Publishing Service Metadata for the WCF Receive Adapters</span></span>](../core/publishing-service-metadata-for-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="64108-116">考量發佈 WCF 服務使用 WCF 接收配接器</span><span class="sxs-lookup"><span data-stu-id="64108-116">Considerations When Publishing WCF Services with the WCF Receive Adapters</span></span>](../core/considerations-when-publishing-wcf-services-with-the-wcf-receive-adapters.md)  
  
-   [<span data-ttu-id="64108-117">SOAP 標頭與已發佈的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="64108-117">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)  
  
-   [<span data-ttu-id="64108-118">如何從協調流程發佈為 WCF 服務擲回錯誤例外狀況</span><span class="sxs-lookup"><span data-stu-id="64108-118">How to Throw Fault Exceptions from Orchestrations Published as WCF Services</span></span>](../core/how-to-throw-fault-exceptions-from-orchestrations-published-as-wcf-services.md)