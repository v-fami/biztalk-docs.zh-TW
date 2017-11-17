---
title: "實作會反白顯示的服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, performance
- performance, service solutions
- service solution tutorial, implementing
ms.assetid: 3dbd8dfd-45b7-4290-ba07-b0c5e6264629
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c593c24c72e5666525001e6a52e2b0bf6eac2de
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-highlights-of-the-service-oriented-solution"></a><span data-ttu-id="c9e88-102">實作會反白顯示的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="c9e88-102">Implementation Highlights of the Service Oriented Solution</span></span>
<span data-ttu-id="c9e88-103">解決特定內容中的特定問題之解決方案。</span><span class="sxs-lookup"><span data-stu-id="c9e88-103">A solution solves a particular problem in a specific context.</span></span> <span data-ttu-id="c9e88-104">服務導向解決方案也不例外，且專用於 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和此實例。</span><span class="sxs-lookup"><span data-stu-id="c9e88-104">The Service Oriented solution is no exception and is specific to Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and the scenario.</span></span> <span data-ttu-id="c9e88-105">如需 Woodgrove Bank 案例的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="c9e88-105">For more information about the Woodgrove Bank scenario, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span>  
  
 <span data-ttu-id="c9e88-106">開發此實例時，有幾個層面已經證實為減少回應時間至可接受層級的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="c9e88-106">While developing the scenario, several areas proved to be bottlenecks in reducing response times to an acceptable level.</span></span> <span data-ttu-id="c9e88-107">使用配接器傳送訊息至後端系統，會在取得回應時造成顯著的延遲。</span><span class="sxs-lookup"><span data-stu-id="c9e88-107">Sending messages to the backend systems using the adapters introduces significant latency in getting back responses.</span></span> <span data-ttu-id="c9e88-108">一般而言，配接器本身造成極少延遲。</span><span class="sxs-lookup"><span data-stu-id="c9e88-108">In general, adapters by themselves offer very low latency.</span></span> <span data-ttu-id="c9e88-109">不過，BizTalk 的分散式架構需要配接器使用 MessageBox 與協調流程主控件執行個體通訊。</span><span class="sxs-lookup"><span data-stu-id="c9e88-109">However, the distributed architecture of BizTalk requires adapters to communicate with the orchestration host instances using the message box.</span></span> <span data-ttu-id="c9e88-110">這將造成需往返資料庫，並影響延遲時間。</span><span class="sxs-lookup"><span data-stu-id="c9e88-110">This introduces round trips to the database and affects latency times.</span></span> <span data-ttu-id="c9e88-111">基於這個原因，此解決方案的內嵌版本 (最快速的版本) 在協調流程本身建置可直接呼叫後端系統的配接器功能。</span><span class="sxs-lookup"><span data-stu-id="c9e88-111">For this reason, the inline version of the solution (the fastest version) builds the adapter functionality in the orchestration itself calls the back-end systems directly.</span></span> <span data-ttu-id="c9e88-112">後端系統有三種，這表示有三種可能的不同機制可以和後端系統通訊。</span><span class="sxs-lookup"><span data-stu-id="c9e88-112">With three different back-end systems, that means potentially three different mechanisms to communicate with the back-end systems.</span></span>  
  
 <span data-ttu-id="c9e88-113">另一個已證實有效能問題的層面是從「企業單一登入」(SSO) 擷取組態資料。</span><span class="sxs-lookup"><span data-stu-id="c9e88-113">Another area that proved a performance problem was retrieving configuration data from Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="c9e88-114">若要加速擷取時間時保留為了方便和普遍性的 SSO，解決方案會使用本機快取組態值。</span><span class="sxs-lookup"><span data-stu-id="c9e88-114">To retain the convenience and universality of SSO while speeding up retrieval time, the solution uses a local cache for configuration values.</span></span> <span data-ttu-id="c9e88-115">使用 SSO 也能讓您更容易管理組態資料。</span><span class="sxs-lookup"><span data-stu-id="c9e88-115">Using SSO also allows easier management of the configuration data.</span></span> <span data-ttu-id="c9e88-116">您不需在執行主控件執行個體的伺服器上變更設定，就能新增其他主控件執行個體以滿足延遲與效能需求。</span><span class="sxs-lookup"><span data-stu-id="c9e88-116">Adding additional host instances to meet latency and performance requirements does not require changing settings on the server running the host instance.</span></span>  
  
 <span data-ttu-id="c9e88-117">此解決方案的另一個特殊項目是可直接從程式碼呼叫管線。</span><span class="sxs-lookup"><span data-stu-id="c9e88-117">Another unusual element of the solution is calling pipelines directly from code.</span></span> <span data-ttu-id="c9e88-118">這可以讓您重複使用自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="c9e88-118">This allows reuse of the custom pipeline components.</span></span>  
  
 <span data-ttu-id="c9e88-119">最後，您可以變更數個 BizTalk Server 設定，以從這個解決方案提升其他效能。</span><span class="sxs-lookup"><span data-stu-id="c9e88-119">Finally, there are several BizTalk Server settings that you can change to squeeze out the last bit of speed from the solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c9e88-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="c9e88-120">In This Section</span></span>  
  
-   [<span data-ttu-id="c9e88-121">內嵌後端叫用</span><span class="sxs-lookup"><span data-stu-id="c9e88-121">Inlining Back-end Invocation</span></span>](../core/inlining-back-end-invocation.md)  
  
-   [<span data-ttu-id="c9e88-122">有效使用 SSO，在服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="c9e88-122">Using SSO Efficiently in the Service Oriented Solution</span></span>](../core/using-sso-efficiently-in-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="c9e88-123">使用管線從服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="c9e88-123">Using Pipelines from the Service Oriented Solution</span></span>](../core/using-pipelines-from-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="c9e88-124">調整服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="c9e88-124">Tuning the Service Oriented Solution</span></span>](../core/tuning-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="c9e88-125">減少傳輸類型與處理</span><span class="sxs-lookup"><span data-stu-id="c9e88-125">Decoupling Transport Type and Processing</span></span>](../core/decoupling-transport-type-and-processing.md)