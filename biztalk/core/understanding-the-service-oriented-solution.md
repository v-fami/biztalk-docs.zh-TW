---
title: "瞭解服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, background information
- service solutions, about service solutions
- service solution tutorial, about service solution tutorial
- Service Oriented Architecture (SOA)
ms.assetid: 56a2ad90-74bb-489a-ab1d-900f3bea3d64
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8be3a1e7a05c2c60f1ab16c6da4df74dddf7adb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-the-service-oriented-solution"></a><span data-ttu-id="74470-102">瞭解服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="74470-102">Understanding the Service Oriented Solution</span></span>
<span data-ttu-id="74470-103">服務導向解決方案提供以服務方式設計的信用結餘報告應用程式。</span><span class="sxs-lookup"><span data-stu-id="74470-103">The service oriented solution presents a credit balance reporting application designed as a service.</span></span> <span data-ttu-id="74470-104">接著應用程式會使用三個以服務方式公開的後端應用程式，來取得信用結餘所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="74470-104">The application, in turn, uses three backend applications, exposed as services themselves, to get the information needed for the credit balance.</span></span>  
  
 <span data-ttu-id="74470-105">「服務導向架構」(SOA) 是一種與建立分散系統部分重疊的方式。</span><span class="sxs-lookup"><span data-stu-id="74470-105">A Service Oriented Architecture (SOA) is an approach that partially overlaps building distributed systems.</span></span> <span data-ttu-id="74470-106">服務導向方法具有一些特色：</span><span class="sxs-lookup"><span data-stu-id="74470-106">A service-oriented approach has several characteristics:</span></span>  
  
-   <span data-ttu-id="74470-107">鬆散耦合。</span><span class="sxs-lookup"><span data-stu-id="74470-107">Loosely coupled.</span></span> <span data-ttu-id="74470-108">應用程式的商務邏輯與處理服務的邏輯是分開的。</span><span class="sxs-lookup"><span data-stu-id="74470-108">The application's business logic is separate from the logic of handling the service.</span></span>  
  
-   <span data-ttu-id="74470-109">可搜尋的。</span><span class="sxs-lookup"><span data-stu-id="74470-109">Discoverable.</span></span> <span data-ttu-id="74470-110">應該要有一個應用程式用以尋找服務的機制。</span><span class="sxs-lookup"><span data-stu-id="74470-110">There should be a mechanism for applications to find the service.</span></span>  
  
-   <span data-ttu-id="74470-111">合約。</span><span class="sxs-lookup"><span data-stu-id="74470-111">Contractual.</span></span> <span data-ttu-id="74470-112">服務的介面會在使用者與服務之間實作合約。</span><span class="sxs-lookup"><span data-stu-id="74470-112">The interface to the service implements the contract between users and the service.</span></span>  
  
 <span data-ttu-id="74470-113">雖然文獻上通常會將服務導向方法視為與 Web 服務相同，但是它們不全然相同。</span><span class="sxs-lookup"><span data-stu-id="74470-113">Although the literature often treats service oriented approaches as synonymous with web services, they are not necessarily synonyms.</span></span> <span data-ttu-id="74470-114">Web 服務為實作服務導向解決方案提供一個有效的方法，但您仍可使用其他技術 (例如 .NET 遠端) 來建立服務。</span><span class="sxs-lookup"><span data-stu-id="74470-114">Web services present an attractive way to implement service oriented solutions, but you can use other technologies, such as .NET remoting, to create services.</span></span>  
  
 <span data-ttu-id="74470-115">如需服務導向架構的詳細資訊，請參閱 < Service Interface"網址[http://go.microsoft.com/fwlink/?LinkId=46185](http://go.microsoft.com/fwlink/?LinkId=46185)以及 < Service-Oriented Integration 在[http://go.microsoft.com/fwlink/?LinkId=46186](http://go.microsoft.com/fwlink/?LinkId=46186)。</span><span class="sxs-lookup"><span data-stu-id="74470-115">For more information about service oriented architectures, see "Service Interface" at [http://go.microsoft.com/fwlink/?LinkId=46185](http://go.microsoft.com/fwlink/?LinkId=46185) and "Service-Oriented Integration" at [http://go.microsoft.com/fwlink/?LinkId=46186](http://go.microsoft.com/fwlink/?LinkId=46186).</span></span>  
  
