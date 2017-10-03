---
title: "設計系統架構，以便讓 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, security
- security, deploying
ms.assetid: b7ded72a-2487-4bb7-9894-cd13235a52c7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a18656a2d4d3827cd38a3f791af2ac856df8ce36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="designing-the-system-architectures-for-biztalk-server"></a><span data-ttu-id="6196f-102">設計 BizTalk Server 的系統架構</span><span class="sxs-lookup"><span data-stu-id="6196f-102">Designing the System Architectures for BizTalk Server</span></span>
<span data-ttu-id="6196f-103">對 Microsoft® BizTalk® Server 部署的安全性、效能、可用性及運作上面的需求，是完全根據您的商務需要、需求、商務夥伴以及公司規模等等而定。</span><span class="sxs-lookup"><span data-stu-id="6196f-103">The requirements of your Microsoft® BizTalk® Server deployment for security, performance, availability, and operation are highly dependent on your business needs, requirements, partners, company size, and so on.</span></span> <span data-ttu-id="6196f-104">要將 BizTalk Server 元件的任何單一組態當作典型組態，並提供規定的指南，是相當困難的，因此本節提供在大型企業的分散式安全生產環境組態中，設定不同 BizTalk Server 功能的指南及建議。</span><span class="sxs-lookup"><span data-stu-id="6196f-104">While it is difficult to consider any single configuration of BizTalk Server components as typical and provide prescriptive guidance for it, this section provides guidance and recommendations on how to configure the different BizTalk Server features in a distributed, secure configuration for the production environment of a large enterprise.</span></span>  
  
 <span data-ttu-id="6196f-105">本節所提供的架構，目的在提供於高度分散環境中部署 BizTalk Server 的參考，而這種高度分散的環境將是您深入考慮的重點。</span><span class="sxs-lookup"><span data-stu-id="6196f-105">The architectures presented in this section aim to provide you with reference information about deploying BizTalk Server in a highly distributed environment where you take into consideration defense in depth.</span></span> <span data-ttu-id="6196f-106">BizTalk Server 的每個應用程式可能有它自己組獨特的問題領域，使用的通訊協定為基礎的安全性需求，而解決方案的特定環境的操作。</span><span class="sxs-lookup"><span data-stu-id="6196f-106">Every application for BizTalk Server is likely to have its own unique set of security requirements based on the problem domain, the protocols used, and the particular environment the solution operates in.</span></span> <span data-ttu-id="6196f-107">效能、 可用性及成本考量則會進一步影響這些需求。</span><span class="sxs-lookup"><span data-stu-id="6196f-107">Performance, availability, and cost considerations further influence these requirements.</span></span> <span data-ttu-id="6196f-108">您應該使用本文件中的這些架構及建議，然後按照需求、威脅及公司的資產，量身訂作自己的 BizTalk Server 部署。</span><span class="sxs-lookup"><span data-stu-id="6196f-108">You should use these architectures and the recommendations within this document as the building blocks to create your own BizTalk Server deployment tailored to the needs, threats and assets of your company.</span></span>  
  
 <span data-ttu-id="6196f-109">本節包含的資訊有：如何設計 BizTalk Server 的系統架構來保護 BizTalk Server 中不同功能的安全、進一步保護伺服器處理及儲存的資料安全，以及如何將伺服器放置在分散式的環境中，因為這樣的環境可減少重要資料及伺服器因為攻擊或損壞而遭到破壞的可能性。</span><span class="sxs-lookup"><span data-stu-id="6196f-109">This section contains information about how you can design the system architecture for BizTalk Server to secure the different features in BizTalk Server, and consequently, secure the data that the servers process and store, and how to place the servers in a distributed environment that minimize the potential for critical data and servers being compromised in the event of an attack or disaster.</span></span> <span data-ttu-id="6196f-110">本節未提供設定部署或測試環境的建議，或將組件部署到生產環境的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6196f-110">This section does not provide recommendations for configuring development, or test environments, or details for deploying an assembly into a production environment.</span></span> <span data-ttu-id="6196f-111">如需部署組件的詳細資訊，請參閱[瞭解 BizTalk 應用程式部署和管理](../core/understanding-biztalk-application-deployment-and-management.md)。</span><span class="sxs-lookup"><span data-stu-id="6196f-111">For more information about deploying assemblies, see [Understanding BizTalk Application Deployment and Management](../core/understanding-biztalk-application-deployment-and-management.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6196f-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="6196f-112">In This Section</span></span>  
  
-   [<span data-ttu-id="6196f-113">設計安全架構</span><span class="sxs-lookup"><span data-stu-id="6196f-113">Designing a Secure Architecture</span></span>](../core/designing-a-secure-architecture.md)  
  
-   [<span data-ttu-id="6196f-114">設計分散式的架構</span><span class="sxs-lookup"><span data-stu-id="6196f-114">Designing a Distributed Architecture</span></span>](../core/designing-a-distributed-architecture.md)  
  
-   [<span data-ttu-id="6196f-115">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="6196f-115">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)