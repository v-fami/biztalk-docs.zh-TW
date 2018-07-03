---
title: 使用 ESB 工具組，在 BizTalk Server 中的 SOA 控管整合 |Microsoft Docs
description: 挑戰 SOA 式系統和協力廠商整合使用 BizTalk Server 中的 ESB 工具組的清單
caps.latest.revision: 3
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ccb5ac2d-cd90-414d-a6c7-045a8fe9450b
ms.author: mandia
ms.openlocfilehash: 1b989373f4e0f10439374842c2dcf6c8b8226165
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023044"
---
# <a name="soa-governance-integration"></a><span data-ttu-id="97492-103">SOA 控管整合</span><span class="sxs-lookup"><span data-stu-id="97492-103">SOA Governance Integration</span></span>
<span data-ttu-id="97492-104">企業級應用程式必須支援穩定且可靠的管理功能，能夠以符合商務需求、 政府法規、 服務等級協定 (Sla)，與客戶和交易夥伴的期望。</span><span class="sxs-lookup"><span data-stu-id="97492-104">Enterprise-level applications must support robust and reliable management features to be able to comply with business requirements, government legislation, service level agreements (SLAs), and customer and trading partner expectations.</span></span> <span data-ttu-id="97492-105">執行階段管理特別著重於的挑戰和需求，成功地執行服務導向架構 (SOA) – 為基礎的系統符合這些需求。</span><span class="sxs-lookup"><span data-stu-id="97492-105">Run-time governance focuses specifically on the challenges of, and requirements for, successfully running service-oriented architecture (SOA)–based systems that meet these requirements.</span></span> <span data-ttu-id="97492-106">商務系統所提供品質是服務的定義其成功或失敗的主要因素。</span><span class="sxs-lookup"><span data-stu-id="97492-106">The quality of service delivered by a business system is the predominant factor that defines its success or failure.</span></span>  

## <a name="soa-challenges"></a><span data-ttu-id="97492-107">SOA 挑戰</span><span class="sxs-lookup"><span data-stu-id="97492-107">SOA challenges</span></span>  
 <span data-ttu-id="97492-108">SOA 為基礎的系統部署到生產環境的企業面臨一些挑戰，包括下列：</span><span class="sxs-lookup"><span data-stu-id="97492-108">Businesses deploying SOA-based systems into production face a number of challenges, including the following:</span></span>  

-   <span data-ttu-id="97492-109">維護和升級的成本降至最低，並允許累加式更新</span><span class="sxs-lookup"><span data-stu-id="97492-109">Minimizing the cost of maintenance and upgrades, and allowing incremental updates</span></span>  

-   <span data-ttu-id="97492-110">允許透過商務程序管理和撰寫工具的快速變更</span><span class="sxs-lookup"><span data-stu-id="97492-110">Allowing rapid change through business process management and composition tools</span></span>  

-   <span data-ttu-id="97492-111">端對端安全性;這包括信任和訊息的寄件者、 接收者，與內容的隱私權保護</span><span class="sxs-lookup"><span data-stu-id="97492-111">End-to-end security; this includes trust and protection of the privacy of message senders, receivers, and content</span></span>  

-   <span data-ttu-id="97492-112">用來識別、 管理和修復所發生的例外狀況</span><span class="sxs-lookup"><span data-stu-id="97492-112">Identifying, managing, and repairing exceptions as they occur</span></span>  

-   <span data-ttu-id="97492-113">分開處理服務和取用者</span><span class="sxs-lookup"><span data-stu-id="97492-113">Decoupling of services and consumers</span></span>  

-   <span data-ttu-id="97492-114">測量並證明位移成本考量的 SOA 應用程式的商業價值</span><span class="sxs-lookup"><span data-stu-id="97492-114">Measuring and proving the business value of SOA applications to offset cost concerns</span></span>  

-   <span data-ttu-id="97492-115">重複或否則不需要服務的激增的控制項 （控管）</span><span class="sxs-lookup"><span data-stu-id="97492-115">Control (governance) of the proliferation of duplicate or otherwise unnecessary services</span></span>  

-   <span data-ttu-id="97492-116">促進識別適當的服務所需的潛在使用者減少初始開發成本</span><span class="sxs-lookup"><span data-stu-id="97492-116">Facilitating the identification of the appropriate services required by potential users to reduce initial development cost</span></span>  

-   <span data-ttu-id="97492-117">最小化成本及風險持續性的維護及變更服務的生命週期管理</span><span class="sxs-lookup"><span data-stu-id="97492-117">Managing the life cycle of services to minimize the cost and risk of ongoing maintenance and change</span></span>  

-   <span data-ttu-id="97492-118">簡化適當的服務 （分離位置、 傳輸、 原則、 標準和傳訊樣式） 實際的使用量</span><span class="sxs-lookup"><span data-stu-id="97492-118">Simplifying the actual usage of appropriate services (decoupling location, transport, policies, standards, and messaging styles)</span></span>  

-   <span data-ttu-id="97492-119">報告功能，用來識別誰正在使用的服務、 地點及原因</span><span class="sxs-lookup"><span data-stu-id="97492-119">Reporting facilities used to identify who is using which service, where, and why</span></span>  

## <a name="next-steps"></a><span data-ttu-id="97492-120">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="97492-120">Next steps</span></span>
 <span data-ttu-id="97492-121">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援這兩個協力廠商執行階段管理系統的整合：</span><span class="sxs-lookup"><span data-stu-id="97492-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports integration with two third-party run-time governance systems:</span></span>  

- <span data-ttu-id="97492-122">**Sentinet SOA 解析程式與 BizTalk Server Extensions**。</span><span class="sxs-lookup"><span data-stu-id="97492-122">**Sentinet SOA Resolver and BizTalk Server Extensions**.</span></span> <span data-ttu-id="97492-123">如需有關如何 Sentinet 擴充[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]功能，請參閱[使用 Sentinet 擴充 BizTalk ESB Toolkit 功能](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md)。</span><span class="sxs-lookup"><span data-stu-id="97492-123">For more information on how Sentinet extends [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] capabilities, see [Extending BizTalk ESB Toolkit Capabilities with Sentinet](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md).</span></span>

- <span data-ttu-id="97492-124">[SOA BizTalk 管理點](../esb-toolkit/soa-biztalk-management-point.md)SOA 軟體，inc.提供</span><span class="sxs-lookup"><span data-stu-id="97492-124">[SOA BizTalk Management Point](../esb-toolkit/soa-biztalk-management-point.md) from SOA Software, Inc.</span></span>  

- <span data-ttu-id="97492-125">[AmberPoint BizTalk Nano 代理程式](../esb-toolkit/amberpoint-biztalk-nano-agent.md)AmberPoint，inc.提供</span><span class="sxs-lookup"><span data-stu-id="97492-125">[AmberPoint BizTalk Nano Agent](../esb-toolkit/amberpoint-biztalk-nano-agent.md) from AmberPoint, Inc.</span></span>
