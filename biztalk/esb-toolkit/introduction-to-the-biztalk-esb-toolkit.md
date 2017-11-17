---
title: "BizTalk ESB 工具組簡介 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ESBToolkitV2.introduction
ms.assetid: 98a957b8-5855-4872-b7e7-58a2e1d6b2b8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9763e55c44fc3ea45ab93127ffae8c9c742f0dc9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="introduction-to-the-biztalk-esb-toolkit"></a><span data-ttu-id="bf43e-102">BizTalk ESB 工具組簡介</span><span class="sxs-lookup"><span data-stu-id="bf43e-102">Introduction to the BizTalk ESB Toolkit</span></span>
<span data-ttu-id="bf43e-103">說明的架構和 Microsoft 內容[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="bf43e-103">Explains the architecture and contents of the Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="bf43e-104">文件也會示範如何套用開發企業應用程式，請啟用彈性且更安全的企業服務匯流排 (ESB) 架構模式和可重複使用的服務，以及快速組織現有服務的新端對端商務程序。</span><span class="sxs-lookup"><span data-stu-id="bf43e-104">The documentation also demonstrates how to apply an Enterprise Service Bus (ESB) architecture pattern to develop enterprise applications that enable flexible, secure, and reusable services and rapid organization of existing services into new end-to-end business processes.</span></span>  
  
## <a name="what-is-an-enterprise-service-bus"></a><span data-ttu-id="bf43e-105">什麼是企業服務匯流排？</span><span class="sxs-lookup"><span data-stu-id="bf43e-105">What Is an Enterprise Service Bus?</span></span>  
 <span data-ttu-id="bf43e-106">企業服務匯流排廣泛使用的實作基礎結構啟用 Service-Oriented 架構 (SOA) 的內容中的詞彙。</span><span class="sxs-lookup"><span data-stu-id="bf43e-106">The term Enterprise Service Bus is widely used in the context of implementing an infrastructure for enabling Service-Oriented Architecture (SOA).</span></span> <span data-ttu-id="bf43e-107">不過，SOA 方案部署的實際經驗已經示範 ESB 是建置完整 Service-Oriented 基礎結構 (SOI) 所需的許多元件的其中之一。</span><span class="sxs-lookup"><span data-stu-id="bf43e-107">However, real-world experience with the deployment of SOA solutions has demonstrated that an ESB is only one of many components required to build a comprehensive Service-Oriented Infrastructure (SOI).</span></span> <span data-ttu-id="bf43e-108">中的數字的方向發展"ESB 」 一詞，其定義不同的個別 ESB 和整合平台供應商的解譯與特定的 SOA 開發案的需求。</span><span class="sxs-lookup"><span data-stu-id="bf43e-108">The term "ESB" has evolved in a number of directions—its definition varies with the interpretation of individual ESB and integration platform vendors and with the requirements of particular SOA initiatives.</span></span>  
  
 <span data-ttu-id="bf43e-109">根據 Microsoft 已收集了與許多成功的真實世界 SOI 實作的經驗，Microsoft 會視為是集合的架構模式基礎上傳統企業應用程式整合 (EAI)，企業服務匯流排訊息導向中介軟體、 Web 服務、.NET 和 Java 的互通性、 主機系統整合，以及與服務和資產的儲存機制的互通性。</span><span class="sxs-lookup"><span data-stu-id="bf43e-109">Based on the experience Microsoft has gathered from many successful real-world SOI implementations, Microsoft considers an Enterprise Service Bus to be a collection of architectural patterns based on traditional Enterprise Application Integration (EAI), message-oriented middleware, Web services, .NET and Java interoperability, host system integration, and interoperability with service registries and asset repositories.</span></span> <span data-ttu-id="bf43e-110">圖 1 說明企業服務匯流排的架構。</span><span class="sxs-lookup"><span data-stu-id="bf43e-110">Figure 1 illustrates the architecture of an Enterprise Service Bus.</span></span>  
  
 <span data-ttu-id="bf43e-111">![ESB 概觀](../esb-toolkit/media/esboverview.gif "ESBOverview")</span><span class="sxs-lookup"><span data-stu-id="bf43e-111">![ESB Overview](../esb-toolkit/media/esboverview.gif "ESBOverview")</span></span>  
  
 <span data-ttu-id="bf43e-112">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="bf43e-112">**Figure 1**</span></span>  
  
 <span data-ttu-id="bf43e-113">**企業服務匯流排架構所提供的連線的高層級表示法**</span><span class="sxs-lookup"><span data-stu-id="bf43e-113">**A high-level representation of the connectivity provided by the Enterprise Service Bus architecture**</span></span>  

<span data-ttu-id="bf43e-114">\<！---舊文字與舊的連結</span><span class="sxs-lookup"><span data-stu-id="bf43e-114">\<!---  Old text with old links</span></span>
## <a name="the-industry-view-of-esb"></a><span data-ttu-id="bf43e-115">ESB [產業] 檢視</span><span class="sxs-lookup"><span data-stu-id="bf43e-115">The Industry View of ESB</span></span>  
 <span data-ttu-id="bf43e-116">有許多相關的資訊來源 ESB 設計、 架構、 基礎結構，以及實作從業界供應商、 系統整合者和獨立的來源。</span><span class="sxs-lookup"><span data-stu-id="bf43e-116">There are many sources of information about ESB design, architecture, infrastructure, and implementation available from industry suppliers, system integrators, and independent sources.</span></span>  
<span data-ttu-id="bf43e-117">-->
\<!---</span><span class="sxs-lookup"><span data-stu-id="bf43e-117">-->
\<!---</span></span>    
 <span data-ttu-id="bf43e-118">IBM 定義 ESB 做為系統，"...enables 商務，讓使用完整、 具彈性，且一致的方法到整合，同時還可降低要整合的應用程式的複雜性。</span><span class="sxs-lookup"><span data-stu-id="bf43e-118">IBM defines ESB as a system that "...enables a business to make use of a comprehensive, flexible, and consistent approach to integration while also reducing the complexity of the applications being integrated.</span></span> <span data-ttu-id="bf43e-119">由於的複雜且不同的商務需求，ESB 統一訊息導向 evolutional 進展，導向事件和服務導向整合的應用程式和服務的方法。 」</span><span class="sxs-lookup"><span data-stu-id="bf43e-119">Due to the complex and varying nature of business needs, ESB is an evolutional progression that unifies message oriented, event driven and service oriented approaches for integrating applications and service."</span></span> <span data-ttu-id="bf43e-120">IBM 說明優點為"...greater 重複使用的分隔應用程式 logics 和整合工作，以便您可以減少數目、 大小和整合介面的複雜性 IT 資產"以及"..搭配最低限度的.add 或變更服務中斷現有的 IT 環境。降低成本和商務的變更所涉及的風險和新的機會發生 」。</span><span class="sxs-lookup"><span data-stu-id="bf43e-120">IBM describes the advantages as "...greater reuse of IT assets by separating application logics and integration tasks, so you can reduce the number, size, and complexity of integration interfaces," and the ability to "...add or change services with minimal interruption to existing IT environment; reduce cost and risk involved as business changes and new opportunities arise."</span></span> <span data-ttu-id="bf43e-121">如需詳細資訊，請參閱[WebSphere 軟體](http://go.microsoft.com/fwlink/p/?LinkId=185958)([http://go.microsoft.com/fwlink/p/?LinkId=185958](http://go.microsoft.com/fwlink/p/?LinkId=185958)) IBM 網站上。</span><span class="sxs-lookup"><span data-stu-id="bf43e-121">For more information, see [WebSphere software](http://go.microsoft.com/fwlink/p/?LinkId=185958)([http://go.microsoft.com/fwlink/p/?LinkId=185958](http://go.microsoft.com/fwlink/p/?LinkId=185958))on the IBM Web site.</span></span>  
<span data-ttu-id="bf43e-122">-->
\<！---舊文字的舊 Sonic 解決方案提供 ESB，全面探討討論的主要層面和它的連結和商業優勢。</span><span class="sxs-lookup"><span data-stu-id="bf43e-122">-->
\<!---    Old text with old links Sonic Solutions provide a comprehensive examination of ESB, discussing the principle aspects, and the IT and business benefits.</span></span> <span data-ttu-id="bf43e-123">這些主題說明 ESB 的需求: 「 若要將舊的和新的整合，服務導向架構 (SOA) 需要可以連接任何 IT 資源，無論基礎結構內技術或部署的任一處。"</span><span class="sxs-lookup"><span data-stu-id="bf43e-123">They describe the requirement for ESB: "To integrate old and new, service-oriented architecture (SOA) needs an infrastructure that can connect any IT resource, whatever its technology or wherever it is deployed."</span></span> <span data-ttu-id="bf43e-124">如需詳細資訊，請參閱[企業服務匯流排 (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185959)([http://go.microsoft.com/fwlink/p/?LinkId=185959](http://go.microsoft.com/fwlink/p/?LinkId=185959)) Sonic 解決方案網站上。</span><span class="sxs-lookup"><span data-stu-id="bf43e-124">For more information, see [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185959)([http://go.microsoft.com/fwlink/p/?LinkId=185959](http://go.microsoft.com/fwlink/p/?LinkId=185959)) on the Sonic Solutions Web site.</span></span>  
<span data-ttu-id="bf43e-125">-->
\<！---與舊連結 TIBCO 軟體的舊文字定義為 ESB"...a 標準為基礎的通訊層中的服務導向架構 (SOA)，可讓服務可用於跨多個通訊協定 [] 簡化服務部署和管理，並將升級服務在異質環境中的重複使用。 」</span><span class="sxs-lookup"><span data-stu-id="bf43e-125">-->
\<!---    Old text with old links TIBCO Software define ESB as "...a standards-based communication layer in a service- oriented architecture (SOA) that enables services to be used across multiple communication protocols [to] simplify service deployment and management, and promote service reuse in a heterogeneous environment."</span></span> <span data-ttu-id="bf43e-126">這些建議，為了提供這些功能，Esb"...support 都屬開放式標準與專利技術，包括 Web 服務和 UDDI 為基礎的登錄，才能探索及發佈服務、 Java 訊息服務 (JMS) 和其他廣泛的已部署訊息通訊協定、 標準式 (XML) 轉換和基本的訊息路由。 」</span><span class="sxs-lookup"><span data-stu-id="bf43e-126">They suggest, in order to provide these capabilities, ESBs "...support both open standards and proprietary technologies, including Web services and UDDI-based registries to discover and publish services, Java Message Service (JMS) and other widely deployed messaging protocols, standards-based (XML) transformations, and basic message routing."</span></span> <span data-ttu-id="bf43e-127">如需詳細資訊，請參閱[企業服務匯流排 (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185960)([http://go.microsoft.com/fwlink/?LinkId=185960](http://go.microsoft.com/fwlink/p/?LinkId=185960)) TIBCO 網站上。</span><span class="sxs-lookup"><span data-stu-id="bf43e-127">For more information, see [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185960)([http://go.microsoft.com/fwlink/?LinkId=185960](http://go.microsoft.com/fwlink/p/?LinkId=185960)) on the TIBCO Web site.</span></span>  
<span data-ttu-id="bf43e-128">-->
\<！---作者為 David Chappell 陳述，舊的連結，在他的書籍，企業服務匯流排，描述中的舊文字 」 而不是比傳統的企業應用程式整合產品的中樞和支點架構符合，ESB 提供高分散式的方式整合。 」</span><span class="sxs-lookup"><span data-stu-id="bf43e-128">-->
\<!---    Old text with old links In the description of his book, Enterprise Service Bus, author David Chappell states that "Rather than conform to the hub-and-spoke architecture of traditional enterprise application integration products, ESB provides a highly distributed approach to integration."</span></span> <span data-ttu-id="bf43e-129">他將新增 「 … with 獨特功能，可以讓個別的部門或業務單位來建置出其整合中的專案、 累加且容易吸收的區塊，同時仍然能夠連接在一起維護自己的本機控制項和自主性，每個整合專案到較大、 更通用整合網狀架構或方格。 」</span><span class="sxs-lookup"><span data-stu-id="bf43e-129">He adds "...with unique capabilities that allow individual departments or business units to build out their integration projects in incremental, digestible chunks, maintaining their own local control and autonomy, while still being able to connect together each integration project into a larger, more global integration fabric, or grid."</span></span> <span data-ttu-id="bf43e-130">如需詳細資訊，請參閱 David Chappell 所著的企業服務匯流排：</span><span class="sxs-lookup"><span data-stu-id="bf43e-130">For more information, see Enterprise Service Bus by David Chappell:</span></span>  
<span data-ttu-id="bf43e-131">-->
\<！---舊文字與舊的連結</span><span class="sxs-lookup"><span data-stu-id="bf43e-131">-->
\<!---    Old text with old links</span></span>
-   <span data-ttu-id="bf43e-132">David Chappell</span><span class="sxs-lookup"><span data-stu-id="bf43e-132">Chappell, David.</span></span> <span data-ttu-id="bf43e-133">企業服務匯流排。</span><span class="sxs-lookup"><span data-stu-id="bf43e-133">Enterprise Service Bus.</span></span> <span data-ttu-id="bf43e-134">O'Reilly Media，Inc.Sebastopol、 CA:2004.</span><span class="sxs-lookup"><span data-stu-id="bf43e-134">Sebastopol, CA: O'Reilly Media, Inc. 2004.</span></span>  
-->

  
## <a name="the-biztalk-esb-toolkit"></a><span data-ttu-id="bf43e-135">BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="bf43e-135">The BizTalk ESB Toolkit</span></span>
 <span data-ttu-id="bf43e-136">本文件中的，整個導入了架構設計人員和開發人員 ESB 架構概念因為收件者所[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，並說明 ESB 元件，透過一組普遍接受的 ESB 使用案例的功能。</span><span class="sxs-lookup"><span data-stu-id="bf43e-136">This documentation, as a whole, introduces architects and developers to ESB architectural concepts as addressed by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and explains the functionality of the ESB components through a set of commonly accepted ESB use cases.</span></span>  
  
 <span data-ttu-id="bf43e-137">本節介紹[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，並包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="bf43e-137">This section provides an introduction to the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and includes the following topics:</span></span>  
  
-   [<span data-ttu-id="bf43e-138">BizTalk ESB 工具組的概觀</span><span class="sxs-lookup"><span data-stu-id="bf43e-138">Overview of the BizTalk ESB Toolkit</span></span>](../esb-toolkit/overview-of-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="bf43e-139">BizTalk ESB 工具組的內容</span><span class="sxs-lookup"><span data-stu-id="bf43e-139">Contents of the BizTalk ESB Toolkit</span></span>](../esb-toolkit/contents-of-the-biztalk-esb-toolkit.md)  
  
 <span data-ttu-id="bf43e-140">這份文件也包含下列主題章節：</span><span class="sxs-lookup"><span data-stu-id="bf43e-140">This documentation also includes the following topic sections:</span></span>  
  
-   [<span data-ttu-id="bf43e-141">開始使用 BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="bf43e-141">Getting Started with the BizTalk ESB Toolkit</span></span>](../esb-toolkit/getting-started-with-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="bf43e-142">重要案例及開發工作</span><span class="sxs-lookup"><span data-stu-id="bf43e-142">Key Scenarios and Development Tasks</span></span>](../esb-toolkit/key-scenarios-and-development-tasks.md)  
  
-   [<span data-ttu-id="bf43e-143">建立行程使用路線設計工具</span><span class="sxs-lookup"><span data-stu-id="bf43e-143">Creating Itineraries Using Itinerary Designer</span></span>](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)  
  
-   [<span data-ttu-id="bf43e-144">BizTalk ESB 工具組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="bf43e-144">BizTalk ESB Toolkit Sample Applications</span></span>](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)  
  
-   [<span data-ttu-id="bf43e-145">修改和擴充 BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="bf43e-145">Modifying and Extending the BizTalk ESB Toolkit</span></span>](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="bf43e-146">使用 BizTalk ESB 工具組系統管理</span><span class="sxs-lookup"><span data-stu-id="bf43e-146">Administration with the BizTalk ESB Toolkit</span></span>](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)  
  
-   [<span data-ttu-id="bf43e-147">SOA 控管整合</span><span class="sxs-lookup"><span data-stu-id="bf43e-147">SOA Governance Integration</span></span>](../esb-toolkit/soa-governance-integration.md)  
  
-   [<span data-ttu-id="bf43e-148">疑難排解</span><span class="sxs-lookup"><span data-stu-id="bf43e-148">Troubleshooting</span></span>](../esb-toolkit/troubleshooting-the-biztalk-esb-toolkit.md)