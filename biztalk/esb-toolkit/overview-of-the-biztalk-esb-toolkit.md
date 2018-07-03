---
title: 在 BizTalk Server 中的 ESB 工具組的概觀 |Microsoft Docs
description: ESB 工具組和它會在 BizTalk Server 中的說明
caps.latest.revision: 6
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e190b34-40bc-4f27-9b4f-56e98591e1d4
ms.author: mandia
ms.openlocfilehash: 404e93739d45cbca0235990dc7d2014bf38e0a84
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008783"
---
# <a name="what-is-the-biztalk-esb-toolkit"></a><span data-ttu-id="ae840-103">什麼是 BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="ae840-103">What is the BizTalk ESB Toolkit</span></span>

## <a name="overview"></a><span data-ttu-id="ae840-104">概觀</span><span class="sxs-lookup"><span data-stu-id="ae840-104">Overview</span></span>
<span data-ttu-id="ae840-105">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk server 功能，以支援鬆散偶合的傳訊架構。</span><span class="sxs-lookup"><span data-stu-id="ae840-105">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the capabilities of BizTalk Server to support a loosely coupled messaging architecture.</span></span> <span data-ttu-id="ae840-106">大部分的開發人員熟悉程式碼導向、 程序，或物件導向的開發架構。</span><span class="sxs-lookup"><span data-stu-id="ae840-106">Most developers are familiar with code-oriented, procedural, or object-oriented development paradigms.</span></span> <span data-ttu-id="ae840-107">不過，當開始來開發 BizTalk 解決方案時，開發人員會嘗試尋找 BizTalk Server 的訊息導向功能。</span><span class="sxs-lookup"><span data-stu-id="ae840-107">However, when starting to develop BizTalk solutions, developers tend to overlook the message-oriented capabilities of BizTalk Server.</span></span>  
  
 <span data-ttu-id="ae840-108">BizTalk Server 包含功能強大的發佈/訂閱機制的運作方式是建立並填入訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="ae840-108">BizTalk Server includes a powerful publish/subscribe mechanism that works by creating and filling subscriptions.</span></span> <span data-ttu-id="ae840-109">當新的訊息抵達 BizTalk Message Box 資料庫中時，訊息代理程式會識別訂閱者，並將訊息傳送至任何有訂用帳戶的端點。</span><span class="sxs-lookup"><span data-stu-id="ae840-109">When a new message arrives in the BizTalk Message Box database, a message agent identifies subscribers and sends the message to any endpoints that have subscriptions.</span></span> <span data-ttu-id="ae840-110">訂用帳戶可以建立數種方式，包括繫結至接收埠，讓等待的訊息，或建立傳送埠與篩選條件，符合的屬性 （例如類型、 接收訊息的相互關聯的接收的協調流程點或路由傳送的屬性的值）。</span><span class="sxs-lookup"><span data-stu-id="ae840-110">Subscriptions can be created in several ways, including binding an orchestration to a receive port, having a correlated receive waiting for a message, or creating a send port with a filter condition that matches a property of the message (such as the type, the receive point, or the value of a routable property).</span></span>  
  
 <span data-ttu-id="ae840-111">藉此有效率且可調整的方法，BizTalk Server 可讓開發人員若要建立一系列的不連續的子處理序，定義其引動過程，觸發程序，而不必擔心有關順序的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="ae840-111">By providing this efficient and scalable approach, BizTalk Server enables developers to create a series of discrete sub-processes, define the types of messages that trigger their invocation, and not worry about the sequence.</span></span> <span data-ttu-id="ae840-112">處理程序起始訊息到達的訊息; 上執行其處理它會處理訊息之後，它可以提供這個或另一個訊息至 Messagebox 資料庫，這反而可能會啟動一個以上的子處理序。</span><span class="sxs-lookup"><span data-stu-id="ae840-112">A process initiated by the arrival of a message performs its processing on the message; after it processes the message, it can deliver this or another message to the Message Box database, which, in turn, may activate one or more sub-processes.</span></span>  
  
 <span data-ttu-id="ae840-113">Microsoft 會提供所需的建置完整的服務導向基礎結構，包括 Windows Server、.NET Framework，以及 BizTalk Server 的主要建置組塊。</span><span class="sxs-lookup"><span data-stu-id="ae840-113">Microsoft provides key building blocks that are required for building comprehensive Service-Oriented Infrastructures, including Windows Server, the .NET Framework, and BizTalk Server.</span></span> <span data-ttu-id="ae840-114">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]因為它提供的最常見的 ESB 服務，包括下列的基礎，根據 BizTalk Server:</span><span class="sxs-lookup"><span data-stu-id="ae840-114">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is based on BizTalk Server because it provides the basis for the most common ESB services, including the following:</span></span>  
  
-   <span data-ttu-id="ae840-115">訊息路由</span><span class="sxs-lookup"><span data-stu-id="ae840-115">Message routing</span></span>  
  
