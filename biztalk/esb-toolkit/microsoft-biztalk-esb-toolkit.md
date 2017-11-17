---
title: "Microsoft BizTalk ESB 工具組 |Microsoft 文件"
description: "簡介、 常見的案例和 ESB toolkit，BizTalk Server 中的元件"
caps.latest.revision: "14"
author: MandiOhlinger
manager: anneta
ms.custom: 
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17ffaebc-7e33-4de8-8e94-109cd5d16ca0
ms.author: mandia
ms.openlocfilehash: 1763ed4bb7f090b91565c3a5f5f480d2c081b48c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="microsoft-biztalk-esb-toolkit"></a><span data-ttu-id="78efd-103">Microsoft BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="78efd-103">Microsoft BizTalk ESB Toolkit</span></span>
<span data-ttu-id="78efd-104">![BizTalk ESB 工具組標誌](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")</span><span class="sxs-lookup"><span data-stu-id="78efd-104">![BizTalk ESB Toolkit Logo](../esb-toolkit/media/biztalkesbtoolkitlogo.gif "BizTalkESBToolkitLogo")</span></span>  
  
## <a name="summary"></a><span data-ttu-id="78efd-105">摘要</span><span class="sxs-lookup"><span data-stu-id="78efd-105">Summary</span></span>  
 <span data-ttu-id="78efd-106">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]使用[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]支援鬆散偶合的傳訊架構。</span><span class="sxs-lookup"><span data-stu-id="78efd-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] uses [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] to support a loosely coupled messaging architecture.</span></span> <span data-ttu-id="78efd-107">BizTalk Server 包含的功能強大的發佈/訂閱機制傳訊的運作方式是建立的應用程式和填滿訂閱，其可提供高效率且可擴充的平台服務導向架構 (SOA) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78efd-107">BizTalk Server includes a powerful publish/subscribe mechanism for messaging applications that works by creating and filling subscriptions, which provides a highly efficient and scalable platform for service-oriented architecture (SOA) applications.</span></span>  
  
 <span data-ttu-id="78efd-108">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]擴充 BizTalk Server 提供的新功能，專注於建置穩固、 連線、 服務導向整合行程為基礎的服務引動過程輕量型的服務的應用程式範圍的功能組合、 動態解析的端點和地圖、 Web 服務和 WS-* 整合，錯誤管理和報表，以及與第三方 SOA 控管解決方案的整合。</span><span class="sxs-lookup"><span data-stu-id="78efd-108">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] extends the functionality of BizTalk Server to provide a range of new capabilities focused on building robust, connected, service-oriented applications that incorporate itinerary-based service invocation for lightweight service composition, dynamic resolution of endpoints and maps, Web service and WS-* integration, fault management and reporting, and integration with third-party SOA governance solutions.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="78efd-109">概觀</span><span class="sxs-lookup"><span data-stu-id="78efd-109">Overview</span></span>  
 <span data-ttu-id="78efd-110">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]提供的架構指引、 模式和 BizTalk Server 和.NET Framework 元件，以簡化開發的企業服務匯流排 (ESB) 上的 Microsoft 平台，並允許以擴充 Microsoft 客戶的集合他們自己的訊息和整合解決方案。</span><span class="sxs-lookup"><span data-stu-id="78efd-110">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides architectural guidance, patterns, and a collection of BizTalk Server and .NET Framework components to simplify the development of an Enterprise Service Bus (ESB) on the Microsoft platform and to allow Microsoft customers to extend their own messaging and integration solutions.</span></span>  
  
