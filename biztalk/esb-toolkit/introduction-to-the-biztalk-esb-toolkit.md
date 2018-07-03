---
title: BizTalk ESB 工具組簡介 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ESBToolkitV2.introduction
ms.assetid: 98a957b8-5855-4872-b7e7-58a2e1d6b2b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5cfab980a869029d565d378aaf0f75a147403f3e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986719"
---
# <a name="introduction-to-the-biztalk-esb-toolkit"></a><span data-ttu-id="ac34d-102">BizTalk ESB 工具組簡介</span><span class="sxs-lookup"><span data-stu-id="ac34d-102">Introduction to the BizTalk ESB Toolkit</span></span>
<span data-ttu-id="ac34d-103">說明的架構與 Microsoft 的內容[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ac34d-103">Explains the architecture and contents of the Microsoft [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="ac34d-104">文件也會示範如何套用使用企業服務匯流排 (ESB) 架構模式，可開發企業應用程式可讓彈性、 安全、 可重複使用的服務和快速組織現有服務的新端對端商務程序。</span><span class="sxs-lookup"><span data-stu-id="ac34d-104">The documentation also demonstrates how to apply an Enterprise Service Bus (ESB) architecture pattern to develop enterprise applications that enable flexible, secure, and reusable services and rapid organization of existing services into new end-to-end business processes.</span></span>  

## <a name="what-is-an-enterprise-service-bus"></a><span data-ttu-id="ac34d-105">什麼是企業服務匯流排？</span><span class="sxs-lookup"><span data-stu-id="ac34d-105">What Is an Enterprise Service Bus?</span></span>  
 <span data-ttu-id="ac34d-106">企業服務匯流排廣泛使用於實作基礎結構的方式啟用服務導向架構 (SOA) 的內容中的詞彙。</span><span class="sxs-lookup"><span data-stu-id="ac34d-106">The term Enterprise Service Bus is widely used in the context of implementing an infrastructure for enabling Service-Oriented Architecture (SOA).</span></span> <span data-ttu-id="ac34d-107">不過，與部署 SOA 解決方案的真實世界體驗已示範 ESB 是其中一個來建置完整的服務導向基礎結構 (SOI) 所需的許多元件。</span><span class="sxs-lookup"><span data-stu-id="ac34d-107">However, real-world experience with the deployment of SOA solutions has demonstrated that an ESB is only one of many components required to build a comprehensive Service-Oriented Infrastructure (SOI).</span></span> <span data-ttu-id="ac34d-108">」 的 ESB 」 的發展方向數的詞彙，其定義不同的個別 ESB 和整合的平台廠商解譯與特定的 SOA 方案的需求。</span><span class="sxs-lookup"><span data-stu-id="ac34d-108">The term "ESB" has evolved in a number of directions—its definition varies with the interpretation of individual ESB and integration platform vendors and with the requirements of particular SOA initiatives.</span></span>  

 <span data-ttu-id="ac34d-109">Microsoft 已收集了許多成功的真實世界 SOI 實作從經驗為基礎，Microsoft 會考慮企業服務匯流排是架構在傳統企業應用程式整合 (EAI) 的架構模式的集合訊息導向中介軟體、 Web 服務、.NET 和 Java 互通性、 主機系統整合，以及與服務登錄與資產存放庫的互通性。</span><span class="sxs-lookup"><span data-stu-id="ac34d-109">Based on the experience Microsoft has gathered from many successful real-world SOI implementations, Microsoft considers an Enterprise Service Bus to be a collection of architectural patterns based on traditional Enterprise Application Integration (EAI), message-oriented middleware, Web services, .NET and Java interoperability, host system integration, and interoperability with service registries and asset repositories.</span></span> <span data-ttu-id="ac34d-110">圖 1 說明企業服務匯流排的架構。</span><span class="sxs-lookup"><span data-stu-id="ac34d-110">Figure 1 illustrates the architecture of an Enterprise Service Bus.</span></span>  

 <span data-ttu-id="ac34d-111">![ESB 概觀](../esb-toolkit/media/esboverview.gif "ESBOverview")</span><span class="sxs-lookup"><span data-stu-id="ac34d-111">![ESB Overview](../esb-toolkit/media/esboverview.gif "ESBOverview")</span></span>  

 <span data-ttu-id="ac34d-112">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="ac34d-112">**Figure 1**</span></span>  

 <span data-ttu-id="ac34d-113">**讀者介紹企業服務匯流排架構所提供的連線**</span><span class="sxs-lookup"><span data-stu-id="ac34d-113">**A high-level representation of the connectivity provided by the Enterprise Service Bus architecture**</span></span>  

<!---  Old text with old links
## The Industry View of ESB  
 There are many sources of information about ESB design, architecture, infrastructure, and implementation available from industry suppliers, system integrators, and independent sources.  
-->
<!---    
 IBM defines ESB as a system that "...enables a business to make use of a comprehensive, flexible, and consistent approach to integration while also reducing the complexity of the applications being integrated. Due to the complex and varying nature of business needs, ESB is an evolutional progression that unifies message oriented, event driven and service oriented approaches for integrating applications and service." IBM describes the advantages as "...greater reuse of IT assets by separating application logics and integration tasks, so you can reduce the number, size, and complexity of integration interfaces," and the ability to "...add or change services with minimal interruption to existing IT environment; reduce cost and risk involved as business changes and new opportunities arise." For more information, see [WebSphere software](http://go.microsoft.com/fwlink/p/?LinkId=185958)([http://go.microsoft.com/fwlink/p/?LinkId=185958](http://go.microsoft.com/fwlink/p/?LinkId=185958))on the IBM Web site.  
-->
<!---    Old text with old links
 Sonic Solutions provide a comprehensive examination of ESB, discussing the principle aspects, and the IT and business benefits. They describe the requirement for ESB: "To integrate old and new, service-oriented architecture (SOA) needs an infrastructure that can connect any IT resource, whatever its technology or wherever it is deployed." For more information, see [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185959)([http://go.microsoft.com/fwlink/p/?LinkId=185959](http://go.microsoft.com/fwlink/p/?LinkId=185959)) on the Sonic Solutions Web site.  
-->
<!---    Old text with old links
 TIBCO Software define ESB as "...a standards-based communication layer in a service- oriented architecture (SOA) that enables services to be used across multiple communication protocols [to] simplify service deployment and management, and promote service reuse in a heterogeneous environment." They suggest, in order to provide these capabilities, ESBs "...support both open standards and proprietary technologies, including Web services and UDDI-based registries to discover and publish services, Java Message Service (JMS) and other widely deployed messaging protocols, standards-based (XML) transformations, and basic message routing." For more information, see [Enterprise Service Bus (ESB)](http://go.microsoft.com/fwlink/p/?LinkId=185960)([http://go.microsoft.com/fwlink/?LinkId=185960](http://go.microsoft.com/fwlink/p/?LinkId=185960)) on the TIBCO Web site.  
-->
<!---    Old text with old links
 In the description of his book, Enterprise Service Bus, author David Chappell states that "Rather than conform to the hub-and-spoke architecture of traditional enterprise application integration products, ESB provides a highly distributed approach to integration." He adds "...with unique capabilities that allow individual departments or business units to build out their integration projects in incremental, digestible chunks, maintaining their own local control and autonomy, while still being able to connect together each integration project into a larger, more global integration fabric, or grid." For more information, see Enterprise Service Bus by David Chappell:  
-->
<!---    Old text with old links
-   Chappell, David. Enterprise Service Bus. Sebastopol, CA: O'Reilly Media, Inc. 2004.  
-->


## <a name="the-biztalk-esb-toolkit"></a><span data-ttu-id="ac34d-114">BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="ac34d-114">The BizTalk ESB Toolkit</span></span>
 <span data-ttu-id="ac34d-115">整體而言，此文件介紹架構設計人員和開發人員 ESB 架構概念為定址[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，並說明透過一組容易被接受的 ESB 使用案例的 ESB 元件的功能。</span><span class="sxs-lookup"><span data-stu-id="ac34d-115">This documentation, as a whole, introduces architects and developers to ESB architectural concepts as addressed by the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and explains the functionality of the ESB components through a set of commonly accepted ESB use cases.</span></span>  

 <span data-ttu-id="ac34d-116">本節提供的簡介[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]，並包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="ac34d-116">This section provides an introduction to the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], and includes the following topics:</span></span>  

- [<span data-ttu-id="ac34d-117">BizTalk ESB 工具組概觀</span><span class="sxs-lookup"><span data-stu-id="ac34d-117">Overview of the BizTalk ESB Toolkit</span></span>](../esb-toolkit/overview-of-the-biztalk-esb-toolkit.md)  

- [<span data-ttu-id="ac34d-118">BizTalk ESB 工具組內容</span><span class="sxs-lookup"><span data-stu-id="ac34d-118">Contents of the BizTalk ESB Toolkit</span></span>](../esb-toolkit/contents-of-the-biztalk-esb-toolkit.md)  

  <span data-ttu-id="ac34d-119">這份文件也會包含下列主題章節：</span><span class="sxs-lookup"><span data-stu-id="ac34d-119">This documentation also includes the following topic sections:</span></span>  

- [<span data-ttu-id="ac34d-120">開始使用 BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="ac34d-120">Getting Started with the BizTalk ESB Toolkit</span></span>](../esb-toolkit/getting-started-with-the-biztalk-esb-toolkit.md)  

- [<span data-ttu-id="ac34d-121">主要案例和開發工作</span><span class="sxs-lookup"><span data-stu-id="ac34d-121">Key Scenarios and Development Tasks</span></span>](../esb-toolkit/key-scenarios-and-development-tasks.md)  

- [<span data-ttu-id="ac34d-122">使用路線設計工具建立路線</span><span class="sxs-lookup"><span data-stu-id="ac34d-122">Creating Itineraries Using Itinerary Designer</span></span>](../esb-toolkit/creating-itineraries-using-itinerary-designer.md)  

- [<span data-ttu-id="ac34d-123">BizTalk ESB 工具組範例應用程式</span><span class="sxs-lookup"><span data-stu-id="ac34d-123">BizTalk ESB Toolkit Sample Applications</span></span>](../esb-toolkit/biztalk-esb-toolkit-sample-applications.md)  

- [<span data-ttu-id="ac34d-124">修改和擴充 BizTalk ESB 工具組</span><span class="sxs-lookup"><span data-stu-id="ac34d-124">Modifying and Extending the BizTalk ESB Toolkit</span></span>](../esb-toolkit/modifying-and-extending-the-biztalk-esb-toolkit.md)  

- [<span data-ttu-id="ac34d-125">使用 BizTalk ESB 工具組管理</span><span class="sxs-lookup"><span data-stu-id="ac34d-125">Administration with the BizTalk ESB Toolkit</span></span>](../esb-toolkit/administration-with-the-biztalk-esb-toolkit.md)  

- [<span data-ttu-id="ac34d-126">SOA 控管整合</span><span class="sxs-lookup"><span data-stu-id="ac34d-126">SOA Governance Integration</span></span>](../esb-toolkit/soa-governance-integration.md)  

- [<span data-ttu-id="ac34d-127">疑難排解</span><span class="sxs-lookup"><span data-stu-id="ac34d-127">Troubleshooting</span></span>](../esb-toolkit/troubleshooting-the-biztalk-esb-toolkit.md)
