---
title: "減少傳輸類型與處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transport types, decoupling processing
- processing, decoupling transport types
- transport types
- transport types, service solutions
- service solution tutorial, MQSeries adapters
- processing, service solutions
- service solution tutorial, decoupling transport type and processing
- correlations, MQSeries adapters
- MQSeries adapters, correlations
- MQSeries adapters, service solutions
ms.assetid: 0b2c733a-e2c7-42ff-a733-f712fde38f7e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b14522c6bbf9393bc22f632c4db5eeb5e4a22a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="decoupling-transport-type-and-processing"></a><span data-ttu-id="0daa9-102">減少傳輸類型與處理</span><span class="sxs-lookup"><span data-stu-id="0daa9-102">Decoupling Transport Type and Processing</span></span>
<span data-ttu-id="0daa9-103">在服務導向解決方案中，清除線段經常存在於商務程序與特定的傳輸及接收訊息之間。</span><span class="sxs-lookup"><span data-stu-id="0daa9-103">In a service oriented solution, a clear line often exists between the business processing and the specifics of transmitting and receiving messages.</span></span> <span data-ttu-id="0daa9-104">這讓您能單獨變更解決方案的商務程序或訊息部分。</span><span class="sxs-lookup"><span data-stu-id="0daa9-104">This enables you to change the business process or the messaging part of the solution independently.</span></span>  
  
 <span data-ttu-id="0daa9-105">服務導向解決方案會在某個地方違反此設計原則。</span><span class="sxs-lookup"><span data-stu-id="0daa9-105">The service oriented solution violates this design principle in one place.</span></span> <span data-ttu-id="0daa9-106">本節將描述此情況、可能的替代方案以及選取的結構。</span><span class="sxs-lookup"><span data-stu-id="0daa9-106">This section describes the situation, the possible alternatives, and the selected structure.</span></span>  
  
## <a name="correlation-and-the-mqseries-adapter"></a><span data-ttu-id="0daa9-107">相互關聯與 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="0daa9-107">Correlation and the MQSeries Adapter</span></span>  
 <span data-ttu-id="0daa9-108">為了使用 MQSeries 配接器，您無法使用標準的 BizTalk Server 相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="0daa9-108">In order to use the MQSeries adapter, you cannot use the standard BizTalk Server correlation identifiers.</span></span> <span data-ttu-id="0daa9-109">這是因為相互關聯識別碼會進入 IBM 後端系統，而該系統會有自己的相互關聯識別碼系統。</span><span class="sxs-lookup"><span data-stu-id="0daa9-109">This is because the correlation identifier goes to an IBM back-end system that has its own system of correlation identifiers.</span></span> <span data-ttu-id="0daa9-110">相反地，您必須使用**MQSeries.MQMD_CorrelId**和**MQSeries.MQMD_MsgID**屬性。</span><span class="sxs-lookup"><span data-stu-id="0daa9-110">Instead, you must use the **MQSeries.MQMD_CorrelId** and **MQSeries.MQMD_MsgID** properties.</span></span> <span data-ttu-id="0daa9-111">使用這些屬性會潛在地將傳輸專用的資訊置於協調流程與商務程序中。</span><span class="sxs-lookup"><span data-stu-id="0daa9-111">Using these properties potentially puts transport-specific information in the orchestration and, thus, in the business process.</span></span>  
  
 <span data-ttu-id="0daa9-112">處理此相依性的一種方法便是使用 BizTalk Server 相互關聯識別碼，並使用自訂管線元件來轉譯 MQSeries 的相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="0daa9-112">One way to handle this dependency would be to use the BizTalk Server correlation identifier and use a custom pipeline component to translate the correlation identifier for MQSeries.</span></span> <span data-ttu-id="0daa9-113">這會增加實例的複雜度。</span><span class="sxs-lookup"><span data-stu-id="0daa9-113">This adds complexity to the scenario.</span></span> <span data-ttu-id="0daa9-114">此外，若傳輸變更時，必須變更兩個管線元件。</span><span class="sxs-lookup"><span data-stu-id="0daa9-114">In addition, if the transport changes, two pipeline components must be changed.</span></span> <span data-ttu-id="0daa9-115">而且，最後它會重新定位相依性 (位於管線元件中)，而不是解析它。</span><span class="sxs-lookup"><span data-stu-id="0daa9-115">And, ultimately, it relocates the dependency (in the pipeline component) rather than resolving it.</span></span>  
  
 <span data-ttu-id="0daa9-116">另一個選項便是隔離 MQSeries 專用的相互關聯處理，以隔離協調流程及呼叫該協調流程。</span><span class="sxs-lookup"><span data-stu-id="0daa9-116">Another option would be to isolate the MQSeries-specific correlation handling to a separate orchestration and call that orchestration.</span></span> <span data-ttu-id="0daa9-117">這會保留商務程序的獨立性。</span><span class="sxs-lookup"><span data-stu-id="0daa9-117">This would preserve the independence of the business process.</span></span> <span data-ttu-id="0daa9-118">不過，這會在協調流程之間引入編譯階段相依性。</span><span class="sxs-lookup"><span data-stu-id="0daa9-118">However, this introduces a compile-time dependency between the orchestrations.</span></span> <span data-ttu-id="0daa9-119">修改傳輸需要重新編譯兩個協調流程 (例如，從虛設常式到解決方案的配接器版本)。</span><span class="sxs-lookup"><span data-stu-id="0daa9-119">Modifying the transport requires recompiling both orchestrations (as, for example, in going from the stub to the adapter version of the solution).</span></span> <span data-ttu-id="0daa9-120">該呼叫也會增加解決方案的回應時間。</span><span class="sxs-lookup"><span data-stu-id="0daa9-120">The call also adds to the response time for the solution.</span></span>  
  
 <span data-ttu-id="0daa9-121">為了避免增加額外的複雜度和可能降低效能，直接在協調流程中使用 MQSeries 相互關聯似乎是最簡易的。</span><span class="sxs-lookup"><span data-stu-id="0daa9-121">Given the additional complexity and possible decrease in performance, it seemed simplest to use the MQSeries correlation directly in the orchestration.</span></span>  
  
 <span data-ttu-id="0daa9-122">如需配接器和協調流程中的相互關聯的詳細資訊，請參閱[MQSCorrelationSetOrchestration （BizTalk Server 範例）](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="0daa9-122">For more information about the adapter and correlations in orchestrations, see [MQSCorrelationSetOrchestration (BizTalk Server Sample)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0daa9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0daa9-123">See Also</span></span>  
 <span data-ttu-id="0daa9-124">[實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="0daa9-124">[Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="0daa9-125">MQSCorrelationSetOrchestration （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="0daa9-125">MQSCorrelationSetOrchestration (BizTalk Server Sample)</span></span>](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)