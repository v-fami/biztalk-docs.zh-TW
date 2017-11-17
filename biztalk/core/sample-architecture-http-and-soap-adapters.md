---
title: "範例架構： HTTP 和 SOAP 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, security
- architecture, examples
- SOAP adapters, security
- Web Publishing
- security, examples
- security, architecture
- SOAP adapters, architecture examples
- examples, architecture
- architecture, security
- HTTP adapters, architecture examples
- reverse proxy rules
- ISA Server implementation
- HTTP adapters, security
ms.assetid: 935197d0-5108-4970-b237-3c6d5b40c5e9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dae8be185084a9a838876e3d50b605a63c161b66
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-architecture-http-and-soap-adapters"></a><span data-ttu-id="c63fe-102">範例架構： HTTP 和 SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="c63fe-102">Sample Architecture: HTTP and SOAP Adapters</span></span>
<span data-ttu-id="c63fe-103">當您使用的 HTTP 與 SOAP 配接器傳送和接收訊息時，本主題描述的範例架構。</span><span class="sxs-lookup"><span data-stu-id="c63fe-103">This topic describes the sample architecture when you use the HTTP and SOAP adapters to send and receive messages.</span></span>  
  
 <span data-ttu-id="c63fe-104">下圖顯示使用 HTTP 或 SOAP 配接器時 BizTalk Server 範例架構的元件。</span><span class="sxs-lookup"><span data-stu-id="c63fe-104">The following figure shows the components of the BizTalk Server sample architecture when you use the HTTP or SOAP adapters.</span></span>  
  
 <span data-ttu-id="c63fe-105">**圖 1 顯示 HTTP 或 SOAP 配接器的範例架構**</span><span class="sxs-lookup"><span data-stu-id="c63fe-105">**Figure 1 Sample architecture that shows HTTP or SOAP adapters**</span></span>  
  
 <span data-ttu-id="c63fe-106">![範例 HTTP 或 SOAP 配接器的架構](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")</span><span class="sxs-lookup"><span data-stu-id="c63fe-106">![Sample architecture for HTTP or SOAP adapter](../core/media/tdi-sec-refarch-http.gif "TDI_Sec_RefArch_HTTP")</span></span>  
  
 <span data-ttu-id="c63fe-107">此範例架構包含下列章節所討論的元件。</span><span class="sxs-lookup"><span data-stu-id="c63fe-107">This sample architecture contains the components as discussed in the following sections.</span></span>  
  
## <a name="perimeter-networkinternet"></a><span data-ttu-id="c63fe-108">周邊網路─網際網路</span><span class="sxs-lookup"><span data-stu-id="c63fe-108">Perimeter network―Internet</span></span>  
 <span data-ttu-id="c63fe-109">當您使用的 SOAP 和 HTTP 配接器時，我們建議您使用反向 proxy 規則 （TMG Server 實作稱為 Web 發佈） 訊息到來自網際網路對向防火牆 (防火牆 1) 防火牆協助保護電子商務網域 (防火牆 2)，並從此執行外掛式主控的件的 BizTalk 伺服器防火牆。</span><span class="sxs-lookup"><span data-stu-id="c63fe-109">When you use the SOAP and HTTP adapters, we recommend that you use reverse proxy rules (the TMG Server implementation is called Web Publishing) to relay the message from the Internet-facing firewall (Firewall 1) to the firewall that helps protect the E-Business domain (Firewall 2), and from this firewall to the BizTalk Server that runs the isolated host.</span></span> <span data-ttu-id="c63fe-110">如需 Web 發佈 」 規則的詳細資訊，請參閱 Microsoft 網站，網址[http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-110">For more information about Web Publishing rules, see the Microsoft Web site at [http://go.microsoft.com/fwlink/?LinkID=205340](http://go.microsoft.com/fwlink/?LinkID=205340) (http://go.microsoft.com/fwlink/?LinkID=205340).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c63fe-111">當您使用反向 Proxy 時，周邊網路中就不需要 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="c63fe-111">When you use reverse proxy, you do not need Web servers in the perimeter network.</span></span>  
  
## <a name="perimeter-networkintranet"></a><span data-ttu-id="c63fe-112">周邊網路─內部網路</span><span class="sxs-lookup"><span data-stu-id="c63fe-112">Perimeter network―intranet</span></span>  
 <span data-ttu-id="c63fe-113">公司通常會使用 HTTP 與 SOAP 通訊協定來進行網際網路通訊，因此內部網路周邊網路中不需要任何伺服器來支援此實例。</span><span class="sxs-lookup"><span data-stu-id="c63fe-113">Companies commonly use the HTTP and SOAP protocols for Internet-based communications, and therefore you do not need any servers in the intranet perimeter network to support this scenario.</span></span> <span data-ttu-id="c63fe-114">若您在透過 HTTP 或 SOAP 通訊協定來整合 BizTalk Server 的內部網路中有內部應用程式，就應該遵循針對網際網路周邊網路的建議。</span><span class="sxs-lookup"><span data-stu-id="c63fe-114">If you have an internal application in the intranet that integrates with BizTalk Server through the HTTP or SOAP protocols, you should follow the recommendations for the Internet perimeter network.</span></span>  
  
## <a name="e-business-domain"></a><span data-ttu-id="c63fe-115">電子商務網域</span><span class="sxs-lookup"><span data-stu-id="c63fe-115">E-Business domain</span></span>  
 <span data-ttu-id="c63fe-116">此網域包含 BizTalk Server 實作所使用的所有基礎結構與應用程式。</span><span class="sxs-lookup"><span data-stu-id="c63fe-116">This domain contains all the infrastructure and applications used by your BizTalk Server implementation.</span></span> <span data-ttu-id="c63fe-117">此網域中的伺服器包括：</span><span class="sxs-lookup"><span data-stu-id="c63fe-117">The servers in this domain are:</span></span>  
  
-   <span data-ttu-id="c63fe-118">**BizTalk Server （處理與追蹤主控件）。**</span><span class="sxs-lookup"><span data-stu-id="c63fe-118">**BizTalk Server (processing and tracking hosts).**</span></span> <span data-ttu-id="c63fe-119">此伺服器有 BizTalk Server 執行階段安裝，而且擁有主控件執行個體，其中包含 BizTalk 協調流程、管線、商務規則引擎以及其他商務程序。</span><span class="sxs-lookup"><span data-stu-id="c63fe-119">This server has an installation of the BizTalk Server runtime, and has instances of the hosts that contain the BizTalk orchestrations, pipelines, Business Rule Engine, and other business processes.</span></span> <span data-ttu-id="c63fe-120">此伺服器還有可支援追蹤狀況監控與商務監控資料之主控件的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c63fe-120">This server also has a host instance of a host that supports tracking of health monitoring and business monitoring data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c63fe-121">當您的效能需求增加時，可以為處理主控件的主控件執行個體在環境中加入更多 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="c63fe-121">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your processing hosts.</span></span>  
  
-   <span data-ttu-id="c63fe-122">**BizTalk Server （SOAP 和 HTTP 配接器的外掛式主控件）。**</span><span class="sxs-lookup"><span data-stu-id="c63fe-122">**BizTalk Server (isolated hosts for SOAP and HTTP adapters).**</span></span> <span data-ttu-id="c63fe-123">此伺服器有 BizTalk Server 執行階段的安裝，而且只擁有主控件的執行個體，其中包含 HTTP 與 SOAP 配接器。</span><span class="sxs-lookup"><span data-stu-id="c63fe-123">This server has an installation of the BizTalk Server runtime, and has only instances of the hosts that contain the HTTP and SOAP adapters.</span></span> <span data-ttu-id="c63fe-124">這些主控件會在個別伺服器上執行，因為這些配接器要求您在執行的電腦上安裝網際網路資訊服務 (IIS)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-124">These hosts run in a separate server because these adapters require that you install Internet Information Services (IIS) on the computer where they run.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c63fe-125">當您的效能需求增加時，可以將更多的 BizTalk Server 新增到您的環境中，以做為 HTTP 與 SOAP 配接器主控件的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="c63fe-125">As your performance needs increase, you can add more BizTalk Servers to your environment for host instances of your HTTP and SOAP adapter hosts.</span></span> <span data-ttu-id="c63fe-126">當您如此做時，還必須設定網路負載平衡 (NLB)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-126">When you do this, you must also configure Network Load Balancing (NLB).</span></span> <span data-ttu-id="c63fe-127">如需如何設定 BizTalk Server 高可用性的詳細資訊，請參閱[高可用性規劃](../core/planning-for-high-availability3.md)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-127">For more information about how to configure BizTalk Server for high availability, see [Planning for High Availability](../core/planning-for-high-availability3.md).</span></span>  
  
-   <span data-ttu-id="c63fe-128">**主要密碼伺服器。**</span><span class="sxs-lookup"><span data-stu-id="c63fe-128">**Master secret server.**</span></span> <span data-ttu-id="c63fe-129">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-129">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="c63fe-130">**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="c63fe-130">**SQL Server.**</span></span> <span data-ttu-id="c63fe-131">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-131">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="c63fe-132">**網域控制站。**</span><span class="sxs-lookup"><span data-stu-id="c63fe-132">**Domain controller.**</span></span> <span data-ttu-id="c63fe-133">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-133">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
-   <span data-ttu-id="c63fe-134">**系統管理工具。**</span><span class="sxs-lookup"><span data-stu-id="c63fe-134">**Administration tools.**</span></span> <span data-ttu-id="c63fe-135">中相同[範例架構： 基本 BizTalk Server](../core/sample-architecture-base-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c63fe-135">Same as in the [Sample Architecture: Base BizTalk Server](../core/sample-architecture-base-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c63fe-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c63fe-136">See Also</span></span>  
 <span data-ttu-id="c63fe-137">[小型與中型公司的範例架構](../core/sample-architectures-for-small-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="c63fe-137">[Sample Architectures for Small & Medium-Sized Companies](../core/sample-architectures-for-small-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="c63fe-138">威脅模型分析的範例案例</span><span class="sxs-lookup"><span data-stu-id="c63fe-138">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)