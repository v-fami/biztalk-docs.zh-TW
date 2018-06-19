---
title: 縮小架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, small distributions
- architecture, examples
ms.assetid: e25798aa-4a1e-418c-9e0c-db964e8b5a80
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a112f3f737a1a5aec0cfac16b7689d3dada1e8ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269358"
---
# <a name="scaled-down-architecture"></a><span data-ttu-id="55dd6-102">縮小架構</span><span class="sxs-lookup"><span data-stu-id="55dd6-102">Scaled Down Architecture</span></span>
<span data-ttu-id="55dd6-103">如需系統架構的完整資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]部署，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="55dd6-103">For complete information about the system architecture for[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="55dd6-104">下圖提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 架構範例，這個架構合併了部分網域與 BizTalk Server，以降低您需要的伺服器與防火牆數量。</span><span class="sxs-lookup"><span data-stu-id="55dd6-104">The following figure provides a sample [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] architecture that combines some of the domains and BizTalk Servers to reduce the number of servers and firewalls you need.</span></span> <span data-ttu-id="55dd6-105">雖然此架構並非最分散的架構，但仍根據其功能來分隔 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="55dd6-105">While this architecture is not the most distributed, it still separates the BizTalk Servers based on their function.</span></span>  
  
 <span data-ttu-id="55dd6-106">![縮小架構](../core/media/16ebc4ef-ff64-495b-bcac-5c1fd70ca173.gif "16ebc4ef-ff64-495b-bcac-5c1fd70ca173")</span><span class="sxs-lookup"><span data-stu-id="55dd6-106">![Scaled down architecture](../core/media/16ebc4ef-ff64-495b-bcac-5c1fd70ca173.gif "16ebc4ef-ff64-495b-bcac-5c1fd70ca173")</span></span>  
  
        Scaled Down Architecture  
  
 <span data-ttu-id="55dd6-107">在上圖中，服務介面與服務網域中的伺服器對應至 BizTalk 主控件，而不是實體伺服器。</span><span class="sxs-lookup"><span data-stu-id="55dd6-107">In the previous figure, the servers in the service interfaces and services domain correspond to BizTalk Hosts, and not physical servers.</span></span> <span data-ttu-id="55dd6-108">雖然建議您將主要密碼伺服器與管理工具保存在獨立電腦中，但您可以讓追蹤、處理、傳送以及接收主控件的主控件執行個體在多重電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="55dd6-108">While it is recommended to keep the master secret server and the administrative tools in stand-alone computers, you can have host instances for the tracking, processing, send, and receive hosts running on multiple computers.</span></span> <span data-ttu-id="55dd6-109">同理，周邊網路中的伺服器對應至邏輯位置。</span><span class="sxs-lookup"><span data-stu-id="55dd6-109">Similarly, the servers in the perimeter network correspond to logical locations.</span></span>  
  
 <span data-ttu-id="55dd6-110">周邊網路中 SMTP、訊息佇列、檔案及 SQL 等伺服器，分別對應至郵件伺服器、佇列、目錄或 SQL Server，處理與服務網域中的 BizTalk 接收與傳送主控件會由此接收和傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="55dd6-110">The servers in the perimeter network for SMTP, Message Queuing, File, and SQL correspond to the mail servers, queue, directory, or SQL Server respectively from which the BizTalk receive and send hosts in the processing and services domain receive and send messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55dd6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="55dd6-111">See Also</span></span>  
 <span data-ttu-id="55dd6-112">[縮小具有資訊工作者服務的架構](../core/scaled-down-architecture-with-information-worker-services.md) </span><span class="sxs-lookup"><span data-stu-id="55dd6-112">[Scaled Down Architecture with Information Worker Services](../core/scaled-down-architecture-with-information-worker-services.md) </span></span>  
 <span data-ttu-id="55dd6-113">[大型分散式的架構](../core/large-distributed-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="55dd6-113">[Large Distributed Architecture](../core/large-distributed-architecture.md) </span></span>  
 <span data-ttu-id="55dd6-114">[設計安全架構](../core/designing-a-secure-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="55dd6-114">[Designing a Secure Architecture](../core/designing-a-secure-architecture.md) </span></span>  
 [<span data-ttu-id="55dd6-115">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="55dd6-115">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)