## <a name="common-scenarios"></a><span data-ttu-id="78efd-111">常見狀況</span><span class="sxs-lookup"><span data-stu-id="78efd-111">Common Scenarios</span></span>  
 <span data-ttu-id="78efd-112">實作基礎結構啟用服務導向架構 (SOA) 的內容中廣泛使用企業服務匯流排 (ESB) 一詞。</span><span class="sxs-lookup"><span data-stu-id="78efd-112">The term Enterprise Service Bus (ESB) is widely used in the context of implementing an infrastructure for enabling a service-oriented architecture (SOA).</span></span> <span data-ttu-id="78efd-113">不過，與 SOAs 部署的實際經驗顯示 ESB 是其中一個進行向上完整 Service-Oriented 基礎結構 (SOI) 的許多建置組塊。</span><span class="sxs-lookup"><span data-stu-id="78efd-113">However, real-world experience with the deployment of SOAs has shown that an ESB is only one of many building blocks that make up a comprehensive Service-Oriented Infrastructure (SOI).</span></span> <span data-ttu-id="78efd-114">ESB 已更改一詞在許多不同的方向，以及其定義取決於個別 ESB 和整合平台廠商解譯和需求的特定 SOA initiatives。</span><span class="sxs-lookup"><span data-stu-id="78efd-114">The term ESB has morphed in a number of different directions, and its definition depends on the interpretation of individual ESB and integration platform vendors and on the requirements of particular SOA initiatives.</span></span>  
  
 <span data-ttu-id="78efd-115">根據 Microsoft 已收集了與許多成功的真實世界 SOI 實作的體驗，您可以想像 ESB 傳統企業應用程式整合 (EAI)、 訊息導向中介軟體為基礎的架構模式的集合Web 服務、.NET 和 Java 的互通性、 主機系統整合，以及與服務和資產的儲存機制的互通性。</span><span class="sxs-lookup"><span data-stu-id="78efd-115">Based on the experience Microsoft has gathered from many successful real-world SOI implementations, you can think of an ESB as a collection of architectural patterns based on traditional enterprise application integration (EAI), message-oriented middleware, Web services, .NET and Java interoperability, host system integration, and interoperability with service registries and asset repositories.</span></span>  
  
 <span data-ttu-id="78efd-116">圖 1 顯示的互連 ESB 架構可以提供類型的高階檢視。</span><span class="sxs-lookup"><span data-stu-id="78efd-116">Figure 1 shows a high-level view of the type of interconnectivity that an ESB architecture can provide.</span></span>  
  
 <span data-ttu-id="78efd-117">![ESB 概觀](../esb-toolkit/media/esboverview.gif "ESBOverview")</span><span class="sxs-lookup"><span data-stu-id="78efd-117">![ESB Overview](../esb-toolkit/media/esboverview.gif "ESBOverview")</span></span>  
  
 <span data-ttu-id="78efd-118">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="78efd-118">**Figure 1**</span></span>  
  
 <span data-ttu-id="78efd-119">**連線的高階範例提供的企業服務匯流排架構**</span><span class="sxs-lookup"><span data-stu-id="78efd-119">**A high-level example of the connectivity provided the Enterprise Service Bus architecture**</span></span>  
  
## <a name="audience-requirements"></a><span data-ttu-id="78efd-120">對象的需求</span><span class="sxs-lookup"><span data-stu-id="78efd-120">Audience Requirements</span></span>  
 <span data-ttu-id="78efd-121">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]僅供開發人員建立 Microsoft BizTalk Server 解決方案或其他解決方案使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]元件。</span><span class="sxs-lookup"><span data-stu-id="78efd-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] is intended for developers who create Microsoft BizTalk Server solutions or other solutions that use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] components.</span></span> <span data-ttu-id="78efd-122">若要充分利用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，開發人員應該擁有知識和遇到具有下列工作：</span><span class="sxs-lookup"><span data-stu-id="78efd-122">To take full advantage of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], developers should possess knowledge and experience working with the following:</span></span>  

- [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]

- [!INCLUDE[btsVStudioNoVersion_md](../includes/btsvstudionoversion-md.md)]
  
-   <span data-ttu-id="78efd-123">Microsoft.NET 開發技術，包括 ASP.NET Web 服務和.NET Framework 元件的開發</span><span class="sxs-lookup"><span data-stu-id="78efd-123">Microsoft .NET development techniques, including the development of ASP.NET Web services and .NET Framework components</span></span>  
  
## <a name="design-goals"></a><span data-ttu-id="78efd-124">設計目標</span><span class="sxs-lookup"><span data-stu-id="78efd-124">Design Goals</span></span>  
 <span data-ttu-id="78efd-125">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含一系列的支援和實作鬆散偶合的傳訊環境，可讓您更輕鬆地建立以訊息為基礎的企業應用程式元件間的互通性。</span><span class="sxs-lookup"><span data-stu-id="78efd-125">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] consists of a series of interoperating components that support and implement a loosely coupled messaging environment that makes it easier to build message-based enterprise applications.</span></span> <span data-ttu-id="78efd-126">服務和元件自然可分成下列七個類別：</span><span class="sxs-lookup"><span data-stu-id="78efd-126">The services and components fall naturally into the following seven categories:</span></span>  
  
-   <span data-ttu-id="78efd-127">**Web 服務**： 這些公開內部服務，例如路線處理例外狀況管理、 端點和地圖、 BizTalk Server 作業，以及訊息轉換的解析度。</span><span class="sxs-lookup"><span data-stu-id="78efd-127">**Web services** : These expose internal services such as itinerary processing, exception management, resolution of endpoints and maps, BizTalk Server operations, and message transformation.</span></span>  
  
