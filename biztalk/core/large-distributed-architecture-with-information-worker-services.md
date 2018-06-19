---
title: Large Distributed Architecture 具有資訊工作者服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, examples
- architecture, large distributions
ms.assetid: 92f2d55c-3f51-42ca-99ef-60b23464691e
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6b9b1729411e089566988714b83778abac80eb0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262190"
---
# <a name="large-distributed-architecture-with-information-worker-services"></a><span data-ttu-id="3a650-102">具有資訊工作者服務的大型分散式架構</span><span class="sxs-lookup"><span data-stu-id="3a650-102">Large Distributed Architecture with Information Worker Services</span></span>
<span data-ttu-id="3a650-103">如需設計 BizTalk Server 部署的系統架構的完整資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="3a650-103">For complete information about designing the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="3a650-104">商務活動監控 (BAM) 可讓資訊工作者檢視商務程序以及直接與夥伴通訊。</span><span class="sxs-lookup"><span data-stu-id="3a650-104">Business Activity Monitoring (BAM) gives information workers visibility into the business processes and direct communication with partners.</span></span> <span data-ttu-id="3a650-105">如此將呈現保護這些服務安全的不同需求。</span><span class="sxs-lookup"><span data-stu-id="3a650-105">This presents a different set of requirements for securing these services.</span></span> <span data-ttu-id="3a650-106">資訊工作者很可能在企業網域中有帳戶，而不是在資料網域中有帳戶，而且他們需要存取服務介面網域以存取 BizTalk Server 產生的一些資料。</span><span class="sxs-lookup"><span data-stu-id="3a650-106">Information workers are likely to have accounts in the corporate domain and not in the data domain, and they need access service interfaces domain to access to some of the data BizTalk Server generates.</span></span>  
  
 <span data-ttu-id="3a650-107">下圖顯示包含 BAM 的分散式 BizTalk Server 架構。</span><span class="sxs-lookup"><span data-stu-id="3a650-107">The following figure shows a distributed BizTalk Server architecture that includes BAM.</span></span>  
  
 <span data-ttu-id="3a650-108">![分散式架構](../core/media/5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2.gif "5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2")</span><span class="sxs-lookup"><span data-stu-id="3a650-108">![Distributed Architecture](../core/media/5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2.gif "5aa6ab88-45ee-4b75-8e51-0ba0dd3fb4d2")</span></span>  
<span data-ttu-id="3a650-109">具有資訊工作者服務的分散式 BizTalk Server 架構</span><span class="sxs-lookup"><span data-stu-id="3a650-109">Distributed BizTalk Server Architecture with Information Worker Services</span></span>  
  
 <span data-ttu-id="3a650-110">所示的結構相比較[大型分散式架構](../core/large-distributed-architecture.md)，資訊工作者服務的分散式的架構包含其他資訊工作者服務，如 BAM 入口網站。</span><span class="sxs-lookup"><span data-stu-id="3a650-110">Compared to the architecture shown in [Large Distributed Architecture](../core/large-distributed-architecture.md), the distributed architecture for the information worker services contains an additional information worker services such as BAM Portal.</span></span> <span data-ttu-id="3a650-111">資訊工作者服務容器包含下列伺服器與服務：</span><span class="sxs-lookup"><span data-stu-id="3a650-111">The information worker services container includes the following servers and services:</span></span>  
  
-   <span data-ttu-id="3a650-112">BAM 入口網站伺服器。</span><span class="sxs-lookup"><span data-stu-id="3a650-112">A BAM Portal server.</span></span> <span data-ttu-id="3a650-113">商務使用者會使用 BAM 入口網站來存取 BAM 資料庫以監控關鍵效能指標 (KPI)，這項指標會測量達到商務目標的進度，以及其商務程序的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3a650-113">Business end users use the BAM portal to access the BAM databases to monitor Key Performance Indicators (KPIs), which measure progress toward a business goal, as well as other information about their business process.</span></span> <span data-ttu-id="3a650-114">此伺服器也擁有 BAM 查詢 Web 服務與 BAM 管理 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="3a650-114">This server also has the BAM Query Web service and BAM Management Web service.</span></span>  
  
-   <span data-ttu-id="3a650-115">Bam SQL Server: BAM 主要匯入資料庫、 BAM 封存資料庫、 BAM 星狀結構描述資料庫和 BAM 分析資料庫。</span><span class="sxs-lookup"><span data-stu-id="3a650-115">A SQL Server for BAM: the BAM Primary Import database, BAM Archive database, BAM Star Schema database, and BAM Analysis database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a650-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a650-116">See Also</span></span>  
 <span data-ttu-id="3a650-117">[大型分散式的架構](../core/large-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="3a650-117">[Large Distributed Architecture](../core/large-distributed-architecture.md) </span></span>  
 <span data-ttu-id="3a650-118">[縮小具有資訊工作者服務的架構](../core/scaled-down-architecture-with-information-worker-services.md) </span><span class="sxs-lookup"><span data-stu-id="3a650-118">[Scaled Down Architecture with Information Worker Services](../core/scaled-down-architecture-with-information-worker-services.md) </span></span>  
 <span data-ttu-id="3a650-119">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="3a650-119">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="3a650-120">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="3a650-120">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)