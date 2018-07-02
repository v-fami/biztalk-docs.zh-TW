---
title: 使用模式設計： 服務導向解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- patterns [service solutions], examples
- examples, programming patterns
- patterns [service solutions], designing
- designing, programming patterns
ms.assetid: c196cd9d-2b2d-4548-bc7d-26196f7c2878
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32096bfa790f52ab29eed9d4b6b849688c73c922
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970999"
---
# <a name="designing-with-patterns-the-service-oriented-solution"></a><span data-ttu-id="84b48-102">使用模式設計： 服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="84b48-102">Designing with Patterns: the Service Oriented Solution</span></span>
<span data-ttu-id="84b48-103">服務導向解決方案會示範如何將 BizTalk 應用程式公開為供其他應用程式使用的服務。</span><span class="sxs-lookup"><span data-stu-id="84b48-103">The service-oriented solution shows how to expose a BizTalk application as a service for use by other applications.</span></span> <span data-ttu-id="84b48-104">將應用程式當作服務使用，可讓其他應用程式更輕易地使用資訊以及在它們提供的服務中使用資訊。</span><span class="sxs-lookup"><span data-stu-id="84b48-104">Presenting an application as a service enables other applications to easily consume the information and use it in the services that they provide.</span></span> <span data-ttu-id="84b48-105">如需服務介面查看 「 服務介面 」 [ http://go.microsoft.com/fwlink/?LinkId=46185 ](http://go.microsoft.com/fwlink/?LinkId=46185)。</span><span class="sxs-lookup"><span data-stu-id="84b48-105">For more information about service interfaces see "Service Interface" at [http://go.microsoft.com/fwlink/?LinkId=46185](http://go.microsoft.com/fwlink/?LinkId=46185).</span></span> <span data-ttu-id="84b48-106">如需服務導向整合的詳細資訊請參閱 < Service-Oriented Integration 網址[ http://go.microsoft.com/fwlink/?LinkId=46186 ](http://go.microsoft.com/fwlink/?LinkId=46186)。</span><span class="sxs-lookup"><span data-stu-id="84b48-106">For more information about service-oriented integration see "Service-Oriented Integration" at [http://go.microsoft.com/fwlink/?LinkId=46186](http://go.microsoft.com/fwlink/?LinkId=46186).</span></span>  
  
 <span data-ttu-id="84b48-107">解決方案是一個信用資訊應用程式，彙總來自其他三個不同應用程式的相關資訊後，提供資訊做為 Web 服務回應。</span><span class="sxs-lookup"><span data-stu-id="84b48-107">The solution is a credit information application that provides the information as a Web service response, after aggregating relevant information from three other applications.</span></span> <span data-ttu-id="84b48-108">應用程式會合併結果，並傳回包含摘要信用資訊的一個訊息。</span><span class="sxs-lookup"><span data-stu-id="84b48-108">The application consolidates the results and returns a single message containing the summarized credit information.</span></span> <span data-ttu-id="84b48-109">三個後端系統如下：</span><span class="sxs-lookup"><span data-stu-id="84b48-109">The three back-end systems are as follows:</span></span>  
  
- <span data-ttu-id="84b48-110">**SAP 企業系統。**</span><span class="sxs-lookup"><span data-stu-id="84b48-110">**SAP Enterprise System.**</span></span> <span data-ttu-id="84b48-111">SAP 後端提供客戶的整體信用限制。</span><span class="sxs-lookup"><span data-stu-id="84b48-111">The SAP back end provides the customer's overall credit limit.</span></span> <span data-ttu-id="84b48-112">解決方案會與此使用中的 SAP 配接器的後端系統通訊[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="84b48-112">The solution communicates with this backend system using the SAP adapter in [!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)].</span></span>  
  
- <span data-ttu-id="84b48-113">**擱置交易系統。**</span><span class="sxs-lookup"><span data-stu-id="84b48-113">**Pending Transactions System.**</span></span> <span data-ttu-id="84b48-114">暫停交易系統會報告超過帳戶的交易總數。</span><span class="sxs-lookup"><span data-stu-id="84b48-114">The Pending Transactions system reports the total amount of transactions outstanding against the account.</span></span> <span data-ttu-id="84b48-115">解決方案會使用 Microsoft Host Integration Server (HIS) 與 Windows Server 的大型主機通訊。</span><span class="sxs-lookup"><span data-stu-id="84b48-115">The solution uses Microsoft Host Integration Server (HIS) to communicate with the mainframe from Windows Server.</span></span> <span data-ttu-id="84b48-116">解決方案也會使用 HIS 的交易整合器技術。</span><span class="sxs-lookup"><span data-stu-id="84b48-116">It also uses the Transaction Integrator technology of HIS.</span></span> <span data-ttu-id="84b48-117">這些技術可讓系統以 Web 服務的方式與大型主機互動。</span><span class="sxs-lookup"><span data-stu-id="84b48-117">These enable the system to interact with the mainframe as a Web service.</span></span> <span data-ttu-id="84b48-118">BizTalk 協調流程會使用這個 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="84b48-118">The BizTalk orchestration consumes this Web service.</span></span>  
  
- <span data-ttu-id="84b48-119">**付款追蹤系統。**</span><span class="sxs-lookup"><span data-stu-id="84b48-119">**Payment Tracking System.**</span></span> <span data-ttu-id="84b48-120">付款追蹤系統可報告個人上次進行的付款。</span><span class="sxs-lookup"><span data-stu-id="84b48-120">The Payment Tracking system reports the last payment the individual made.</span></span> <span data-ttu-id="84b48-121">這個系統使用 MQSeries。</span><span class="sxs-lookup"><span data-stu-id="84b48-121">This system uses MQSeries.</span></span>  
  
  <span data-ttu-id="84b48-122">如同您回想起的解決方案概觀，您也可以透過 MQSeries 查詢來使用非 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="84b48-122">As you may recall from the overview of the solution, you can also use a non-Web service interface through MQSeries queues.</span></span> <span data-ttu-id="84b48-123">(如需應用程式的一般結構的詳細資訊，請參閱[了解服務導向解決方案](../core/understanding-the-service-oriented-solution.md))。</span><span class="sxs-lookup"><span data-stu-id="84b48-123">(For more information about the general structure of the application, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md)).</span></span> <span data-ttu-id="84b48-124">雖然 Web 服務是建立服務導向架構最常用的方法，但不是所有應用程式都可使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="84b48-124">Although Web services are the most common way to construct service oriented architectures, not all applications can use them.</span></span> <span data-ttu-id="84b48-125">使用 BizTalk Server 解決方案，您可提供除了 Web 服務外，其他的方法讓傳統應用程式來使用服務。</span><span class="sxs-lookup"><span data-stu-id="84b48-125">With BizTalk Server solutions you can provide, along with Web services, alternate ways for legacy applications to use the service.</span></span>  
  
  <span data-ttu-id="84b48-126">MQSeries 存取可模擬傳統互動式語音回應系統可能會使用解決方案的作法。</span><span class="sxs-lookup"><span data-stu-id="84b48-126">The MQSeries access simulates how a legacy interactive voice response system might use the solution.</span></span> <span data-ttu-id="84b48-127">MQSeries 存取加上 Web 服務存取，可示範一個解決方案如何被傳統應用程式及新應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="84b48-127">The MQSeries access, along with the Web service access, shows how a single solution can be used by both legacy applications and new applications.</span></span>  
  
