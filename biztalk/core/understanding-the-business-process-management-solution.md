---
title: 了解商務程序管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solutions, resources
- process management solutions, applications
- process management solution tutorial, background information
- process management solutions, about process management solutions
- applications, process management solutions
ms.assetid: fa6ad8d2-08d7-4770-9394-835f99bfd146
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9759f6521297377b204f0695a511de40d22a830d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287902"
---
# <a name="understanding-the-business-process-management-solution"></a><span data-ttu-id="bc51f-102">瞭解商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="bc51f-102">Understanding the Business Process Management Solution</span></span>
<span data-ttu-id="bc51f-103">本節描述的解決方案會呈現一個實作商務程序管理應用程式的方法。</span><span class="sxs-lookup"><span data-stu-id="bc51f-103">The solution described in this section presents one way to implement a business process management application.</span></span> <span data-ttu-id="bc51f-104">在理想的商務程序管理員中，代表商務程序之解決方案的部分 (商務規則、與特定後端系統通訊、傳送回應訊息)，會與支援程序的基礎結構分開。</span><span class="sxs-lookup"><span data-stu-id="bc51f-104">In an ideal business process manager, the parts of the solution representing the business process—the business rules, communicating with specific backend systems, sending response messages—are separate from the infrastructure supporting the process.</span></span>  
  
 <span data-ttu-id="bc51f-105">在這個解決方案中，Southridge Video 的有線服務訂單系統，商務程序會分割成一連串的階段。</span><span class="sxs-lookup"><span data-stu-id="bc51f-105">In this solution, a cable service ordering system for Southridge Video, the business process is broken into a series of stages.</span></span> <span data-ttu-id="bc51f-106">對於商務規則和後端系統一無所知的訂單管理員，會引導階段的作業。</span><span class="sxs-lookup"><span data-stu-id="bc51f-106">An order manager, which knows nothing about the business rules and backend systems, directs the operation of the stages.</span></span> <span data-ttu-id="bc51f-107">訂單管理員會從訂單仲介接收訂單，而訂單仲介會將訂單引導至數位不同的訂單管理員。</span><span class="sxs-lookup"><span data-stu-id="bc51f-107">The order manager receives orders from an order broker, which can direct orders to several different order managers.</span></span>  
  
 <span data-ttu-id="bc51f-108">這個解決方案充分利用了 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的功能，並顯示了 (但不只是) 使用應用程式內部的訊息來協調應用程式的部分。</span><span class="sxs-lookup"><span data-stu-id="bc51f-108">The solution makes extensive use of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] features and shows, among other things, the use of messages internal to the application for coordinating parts of the application.</span></span>  
  
## <a name="reader-guidance"></a><span data-ttu-id="bc51f-109">使用指南</span><span class="sxs-lookup"><span data-stu-id="bc51f-109">Reader Guidance</span></span>  
 <span data-ttu-id="bc51f-110">這份文件假設您已熟悉 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bc51f-110">This document assumes that you are familiar with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span> <span data-ttu-id="bc51f-111">同時假設您也瞭解企業應用程式整合和 Web 服務的基本概念。</span><span class="sxs-lookup"><span data-stu-id="bc51f-111">It also assumes that you understand basic concepts about enterprise application integration and Web services.</span></span>  
  
 <span data-ttu-id="bc51f-112">此外，若要閱讀和依照開發人員文件，您應該熟悉如何使用建置應用程式[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]且具有執行下列工作： 建立專案、 設定參考，以及偵錯和測試 BizTalk解決方案。</span><span class="sxs-lookup"><span data-stu-id="bc51f-112">In addition, to read and follow the developer documentation, you should be familiar with how to build applications by using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] and with performing the following tasks: creating projects, setting references, and debugging and testing BizTalk solutions.</span></span>  
  
