---
title: 縮小架構具有資訊工作者服務 |Microsoft 文件
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
ms.assetid: ce1217bf-84a5-4888-89ba-dce85dc38340
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d02558e5904bf740c09ea0db614b2189555ac75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269246"
---
# <a name="scaled-down-architecture-with-information-worker-services"></a><span data-ttu-id="b6b85-102">使用資訊工作者服務縮小架構</span><span class="sxs-lookup"><span data-stu-id="b6b85-102">Scaled Down Architecture with Information Worker Services</span></span>
<span data-ttu-id="b6b85-103">完成 BizTalk Server 部署的系統架構的詳細資訊，請參閱[範例 BizTalk Server 架構](../core/sample-biztalk-server-architectures.md)。</span><span class="sxs-lookup"><span data-stu-id="b6b85-103">For complete information about the system architecture for BizTalk Server deployment, see [Sample BizTalk Server Architectures](../core/sample-biztalk-server-architectures.md).</span></span>  
  
 <span data-ttu-id="b6b85-104">下圖提供範例 BizTalk Server 架構，包括結合一些網域與 BizTalk Server 以降低您需要的伺服器與防火牆之數目的資訊工作者服務。</span><span class="sxs-lookup"><span data-stu-id="b6b85-104">The following figure provides a sample BizTalk Server architecture including the information worker services that combines some of the domains and BizTalk Servers to reduce the number of servers and firewalls you need.</span></span> <span data-ttu-id="b6b85-105">雖然此架構並非最分散的架構，但仍根據其功能來分隔 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="b6b85-105">While this architecture is not the most distributed, it still separates the BizTalk Servers based on their function.</span></span>  
  
 <span data-ttu-id="b6b85-106">![規模縮減拓撲](../core/media/cd3c85df-40f5-4382-9f8b-b2609f76e8b1.gif "cd3c85df-40f5-4382-9f8b-b2609f76e8b1")</span><span class="sxs-lookup"><span data-stu-id="b6b85-106">![Scaledown Topology](../core/media/cd3c85df-40f5-4382-9f8b-b2609f76e8b1.gif "cd3c85df-40f5-4382-9f8b-b2609f76e8b1")</span></span>  
  
        Scaled Down Architecture with Information Worker Services  
  
 <span data-ttu-id="b6b85-107">在上圖中，服務介面與服務網域中的伺服器對應至 BizTalk 主控件，而不是實體伺服器。</span><span class="sxs-lookup"><span data-stu-id="b6b85-107">In the previous figure, the servers in the service interfaces and services domain correspond to BizTalk Hosts, and not physical servers.</span></span> <span data-ttu-id="b6b85-108">雖然建議您將主要密碼伺服器與管理工具保存在獨立電腦中，但您可以讓追蹤、處理、傳送以及接收主控件的主控件執行個體在多重電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="b6b85-108">While it is recommended to keep the master secret server and the administrative tools in stand-alone computers, you can have host instances for the tracking, processing, send, and receive hosts running on multiple computers.</span></span> <span data-ttu-id="b6b85-109">同理，周邊網路中的伺服器對應至邏輯位置。</span><span class="sxs-lookup"><span data-stu-id="b6b85-109">Similarly, the servers in the perimeter network correspond to logical locations.</span></span>  
  
 <span data-ttu-id="b6b85-110">周邊網路中的 SMTP、Windows 訊息佇列 (也稱為 MSMQ)、檔案以及 SQL 伺服器，分別對應至郵件伺服器、佇列、目錄或 SQL Server，服務介面網域中的 BizTalk 接收與傳送主控件由此接收和傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b6b85-110">The servers in the perimeter network for SMTP, Windows Message Queuing (also known as MSMQ), File, and SQL correspond to the mail servers, queue, directory, or SQL Server respectively from which the BizTalk receive and send hosts in the service interfaces domain receive and send messages.</span></span>  
  
 <span data-ttu-id="b6b85-111">資料網域中的 BAM 資料庫包含「BAM 主要匯入」、「BAM 分析」、「BAM 星狀結構描述」以及「BAM 封存」資料庫。</span><span class="sxs-lookup"><span data-stu-id="b6b85-111">The BAM databases in the data domain are BAM Primary Import, BAM Analysis, BAM Star Schema, and BAM Archive databases.</span></span> <span data-ttu-id="b6b85-112">「資料」網域中的「追蹤」與「分析」資料庫是 BizTalk Server 用於儲存追蹤資訊的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b6b85-112">The Tracking and Analysis databases in the Data domain are the ones BizTalk Server uses for storing tracking information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6b85-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6b85-113">See Also</span></span>  
 <span data-ttu-id="b6b85-114">[縮小架構](../core/scaled-down-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="b6b85-114">[Scaled Down Architecture](../core/scaled-down-architecture.md) </span></span>  
 <span data-ttu-id="b6b85-115">[具有資訊工作者服務的大型分散式的架構](../core/large-distributed-architecture-with-information-worker-services.md) </span><span class="sxs-lookup"><span data-stu-id="b6b85-115">[Large Distributed Architecture with Information Worker Services](../core/large-distributed-architecture-with-information-worker-services.md) </span></span>  
 <span data-ttu-id="b6b85-116">[設計安全架構](../core/designing-a-secure-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="b6b85-116">[Designing a Secure Architecture](../core/designing-a-secure-architecture.md) </span></span>  
 [<span data-ttu-id="b6b85-117">BizTalk Server 架構範例</span><span class="sxs-lookup"><span data-stu-id="b6b85-117">Sample BizTalk Server Architectures</span></span>](../core/sample-biztalk-server-architectures.md)