-   <span data-ttu-id="ae840-116">訊息驗證</span><span class="sxs-lookup"><span data-stu-id="ae840-116">Message validation</span></span>  
  
-   <span data-ttu-id="ae840-117">訊息轉換</span><span class="sxs-lookup"><span data-stu-id="ae840-117">Message transformation</span></span>  
  
-   <span data-ttu-id="ae840-118">連線的可延伸的配接器架構</span><span class="sxs-lookup"><span data-stu-id="ae840-118">Extensible adapter framework for connectivity</span></span>  
  
-   <span data-ttu-id="ae840-119">服務協調流程</span><span class="sxs-lookup"><span data-stu-id="ae840-119">Service orchestration</span></span>  
  
-   <span data-ttu-id="ae840-120">商務規則引擎</span><span class="sxs-lookup"><span data-stu-id="ae840-120">Business rules engine</span></span>  
  
-   <span data-ttu-id="ae840-121">商務活動監控</span><span class="sxs-lookup"><span data-stu-id="ae840-121">Business activity monitoring</span></span>  
  
-   <span data-ttu-id="ae840-122">Web 服務和 WS-\* 整合 （WCF 配接器）</span><span class="sxs-lookup"><span data-stu-id="ae840-122">Web service and WS-\* integration (WCF adapter)</span></span>  