## <a name="ordering-cable-service-from-southridge-video"></a><span data-ttu-id="bc51f-113">排序從 Southridge Video 的有線服務</span><span class="sxs-lookup"><span data-stu-id="bc51f-113">Ordering Cable Service from Southridge Video</span></span>  
 <span data-ttu-id="bc51f-114">商務程序管理解決方案會實作 Southridge Video 的有線服務訂購系統。</span><span class="sxs-lookup"><span data-stu-id="bc51f-114">The business process management solution implements a cable service ordering system for Southridge Video.</span></span> <span data-ttu-id="bc51f-115">客戶撥打電話到服務中心，服務中心內會有客戶服務代表接收訂單並將之輸入訂單系統。</span><span class="sxs-lookup"><span data-stu-id="bc51f-115">Customers phone into a call center where a customer service representative takes the order and enters it into the order system.</span></span> <span data-ttu-id="bc51f-116">下圖顯示透過系統的一般訂單流程：</span><span class="sxs-lookup"><span data-stu-id="bc51f-116">The following diagram shows the general flow of an order through the system:</span></span>  
  
 <span data-ttu-id="bc51f-117">![商務程序管理解決方案工作流程](../core/media/business-process-manager-solution-work-flow.gif "Business_Process_Manager_Solution_Work_Flow")</span><span class="sxs-lookup"><span data-stu-id="bc51f-117">![Business Process Management Solution Work Flow](../core/media/business-process-manager-solution-work-flow.gif "Business_Process_Manager_Solution_Work_Flow")</span></span>  
  
 <span data-ttu-id="bc51f-118">訂單會移至訂單仲介，訂單仲介會將訂單傳送到訂單管理員。</span><span class="sxs-lookup"><span data-stu-id="bc51f-118">Orders go to the order broker, which sends the order on to the order manager.</span></span> <span data-ttu-id="bc51f-119">訂單管理員會以正確的順序來執行處理階段，以處理訂單。</span><span class="sxs-lookup"><span data-stu-id="bc51f-119">The order manager runs the processing stages in the proper sequence to process the order.</span></span> <span data-ttu-id="bc51f-120">請注意，有些類型的錯誤會移至作業中心以進行修正和重新提交，而解決方案會在 SQL Server 資料表中記錄每張訂單的歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="bc51f-120">Notice that some kinds of errors go to an operations center for correction and resubmission, and that the solution records the history of each order in a SQL Server table.</span></span>  
  
 <span data-ttu-id="bc51f-121">下圖說明處理訂單之步驟的概要。</span><span class="sxs-lookup"><span data-stu-id="bc51f-121">The following diagram shows the broad outline of the steps in processing an order.</span></span>  
  
 <span data-ttu-id="bc51f-122">![商務程序管理解決方案順序](../core/media/business-process-manager-solution-sequence.gif "Business_Process_Manager_Solution_Sequence")</span><span class="sxs-lookup"><span data-stu-id="bc51f-122">![Business Process Management Solution Sequence](../core/media/business-process-manager-solution-sequence.gif "Business_Process_Manager_Solution_Sequence")</span></span>  
  
 <span data-ttu-id="bc51f-123">請注意，訂單可以更新，也可以取消。</span><span class="sxs-lookup"><span data-stu-id="bc51f-123">Notice that an order can be updated as well as canceled.</span></span>  
  