-   <span data-ttu-id="78efd-128">**路線服務**： 包括執行行程為基礎的路由協調流程和傳訊為主服務[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="78efd-128">**Itinerary services** : These include orchestration-based and messaging-based services for performing itinerary-based routing for [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="78efd-129">您可以建立自訂服務的行程為基礎的路由。</span><span class="sxs-lookup"><span data-stu-id="78efd-129">You can create custom services for itinerary-based routing.</span></span>  
  
-   <span data-ttu-id="78efd-130">**路線上-坡道提升。**</span><span class="sxs-lookup"><span data-stu-id="78efd-130">**Itinerary on-ramps.**</span></span> <span data-ttu-id="78efd-131">這些接收外部的訊息、 附加適當的路線，每個訊息，以及執行路線處理;他們使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，來動態解析的端點和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="78efd-131">These receive external messages, attach the appropriate itinerary for each message, and perform itinerary processing; they use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.</span></span>  
  
-   <span data-ttu-id="78efd-132">**在坡道提升**： 這些接收外部訊息格式和傳輸，例如 HTTP、 JMS、 WMQ、 FTP、 一般檔案和 XML 的範圍中。</span><span class="sxs-lookup"><span data-stu-id="78efd-132">**On-ramps** : These receive external messages in a range of formats and transports, such as HTTP, JMS, WMQ, FTP, Flat File, and XML.</span></span> <span data-ttu-id="78efd-133">它們是典型的 BizTalk Server 接收位置，或者使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和配接器提供者架構，來動態解析的端點和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="78efd-133">They are typical BizTalk Server receive locations that optionally use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop pipeline components and the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.</span></span>  
  
-   <span data-ttu-id="78efd-134">**關閉坡道提升**： 這些實作使用之格式和傳輸，例如 SOAP、 WCF、 JMS、 WMQ、 FTP、 HTTP、 一般檔案、 XML 或任何其他自訂格式的訊息的傳遞傳送埠。</span><span class="sxs-lookup"><span data-stu-id="78efd-134">**Off-ramps** : These implement send ports for the delivery of messages using formats and transports such as SOAP, WCF, JMS, WMQ, FTP, HTTP, Flat File, XML, or any other custom formats.</span></span> <span data-ttu-id="78efd-135">它們是一般 BizTalk Server 動態傳送埠，會直接繫結至 Messagebox，並選擇性地使用[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]interop 管線元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]解析器和動態的端點解析的配接器提供者架構與中繼資料。</span><span class="sxs-lookup"><span data-stu-id="78efd-135">They are typical BizTalk Server dynamic send ports that are direct-bound to the Message Box and that optionally use the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] interop pipeline components and the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Provider Framework for dynamic resolution of endpoints and metadata.</span></span>  
  
-   <span data-ttu-id="78efd-136">**例外狀況管理架構**： 這包括例外狀況的例外狀況管理應用程式開發介面，Web 服務和元件的擴充，程序，將例外狀況詳細資料傳遞給 ESB 管理入口網站。</span><span class="sxs-lookup"><span data-stu-id="78efd-136">**Exception Management Framework** : This includes the exception Web service, the exception management API, and components that enrich, process, and pass exception details to the ESB Management Portal.</span></span>  
  
