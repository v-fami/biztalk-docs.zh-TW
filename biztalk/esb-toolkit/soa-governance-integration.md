---
title: 使用 BizTalk Server 中 ESB Toolkit 的 SOA 控管整合 |Microsoft 文件
description: SOA 基礎系統及協力廠商與整合 BizTalk Server 中的 ESB Toolkit 的挑戰的清單
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
ms.openlocfilehash: 9e1489e01a8918d1dfa7ca61a69d57f5d7316f68
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22295014"
---
# <a name="soa-governance-integration"></a><span data-ttu-id="08926-103">SOA 控管整合</span><span class="sxs-lookup"><span data-stu-id="08926-103">SOA Governance Integration</span></span>
<span data-ttu-id="08926-104">企業級應用程式必須支援穩定且可靠的管理功能，能夠以符合商務需求、 政府法規、 服務等級協定 (Sla)，以及客戶及交易夥伴的期望。</span><span class="sxs-lookup"><span data-stu-id="08926-104">Enterprise-level applications must support robust and reliable management features to be able to comply with business requirements, government legislation, service level agreements (SLAs), and customer and trading partner expectations.</span></span> <span data-ttu-id="08926-105">執行階段控管著重於特別的挑戰之一和需求，成功地執行服務導向架構 (SOA) – 架構的系統符合這些需求。</span><span class="sxs-lookup"><span data-stu-id="08926-105">Run-time governance focuses specifically on the challenges of, and requirements for, successfully running service-oriented architecture (SOA)–based systems that meet these requirements.</span></span> <span data-ttu-id="08926-106">商務系統所傳遞品質是服務的定義其成功或失敗的主要因素。</span><span class="sxs-lookup"><span data-stu-id="08926-106">The quality of service delivered by a business system is the predominant factor that defines its success or failure.</span></span>  

## <a name="soa-challenges"></a><span data-ttu-id="08926-107">SOA 挑戰</span><span class="sxs-lookup"><span data-stu-id="08926-107">SOA challenges</span></span>  
 <span data-ttu-id="08926-108">SOA 型系統部署到實際執行環境的企業面臨一些挑戰，如下所示：</span><span class="sxs-lookup"><span data-stu-id="08926-108">Businesses deploying SOA-based systems into production face a number of challenges, including the following:</span></span>  
  
-   <span data-ttu-id="08926-109">維護和升級的成本降至最低，並允許累加式更新</span><span class="sxs-lookup"><span data-stu-id="08926-109">Minimizing the cost of maintenance and upgrades, and allowing incremental updates</span></span>  
  
-   <span data-ttu-id="08926-110">允許透過商務程序管理和撰寫工具快速變更</span><span class="sxs-lookup"><span data-stu-id="08926-110">Allowing rapid change through business process management and composition tools</span></span>  
  
-   <span data-ttu-id="08926-111">端對端安全性。這包括信任和保護訊息的寄件者、 接收者，與內容的隱私權。</span><span class="sxs-lookup"><span data-stu-id="08926-111">End-to-end security; this includes trust and protection of the privacy of message senders, receivers, and content</span></span>  
  
-   <span data-ttu-id="08926-112">識別、 管理和修復發生的例外狀況</span><span class="sxs-lookup"><span data-stu-id="08926-112">Identifying, managing, and repairing exceptions as they occur</span></span>  
  
-   <span data-ttu-id="08926-113">分開處理服務和取用者</span><span class="sxs-lookup"><span data-stu-id="08926-113">Decoupling of services and consumers</span></span>  
  
-   <span data-ttu-id="08926-114">測量，並證明位移成本考量 SOA 應用程式的商務價值</span><span class="sxs-lookup"><span data-stu-id="08926-114">Measuring and proving the business value of SOA applications to offset cost concerns</span></span>  
  
-   <span data-ttu-id="08926-115">控制重複或否則不需要服務的激增 （控管）</span><span class="sxs-lookup"><span data-stu-id="08926-115">Control (governance) of the proliferation of duplicate or otherwise unnecessary services</span></span>  
  
-   <span data-ttu-id="08926-116">促進潛在使用者初始的開發成本的降低所需的適當服務識別</span><span class="sxs-lookup"><span data-stu-id="08926-116">Facilitating the identification of the appropriate services required by potential users to reduce initial development cost</span></span>  
  
-   <span data-ttu-id="08926-117">管理服務的成本與持續性的維護的風險降至最低，並變更生命週期</span><span class="sxs-lookup"><span data-stu-id="08926-117">Managing the life cycle of services to minimize the cost and risk of ongoing maintenance and change</span></span>  
  
-   <span data-ttu-id="08926-118">簡化的實際使用適當的服務 （分離位置、 傳輸、 原則、 標準和傳訊樣式）</span><span class="sxs-lookup"><span data-stu-id="08926-118">Simplifying the actual usage of appropriate services (decoupling location, transport, policies, standards, and messaging styles)</span></span>  
  
-   <span data-ttu-id="08926-119">報告功能用來識別誰正在使用哪一種服務，，和原因</span><span class="sxs-lookup"><span data-stu-id="08926-119">Reporting facilities used to identify who is using which service, where, and why</span></span>  

## <a name="next-steps"></a><span data-ttu-id="08926-120">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="08926-120">Next steps</span></span>
 <span data-ttu-id="08926-121">[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]支援與兩個協力廠商執行階段控管系統整合：</span><span class="sxs-lookup"><span data-stu-id="08926-121">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports integration with two third-party run-time governance systems:</span></span>  
  
-   <span data-ttu-id="08926-122">**Sentinet SOA 解析器和 BizTalk Server Extensions**。</span><span class="sxs-lookup"><span data-stu-id="08926-122">**Sentinet SOA Resolver and BizTalk Server Extensions**.</span></span> <span data-ttu-id="08926-123">如需有關如何 Sentinet 擴充[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]功能，請參閱[擴充 BizTalk ESB Toolkit 功能 Sentinet](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md)。</span><span class="sxs-lookup"><span data-stu-id="08926-123">For more information on how Sentinet extends [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] capabilities, see [Extending BizTalk ESB Toolkit Capabilities with Sentinet](../technical-guides/extending-biztalk-esb-toolkit-capabilities-with-sentinet.md).</span></span>
  
-   <span data-ttu-id="08926-124">[SOA BizTalk 管理點](../esb-toolkit/soa-biztalk-management-point.md)從 SOA 軟體，inc.</span><span class="sxs-lookup"><span data-stu-id="08926-124">[SOA BizTalk Management Point](../esb-toolkit/soa-biztalk-management-point.md) from SOA Software, Inc.</span></span>  
  
-   <span data-ttu-id="08926-125">[AmberPoint BizTalk Nano Agent](../esb-toolkit/amberpoint-biztalk-nano-agent.md)從 AmberPoint，inc.</span><span class="sxs-lookup"><span data-stu-id="08926-125">[AmberPoint BizTalk Nano Agent](../esb-toolkit/amberpoint-biztalk-nano-agent.md) from AmberPoint, Inc.</span></span>