## <a name="business-requirements"></a><span data-ttu-id="bc51f-124">商務需求</span><span class="sxs-lookup"><span data-stu-id="bc51f-124">Business Requirements</span></span>  
 <span data-ttu-id="bc51f-125">商務程序管理解決方案是 Southridge Video (有線服務提供者) 訂單系統的範例。</span><span class="sxs-lookup"><span data-stu-id="bc51f-125">The business process management solution is an example of an order system for Southridge Video, a cable service provider.</span></span> <span data-ttu-id="bc51f-126">它會顯示一個在 Microsoft BizTalk Server 中實作程序管理員模式的方法。</span><span class="sxs-lookup"><span data-stu-id="bc51f-126">It shows one way to implement the process manager pattern in Microsoft BizTalk Server.</span></span> <span data-ttu-id="bc51f-127">這個解決方案會使用一個協調流程，透過實作商務程序的兩個附屬協調流程，來管理訂單流程。</span><span class="sxs-lookup"><span data-stu-id="bc51f-127">The solution uses an orchestration to manage the flow of orders through two satellite orchestrations that implement the business process.</span></span> <span data-ttu-id="bc51f-128">這個結構來自解決方案的商務需求，其中包括下列項目：</span><span class="sxs-lookup"><span data-stu-id="bc51f-128">This structure comes out of the solution's business requirements which include the following:</span></span>  
  
-   <span data-ttu-id="bc51f-129">管理商務程序版本的能力</span><span class="sxs-lookup"><span data-stu-id="bc51f-129">Ability to version the business process</span></span>  
  
-   <span data-ttu-id="bc51f-130">處理長時間執行的訂單</span><span class="sxs-lookup"><span data-stu-id="bc51f-130">Process long-running orders</span></span>  
  
-   <span data-ttu-id="bc51f-131">修改或取消仍在處理的訂單 (補充傳遞訂單)</span><span class="sxs-lookup"><span data-stu-id="bc51f-131">Modify or cancel orders that are still being processed (supplement in-flight orders)</span></span>  
  
-   <span data-ttu-id="bc51f-132">避免擱置訂單</span><span class="sxs-lookup"><span data-stu-id="bc51f-132">Avoid suspended orders</span></span>  
  
-   <span data-ttu-id="bc51f-133">透過整個程序追蹤訂單</span><span class="sxs-lookup"><span data-stu-id="bc51f-133">Track orders through the entire process</span></span>  
  
-   <span data-ttu-id="bc51f-134">批次訂單處理</span><span class="sxs-lookup"><span data-stu-id="bc51f-134">Batch order processing</span></span>  
  
-   <span data-ttu-id="bc51f-135">接收來自遠端資料中心的訂單</span><span class="sxs-lookup"><span data-stu-id="bc51f-135">Accept orders from remote data centers</span></span>  
  
-   <span data-ttu-id="bc51f-136">允許不同群組處理訂單處理的部分</span><span class="sxs-lookup"><span data-stu-id="bc51f-136">Allowing different groups to handle parts of the order processing</span></span>  
  
-   <span data-ttu-id="bc51f-137">藉由新增 BizTalk 群組來擴充應用程式</span><span class="sxs-lookup"><span data-stu-id="bc51f-137">Scale the application by adding BizTalk groups</span></span>  
  