## <a name="patterns-used-in-the-service-oriented-solution"></a><span data-ttu-id="84b48-128">服務導向解決方案使用的模式</span><span class="sxs-lookup"><span data-stu-id="84b48-128">Patterns Used in the Service Oriented Solution</span></span>  
 <span data-ttu-id="84b48-129">下圖顯示服務導向解決方案中簡易的模式版本。</span><span class="sxs-lookup"><span data-stu-id="84b48-129">The following diagram shows a simplified version of the patterns in the service-oriented solution.</span></span>  
  
 <span data-ttu-id="84b48-130">![服務&#45;導向解決方案模式](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")</span><span class="sxs-lookup"><span data-stu-id="84b48-130">![Service&#45;Oriented Solution Patterns](../core/media/service-oriented-solution-patterns.gif "Service_Oriented_Solution_Patterns")</span></span>  
  
 <span data-ttu-id="84b48-131">解決方案包含四個主要部分，每一個都代表一種模式： 服務介面、 以內容為基礎的路由器、 收件者的清單和彙總工具。</span><span class="sxs-lookup"><span data-stu-id="84b48-131">The solution consists of four main parts, each of which represents a pattern: the service interface, a content-based router, a recipient list, and an aggregator.</span></span> <span data-ttu-id="84b48-132">服務介面代表連線到解決方案的介面機制。</span><span class="sxs-lookup"><span data-stu-id="84b48-132">The service interface represents the interface mechanism that makes it possible to connect to the solution.</span></span> <span data-ttu-id="84b48-133">內容型路由器會檢查訊息的有效性，若訊息無效則會傳送錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="84b48-133">The content-based router checks the validity of the message and sends an error message if it is invalid.</span></span> <span data-ttu-id="84b48-134">收件者清單會將訊息傳送給三個後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="84b48-134">The recipient list sends the message to the three back-end applications.</span></span> <span data-ttu-id="84b48-135">後端應用程式回應時，彙總程式會將回應結合為單一的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="84b48-135">As the back-end applications respond, the aggregator combines the responses into a single response message.</span></span> <span data-ttu-id="84b48-136">然後回應訊息會透過服務介面回到要求者。</span><span class="sxs-lookup"><span data-stu-id="84b48-136">The response message goes back to the requester through the service interface.</span></span>  
  
 <span data-ttu-id="84b48-137">請注意，圖表中有許多未指定項目：</span><span class="sxs-lookup"><span data-stu-id="84b48-137">Note that a lot is left unspecified in the diagram:</span></span>  
  
-   <span data-ttu-id="84b48-138">圖表中省略了訊息轉譯程式，解決方案需要它來與外部系統通訊。</span><span class="sxs-lookup"><span data-stu-id="84b48-138">The diagram omits message translators, which are required by the solution in order to communicate with the external systems.</span></span>  
  
-   <span data-ttu-id="84b48-139">圖表未指明如何與後端程序通訊。</span><span class="sxs-lookup"><span data-stu-id="84b48-139">The diagram doesn't specify how to communicate with the back-end processes.</span></span>  
  
-   <span data-ttu-id="84b48-140">圖表也未指明服務介面的本質。</span><span class="sxs-lookup"><span data-stu-id="84b48-140">The diagram also does not specify the nature of the service interface.</span></span>  
  
-   <span data-ttu-id="84b48-141">圖表未指出要不要使用同步或非同步通訊。</span><span class="sxs-lookup"><span data-stu-id="84b48-141">Nor does the diagram indicate whether or not to use synchronous or asynchronous communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84b48-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84b48-142">See Also</span></span>  
 <span data-ttu-id="84b48-143">[開發服務導向解決方案](../core/developing-a-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="84b48-143">[Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="84b48-144">轉譯模式的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="84b48-144">Translating the Patterns of the Service Oriented Solution</span></span>](../core/translating-the-patterns-of-the-service-oriented-solution.md)