## <a name="reader-guidance"></a><span data-ttu-id="74470-116">使用指南</span><span class="sxs-lookup"><span data-stu-id="74470-116">Reader Guidance</span></span>  
 <span data-ttu-id="74470-117">此解決方案的文件假設您已熟悉[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="74470-117">The documentation for this solution assumes that you are familiar with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="74470-118">它也假設您瞭解企業應用程式整合與 Web 服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="74470-118">It also assumes that you understand basic concepts about enterprise application integration and web services.</span></span>  
  
 <span data-ttu-id="74470-119">此外，若要閱讀和依照開發人員文件，您應該熟悉如何使用建置應用程式[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]且具有執行下列工作： 建立專案、 設定參考，以及偵錯和測試 BizTalk解決方案。</span><span class="sxs-lookup"><span data-stu-id="74470-119">In addition, to read and follow the developer documentation, you should be familiar with how to build applications by using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and with performing the following tasks: creating projects, setting references, and debugging and testing BizTalk solutions.</span></span>  
  
## <a name="credit-card-reporting-at-woodgrove-bank"></a><span data-ttu-id="74470-120">Woodgrove 銀行的信用卡報告</span><span class="sxs-lookup"><span data-stu-id="74470-120">Credit Card Reporting at Woodgrove Bank</span></span>  
 <span data-ttu-id="74470-121">服務導向架構解決方案是 Woodgrove 銀行的信用卡結餘報告服務。</span><span class="sxs-lookup"><span data-stu-id="74470-121">The service oriented architecture solution is a credit card balance reporting service for Woodgrove Bank.</span></span> <span data-ttu-id="74470-122">雖然此銀行是虛構的，不過此實例是根據實際已部署的客戶應用程式所設計。</span><span class="sxs-lookup"><span data-stu-id="74470-122">Although the bank is fictional, the scenario is not—the scenario is based on an actual, deployed, customer application.</span></span>  
  
 <span data-ttu-id="74470-123">在此實例中，信用卡結餘的要求有兩個來源：</span><span class="sxs-lookup"><span data-stu-id="74470-123">In the scenario, requests for credit card balances come from two sources:</span></span>  
  
-   <span data-ttu-id="74470-124">互動語音回應 (IVR) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="74470-124">An Interactive Voice Response (IVR) application.</span></span>  
  
-   <span data-ttu-id="74470-125">像網頁或自訂用戶端應用程式等互動式用戶端。</span><span class="sxs-lookup"><span data-stu-id="74470-125">An interactive client such as a web page or custom client application.</span></span>  
  
 <span data-ttu-id="74470-126">解決方案會透過 MQSeries 接收 IVR 應用程式的要求。</span><span class="sxs-lookup"><span data-stu-id="74470-126">The solution receives requests from the IVR application through MQSeries.</span></span> <span data-ttu-id="74470-127">它會使用 HTTP 與 SOAP，透過 Web 服務來處理互動式用戶端的要求。</span><span class="sxs-lookup"><span data-stu-id="74470-127">It handles requests from the interactive client through a web service using HTTP and SOAP.</span></span>  
  
 <span data-ttu-id="74470-128">新的服務導向架構應用程式通常需要與使用較舊技術的舊應用程式一起運作，以及與使用 Web 服務的網站等現有的應用程式一起運作。</span><span class="sxs-lookup"><span data-stu-id="74470-128">New service oriented architecture applications often need to work with legacy applications that use older technologies, as well as function with modern applications such as web sites that consume web services.</span></span> <span data-ttu-id="74470-129">此實例仿造此真實世界需求：IVR 應用程式代表舊的應用程式，而客戶服務用戶端應用程式則是現有的應用程式。</span><span class="sxs-lookup"><span data-stu-id="74470-129">The scenario models this real world requirement—the IVR application represents a legacy application, while the customer service client application, is the modern one.</span></span>  
  
 <span data-ttu-id="74470-130">Woodgrove 銀行的應用程式會使用來自三個舊後端系統的資料來回應要求：</span><span class="sxs-lookup"><span data-stu-id="74470-130">The Woodgrove Bank application uses data from three backend, legacy systems to respond to requests:</span></span>  
  
-   <span data-ttu-id="74470-131">提供整個信用限制的應用程式。</span><span class="sxs-lookup"><span data-stu-id="74470-131">An application that provides the overall credit limit.</span></span> <span data-ttu-id="74470-132">這是主機電腦上的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="74470-132">This is a SAP system on a mainframe computer.</span></span>  
  
-   <span data-ttu-id="74470-133">擱置交易系統，會報告根據帳戶所擱置的交易總量。</span><span class="sxs-lookup"><span data-stu-id="74470-133">A pending transactions system that reports the total amount for transactions pending against the account.</span></span> <span data-ttu-id="74470-134">此系統是主機或 AS/400 系統。</span><span class="sxs-lookup"><span data-stu-id="74470-134">This system is a mainframe or AS/400 system.</span></span> <span data-ttu-id="74470-135">解決方案會使用 Web 服務和 Microsoft Host Integration Server (HIS)，與主機或 AS/400 系統通訊。</span><span class="sxs-lookup"><span data-stu-id="74470-135">The solution uses a web service and Microsoft Host Integration Server (HIS) to communicate with the mainframe or AS/400 system.</span></span>  
  
-   <span data-ttu-id="74470-136">付款交易系統，會提供對系統所做的最後付款。</span><span class="sxs-lookup"><span data-stu-id="74470-136">A payment tracking system that gives the last payment made to the system.</span></span> <span data-ttu-id="74470-137">可使用 MQSeries，抵達付款追蹤系統。</span><span class="sxs-lookup"><span data-stu-id="74470-137">The payment tracking system can be reached using MQSeries.</span></span>  
  
 <span data-ttu-id="74470-138">從舊系統收集和編譯資訊之後，解決方案會將回應傳送回原始應用程式，因此會傳回給客戶。</span><span class="sxs-lookup"><span data-stu-id="74470-138">After gathering and compiling the information from the legacy systems, the solution sends the response back to the originating application and, thus, to the customer.</span></span>  
  
## <a name="business-requirements"></a><span data-ttu-id="74470-139">商務需求</span><span class="sxs-lookup"><span data-stu-id="74470-139">Business Requirements</span></span>  
 <span data-ttu-id="74470-140">因為信用報告應用程式會即時回應客戶要求，所以它的延遲必須很短才能快速處理要求。</span><span class="sxs-lookup"><span data-stu-id="74470-140">Because the credit reporting application responds in real time to customer requests, it must have low latency in order to handle requests quickly.</span></span> <span data-ttu-id="74470-141">此外，它也必須處理很高的同時要求數。</span><span class="sxs-lookup"><span data-stu-id="74470-141">In addition, it must also be able to handle high numbers of simultaneous requests.</span></span> <span data-ttu-id="74470-142">解決方案會使用機密資訊與公用介面，因此安全性是一項重要議題。</span><span class="sxs-lookup"><span data-stu-id="74470-142">The solution uses sensitive information and a public interface so that security is significant concern.</span></span> <span data-ttu-id="74470-143">最後，服務必須是可靠的。</span><span class="sxs-lookup"><span data-stu-id="74470-143">Finally, the service needs to be reliable.</span></span>  
  
 <span data-ttu-id="74470-144">如需解決方案如何符合這些需求的資訊，請參閱[開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="74470-144">For information about how the solution meets these requirements, see [Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md).</span></span>  
  
## <a name="performance-characteristics"></a><span data-ttu-id="74470-145">效能特色</span><span class="sxs-lookup"><span data-stu-id="74470-145">Performance Characteristics</span></span>  
 <span data-ttu-id="74470-146">為了符合商業需求，實例具有下列效能特色：</span><span class="sxs-lookup"><span data-stu-id="74470-146">To meet the business requirements, the scenario has the following performance characteristics:</span></span>  
  
-   <span data-ttu-id="74470-147">每秒 40 個內送要求的可維持輸送量。</span><span class="sxs-lookup"><span data-stu-id="74470-147">Sustained throughput of 40 incoming requests per second.</span></span>  
  
-   <span data-ttu-id="74470-148">每秒 100 個內送要求的尖峰輸送量。</span><span class="sxs-lookup"><span data-stu-id="74470-148">Peak throughput of 100 incoming requests per second.</span></span>  
  
-   <span data-ttu-id="74470-149">在 1000 毫秒之下，可服務 (BizTalk Server 內外) 90% 的要求。</span><span class="sxs-lookup"><span data-stu-id="74470-149">90 percent of the requests to be serviced (in and out of BizTalk Server) in under 1000 milliseconds.</span></span>  
  
-   <span data-ttu-id="74470-150">在 2000 毫秒之下，可服務 (BizTalk Server 內外) 95% 的要求。</span><span class="sxs-lookup"><span data-stu-id="74470-150">95 percent of the requests to be serviced (in and out of BizTalk Server) in under 2000 milliseconds.</span></span>  
  
-   <span data-ttu-id="74470-151">在 5000 毫秒之下，可服務 (BizTalk Server 內外) 100% 的要求。</span><span class="sxs-lookup"><span data-stu-id="74470-151">100 percent of the requests to be serviced (in and out of BizTalk Server) in under 5000 milliseconds.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74470-152">這些時間不包括後端系統的延遲時間。</span><span class="sxs-lookup"><span data-stu-id="74470-152">These times do not include the latency times of the back end systems.</span></span>  
  
## <a name="three-versions-of-the-solution"></a><span data-ttu-id="74470-153">解決方案的三個版本</span><span class="sxs-lookup"><span data-stu-id="74470-153">Three Versions of the Solution</span></span>  
 <span data-ttu-id="74470-154">解決方案有三個版本：</span><span class="sxs-lookup"><span data-stu-id="74470-154">There are three versions of the solution:</span></span>  
  
-   <span data-ttu-id="74470-155">虛設常式版本會以軟體虛設常式取代所有的後端系統。</span><span class="sxs-lookup"><span data-stu-id="74470-155">The stub version replaces all of the backend systems with software stubs.</span></span> <span data-ttu-id="74470-156">虛設常式會模擬後端系統。</span><span class="sxs-lookup"><span data-stu-id="74470-156">The stubs simulate the backend systems.</span></span> <span data-ttu-id="74470-157">這個版本提供在單一電腦上部署和執行解決方案的快速方式。</span><span class="sxs-lookup"><span data-stu-id="74470-157">This version provides a quick way to deploy and run the solution on a single computer.</span></span>  
  
-   <span data-ttu-id="74470-158">配接器版本會使用 BizTalk 配接器，連線至後端系統。</span><span class="sxs-lookup"><span data-stu-id="74470-158">The adapter version uses BizTalk adapters to connect to the backend systems.</span></span> <span data-ttu-id="74470-159">這個版本是某些人實作解決方案時可能會先考慮的方式。</span><span class="sxs-lookup"><span data-stu-id="74470-159">This version is how one might first think to implement the solution.</span></span> <span data-ttu-id="74470-160">不過，使用配接器將訊息傳送回後端系統，會在傳回回應時產生明顯的延遲。</span><span class="sxs-lookup"><span data-stu-id="74470-160">However, sending messages to the backend systems using the adapters introduces significant latency in getting back responses.</span></span> <span data-ttu-id="74470-161">雖然配接器本身的延遲時間很短，但是 BizTalk Server 的分散式架構需要配接器使用訊息方塊，與協調流程主控件執行個體進行通訊。</span><span class="sxs-lookup"><span data-stu-id="74470-161">While adapters by themselves could offer very low latency, the distributed architecture of BizTalk Server requires adapters to communicate with the orchestration host instances using the message box.</span></span> <span data-ttu-id="74470-162">這將造成需往返資料庫，並影響延遲時間。</span><span class="sxs-lookup"><span data-stu-id="74470-162">This introduces round trips to the database and affects latency times.</span></span>  
  
-   <span data-ttu-id="74470-163">內嵌版本會以直接與後端系統通訊的內嵌程式碼取代配接器。</span><span class="sxs-lookup"><span data-stu-id="74470-163">The inline version replaces the adapters with inline code that communicates directly with the backend systems.</span></span> <span data-ttu-id="74470-164">解決方案的內嵌版本具有最低的延遲與最高的傳送量。</span><span class="sxs-lookup"><span data-stu-id="74470-164">The inline version of the solution has the lowest latency and the highest throughput.</span></span>  
  
 <span data-ttu-id="74470-165">部署指南為建立和部署解決方案的所有三個版本提供指引，並在每個版本中提供一個方法，以便對擱置的交易系統模擬透過 HIS 的連線。</span><span class="sxs-lookup"><span data-stu-id="74470-165">The deployment guide provides directions for building and deploying all three versions of the solution, as well as providing a way, in each version, to simulate the connection through HIS to the pending transactions system.</span></span> <span data-ttu-id="74470-166">建置和部署方案的相關資訊，請參閱[部署服務導向解決方案](../core/deploying-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="74470-166">For information about building and deploying the solution, see [Deploying the Service Oriented Solution](../core/deploying-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74470-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74470-167">See Also</span></span>  
 [<span data-ttu-id="74470-168">服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="74470-168">Service Oriented Solution</span></span>](../core/service-oriented-solution.md)