## <a name="core-capabilities"></a><span data-ttu-id="ae840-123">核心功能</span><span class="sxs-lookup"><span data-stu-id="ae840-123">Core capabilities</span></span>  
 <span data-ttu-id="ae840-124">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk Server 提供各種新功能，著重於建置強固、 連結、 服務導向應用程式的功能。</span><span class="sxs-lookup"><span data-stu-id="ae840-124">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the functionality of BizTalk Server to provide a range of new capabilities focused on building robust, connected, service-oriented applications.</span></span> <span data-ttu-id="ae840-125">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]視為個別可以連線的工作單位中的 BizTalk Server 元件所需，以形成鬆散結合的解決方案。</span><span class="sxs-lookup"><span data-stu-id="ae840-125">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] treats BizTalk Server components as individual units of work that can be connected, as desired, to form loosely coupled solutions.</span></span> <span data-ttu-id="ae840-126">以下是一些核心功能，[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供增強的 BizTalk Server 功能：</span><span class="sxs-lookup"><span data-stu-id="ae840-126">The following are some of the core capabilities that the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides to enhance the capabilities of BizTalk Server:</span></span>  
  
- <span data-ttu-id="ae840-127">**原則導向的中繼。**</span><span class="sxs-lookup"><span data-stu-id="ae840-127">**Policy driven mediation.**</span></span> <span data-ttu-id="ae840-128">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ae840-128">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
  - <span data-ttu-id="ae840-129">它提供以路線為基礎的路由支援輕量服務組合，發行當時的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae840-129">It provides itinerary-based routing that supports lightweight service composition at the time of message publication.</span></span> <span data-ttu-id="ae840-130">這個方法可動態探索的服務端點和中繼需求使用服務登錄或商務規則原則路由傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae840-130">This approach allows dynamic discovery of service endpoints and mediation requirements for message routing using a service registry or the business rules policy.</span></span>  
  
  - <span data-ttu-id="ae840-131">針對所收到的路線為基礎的路由使用伺服器端路線動態解析和訊息後加入至訊息內容時，它會新增原則集中化的支援。</span><span class="sxs-lookup"><span data-stu-id="ae840-131">It adds support for policy centralization for itinerary-based routing using server-side itineraries that are dynamically resolved and added to the message context after a message is received.</span></span> <span data-ttu-id="ae840-132">管理在中央位置的路線，可讓來自完全不會察覺的方式會路由傳送其要求的用戶端的訊息處理。</span><span class="sxs-lookup"><span data-stu-id="ae840-132">Managing itineraries in a central location enables the processing of messages from clients that are completely unaware of how their requests are being routed.</span></span>  
  
  - <span data-ttu-id="ae840-133">它會使用一個增強型的版本[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，可使用動態端點解析和轉換需求; 如此有效即可減少來自服務的取用者。</span><span class="sxs-lookup"><span data-stu-id="ae840-133">It uses an enhanced version of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework, which enables dynamic resolution of endpoints and transformation requirements; this effectively decouples the consumer from the services.</span></span>  
  
- <span data-ttu-id="ae840-134">**將系統的連線。**</span><span class="sxs-lookup"><span data-stu-id="ae840-134">**Connecting systems.**</span></span> <span data-ttu-id="ae840-135">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ae840-135">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
  -   <span data-ttu-id="ae840-136">它提供標準化 XML 訊息的命名空間的管線元件。</span><span class="sxs-lookup"><span data-stu-id="ae840-136">It provides pipeline components that normalize XML message namespaces.</span></span>  
  
  -   <span data-ttu-id="ae840-137">它整合了 JMS 透過 WebSphere MQ 配接器的 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="ae840-137">It integrates with JMS through the WebSphere MQ adapter for BizTalk Server.</span></span>  
  
  -   <span data-ttu-id="ae840-138">它可協助啟用動態服務彙總、 訊息路由、 訊息驗證和訊息轉換的訊息交換模式。</span><span class="sxs-lookup"><span data-stu-id="ae840-138">It facilitates message exchange patterns that enable dynamic service aggregation, message routing, message validation, and message transformation.</span></span>  
  
  -   <span data-ttu-id="ae840-139">它支援從登錄和使用 UDDI 3.0 的存放庫整合的服務端點探索。</span><span class="sxs-lookup"><span data-stu-id="ae840-139">It supports service endpoint discovery from registry and repository integration using UDDI 3.0.</span></span>  
  
  -   <span data-ttu-id="ae840-140">它支援訊息路由透過特定業務 (LOB) 配接器使用 WCF 自訂 BizTalk 配接器的 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="ae840-140">It supports message routing through line-of-business (LOB) adapters by using the WCF-Custom BizTalk Adapter for BizTalk Server.</span></span>  
  
- <span data-ttu-id="ae840-141">**管理和監視。**</span><span class="sxs-lookup"><span data-stu-id="ae840-141">**Management and monitoring.**</span></span> <span data-ttu-id="ae840-142">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ae840-142">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
  -   <span data-ttu-id="ae840-143">它提供例外狀況管理架構和工具。</span><span class="sxs-lookup"><span data-stu-id="ae840-143">It provides exception management framework and tools.</span></span>  
  
  -   <span data-ttu-id="ae840-144">它有助於訊息修復和重新提交使用管理入口網站中，隨附的範例應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae840-144">It facilitates message repair and resubmission using a management portal, shipped as a sample application.</span></span> <span data-ttu-id="ae840-145">此 Web 應用程式特定的錯誤發生時，也支援可自訂的電子郵件通知。</span><span class="sxs-lookup"><span data-stu-id="ae840-145">This Web application also supports customizable e-mail notifications when a specific error occurs.</span></span>  
  
  -   <span data-ttu-id="ae840-146">它可讓 BizTalk Server 端點及登錄整合、 管理和發行集。</span><span class="sxs-lookup"><span data-stu-id="ae840-146">It allows BizTalk Server endpoint and registry integration, management, and publication.</span></span>  
  
  -   <span data-ttu-id="ae840-147">它提供設定版本的伺服器端路線的集中存放的庫。</span><span class="sxs-lookup"><span data-stu-id="ae840-147">It provides a centralized repository of versioned server-side itineraries.</span></span>  
  
  -   <span data-ttu-id="ae840-148">它支援報告和分析用於 BizTalk Server 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae840-148">It supports reporting and analytics for BizTalk Server applications.</span></span>  
  
  -   <span data-ttu-id="ae840-149">它包含商務活動監控元件，可追蹤路線服務的執行，包括開始時間、 結束時間和服務中繼序列。</span><span class="sxs-lookup"><span data-stu-id="ae840-149">It includes Business Activity Monitoring components to track itinerary service execution, including start time, end time, and service mediation sequence.</span></span>  
  
- <span data-ttu-id="ae840-150">**SOA 控管。**</span><span class="sxs-lookup"><span data-stu-id="ae840-150">**SOA governance.**</span></span> <span data-ttu-id="ae840-151">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]會進行下列作業：</span><span class="sxs-lookup"><span data-stu-id="ae840-151">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] does the following:</span></span>  
  
  -   <span data-ttu-id="ae840-152">它整合了第三方 SOA 控管解決方案，包括內嵌的管理代理程式，以便讓 BizTalk Server 從 AmberPoint 和 SOA 軟體。</span><span class="sxs-lookup"><span data-stu-id="ae840-152">It integrates with third-party SOA governance solutions, including embedded management agents for BizTalk Server from AmberPoint and SOA Software.</span></span>  

> [!TIP]
> <span data-ttu-id="ae840-153">[了解 BizTalk Server](../core/understanding-biztalk-server.md)等等，傳訊引擎，提供更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ae840-153">[Understanding BizTalk Server](../core/understanding-biztalk-server.md) provides more details on the messaging engine, and more.</span></span>

## <a name="get-some-help"></a><span data-ttu-id="ae840-154">取得相關協助</span><span class="sxs-lookup"><span data-stu-id="ae840-154">Get some help</span></span>
<span data-ttu-id="ae840-155">取得相關協助，以及可協助其他人在[BizTalk ESB Toolkit 論壇](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409)。</span><span class="sxs-lookup"><span data-stu-id="ae840-155">Get some help, and help others at the [BizTalk ESB Toolkit forums](http://go.microsoft.com/fwlink/?LinkID=185951&clcid=0x409).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae840-156">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="ae840-156">Next steps</span></span>
[<span data-ttu-id="ae840-157">BizTalk ESB 工具組內容</span><span class="sxs-lookup"><span data-stu-id="ae840-157">Contents of the BizTalk ESB Toolkit</span></span>](contents-of-the-biztalk-esb-toolkit.md)  
