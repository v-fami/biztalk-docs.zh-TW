---
title: 將協調流程效能最佳化 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 437c7325-f037-451a-8dbd-f8d8c8889e20
caps.latest.revision: 25
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 473c6e904def7f58adcb52eb26e46891be9c41d0
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971879"
---
# <a name="optimizing-orchestration-performance"></a><span data-ttu-id="39222-102">最佳化協調流程效能</span><span class="sxs-lookup"><span data-stu-id="39222-102">Optimizing Orchestration Performance</span></span>
<span data-ttu-id="39222-103">本主題描述使用協調流程在 BizTalk Server 解決方案最佳做法。</span><span class="sxs-lookup"><span data-stu-id="39222-103">This topic describes best practices for using orchestrations in BizTalk Server solutions.</span></span> <span data-ttu-id="39222-104">這包括建議：</span><span class="sxs-lookup"><span data-stu-id="39222-104">This includes recommendations for:</span></span>  
  
-   <span data-ttu-id="39222-105">降低延遲的使用協調流程的 BizTalk Server 解決方案</span><span class="sxs-lookup"><span data-stu-id="39222-105">Reducing latency of BizTalk Server solutions that use orchestrations</span></span>  
  
    -   <span data-ttu-id="39222-106">排除訊息只是模式的協調流程</span><span class="sxs-lookup"><span data-stu-id="39222-106">Eliminating orchestrations for messaging only patterns</span></span>  
  
    -   <span data-ttu-id="39222-107">使用內嵌從協調流程會傳送</span><span class="sxs-lookup"><span data-stu-id="39222-107">Utilizing inline sends from orchestrations</span></span>  
  
    -   <span data-ttu-id="39222-108">最小化協調流程持續點</span><span class="sxs-lookup"><span data-stu-id="39222-108">Minimizing orchestration persistence points</span></span>  
  
-   <span data-ttu-id="39222-109">巢狀協調流程</span><span class="sxs-lookup"><span data-stu-id="39222-109">Nesting orchestrations</span></span>  
  
-   <span data-ttu-id="39222-110">協調流程的設計模式</span><span class="sxs-lookup"><span data-stu-id="39222-110">Orchestration design patterns</span></span>  
  
-   <span data-ttu-id="39222-111">協調流程例外狀況處理區塊</span><span class="sxs-lookup"><span data-stu-id="39222-111">Orchestration exception handling blocks</span></span>  
  
## <a name="recommendations-for-optimizing-orchestrations-for-low-latency-scenarios"></a><span data-ttu-id="39222-112">最佳化的低延遲案例的協調流程的建議事項</span><span class="sxs-lookup"><span data-stu-id="39222-112">Recommendations for optimizing orchestrations for low latency scenarios</span></span>  
 <span data-ttu-id="39222-113">下列技術可用來減少使用協調流程的 BizTalk Server 解決方案的延遲。</span><span class="sxs-lookup"><span data-stu-id="39222-113">The following techniques can be used to reduce latency of BizTalk Server solutions that use orchestrations.</span></span>  
  