-   <span data-ttu-id="78efd-137">**ESB 管理入口網站**： 這會提供登錄佈建、 例外狀況中繼、 警示的通知和分析。</span><span class="sxs-lookup"><span data-stu-id="78efd-137">**ESB Management Portal** : This provides registry provisioning, exception mediation, alert notification, and analytics.</span></span>  
  
 <span data-ttu-id="78efd-138">許多這些元件和服務所實作的功能上都必須依賴[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]，例如協調流程、 轉換和商務規則引擎和 Messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="78efd-138">Many of these components and services rely on features implemented by [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)], such as the Orchestration, Transformation, and Business Rules engines and the Message Box database.</span></span> <span data-ttu-id="78efd-139">圖 2 顯示的圖解檢視的類別。元件和服務通常發生在每個類別。所使用的核心 BizTalk Server 系統元件和[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="78efd-139">Figure 2 shows a schematic view of the categories; the components and services typically occurring within each category; and the core BizTalk Server system components used by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span>  
  
 <span data-ttu-id="78efd-140">![ESB 架構](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")</span><span class="sxs-lookup"><span data-stu-id="78efd-140">![ESB Architecture](../esb-toolkit/media/esbarchitecture.gif "ESBArchitecture")</span></span>  
  
 <span data-ttu-id="78efd-141">**圖 2**</span><span class="sxs-lookup"><span data-stu-id="78efd-141">**Figure 2**</span></span>  
  
 <span data-ttu-id="78efd-142">**架構和元件[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="78efd-142">**The architecture and components of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]**</span></span>  
  
## <a name="how-the-biztalk-esb-toolkit-works"></a><span data-ttu-id="78efd-143">BizTalk ESB 工具組的運作方式</span><span class="sxs-lookup"><span data-stu-id="78efd-143">How the BizTalk ESB Toolkit Works</span></span>  
 <span data-ttu-id="78efd-144">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]接受輸入的訊息，並執行運算，可能是 （但並非一定） 上執行處理程序，例如轉換、 傳遞或任何其他自訂定義處理程序。</span><span class="sxs-lookup"><span data-stu-id="78efd-144">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] accepts inbound messages and operates on them, perhaps (but not always) by performing processes such as transformation, delivery, or any other custom defined process.</span></span> <span data-ttu-id="78efd-145">若要指定作業所需，核心處理元件所需的訊息來包含相關聯的指示或定義要套用的程序的中繼資料及訊息內容下執行的工作。</span><span class="sxs-lookup"><span data-stu-id="78efd-145">To specify the operations required, the core processing components require a message to contain associated instructions or metadata that define the processes to apply and the tasks to execute with the message content.</span></span>  
  
 <span data-ttu-id="78efd-146">這種方法可提供服務; 之間的鬆散結合這表示 ESB 不需要事先了解之特定處理的每個訊息。</span><span class="sxs-lookup"><span data-stu-id="78efd-146">This approach provides loose coupling between services; this means that the ESB does not require prior knowledge of the specific processing for each message.</span></span> <span data-ttu-id="78efd-147">它只需要知道處理程序，以及如何套用每個處理序的可能範圍。</span><span class="sxs-lookup"><span data-stu-id="78efd-147">It just has to know the possible range of processes and how to apply each process.</span></span> <span data-ttu-id="78efd-148">指定可用的處理序和處理程序與在訊息中的指示之間的對應之選項的各種提供彈性的機制，來設定和調整行為，而不需要變更程式碼和重新部署元件。</span><span class="sxs-lookup"><span data-stu-id="78efd-148">The wide range of options for specifying the available processes and the mapping between the processes and the instructions within messages provides a flexible mechanism for configuring and adjusting behavior, without requiring changes to code and redeployment of components.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="78efd-149">本節內容</span><span class="sxs-lookup"><span data-stu-id="78efd-149">In this section</span></span>

- [<span data-ttu-id="78efd-150">安裝和設定 Microsoft BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="78efd-150">Install and configure the Microsoft BizTalk ESB Toolkit</span></span>](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)

- [<span data-ttu-id="78efd-151">BizTalk ESB 工具組簡介</span><span class="sxs-lookup"><span data-stu-id="78efd-151">Introduction to the BizTalk ESB Toolkit</span></span>](introduction-to-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="78efd-152">開始使用，並了解 BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="78efd-152">Getting started and understanding the BizTalk ESB Toolkit</span></span>](getting-started-with-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="78efd-153">重要案例及開發工作</span><span class="sxs-lookup"><span data-stu-id="78efd-153">Key scenarios and development tasks</span></span>](key-scenarios-and-development-tasks.md)

- [<span data-ttu-id="78efd-154">建立行程使用路線設計工具</span><span class="sxs-lookup"><span data-stu-id="78efd-154">Creating itineraries using itinerary designer</span></span>](creating-itineraries-using-itinerary-designer.md)

- [<span data-ttu-id="78efd-155">BizTalk ESB 工具組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="78efd-155">BizTalk ESB Toolkit sample applications</span></span>](biztalk-esb-toolkit-sample-applications.md)

- [<span data-ttu-id="78efd-156">修改和擴充 BizTalk ESB Toolkit</span><span class="sxs-lookup"><span data-stu-id="78efd-156">Modifying and extending the BizTalk ESB Toolkit</span></span>](modifying-and-extending-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="78efd-157">使用 BizTalk ESB 工具組系統管理</span><span class="sxs-lookup"><span data-stu-id="78efd-157">Administration with the BizTalk ESB Toolkit</span></span>](administration-with-the-biztalk-esb-toolkit.md)

- [<span data-ttu-id="78efd-158">SOA 控管整合</span><span class="sxs-lookup"><span data-stu-id="78efd-158">SOA governance integration</span></span>](soa-governance-integration.md)

- [<span data-ttu-id="78efd-159">疑難排解 BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="78efd-159">Troubleshooting the BizTalk ESB Toolkit</span></span>](troubleshooting-the-biztalk-esb-toolkit.md)
  
## <a name="related-topics"></a><span data-ttu-id="78efd-160">相關主題</span><span class="sxs-lookup"><span data-stu-id="78efd-160">Related topics</span></span>  
  
-   [<span data-ttu-id="78efd-161">BizTalk 服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="78efd-161">BizTalk Service Oriented Solutions</span></span>](../core/service-oriented-solution.md)

- [<span data-ttu-id="78efd-162">使用 BizTalk Server Web 服務</span><span class="sxs-lookup"><span data-stu-id="78efd-162">Using Web Services with BizTalk Server</span></span>](../core/using-web-services.md)  