-   <span data-ttu-id="bc51f-138">透過遠端將訂單管理員公佈成應用程式伺服器</span><span class="sxs-lookup"><span data-stu-id="bc51f-138">Expose, by remoting, the order manager as an application server</span></span>  
  
 <span data-ttu-id="bc51f-139">Southridge Video 的商務需求產生三部分結構： 訂單仲介、 程序管理員和商務程序本身。</span><span class="sxs-lookup"><span data-stu-id="bc51f-139">The business requirements of Southridge Video produce a three-part structure: an order broker, a process manager, and the business process itself.</span></span> <span data-ttu-id="bc51f-140">Southridge Video 有兩個個別的 IT 群組會涉及此應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc51f-140">Southridge Videohas two separate IT groups involved in the application.</span></span> <span data-ttu-id="bc51f-141">傳訊群組會維護企業傳訊基礎結構，並提供將應用程式連線至該基礎結構的元件。</span><span class="sxs-lookup"><span data-stu-id="bc51f-141">A messaging group maintains the corporate messaging infrastructure and provides the components for connecting applications to that infrastructure.</span></span> <span data-ttu-id="bc51f-142">另一個群組會寫入和維護特定商務程序的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc51f-142">Another group writes and maintains applications for specific business processes.</span></span> <span data-ttu-id="bc51f-143">因此，訂單仲介會與訂單程序管理員和程序階段分開，如此即可由個別的群組來維護。</span><span class="sxs-lookup"><span data-stu-id="bc51f-143">Thus, the order broker is separate from the order process manager and process stages so that it can be maintained by a separate group.</span></span> <span data-ttu-id="bc51f-144">因為訂單仲介是個別的元件，所以它也可以擴充到仲介訂單，並傳到多個程序管理員。</span><span class="sxs-lookup"><span data-stu-id="bc51f-144">Because it is a separate component, the order broker can also be extended to broker orders to multiple process managers.</span></span> <span data-ttu-id="bc51f-145">可能會加入程序管理員以支援新的營業項目，像是 VIP 服務。</span><span class="sxs-lookup"><span data-stu-id="bc51f-145">A process manager might be added to support a new business line, such as VIP service.</span></span>  
  
 <span data-ttu-id="bc51f-146">Southridge Video 訂單是長時間執行的處理序： 有線服務訂單可能需要從一分鐘到一年才能完成。</span><span class="sxs-lookup"><span data-stu-id="bc51f-146">Southridge Video orders are long running processes: a cable order may take anywhere from a minute to a year to complete.</span></span> <span data-ttu-id="bc51f-147">因為 BizTalk 協調流程的執行個體必須執行以完成，這表示協調流程執行個體的存留期間最多為一年。</span><span class="sxs-lookup"><span data-stu-id="bc51f-147">Because an instance of a BizTalk orchestration must run to completion, this means that an orchestration instance could have a lifetime of up to a year.</span></span>  
  
 <span data-ttu-id="bc51f-148">Southridge Video 需要長時間執行程序的架構，該程序允許應用程式元件在訂單處理期間進行變更。</span><span class="sxs-lookup"><span data-stu-id="bc51f-148">Southridge Video needs an architecture for long running processes that allows for application components to change during order processing.</span></span> <span data-ttu-id="bc51f-149">因此，Southridge 會將訂單處理分割成多個階段，如此一來即可使用最新的程序元件來完成訂單。</span><span class="sxs-lookup"><span data-stu-id="bc51f-149">Thus, Southridge divides order processing into multiple stages so that an order can complete using the newest process components.</span></span> <span data-ttu-id="bc51f-150">如需如何判斷階段界限商務程序中的資訊，請參閱[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="bc51f-150">For information about how to determine stage boundaries in a business process, see [Some Design Principles in the Business Process Management Solution](../core/some-design-principles-in-the-business-process-management-solution.md).</span></span>  
  
 <span data-ttu-id="bc51f-151">訂單的長處理時間，在某種程度上也會判斷是否需要變更傳遞訂單。</span><span class="sxs-lookup"><span data-stu-id="bc51f-151">The long processing time for an order also, in part, determines the need to change in-flight orders.</span></span> <span data-ttu-id="bc51f-152">修改訂單是解決方案包含大量中斷系統的原因之一。</span><span class="sxs-lookup"><span data-stu-id="bc51f-152">Modifying orders is one of the reasons that the solution includes an extensive system of interrupts.</span></span> <span data-ttu-id="bc51f-153">這個中斷系統會在訂單完成之前，簡化訂單變更或取消作業。</span><span class="sxs-lookup"><span data-stu-id="bc51f-153">This interrupt system simplifies making order changes or cancellations before they are complete.</span></span> <span data-ttu-id="bc51f-154">這個解決方案會使用 .NET 訊息，在解決方案的功能部分之間進行通訊，以處理中斷。</span><span class="sxs-lookup"><span data-stu-id="bc51f-154">The solution uses .NET messages to communicate between functional parts of the solution to handle interruptions.</span></span>  
  
 <span data-ttu-id="bc51f-155">因為系統有眾多外部相依性，特定作業可以在失敗後重試。</span><span class="sxs-lookup"><span data-stu-id="bc51f-155">Because the system has numerous external dependencies, certain operations can be retried after failure.</span></span> <span data-ttu-id="bc51f-156">例如，若後端系統無法使用，而對其要求逾時，這個解決方案會等候適當的間隔並重試要求。</span><span class="sxs-lookup"><span data-stu-id="bc51f-156">For example, if a backend system is unavailable and a request to it times out, the solution waits an appropriate interval and retries the request.</span></span> <span data-ttu-id="bc51f-157">因為外部系統的連線是透過自訂程式碼，這部分的解決方案會廣泛使用 .NET 反映，以允許重試物件方法。</span><span class="sxs-lookup"><span data-stu-id="bc51f-157">Because connections to external systems are through custom code, this portion of the solution makes extensive use of .NET reflection to allow object methods to be retried.</span></span>  
  
 <span data-ttu-id="bc51f-158">如同解決方案是以實際公司做為基礎一樣，它會假設訂單處理的問題可以由人員在作業群組中處理。</span><span class="sxs-lookup"><span data-stu-id="bc51f-158">The solution assumes, like the real-life company it is based on, that problems with order processing can be handled by people in an operations group.</span></span> <span data-ttu-id="bc51f-159">同理，部分類型的訂單錯誤將傳回給客戶服務代表參考，客戶服務代表可以取消或修正並重新提交訂單。</span><span class="sxs-lookup"><span data-stu-id="bc51f-159">Similarly, some kind of order errors will be referred back to a customer service representative who may cancel or correct and re-submit the order.</span></span>  
  
## <a name="business-process-management-solution-resources"></a><span data-ttu-id="bc51f-160">商務程序管理解決方案資源</span><span class="sxs-lookup"><span data-stu-id="bc51f-160">Business Process Management Solution Resources</span></span>  
 <span data-ttu-id="bc51f-161">閱讀下列文件，以取得有關商務程序管理解決方案的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="bc51f-161">Read the following documents for additional information about the business process management solution.</span></span>  
  
### <a name="business-process-management-solution-resources"></a><span data-ttu-id="bc51f-162">商務程序管理解決方案資源</span><span class="sxs-lookup"><span data-stu-id="bc51f-162">Business Process Management Solution Resources</span></span>  
  
-   [<span data-ttu-id="bc51f-163">開發商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="bc51f-163">Developing a Business Process Management Solution</span></span>](../core/developing-a-business-process-management-solution.md)  
  
     <span data-ttu-id="bc51f-164">開發人員與軟體設計師可以使用這本指南，為建置和執行商務程序管理應用程式所需的所有程式碼、模式、架構和效能設計問題提供相關文件。</span><span class="sxs-lookup"><span data-stu-id="bc51f-164">Developers and Software Architects can use this guide to document all code, patterns, architecture, and performance design issues required to build and run the business process management application.</span></span>  
  
-   [<span data-ttu-id="bc51f-165">部署商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="bc51f-165">Deploying the Business Process Management Solution</span></span>](../core/deploying-the-business-process-management-solution.md)  
  
     <span data-ttu-id="bc51f-166">對於 BizTalk 有基本認識的 IT 專業人員可以使用這本指南，來建置和執行商務程序管理應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc51f-166">The IT professional with a general understanding of BizTalk Server can use this guide to build and run the Business Process Management application.</span></span> <span data-ttu-id="bc51f-167">本指南假設讀者對於應用程式如何在分散式環境中運作，已有基本的認識。</span><span class="sxs-lookup"><span data-stu-id="bc51f-167">The guide assumes a general understanding of how the application works in a distributed environment.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc51f-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc51f-168">See Also</span></span>  
 [<span data-ttu-id="bc51f-169">商務程序管理解決方案</span><span class="sxs-lookup"><span data-stu-id="bc51f-169">Business Process Management Solution</span></span>](../core/business-process-management-solution.md)