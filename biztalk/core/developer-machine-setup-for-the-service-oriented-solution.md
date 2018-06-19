---
title: 開發人員電腦設定為服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- developer servers
- service solution tutorial, deployment prerequisites
- service solution tutorial, developer servers
ms.assetid: a088696f-c1ee-4578-ac02-af29b6de086b
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb3407dbccbc4dccc902892cf04fa71991b8d93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239454"
---
# <a name="developer-machine-setup-for-the-service-oriented-solution"></a><span data-ttu-id="d0fb8-102">服務導向解決方案的開發人員電腦設定</span><span class="sxs-lookup"><span data-stu-id="d0fb8-102">Developer Machine Setup for the Service Oriented Solution</span></span>
<span data-ttu-id="d0fb8-103">「服務導向架構」(Service Oriented Architecture，SOA) 是一種建置分散式系統的方法。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-103">Service Oriented Architecture (SOA) is an approach to building distributed systems.</span></span> <span data-ttu-id="d0fb8-104">服務導向解決方案展示如何將數個使用不同通訊協定的後端系統彙總成用戶端可以取用的單一服務。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-104">The service oriented solution demonstrates how several back-end systems using different protocols can be aggregated into a single service that clients can consume.</span></span> <span data-ttu-id="d0fb8-105">此方案整合服務的方法也將確保您能滿足服務等級協議上的交貨及效能等特徵。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-105">This solution integrates services with an approach that guarantees delivery and performance characteristics for the service level agreement that you need to satisfy.</span></span>  
  
 <span data-ttu-id="d0fb8-106">服務導向解決方案是依照一個服務等級協議實例來建立模型，此實例會給定三秒的時間，讓 BizTalk Server 和連線於此的商務營運系統 (LOB) 應用程式伺服器可以回應服務要求。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-106">The service oriented solution is modeled after a service-level agreement scenario in which BizTalk Server and the Line of Business (LOB) application servers connected to it are given three seconds to respond with a service request.</span></span> <span data-ttu-id="d0fb8-107">這三秒中有一秒可能會給 BizTalk Server 佔用。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-107">One of those three seconds may be taken up by the BizTalk Server.</span></span>  
  
 <span data-ttu-id="d0fb8-108">有三個版本的服務導向解決方案： 配接器、 內嵌和虛設常式。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-108">There are three versions of the service oriented solution: adapter, inline, and stub.</span></span> <span data-ttu-id="d0fb8-109">如需服務導向解決方案的三個版本之間差異的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-109">For more information about the differences between three versions of the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span> <span data-ttu-id="d0fb8-110">如果您是開發人員，請取得使用虛設常式版實例執行的實例。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-110">As a developer, you get the scenario running by using the stub version of the scenario.</span></span> <span data-ttu-id="d0fb8-111">這個版本無須使用任何 LOB 後端伺服器即可執行。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-111">This version does not require any LOB back-end servers in order to run.</span></span> <span data-ttu-id="d0fb8-112">在此之後，您可以使用配接器版本的實例，學習如何整合各種配接器與後端伺服器，以及如何設定它們使用 BizTalk 伺服器做為單一服務以進行回應。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-112">After this you can use the adapter version of the scenario to learn how various adapters and back-end servers can be integrated and configured to respond using the BizTalk servers as a single service.</span></span> <span data-ttu-id="d0fb8-113">然後您可以衡量由 BizTalk Server 及其配接器所造成的延遲。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-113">You can then measure the latency induced by BizTalk Server and its adapters.</span></span>  
  
 <span data-ttu-id="d0fb8-114">如果 BizTalk 伺服器延遲超過服務需求，您可以安裝並執行 SOA 內嵌版本，以略過 LOB 配接器持續點。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-114">If the latency for the BizTalk server is in excess of its service requirement, you can bypass the LOB adapter persistence points by installing and running the SOA in-line version.</span></span> <span data-ttu-id="d0fb8-115">由於 MessageBox 持續點的作用，此版本會略過配接器，從而略過這些配接器的延遲比重。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-115">This version bypasses the adapters and subsequently their latency contributions due to the MessageBox persistence point.</span></span> <span data-ttu-id="d0fb8-116">內嵌版本則不同，它會透過「遠端程序呼叫」(RPC) 機制 (如 DCOM)，與後端伺服器直接交談。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-116">Instead, the inline version talks straight to the back-end servers through Remote Procedure Calls (RPC) mechanisms such as DCOM.</span></span>  
  
 <span data-ttu-id="d0fb8-117">如需 MessageBox 持續點的詳細資訊，請參閱[持續性和協調流程引擎](../core/persistence-and-the-orchestration-engine.md)。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-117">For more information about the MessageBox persistence point, see [Persistence and the Orchestration Engine](../core/persistence-and-the-orchestration-engine.md).</span></span>  
  
 <span data-ttu-id="d0fb8-118">這份部署指南說明如何在單一電腦上安裝與測試服務導向解決方案的三個版本。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-118">This deployment guide describes how to install and test the three versions of the service-oriented solution on a single computer.</span></span>  
  
 <span data-ttu-id="d0fb8-119">如需有關服務導向解決方案的詳細資訊，請參閱[瞭解服務導向解決方案](../core/understanding-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="d0fb8-119">For more information about the service-oriented solution, see [Understanding the Service Oriented Solution](../core/understanding-the-service-oriented-solution.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0fb8-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="d0fb8-120">In This Section</span></span>  
  
-   [<span data-ttu-id="d0fb8-121">然後再安裝服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="d0fb8-121">Before Installing the Service Oriented Solution</span></span>](../core/before-installing-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="d0fb8-122">How to Install 虛設常式版本的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="d0fb8-122">How to Install the Stub Version of the Service Oriented Solution</span></span>](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="d0fb8-123">如何安裝內嵌和配接器版本的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="d0fb8-123">How to Install the Inline and Adapter Versions of the Service Oriented Solution</span></span>](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md)  
  
-   [<span data-ttu-id="d0fb8-124">如何執行服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="d0fb8-124">How to Run the Service Oriented Solution</span></span>](../core/how-to-run-the-service-oriented-solution.md)