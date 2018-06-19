---
title: 使用 Web 服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services
- Web services, about Web services
- orchestrations, Web services
- Web services, orchestrations
ms.assetid: a54261e3-d8ef-4770-8d9a-147685846051
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 236acb42c010effe5c3d45cde1daaf9a7097ede5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288254"
---
# <a name="using-web-services"></a><span data-ttu-id="afdd8-102">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="afdd8-102">Using Web Services</span></span>
<span data-ttu-id="afdd8-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 提供了 Web 服務的內建支援。</span><span class="sxs-lookup"><span data-stu-id="afdd8-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Web services.</span></span> <span data-ttu-id="afdd8-104">BizTalk Server 可讓您重複使用及彙總協調流程中的所有現有 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afdd8-104">BizTalk Server enables the reuse and aggregation of all your existing Web services within your orchestrations.</span></span> <span data-ttu-id="afdd8-105">您也可以將協調流程發佈 (公開) 為 Web 服務，以區隔 Web 服務邏輯與商務程序邏輯。</span><span class="sxs-lookup"><span data-stu-id="afdd8-105">You can also publish (expose) your orchestrations as Web services to separate the Web service logic from the business process logic.</span></span>  
  
 <span data-ttu-id="afdd8-106">BizTalk Server 實作了 Web 服務原生配接器的支援。</span><span class="sxs-lookup"><span data-stu-id="afdd8-106">BizTalk Server implements support for native adapters in Web services.</span></span> <span data-ttu-id="afdd8-107">原生配接器支援提供 Web 服務的擴充性、容錯和追蹤功能，且無須撰寫任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="afdd8-107">Native adapter support provides scalability, fault tolerance, and tracking capabilities for Web services without writing a single line of code.</span></span> <span data-ttu-id="afdd8-108">SOAP 配接器的相關資訊，請參閱[SOAP 配接器](../core/soap-adapter.md)。</span><span class="sxs-lookup"><span data-stu-id="afdd8-108">For information about the SOAP adapter, see [SOAP Adapter](../core/soap-adapter.md).</span></span>  
  
 <span data-ttu-id="afdd8-109">在 BizTalk Server 中的 Web 服務支援分為兩類： 使用或呼叫 Web 服務以及發佈或建立 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afdd8-109">The Web services support in BizTalk Server falls into two categories: consuming or calling Web services and publishing or creating Web services.</span></span>  
  
 <span data-ttu-id="afdd8-110">使用或發佈 Web 服務之前，您應該先瞭解 ASP.NET 中的 XML Web Service。</span><span class="sxs-lookup"><span data-stu-id="afdd8-110">Before you consume or publish a Web service, you should have an understanding of XML Web services in ASP.NET.</span></span> <span data-ttu-id="afdd8-111">XML Web 服務的基本概念的相關資訊，請參閱文章 < XML Web 服務基本概念 >，網址[http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057)。</span><span class="sxs-lookup"><span data-stu-id="afdd8-111">For information about the basics of XML Web services, see the article "XML Web Services Basics" at [http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057).</span></span>  
  
 <span data-ttu-id="afdd8-112">**使用 Web 服務**</span><span class="sxs-lookup"><span data-stu-id="afdd8-112">**Consuming Web services**</span></span>  
  
 <span data-ttu-id="afdd8-113">您可以從協調流程內使用 (呼叫) Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afdd8-113">You can consume (call) Web services from within an orchestration.</span></span> <span data-ttu-id="afdd8-114">您可以彙總以完成整個商務程序的單一協調流程數個 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afdd8-114">You can aggregate several Web services into single orchestration to complete an entire business process.</span></span>  
  
 <span data-ttu-id="afdd8-115">**發佈 Web 服務**</span><span class="sxs-lookup"><span data-stu-id="afdd8-115">**Publishing Web services**</span></span>  
  
 <span data-ttu-id="afdd8-116">您可以使用 [BizTalk Web 服務發佈精靈] 來發佈 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afdd8-116">You can publish Web services using the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="afdd8-117">協調流程和傳送配接器可以使用這些已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="afdd8-117">Orchestrations and send adapters can use these published Web services.</span></span>  
  
 <span data-ttu-id="afdd8-118">**使用 SOAP 標頭**</span><span class="sxs-lookup"><span data-stu-id="afdd8-118">**Using SOAP headers**</span></span>  
  
 <span data-ttu-id="afdd8-119">BizTalk Server 提供已定義的和未知的 SOAP 標頭支援。</span><span class="sxs-lookup"><span data-stu-id="afdd8-119">BizTalk Server provides support for defined and unknown SOAP headers.</span></span> <span data-ttu-id="afdd8-120">BizTalk Server 會為 Web 服務內每個已定義的 SOAP 標頭建立內容屬性。</span><span class="sxs-lookup"><span data-stu-id="afdd8-120">BizTalk Server creates a context property for each defined SOAP header in the Web service.</span></span>  
  
 <span data-ttu-id="afdd8-121">**Web 服務標準**</span><span class="sxs-lookup"><span data-stu-id="afdd8-121">**Web Services standards**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="afdd8-122">應該與任何 Web 服務標準，在傳送和接收合作。</span><span class="sxs-lookup"><span data-stu-id="afdd8-122"> should work with any Web Services standards when sending and receiving.</span></span> <span data-ttu-id="afdd8-123">並非所有的標準已經過測試。</span><span class="sxs-lookup"><span data-stu-id="afdd8-123">Not all standards have been tested.</span></span> <span data-ttu-id="afdd8-124">一般而言，透過 WCF 支援的標準也支援[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="afdd8-124">Typically, the standards supported by WCF are also supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="afdd8-125">標準範例包括：</span><span class="sxs-lookup"><span data-stu-id="afdd8-125">Sample standards include:</span></span>  
  
-   <span data-ttu-id="afdd8-126">Ws-reliablemessaging</span><span class="sxs-lookup"><span data-stu-id="afdd8-126">WS-ReliableMessaging</span></span>  
  
-   <span data-ttu-id="afdd8-127">WS-Security</span><span class="sxs-lookup"><span data-stu-id="afdd8-127">WS-Security</span></span>  
  
-   <span data-ttu-id="afdd8-128">Ws-secureconversation</span><span class="sxs-lookup"><span data-stu-id="afdd8-128">WS-SecureConversation</span></span>  
  
-   <span data-ttu-id="afdd8-129">Ws-trust</span><span class="sxs-lookup"><span data-stu-id="afdd8-129">WS-Trust</span></span>  
  
-   <span data-ttu-id="afdd8-130">WS-同盟</span><span class="sxs-lookup"><span data-stu-id="afdd8-130">WS-Federation</span></span>  
  
-   <span data-ttu-id="afdd8-131">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="afdd8-131">WS-Addressing</span></span>  
  
-   <span data-ttu-id="afdd8-132">WS 原則</span><span class="sxs-lookup"><span data-stu-id="afdd8-132">WS-Policy</span></span>  
  
-   <span data-ttu-id="afdd8-133">Ws-metadataexchange</span><span class="sxs-lookup"><span data-stu-id="afdd8-133">WS-MetadataExchange</span></span>  
  
-   <span data-ttu-id="afdd8-134">Ws-coordination</span><span class="sxs-lookup"><span data-stu-id="afdd8-134">WS-Coordination</span></span>  
  
-   <span data-ttu-id="afdd8-135">Ws-atomic</span><span class="sxs-lookup"><span data-stu-id="afdd8-135">WS-Atomic</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="afdd8-136">本節內容</span><span class="sxs-lookup"><span data-stu-id="afdd8-136">In This Section</span></span>  
  
-   [<span data-ttu-id="afdd8-137">使用 Web 服務</span><span class="sxs-lookup"><span data-stu-id="afdd8-137">Consuming Web Services</span></span>](../core/consuming-web-services.md)  
  
-   [<span data-ttu-id="afdd8-138">發佈 Web 服務</span><span class="sxs-lookup"><span data-stu-id="afdd8-138">Publishing Web Services</span></span>](../core/publishing-web-services.md)  
  
-   [<span data-ttu-id="afdd8-139">使用 SOAP 標頭</span><span class="sxs-lookup"><span data-stu-id="afdd8-139">Using SOAP Headers</span></span>](../core/using-soap-headers.md)