### <a name="eliminate-orchestrations-for-messaging-only-patterns"></a><span data-ttu-id="39222-114">排除訊息只是模式的協調流程</span><span class="sxs-lookup"><span data-stu-id="39222-114">Eliminate orchestrations for messaging only patterns</span></span>  
 <span data-ttu-id="39222-115">盡可能減少增加整體輸送量並降低延遲的商務程序的協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="39222-115">When possible minimize the use of orchestrations to increase overall throughput and reduce the latency of business processes.</span></span> <span data-ttu-id="39222-116">如果那里長時間執行不需要執行交易，而且不需要叫用數個系統針對每個要求，請考慮消除協調流程，並將商務邏輯移到接收和傳送埠，以減少往返總數BizTalkMsgBoxDb 和減少延遲，因為資料庫存取權。</span><span class="sxs-lookup"><span data-stu-id="39222-116">If there is no need to run long running transactions and there is no need to invoke several systems for each request, then consider eliminating orchestrations and moving business logic to Receive and Send Ports to reduce the total amount of roundtrips to the BizTalkMsgBoxDb and decrease the latency due to database access.</span></span> <span data-ttu-id="39222-117">在此情況下，實作自訂管線，並重複使用先前從協調流程叫用的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="39222-117">In this case, implement custom pipelines and reuse helper classes that were previously invoked from orchestrations.</span></span> <span data-ttu-id="39222-118">使用協調流程，只有在絕對必要時，才實作散佈和收集或群組的設計模式。</span><span class="sxs-lookup"><span data-stu-id="39222-118">Use orchestrations only when strictly needed to implement design patterns as Scatter and Gather or Convoys.</span></span> <span data-ttu-id="39222-119">如需協調流程的設計模式的詳細資訊，請參閱主題[協調流程中實作設計模式](http://go.microsoft.com/fwlink/?LinkId=140042)(http://go.microsoft.com/fwlink/?LinkId=140042) BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="39222-119">For more information about Orchestration Design Patterns, see the topic [Implementing Design Patterns in Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.microsoft.com/fwlink/?LinkId=140042) in the BizTalk Server documentation.</span></span>  
  
### <a name="use-inline-sends-from-orchestrations-to-accommodate-low-latency-scenarios"></a><span data-ttu-id="39222-120">使用內嵌從傳送協調流程以容納低延遲案例</span><span class="sxs-lookup"><span data-stu-id="39222-120">Use inline sends from orchestrations to accommodate low latency scenarios</span></span>  
 <span data-ttu-id="39222-121">可能的話，盡量少用的協調流程和喜好來增加整體輸送量並減少延遲的商務程序的僅限傳訊模式。</span><span class="sxs-lookup"><span data-stu-id="39222-121">Whenever possible, minimize the use of orchestrations and favor messaging-only patterns to increase the overall throughput and reduce the latency of the business processes.</span></span> <span data-ttu-id="39222-122">如果不需要長時間執行的交易，則不需要叫用數個系統的商務邏輯，請考慮移到接收和傳送埠的商務邏輯，並消除的協調流程使用。</span><span class="sxs-lookup"><span data-stu-id="39222-122">If there is no need for long-running transactions and there is no need for business logic to invoke several systems, then consider moving business logic to receive and send Ports and eliminating the use of orchestrations.</span></span> <span data-ttu-id="39222-123">這種方法可以實作自訂的管線，其中重複使用先前從協調流程叫用的協助程式類別。</span><span class="sxs-lookup"><span data-stu-id="39222-123">This approach can be implemented with custom pipelines and which reuse the helper classes that were previously invoked from orchestrations.</span></span> <span data-ttu-id="39222-124">為了達到更佳的效能，在低延遲案例中，採用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="39222-124">In order to achieve better performance in low latency scenarios, adopt one of the following approaches:</span></span>  
  
-   <span data-ttu-id="39222-125">消除不必要的協調流程，並採用僅限傳訊模式，以減少 BizTalk MessageBox 資料庫往返的總數量。</span><span class="sxs-lookup"><span data-stu-id="39222-125">Eliminate unnecessary orchestrations and adopt messaging-only patterns to reduce the total amount of roundtrips to the BizTalk MessageBox database.</span></span> <span data-ttu-id="39222-126">這種方法適用於低延遲，因為內嵌傳送略過 BizTalk 傳訊引擎和相關聯的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="39222-126">This approach accommodates low latency because inline sends bypass the BizTalk messaging engine and the associated overhead.</span></span> <span data-ttu-id="39222-127">協調流程內嵌傳送功能被提供使用 BizTalk Server 2006 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="39222-127">Orchestration inline send functionality is provided with BizTalk Server 2006 and later.</span></span>  
  
-   <span data-ttu-id="39222-128">在協調流程，會排除繫結至實體連接埠的邏輯連接埠，並使用內建以傳送他們的位置。</span><span class="sxs-lookup"><span data-stu-id="39222-128">Inside orchestrations, eliminate logical ports bound to physical ports and use in-line sends in their place.</span></span> <span data-ttu-id="39222-129">例如，內嵌傳送可用來建立 WCF proxy 類別，以叫用下游 Web 服務或存取 SQL Server 資料庫的 ADO.NET 元件的執行個體。</span><span class="sxs-lookup"><span data-stu-id="39222-129">For example, an inline send could be used to create an instance of a  WCF proxy class to invoke a downstream Web service or an ADO.NET component to access a SQL Server database.</span></span> <span data-ttu-id="39222-130">在下列圖表中，當協調流程會具現化商務元件，在內部會使用 WCF 時，會執行內嵌傳送直接叫用下游 Web 服務 proxy 物件：</span><span class="sxs-lookup"><span data-stu-id="39222-130">In the following diagram, an inline send is performed when the orchestration instantiates a business component, which internally makes use of a WCF  proxy object to directly invoke a downstream Web service:</span></span>  
  
     <span data-ttu-id="39222-131">![描述的 BizTalk 協調流程內嵌傳送](../technical-guides/media/inlinesend.gif "InlineSend")</span><span class="sxs-lookup"><span data-stu-id="39222-131">![Depiction of BizTalk Orchestration Inline Send](../technical-guides/media/inlinesend.gif "InlineSend")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39222-132">雖然使用從協調流程內嵌傳送將會大幅減少延遲，但也有這種方法的限制。</span><span class="sxs-lookup"><span data-stu-id="39222-132">Although using inline sends from orchestrations will significantly reduce latency, there are limitations to this approach.</span></span> <span data-ttu-id="39222-133">因為內嵌傳送略過 BizTalk 傳訊引擎，所以無法使用與傳訊引擎提供的下列功能：</span><span class="sxs-lookup"><span data-stu-id="39222-133">Because inline sends bypass the BizTalk messaging engine, the following functionality provided with the messaging engine is not available:</span></span>  
> 
> - <span data-ttu-id="39222-134">交易管線</span><span class="sxs-lookup"><span data-stu-id="39222-134">Transactional pipelines</span></span>  
>   -   <span data-ttu-id="39222-135">可復原管線</span><span class="sxs-lookup"><span data-stu-id="39222-135">Recoverable pipelines</span></span>  
>   -   <span data-ttu-id="39222-136">呼叫 BAM 攔截器 API 的管線</span><span class="sxs-lookup"><span data-stu-id="39222-136">Pipelines that call the BAM interceptor API</span></span>  
>   -   <span data-ttu-id="39222-137">BizTalk Server 配接器支援</span><span class="sxs-lookup"><span data-stu-id="39222-137">BizTalk Server adapter support</span></span>  
>   -   <span data-ttu-id="39222-138">批次處理</span><span class="sxs-lookup"><span data-stu-id="39222-138">Batching</span></span>  
>   -   <span data-ttu-id="39222-139">重試次數</span><span class="sxs-lookup"><span data-stu-id="39222-139">Retries</span></span>  
>   -   <span data-ttu-id="39222-140">相互關聯集初始化</span><span class="sxs-lookup"><span data-stu-id="39222-140">Correlation set initialization</span></span>  
>   -   <span data-ttu-id="39222-141">宣告式組態</span><span class="sxs-lookup"><span data-stu-id="39222-141">Declarative configuration</span></span>  
>   -   <span data-ttu-id="39222-142">次要的傳輸</span><span class="sxs-lookup"><span data-stu-id="39222-142">Secondary transports</span></span>  
>   -   <span data-ttu-id="39222-143">追蹤</span><span class="sxs-lookup"><span data-stu-id="39222-143">Tracking</span></span>  
>   -   <span data-ttu-id="39222-144">BAM 的宣告式用法</span><span class="sxs-lookup"><span data-stu-id="39222-144">Declarative use of BAM</span></span>  
  
 <span data-ttu-id="39222-145">如需不能從協調流程內執行的管線類型的詳細資訊，請參閱主題的 < 限制 > 一節[如何使用運算式執行管線](http://go.microsoft.com/fwlink/?LinkId=158008)(http://go.microsoft.com/fwlink/?LinkId=158008) BizTalk Server 中2010 文件。</span><span class="sxs-lookup"><span data-stu-id="39222-145">For more information about the types of pipelines that cannot be executed from within an orchestration, see the “Restrictions” section of the topic [How to Use Expressions to Execute Pipelines](http://go.microsoft.com/fwlink/?LinkId=158008) (http://go.microsoft.com/fwlink/?LinkId=158008) in the BizTalk Server 2010 documentation.</span></span>  
  
### <a name="optimize-orchestration-latency-by-reducing-the-number-of-persistence-points-if-possible"></a><span data-ttu-id="39222-146">最佳化協調流程的延遲，藉由盡可能減少持續點數目</span><span class="sxs-lookup"><span data-stu-id="39222-146">Optimize orchestration latency by reducing the number of persistence points, if possible</span></span>  
 <span data-ttu-id="39222-147">在協調流程的範圍只需要標示為 「 長時間執行交易式 」 如果您想要使用補償或範圍的逾時。</span><span class="sxs-lookup"><span data-stu-id="39222-147">An orchestration scope only needs to be marked as “long-running transactional” if you want to use compensation or scope timeouts.</span></span> <span data-ttu-id="39222-148">長時間執行交易式範圍會造成額外的持續性端點結尾的範圍內，當您不需要使用補償或範圍逾時應該予以避免。</span><span class="sxs-lookup"><span data-stu-id="39222-148">A long-running transactional scope causes an extra persistence point at the end of the scope, so they should be avoided when you don’t need to use compensation or scope timeouts.</span></span> <span data-ttu-id="39222-149">不可部分完成的範圍會造成保存點結尾的範圍內，但也可保證沒有持續點會發生在不可部分完成的範圍內。</span><span class="sxs-lookup"><span data-stu-id="39222-149">An atomic scope causes a persistence point at the end of the scope, but also guarantees that no persistence points will occur inside the atomic scope.</span></span> <span data-ttu-id="39222-150">這個副作用產生的範圍內沒有持續性有時可用來批次持續點優點 （當執行多個傳送，例如）。</span><span class="sxs-lookup"><span data-stu-id="39222-150">This side-effect of no persistence inside the scope can sometimes be used to your advantage to batch persistence points (when doing multiple sends, for example).</span></span> <span data-ttu-id="39222-151">一般情況下，不過，我們建議盡可能避免不可部分完成範圍。</span><span class="sxs-lookup"><span data-stu-id="39222-151">In general, though, we recommend avoiding atomic scopes if possible.</span></span> <span data-ttu-id="39222-152">協調流程引擎將儲存至永續性儲存體在不同的點，執行中協調流程執行個體的整個狀態，讓執行個體可以稍後再還原於記憶體並執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="39222-152">The orchestration engine saves to persistent storage the entire state of a running orchestration instance at various points, so that the instance can later be restored in memory and carried out to completion.</span></span>   
<span data-ttu-id="39222-153">**在 協調流程的持續點數目是其中一個影響延遲的訊息通過協調流程的關鍵因素**。</span><span class="sxs-lookup"><span data-stu-id="39222-153">**The number of persistence points in an orchestration is one of the key factors influencing the latency of messages flowing through orchestrations**.</span></span> <span data-ttu-id="39222-154">引擎達到保存點，每次執行的協調流程的內部狀態會序列化並儲存到 MessageBox，這項作業會產生延遲成本。</span><span class="sxs-lookup"><span data-stu-id="39222-154">Each time the engine hits a persistence point, the internal state of a running orchestration is serialized and saved to the MessageBox and this operation incurs a latency cost.</span></span> <span data-ttu-id="39222-155">序列化的內部狀態會包含所有的訊息和具現化，但尚未釋放協調流程中的變數。</span><span class="sxs-lookup"><span data-stu-id="39222-155">The serialization of the internal state includes all messages and variables instantiated and not yet released in the orchestration.</span></span> <span data-ttu-id="39222-156">愈多的訊息和變數和其中的愈多，越久，就足以保存協調流程的內部狀態。</span><span class="sxs-lookup"><span data-stu-id="39222-156">The larger the messages and variables and the greater the number of these, the longer it will take to persist the internal state of an orchestration.</span></span> <span data-ttu-id="39222-157">持續點數目過多可能會導致效能大幅降低。</span><span class="sxs-lookup"><span data-stu-id="39222-157">An excessive number of persistence points can lead to significant performance degradation.</span></span> <span data-ttu-id="39222-158">基於這個理由，我們會建議的交易式範圍數目，從而排除不必要的持續點，從協調流程和傳送圖形。</span><span class="sxs-lookup"><span data-stu-id="39222-158">For this reason, we recommend eliminating unnecessary persistence points from orchestrations by reducing the number of transactional scopes and Send shapes.</span></span> <span data-ttu-id="39222-159">這個方法可減少 MessageBox，因為協調流程凍結和解除凍結，增加整體的延展性，並減少協調流程的延遲時間的爭用。</span><span class="sxs-lookup"><span data-stu-id="39222-159">This approach allows decreasing the contention on the MessageBox due to orchestration dehydration and rehydration, increasing the overall scalability, and reducing orchestration latency.</span></span>   
<span data-ttu-id="39222-160">另一個建議是一律讓協調流程的內部狀態保持越小越好。</span><span class="sxs-lookup"><span data-stu-id="39222-160">Another recommendation is to always keep the internal state of an orchestration as small as possible.</span></span> <span data-ttu-id="39222-161">這項技術可以大幅降低 XLANG 引擎序列化、 保存和還原的持續點發生協調流程的內部狀態所花費的時間。</span><span class="sxs-lookup"><span data-stu-id="39222-161">This technique can significantly reduce the time spent by the XLANG Engine serializing, persisting and restoring the internal state of an orchestration in case of persistence point.</span></span> <span data-ttu-id="39222-162">達到此目的的方法之一是盡量建立變數和訊息越慢，並發行這些儘早越好，比方說會導入您的協調流程內的非交易式範圍，並宣告變數和訊息，而不是最高的層級宣告這些內部範圍內。</span><span class="sxs-lookup"><span data-stu-id="39222-162">One way to achieve this is to create variables and messages as late as possible and release them as early as possible; for example introduce non transactional scopes inside your orchestrations and declare variables and messages within these inner scopes instead of declaring them at the top-most level.</span></span> <span data-ttu-id="39222-163">如需有關最小化協調流程持續點的詳細資訊，請參閱 BizTalk Server 2010 文件中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="39222-163">For more information about minimizing orchestration persistence points, see the following topics in the BizTalk Server  2010 documentation:</span></span>  
  
-   <span data-ttu-id="39222-164">[持續性和協調流程引擎](http://go.microsoft.com/fwlink/?LinkID=155292)(http://go.microsoft.com/fwlink/?LinkID=155292)。</span><span class="sxs-lookup"><span data-stu-id="39222-164">[Persistence and the Orchestration Engine](http://go.microsoft.com/fwlink/?LinkID=155292) (http://go.microsoft.com/fwlink/?LinkID=155292).</span></span>  
  
-   <span data-ttu-id="39222-165">[協調流程凍結和解除凍結](http://go.microsoft.com/fwlink/?LinkID=155284)(http://go.microsoft.com/fwlink/?LinkID=155292)。</span><span class="sxs-lookup"><span data-stu-id="39222-165">[Orchestration Dehydration and Rehydration](http://go.microsoft.com/fwlink/?LinkID=155284) (http://go.microsoft.com/fwlink/?LinkID=155292).</span></span>  
  
## <a name="guidelines-for-using-promoted-properties-to-access-message-tags-or-attributes-from-an-orchestration"></a><span data-ttu-id="39222-166">使用指導方針升級屬性，存取訊息標記或屬性時，便從協調流程</span><span class="sxs-lookup"><span data-stu-id="39222-166">Guidelines for using promoted properties to access message tags or attributes from an orchestration</span></span>  
 <span data-ttu-id="39222-167">如果您需要將屬性升級，升級只會用於訊息路由、 篩選和訊息相互關聯的屬性。</span><span class="sxs-lookup"><span data-stu-id="39222-167">If you do need to promote properties, promote only those properties that are used for message routing, filters, and message correlation.</span></span> <span data-ttu-id="39222-168">每個屬性升級需要的解譯器元件 （XML、 一般，自訂） 來辨識文件類型，並使用 XPath 運算式從相對的註解包含在 XSD 中定義的文件類型的訊息中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="39222-168">The promotion of each property requires the disassembler component (XML, Flat, custom) to recognize the document type and to retrieve data from the message using the XPath expression from the relative annotation contained in the XSD that defines the document type.</span></span> <span data-ttu-id="39222-169">此外，每個屬性升級時，訊息代理程式會將訊息發佈到 MessageBox 資料庫會導致個別 bts_InsertProperty 預存程序的呼叫。</span><span class="sxs-lookup"><span data-stu-id="39222-169">In addition, each property promotion causes a separate call of the bts_InsertProperty stored procedure when the Message Agent publishes the message to the MessageBox database.</span></span> <span data-ttu-id="39222-170">如果協調流程需要存取特定項目或 XML 文件所包含的屬性，請使用下列技巧的其中一個：</span><span class="sxs-lookup"><span data-stu-id="39222-170">If an orchestration needs to access a particular element or attribute contained by an XML document, use one of the following techniques:</span></span>  
  
- <span data-ttu-id="39222-171">降低寫入並升級的屬性數目，並排除不是絕對必要。</span><span class="sxs-lookup"><span data-stu-id="39222-171">Reduce the number of written and promoted properties and eliminate those that are not strictly necessary.</span></span>  
  
- <span data-ttu-id="39222-172">消除不必要的辨別的欄位。</span><span class="sxs-lookup"><span data-stu-id="39222-172">Eliminate unnecessary distinguished fields.</span></span> <span data-ttu-id="39222-173">[辨別] 欄位會寫入內容屬性，如其名稱為用來擷取資料的 XPath 運算式，它們可以輕鬆地佔用大量的空間。</span><span class="sxs-lookup"><span data-stu-id="39222-173">The distinguished fields are written context properties and they can easily occupy significant space as their name is equal to the XPath expression that is used to retrieve data.</span></span> <span data-ttu-id="39222-174">[辨別] 屬性定義為在 XSD 中定義的文件類型的註解。</span><span class="sxs-lookup"><span data-stu-id="39222-174">The distinguished property is defined as annotations in the XSD that defines the document type.</span></span> <span data-ttu-id="39222-175">解譯器元件會使用相同的升級屬性採用的方法，並使用定義來尋找該檢查內送文件中的辨別的欄位 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="39222-175">The disassembler component uses the same approach adopted for promoted properties and uses the XPath expression that defines a distinguished field to find it within in the incoming document.</span></span> <span data-ttu-id="39222-176">然後，解譯器元件將屬性寫入內容中位置：</span><span class="sxs-lookup"><span data-stu-id="39222-176">Then, the disassembler component writes a property in the context where:</span></span>  
  
  - <span data-ttu-id="39222-177">**名稱**： 註釋中定義的 XPath 運算式。</span><span class="sxs-lookup"><span data-stu-id="39222-177">**Name**: XPath Expression defined in the annotation.</span></span>  
  
  - <span data-ttu-id="39222-178">**值**： 內送文件中的 XPath 運算式所識別之項目的值。</span><span class="sxs-lookup"><span data-stu-id="39222-178">**Value**: Value of the element identified by the XPath expression within an incoming document.</span></span>  
  
    <span data-ttu-id="39222-179">XPath 運算式可以很長，尤其是有問題的項目是很深的文件結構描述中。</span><span class="sxs-lookup"><span data-stu-id="39222-179">The XPath Expressions can be very long, especially when the element in question is very deep in the document schema.</span></span> <span data-ttu-id="39222-180">因此，越多會辨別欄位，較大的內容大小。</span><span class="sxs-lookup"><span data-stu-id="39222-180">So, the more distinguished fields, the larger the context size.</span></span> <span data-ttu-id="39222-181">這又有不利的影響整體效能。</span><span class="sxs-lookup"><span data-stu-id="39222-181">This in turn adversely affects the overall performance.</span></span>  
  
- <span data-ttu-id="39222-182">使用協調流程執行階段所提供的內建函式 XPath。</span><span class="sxs-lookup"><span data-stu-id="39222-182">Use the XPath built-in function provided by the orchestration runtime.</span></span>  
  
- <span data-ttu-id="39222-183">如果訊息看起來很小 （幾 kb 為單位） 和 XML 格式，您還可以將訊息還原序列化為.NET 類別執行個體並使用公用欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="39222-183">If messages are quite small (a few kilobytes) and XML-formatted, you can de-serialize the message into a .NET class instance and work with public fields and properties.</span></span> <span data-ttu-id="39222-184">如果訊息需要複雜的細節 （自訂程式碼、 商務規則引擎原則等） 使用.NET 類別的執行個體所公開的屬性存取資料是使用 XPath 運算式快得多。</span><span class="sxs-lookup"><span data-stu-id="39222-184">If the message needs a complex elaboration (custom code, Business Rule Engine policies, etc.) accessing data using the properties exposed by an instance of a .NET class is much faster using XPath expressions.</span></span> <span data-ttu-id="39222-185">在完成協調流程所叫用商務邏輯之後，實體物件可以序列化回 BizTalk 訊息。</span><span class="sxs-lookup"><span data-stu-id="39222-185">When the business logic invoked by the orchestration has completed, the entity object can be serialized back into a BizTalk message.</span></span> <span data-ttu-id="39222-186">您可以建立.NET 類別，使用下列工具之一的 XML 結構描述： XSD 工具 (.NET Framework 2.0) 或 SVCUTIL (.NET Framework 3.0)。</span><span class="sxs-lookup"><span data-stu-id="39222-186">You can create .NET classes from an XML schema using one of the following tools: XSD tool (.NET Framework 2.0) or SVCUTIL (.NET Framework 3.0).</span></span>  
  
- <span data-ttu-id="39222-187">啟用從協調流程的協助程式元件。</span><span class="sxs-lookup"><span data-stu-id="39222-187">Enable a helper component from an orchestration.</span></span> <span data-ttu-id="39222-188">這項技術會有優於使用辨別的欄位。</span><span class="sxs-lookup"><span data-stu-id="39222-188">This technique has an advantage over using distinguished fields.</span></span> <span data-ttu-id="39222-189">事實上，協調流程可讀取的 XPath 運算式從設定儲存 （在組態檔、 SSO 組態存放區、 自訂 Db 等等），以便當您有變更的 XPath 運算式，您不必變更和重新部署結構描述，您應進行升級的屬性和 distinguished 欄位。</span><span class="sxs-lookup"><span data-stu-id="39222-189">In fact, an orchestration may read the XPath expression from a config store (config file, SSO Config Store, custom Db, and so on) so, when you have to change the XPath expression, you do not have to change and redeploy a schema, as you should do for promoted properties and distinguished fields.</span></span> <span data-ttu-id="39222-190">下列程式碼範例提供的協助程式元件的範例。</span><span class="sxs-lookup"><span data-stu-id="39222-190">The following code sample provides an example of a helper component.</span></span> <span data-ttu-id="39222-191">元件使用 XPathReader 類別所提供的 BizTalk 執行階段。</span><span class="sxs-lookup"><span data-stu-id="39222-191">The component uses the XPathReader class that is provided by the BizTalk runtime.</span></span> <span data-ttu-id="39222-192">這可讓閱讀文件資料流，直到找到 XPath 運算式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="39222-192">This allows the code to read through the document stream until the XPath expression is found.</span></span>  
  
```  
#region Copyright  
//===  
//Microsoft Windows Server AppFabric Customer Advisory Team (CAT)   
//  
// This sample is supplemental to the technical guidance published on the community  
// blog.  
//   
// Author: Paolo Salvatori.  
//===  
// Copyright © 2010 Microsoft Corporation. All rights reserved.  
//   
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF ANY KIND, EITHER   
// EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE IMPLIED WARRANTIES OF   
// MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. YOU BEAR THE RISK OF USING IT.  
//===  
#endregion  
#region Using Directives  
using System;  
using System.Collections.Generic;  
using System.IO;  
using System.Xml;  
using System.Linq;  
using System.Text;  
using System.Globalization;  
using Microsoft.XLANGs.BaseTypes;   
using Microsoft.BizTalk.Streaming;  
using Microsoft.BizTalk.XPath;  
#endregion  
namespace Microsoft.AppFabric.CAT.Samples.DuplexMEP.Helpers  
{  
public class XPathHelper  
{  
#region Private Constants   
private const string MessageCannotBeNull = "[XPathReader] The message cannot be null.";  
#endregion  
#region Public Static Methods  
public static string GetValue(XLANGMessage message, int partIndex, string xpath)  
{  
try  
{  
if (message == null)  
{  
throw new ApplicationException(MessageCannotBeNull);  
}  
using (Stream stream = message[partIndex].RetrieveAs(typeof(Stream)) as Stream)  
{  
XmlTextReader xmlTextReader = new XmlTextReader(stream);  
XPathCollection xPathCollection = new XPathCollection();  
XPathReader xPathReader = new XPathReader(xmlTextReader, xPathCollection);  
xPathCollection.Add(xpath);  
while (xPathReader.Read())  
{  
if (xPathReader.HasAttributes)  
{  
for (int i = 0; i < xPathReader.AttributeCount; i++)  
{  
xPathReader.MoveToAttribute(i);  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.GetAttribute(i);  
}  
}  
}  
if (xPathReader.Match(xPathCollection[0]))  
{  
return xPathReader.ReadString();  
}  
}  
}  
}  
finally  
{  
message.Dispose();  
}  
return string.Empty;  
}  
#endregion  
}  
}  
```  
  
## <a name="minimize-orchestration-complexity-to-improve-performance"></a><span data-ttu-id="39222-193">若要改善效能的協調流程複雜性降至最低</span><span class="sxs-lookup"><span data-stu-id="39222-193">Minimize orchestration complexity to improve performance</span></span>  
 <span data-ttu-id="39222-194">協調流程的複雜度對於效能有重大影響。</span><span class="sxs-lookup"><span data-stu-id="39222-194">The complexity of orchestrations has a significant impact on performance.</span></span> <span data-ttu-id="39222-195">當協調流程的複雜度增加時，會降低整體效能。</span><span class="sxs-lookup"><span data-stu-id="39222-195">As orchestration complexity increases, overall performance decreases.</span></span> <span data-ttu-id="39222-196">協調流程可用於幾乎無限的各種案例，以及每個案例可能涉及不同複雜度的協調流程。</span><span class="sxs-lookup"><span data-stu-id="39222-196">Orchestrations can be used in an almost infinite variety of scenarios, and each scenario might involve orchestrations of varying complexity.</span></span> <span data-ttu-id="39222-197">避免複雜的協調流程，盡可能改用模組化的方法。</span><span class="sxs-lookup"><span data-stu-id="39222-197">Avoid complex orchestrations when possible in favor of a modular approach.</span></span> <span data-ttu-id="39222-198">換句話說，將您的商務邏輯分成多個可重複使用的協調流程。</span><span class="sxs-lookup"><span data-stu-id="39222-198">In other words, split your business logic into multiple, reusable orchestrations.</span></span>  
  
 <span data-ttu-id="39222-199">如果您需要實作複雜的協調流程，定義訊息和變數，至多個內部的範圍，可能的話，而不是根層級。</span><span class="sxs-lookup"><span data-stu-id="39222-199">If you do need to implement a complex orchestration, define messages and variables into inner scopes whenever possible rather than at the root level.</span></span> <span data-ttu-id="39222-200">這項技術會維護較小的使用量，在記憶體中的每個協調流程，因為變數和訊息時進行處置的流程超出的範圍，其中已定義的變數和訊息。</span><span class="sxs-lookup"><span data-stu-id="39222-200">This technique maintains a smaller footprint in memory for each orchestration because variables and messages are disposed of when the flow leaves the scope where the variables and messages were defined.</span></span> <span data-ttu-id="39222-201">當協調流程會儲存到 MessageBox 持續點，這個方法會特別有幫助。</span><span class="sxs-lookup"><span data-stu-id="39222-201">This approach is particularly beneficial when orchestrations are saved to the MessageBox at persistence points.</span></span>  
  
## <a name="use-the-call-orchestration-shape-versus-the-start-orchestration-shape-to-improve-performance"></a><span data-ttu-id="39222-202">使用 呼叫協調流程圖形與啟動協調流程圖形以改善效能</span><span class="sxs-lookup"><span data-stu-id="39222-202">Use the Call Orchestration shape versus the Start Orchestration shape to improve performance</span></span>  
 <span data-ttu-id="39222-203">避免**啟動協調流程**圖形，並使用**呼叫的協調流程**執行巢狀協調流程的圖形。</span><span class="sxs-lookup"><span data-stu-id="39222-203">Avoid the **Start Orchestration** shape and use the **Call Orchestration** shape to execute a nested orchestration.</span></span> <span data-ttu-id="39222-204">事實上，**呼叫的協調流程**圖形可以用來同步呼叫另一個專案中參考的協調流程。</span><span class="sxs-lookup"><span data-stu-id="39222-204">In fact, The **Call Orchestration** shape can be used to synchronously call an orchestration that is referenced in another project.</span></span> <span data-ttu-id="39222-205">此方法允許在 BizTalk 專案之間重複使用常見的協調流程的工作流程模式。</span><span class="sxs-lookup"><span data-stu-id="39222-205">This approach allows for reuse of common orchestration workflow patterns across BizTalk projects.</span></span> <span data-ttu-id="39222-206">當您叫用另一個巢狀協調流程，以同步方式**呼叫的協調流程**圖形，封閉式協調流程會等待巢狀協調流程完成後再繼續。</span><span class="sxs-lookup"><span data-stu-id="39222-206">When you invoke another nested orchestration synchronously with the **Call Orchestration** shape, the enclosing orchestration waits for the nested orchestration to finish before continuing.</span></span> <span data-ttu-id="39222-207">巢狀協調流程會執行呼叫的協調流程的相同執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="39222-207">The nested orchestration is executed on the same thread that runs the calling orchestration.</span></span>  
  
 <span data-ttu-id="39222-208">**啟動協調流程**圖案大致**呼叫的協調流程**圖形，但在此情況下，巢狀協調流程會呼叫以非同步方式： 中叫用的控制流程協調流程會繼續超出引動過程，而不需等待叫用的協調流程完成其工作。</span><span class="sxs-lookup"><span data-stu-id="39222-208">The **Start Orchestration** shape is similar to the **Call Orchestration** shape, but in this case the nested orchestration is called in an asynchronous manner: the flow of control in the invoking orchestration proceeds beyond the invocation, without waiting for the invoked orchestration to finish its work.</span></span> <span data-ttu-id="39222-209">為了實作之間的呼叫端和被呼叫的協調流程，此分離**啟動協調流程**發佈到 BizTalk Messagebox 的訊息可透過實作。</span><span class="sxs-lookup"><span data-stu-id="39222-209">In order to implement this decoupling between the caller and the called orchestrations, the **Start Orchestration** is implemented via publication of a message to the BizTalk Messagebox.</span></span> <span data-ttu-id="39222-210">內含式 BizTalk 主控件執行個體執行巢狀協調流程接著會取用這個訊息。</span><span class="sxs-lookup"><span data-stu-id="39222-210">This message is then consumed by an in-process BizTalk host instance which executes the nested orchestration.</span></span> <span data-ttu-id="39222-211">可能的話，請使用**呼叫的協調流程**，尤其是如果呼叫的協調流程必須等待結果，以從巢狀協調流程，即可繼續處理。</span><span class="sxs-lookup"><span data-stu-id="39222-211">When possible, use **Call Orchestration**, especially if the calling orchestration needs to wait for a result from the nested orchestration in order to continue processing.</span></span>  <span data-ttu-id="39222-212">如需使用 呼叫協調流程圖形的詳細資訊，請參閱 BizTalk Server 2010 文件中的下列主題：</span><span class="sxs-lookup"><span data-stu-id="39222-212">For more information about using the Call Orchestration shape, see the following topics in the BizTalk Server 2010 documentation:</span></span>  
  
-   <span data-ttu-id="39222-213">[使用協調流程中的直接繫結連接埠](http://go.microsoft.com/fwlink/?LinkId=139902)(http://go.microsoft.com/fwlink/?LinkId=139902)。</span><span class="sxs-lookup"><span data-stu-id="39222-213">[Working with Direct Bound Ports in Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139902) (http://go.microsoft.com/fwlink/?LinkId=139902).</span></span>  
  
-   <span data-ttu-id="39222-214">[巢狀協調流程](http://go.microsoft.com/fwlink/?LinkId=139903)(http://go.microsoft.com/fwlink/?LinkId=139903)。</span><span class="sxs-lookup"><span data-stu-id="39222-214">[Nesting Orchestrations](http://go.microsoft.com/fwlink/?LinkId=139903) (http://go.microsoft.com/fwlink/?LinkId=139903).</span></span>  
  
## <a name="use-xmlreader-with-xlangmessage-versus-using-xmlreader-with-xmldocument-to-improve-orchestration-performance"></a><span data-ttu-id="39222-215">使用 XLANGMessage 中的 XmlReader，與使用 XmlDocument 使用 XmlReader，以改善協調流程效能</span><span class="sxs-lookup"><span data-stu-id="39222-215">Use XmlReader with XLANGMessage versus using XmlReader with XmlDocument to improve orchestration performance</span></span>  
 <span data-ttu-id="39222-216">若要改善.NET 方法，從協調流程呼叫的協調流程效能，使用 XLANGMessage，不 XmlDocument 中的 XmlReader。</span><span class="sxs-lookup"><span data-stu-id="39222-216">To improve orchestration performance for .NET methods called from an orchestration, use XmlReader with XLANGMessage, not XmlDocument.</span></span> <span data-ttu-id="39222-217">下列程式碼範例說明這項功能。</span><span class="sxs-lookup"><span data-stu-id="39222-217">The following code example illustrates this functionality.</span></span>  
  
```csharp  
// As a general rule, use XmlReader with XLANGMessage, not XmlDocument.   
// This is illustrated in the parameter passed into the following code.   
// The XLANG/s compiler doesn't allow a return value of XmlReader   
// so documents must be initially constructed as XmlDocument()  
public static XmlDocument FromMsg(XLANGMessage old)  
{  
    //get at the data  
    XmlDocument ret = new XmlDocument();  
  
    try{  
        XmlReader reader = (XmlReader)old[0].RetrieveAs(typeof(XmlReader));  
        //construct new message from old  
        //read property  
        object msgid = old.GetPropertyValue(typeof(BTS.MessageID));  
    }  
    finally {  
        // Call Dispose on the XLANGMessage object   
        // because the message doesn't belong to the   
        // .NET runtime - it belongs to the Messagebox database   
        old.Dispose();  
    }  
    return ret;  
}  
```  
  
 <span data-ttu-id="39222-218">另一種方法是建立結構描述為基礎的.NET 類別。</span><span class="sxs-lookup"><span data-stu-id="39222-218">Another method would be to create a .NET class based on the schema.</span></span> <span data-ttu-id="39222-219">這會採用較少的記憶體比載入文件**XmlDocument**物件，以及適用於.NET 開發人員提供的結構描述元素的輕鬆存取。</span><span class="sxs-lookup"><span data-stu-id="39222-219">This takes less memory than loading the document into an **XmlDocument** object, as well as providing easy access to the schema elements for .NET developers.</span></span> <span data-ttu-id="39222-220">若要產生 BizTalk 結構描述為基礎的類別，您可以使用 Visual Studio 提供的 xsd.exe 工具。</span><span class="sxs-lookup"><span data-stu-id="39222-220">To generate a class based on a BizTalk schema, you can use the xsd.exe tool provided with Visual Studio.</span></span> <span data-ttu-id="39222-221">例如，執行**xsd.exe \<schema.xsd\> /類別**針對簡單的結構描述，其中包含名為 ItemA 的欄位，ItemB，ItemC，將會產生下列類別。</span><span class="sxs-lookup"><span data-stu-id="39222-221">For example, running **xsd.exe \<schema.xsd\> /classes** against a simple schema containing fields named ItemA, ItemB, ItemC, will produce the following class.</span></span>  
  
```csharp  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1433  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
using System.Xml.Serialization;  
  
//   
// This source code was auto-generated by xsd, Version=2.0.50727.42.  
//  
  
/// <remarks/>  
[System.CodeDom.Compiler.GeneratedCodeAttribute("xsd", "2.0.50727.42")]  
[System.SerializableAttribute()]  
[System.Diagnostics.DebuggerStepThroughAttribute()]  
[System.ComponentModel.DesignerCategoryAttribute("code")]  
[System.Xml.Serialization.XmlTypeAttribute(AnonymousType=true, Namespace="http://Schemas.MySchema")]  
[System.Xml.Serialization.XmlRootAttribute(Namespace="http://Schemas.MySchema", IsNullable=false)]  
public partial class MySchemaRoot {  
  
    private string itemAField;  
  
    private string itemBField;  
  
    private string itemCField;  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemA {  
        get {  
            return this.itemAField;  
        }  
        set {  
            this.itemAField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemB {  
        get {  
            return this.itemBField;  
        }  
        set {  
            this.itemBField = value;  
        }  
    }  
  
    /// <remarks/>  
    [System.Xml.Serialization.XmlElementAttribute(Form=System.Xml.Schema.XmlSchemaForm.Unqualified)]  
    public string ItemC {  
        get {  
            return this.itemCField;  
        }  
        set {  
            this.itemCField = value;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="39222-222">這個類別即可參照您的.NET 組件才能存取的訊息項目，並傳回的物件可以直接指派給訊息。</span><span class="sxs-lookup"><span data-stu-id="39222-222">This class can then be referenced in your .NET assembly in order to access the message elements, and the returned object can be directly assigned to a message.</span></span> <span data-ttu-id="39222-223">以下是類別的範例使用上面所產生。</span><span class="sxs-lookup"><span data-stu-id="39222-223">The following is an example use of the class generated above.</span></span>  
  
```csharp  
public static Root SetValues(Microsoft.XLANGs.BaseTypes.XLANGMessage msg)  
{  
   try  
   {  
   MySchemaRoot rootObj=(MySchemaRoot)msg[0].RetrieveAs(typeof(MySchemaRoot);  
   rootObj.ItemA="value a";  
   rootObj.ItemB="value b";  
   rootObj.ItemC="value c";  
   }  
    finally {  
        msg.Dispose();  
            }  
  
   return rootObj;  
}  
```  
  
 <span data-ttu-id="39222-224">這項技術可讓您處理訊息時，請使用物件導向的方法。</span><span class="sxs-lookup"><span data-stu-id="39222-224">This technique allows you to use an object-oriented approach when processing messages.</span></span> <span data-ttu-id="39222-225">應該使用這項技術，主要被使用相對較小的訊息。</span><span class="sxs-lookup"><span data-stu-id="39222-225">This technique should be used primarily with relatively small messages.</span></span> <span data-ttu-id="39222-226">這是因為即使這項技術會使用比時載入訊息得以減少記憶體**XmlDocument**物件時，整個訊息仍會載入記憶體。</span><span class="sxs-lookup"><span data-stu-id="39222-226">This is because even though this technique uses considerably less memory than when loading the message into an **XmlDocument** object, the entire message is still loaded into memory.</span></span> <span data-ttu-id="39222-227">處理較大的訊息時使用**XmlReader**類別，以讀取訊息並**XmlWriter**類別將訊息寫入。</span><span class="sxs-lookup"><span data-stu-id="39222-227">When processing larger messages, use the **XmlReader** class to read messages and the **XmlWriter** class to write messages.</span></span> <span data-ttu-id="39222-228">使用時**XmlReader**並**XmlWriter**，訊息會包含在**VirtualStream**物件。</span><span class="sxs-lookup"><span data-stu-id="39222-228">When using **XmlReader** and **XmlWriter**, the message is contained in a **VirtualStream** object.</span></span> <span data-ttu-id="39222-229">如果訊息大小超過指定的值**大型訊息閾值 （位元組）** 公開 BizTalk 群組屬性的 [設定] 頁面上，將訊息寫入至檔案系統。</span><span class="sxs-lookup"><span data-stu-id="39222-229">If the message size exceeds the value specified for **Large message threshold (bytes)** that is exposed on the BizTalk Group Properties configuration page, the message is written to the file system.</span></span> <span data-ttu-id="39222-230">這會降低整體效能，但可避免記憶體不足例外狀況。</span><span class="sxs-lookup"><span data-stu-id="39222-230">This decreases overall performance, but avoids out of memory exceptions.</span></span>  
  
## <a name="improve-performance-by-minimizing-the-use-of-logical-ports-bound-to-physical-ports"></a><span data-ttu-id="39222-231">最小化的邏輯連接埠繫結至實體連接埠使用，以改善效能</span><span class="sxs-lookup"><span data-stu-id="39222-231">Improve performance by minimizing the use of logical ports bound to physical ports</span></span>  
 <span data-ttu-id="39222-232">您可以將邏輯連接埠繫結至實體連接埠，使用下列的配接器的使用降至最低，以提升效能：</span><span class="sxs-lookup"><span data-stu-id="39222-232">You can increase performance by minimizing the use of logical ports bound to physical ports that use the following adapters:</span></span>  
  
- <span data-ttu-id="39222-233">SQL Server、 Oracle</span><span class="sxs-lookup"><span data-stu-id="39222-233">SQL Server, Oracle</span></span>  
  
- <span data-ttu-id="39222-234">WSE，HTTP，WCF</span><span class="sxs-lookup"><span data-stu-id="39222-234">WSE, HTTP, WCF</span></span>  
  
- <span data-ttu-id="39222-235">MSMQ、 MQSeries</span><span class="sxs-lookup"><span data-stu-id="39222-235">MSMQ, MQSeries</span></span>  
  
  <span data-ttu-id="39222-236">在 BizTalk Server 2010，請傳送和接收管線可以從協調流程中使用包含在 Microsoft.XLANGs.Pipeline.dll XLANGPipelineManager 類別直接呼叫。</span><span class="sxs-lookup"><span data-stu-id="39222-236">In BizTalk Server 2010, send and receive pipelines can be directly invoked from an orchestration using the XLANGPipelineManager class contained in the Microsoft.XLANGs.Pipeline.dll.</span></span> <span data-ttu-id="39222-237">因此，管線處理可以從移動連接埠至協調流程;協調流程中的邏輯連接埠可以取代為 「 運算式 」 圖形，會叫用指定的.NET 類別的執行個體 （例如，使用 ADO.NET 資料存取元件）。</span><span class="sxs-lookup"><span data-stu-id="39222-237">Thus, the processing of pipelines can be moved from ports to orchestrations; logical ports in an orchestration can be substituted with an Expression shape, which invokes an instance of a given .NET class (for example, a Data Access component using ADO.NET).</span></span> <span data-ttu-id="39222-238">採用這項技術之前, 您應該注意，如果您不使用配接器和實體連接埠，您無法利用其函式，例如批次處理、 重試次數、 宣告式組態和次要傳輸的能力。</span><span class="sxs-lookup"><span data-stu-id="39222-238">Before adopting this technique, you should be aware that if you do not use adapters and physical ports, you lose the ability to leverage their functions, such as batching, retries, declarative configuration, and secondary transports.</span></span>  
  
## <a name="orchestration-design-patterns"></a><span data-ttu-id="39222-239">協調流程的設計模式</span><span class="sxs-lookup"><span data-stu-id="39222-239">Orchestration Design Patterns</span></span>  
 <span data-ttu-id="39222-240">協調流程設計師 」 可讓開發人員實作各種不同的企業整合模式。</span><span class="sxs-lookup"><span data-stu-id="39222-240">The Orchestration Designer allows developers to implement a wide range of enterprise integration patterns.</span></span> <span data-ttu-id="39222-241">一些常見的模式包括彙總工具、 例外狀況處理和補償、 訊息代理程式、 散佈和收集，並循序和平行群組。</span><span class="sxs-lookup"><span data-stu-id="39222-241">Some common patterns include Aggregator, Exception Handling and Compensation, Message Broker, Scatter and Gather, and Sequential and Parallel Convoy.</span></span> <span data-ttu-id="39222-242">這些模式可以用於開發複雜的企業應用程式整合 (EAI)、 服務導向架構 (SOA) 和商務程序管理 (BPM) 解決方案與 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="39222-242">Those patterns can be utilized to develop complex Enterprise Application Integration (EAI), Service-Oriented Architecture (SOA), and Business Process Management (BPM) solutions with BizTalk Server.</span></span> <span data-ttu-id="39222-243">如需協調流程的設計模式的詳細資訊，請參閱主題[協調流程中實作設計模式](http://go.microsoft.com/fwlink/?LinkId=140042)(http://go.microsoft.com/fwlink/?LinkId=140042) BizTalk Server 文件和[模式和最佳作法企業整合](http://go.microsoft.com/fwlink/?LinkId=140043)(http://go.microsoft.com/fwlink/?LinkId=140043)。</span><span class="sxs-lookup"><span data-stu-id="39222-243">For more information about Orchestration Design Patterns, see the topic [Implementing Design Patterns in Orchestrations](http://go.microsoft.com/fwlink/?LinkId=140042) (http://go.microsoft.com/fwlink/?LinkId=140042) in the BizTalk Server documentation and [Patterns and Best Practices for Enterprise Integration](http://go.microsoft.com/fwlink/?LinkId=140043) (http://go.microsoft.com/fwlink/?LinkId=140043).</span></span>  
  
## <a name="make-appropriate-use-of-net-classes-in-orchestrations-to-maximize-performance"></a><span data-ttu-id="39222-244">將效能最大化的協調流程中進行適當地使用.NET 類別</span><span class="sxs-lookup"><span data-stu-id="39222-244">Make appropriate use of .NET classes in orchestrations to maximize performance</span></span>  
 <span data-ttu-id="39222-245">一般情況下，協調流程內使用的.NET 類別可以分成兩種不同類別：</span><span class="sxs-lookup"><span data-stu-id="39222-245">In general, the .NET classes used inside an orchestration can be divided into two distinct categories:</span></span>  
  
-   <span data-ttu-id="39222-246">**協助程式和服務-** 這些類別提供了常見的服務，例如追蹤、 錯誤處理、 快取，以及序列化/還原序列化的協調流程。</span><span class="sxs-lookup"><span data-stu-id="39222-246">**Helpers and services -** These classes provide common services to orchestrations such as tracing, error handling, caching, and serialization/deserialization.</span></span> <span data-ttu-id="39222-247">大部分的這些類別可以實作為沒有內部狀態與多個公用的靜態方法的靜態類別。</span><span class="sxs-lookup"><span data-stu-id="39222-247">Most of these classes can be implemented as static classes with no internal state and multiple public static methods.</span></span> <span data-ttu-id="39222-248">這個方法可避免在相同的時間，有助於減少主機處理序的工作空間，並節省記憶體執行不同的協調流程中建立多個物件相同的類別。</span><span class="sxs-lookup"><span data-stu-id="39222-248">This approach avoids creating multiple objects of the same class in different orchestrations running at the same time, which helps to reduce the working space of host processes and save memory.</span></span> <span data-ttu-id="39222-249">是無狀態的類別有助於減少必須序列化及已凍結的協調流程時，保存到 BizTalk MessageBox 的內部狀態的整體大小。</span><span class="sxs-lookup"><span data-stu-id="39222-249">A class that is stateless helps to reduce the overall size of the internal state that must be serialized and persisted to the BizTalk MessageBox when an orchestration is dehydrated.</span></span>  
  
-   <span data-ttu-id="39222-250">**實體和商務物件-** 您可以使用這些類別來管理實體，例如訂單、 訂單項目及客戶。</span><span class="sxs-lookup"><span data-stu-id="39222-250">**Entities and Business Objects -** You can use these classes to manage entities, such as orders, order items, and customers.</span></span> <span data-ttu-id="39222-251">單一的協調流程可以在內部建立和管理多個相同型別執行個體。</span><span class="sxs-lookup"><span data-stu-id="39222-251">A single orchestration can internally create and manage multiple instances of the same type.</span></span> <span data-ttu-id="39222-252">這些類別通常是具狀態，並且公開公用欄位及/或屬性，以及修改物件的內部狀態的方法。</span><span class="sxs-lookup"><span data-stu-id="39222-252">These classes are typically stateful, and expose public fields and/or properties along with methods to modify the internal state of the object.</span></span> <span data-ttu-id="39222-253">這些類別的執行個體可以動態地建立使用還原的 XLANGMessage 部分序列化成.NET 物件**XmlSerializer**或**DataContractSerializer**類別，或使用**XLANGPart.RetrieveAs**方法。</span><span class="sxs-lookup"><span data-stu-id="39222-253">Instances of these classes can be dynamically created by deserializing an XLANGMessage part into a .NET object by using the **XmlSerializer** or the **DataContractSerializer** classes or by using the **XLANGPart.RetrieveAs** method.</span></span> <span data-ttu-id="39222-254">您應該在建構協調流程中使用的方式，建立盡可能晚期和立即釋出不再需要具狀態的類別的執行個體的非交易式範圍。</span><span class="sxs-lookup"><span data-stu-id="39222-254">You should structure an orchestration using non-transactional scopes in such a way that instances of stateful classes are created as late as possible and released as soon as they are no longer needed.</span></span> <span data-ttu-id="39222-255">這個方法會減少主機處理序的工作空間，並會序列化並保存到 MessageBox 資料庫中，已凍結的協調流程時的內部狀態的整體大小降到最低。</span><span class="sxs-lookup"><span data-stu-id="39222-255">This approach reduces the working space of host processes and minimizes the overall size of the internal state that is serialized and persisted to the MessageBox database when an orchestration is dehydrated.</span></span> <span data-ttu-id="39222-256">如需有關如何使用 BizTalk Server 中的協調流程的詳細資訊，請參閱[BizTalk Server 協調流程的常見問題集](http://go.microsoft.com/fwlink/?LinkID=116886)(http://go.microsoft.com/fwlink/?LinkID=116886)。</span><span class="sxs-lookup"><span data-stu-id="39222-256">For more information about using orchestrations in BizTalk Server, see the article [FAQ for BizTalk Server Orchestrations](http://go.microsoft.com/fwlink/?LinkID=116886) (http://go.microsoft.com/fwlink/?LinkID=116886).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="39222-257">雖然這篇文章針對 BizTalk Server 2004 和 BizTalk Server 2006 所撰寫，所呈現的概念也適用於 BizTalk Server 2010 的協調流程。</span><span class="sxs-lookup"><span data-stu-id="39222-257">While this article is written for BizTalk Server 2004 and BizTalk Server 2006, the concepts presented also apply to BizTalk Server 2010 orchestrations.</span></span>  
  
## <a name="orchestration-exception-handler-blocks"></a><span data-ttu-id="39222-258">協調流程例外狀況處理常式區塊</span><span class="sxs-lookup"><span data-stu-id="39222-258">Orchestration Exception Handler Blocks</span></span>  
 <span data-ttu-id="39222-259">使用協調流程例外狀況處理常式區塊時, 納入一或多個領域 （盡可能非交易式範圍） 中的所有協調流程圖形，並建立至少下列的例外狀況處理常式區塊：</span><span class="sxs-lookup"><span data-stu-id="39222-259">When using Orchestration exception Handler blocks, include all orchestration shapes in one or multiple scopes (non transactional scopes whenever possible) and create at least the following exception handler blocks:</span></span>  
  
- <span data-ttu-id="39222-260">例外狀況處理常式區塊來處理一般 System.Exception 錯誤。</span><span class="sxs-lookup"><span data-stu-id="39222-260">An exception handler block for handling a generic System.Exception error.</span></span>  
  
- <span data-ttu-id="39222-261">例外狀況處理常式來處理一般的例外狀況，以攔截並處理可能未受管理的錯誤的詳細資訊，例如 COM 例外狀況區塊。</span><span class="sxs-lookup"><span data-stu-id="39222-261">An exception handler block for handling a general exception in order to catch and handle possible unmanaged errors, such as COM exceptions.</span></span>  
  
  <span data-ttu-id="39222-262">如需使用協調流程例外狀況處理區塊的詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="39222-262">For more information about using Orchestration exception handling blocks, see the following articles:</span></span>  
  
- <span data-ttu-id="39222-263">[使用 BizTalk Server 例外狀況處理](http://msdn.microsoft.com/library/aa561229.aspx)(http://msdn.microsoft.com/library/aa561229.aspx)。</span><span class="sxs-lookup"><span data-stu-id="39222-263">[Using BizTalk Server Exception Handling](http://msdn.microsoft.com/library/aa561229.aspx) (http://msdn.microsoft.com/library/aa561229.aspx).</span></span>  
  
- <span data-ttu-id="39222-264">[Charles Young 的部落格，BizTalk Server 2006： 補償模型](http://go.microsoft.com/fwlink/?LinkId=158017)(http://go.microsoft.com/fwlink/?LinkId=158017)。</span><span class="sxs-lookup"><span data-stu-id="39222-264">[Charles Young Blog, BizTalk Server 2006: The Compensation Model](http://go.microsoft.com/fwlink/?LinkId=158017) (http://go.microsoft.com/fwlink/?LinkId=158017).</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="39222-265">雖然以撰寫這篇部落格[!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)]納入考量，部落格中所述的原則也適用於 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="39222-265">While this blog was written with [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] in mind, the principles described in the blog also apply to BizTalk Server.</span></span>  
  
## <a name="considerations-when-using-maps-in-orchestrations"></a><span data-ttu-id="39222-266">使用協調流程中的對應時的考量</span><span class="sxs-lookup"><span data-stu-id="39222-266">Considerations when using maps in orchestrations</span></span>  
 <span data-ttu-id="39222-267">在 協調流程中使用對應時，就會適用下列考量：</span><span class="sxs-lookup"><span data-stu-id="39222-267">The following considerations apply when using maps in orchestrations:</span></span>  
  
-   <span data-ttu-id="39222-268">如果您使用對應擷取或設定屬性搭配協調流程中的商務邏輯使用辨別的欄位，或升級屬性。</span><span class="sxs-lookup"><span data-stu-id="39222-268">If you are using a map to extract or set properties used with business logic in an orchestration, use distinguished fields or promoted properties.</span></span> <span data-ttu-id="39222-269">應遵循此做法，因為當擷取或設定值，與對應的文件載入記憶體時使用辨別欄位或升級屬性，協調流程引擎存取的訊息內容但不會載入到記憶體中的文件。</span><span class="sxs-lookup"><span data-stu-id="39222-269">This practice should be followed because when extracting or setting values with a map the document is loaded into memory however when using distinguished fields or promoted properties, the orchestration engine accesses the message context and does not load the document into memory.</span></span>  
  
-   <span data-ttu-id="39222-270">若您使用對應將數個欄位彙總成一個欄位，請使用辨別欄位或升級屬性搭配協調流程變數，以累計結果集。</span><span class="sxs-lookup"><span data-stu-id="39222-270">If you are using a map to aggregate several fields into one field, use distinguished fields or promoted properties with an orchestration variable to accumulate the result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39222-271">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39222-271">See Also</span></span>  
 [<span data-ttu-id="39222-272">最佳化效能</span><span class="sxs-lookup"><span data-stu-id="39222-272">Optimizing Performance</span></span>](../technical-guides/optimizing-performance.md)