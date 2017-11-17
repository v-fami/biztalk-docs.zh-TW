---
title: "透過主控件節流將資源使用最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host throttling
- performance, host throttling
ms.assetid: 823b431d-707d-4201-9a6e-4a879e767b66
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8fa30cb66371ef519741658dec47e08f6f92e871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-resource-usage-through-host-throttling"></a><span data-ttu-id="e8517-102">透過主控件節流將資源使用最佳化</span><span class="sxs-lookup"><span data-stu-id="e8517-102">Optimizing Resource Usage Through Host Throttling</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e8517-103">利用數種不同的 Microsoft 技術，其中每個可能會耗用大量記憶體、 磁碟和 BizTalk server 和包含 BizTalk Server 資料庫的 SQL 伺服器上可用的 CPU 資源。</span><span class="sxs-lookup"><span data-stu-id="e8517-103"> makes use of several different Microsoft technologies, each of which can consume a significant portion of the memory, disk, and CPU resources available on the BizTalk server and the SQL server that contains the BizTalk Server databases.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e8517-104">利用節流機制協助管理以降低使用的資源競爭可用資源的使用。</span><span class="sxs-lookup"><span data-stu-id="e8517-104"> employs a throttling mechanism to help manage the use of available resources to minimize resource use contention.</span></span> <span data-ttu-id="e8517-105">本主題討論此機制的設計。</span><span class="sxs-lookup"><span data-stu-id="e8517-105">This topic discusses the design of this mechanism.</span></span> <span data-ttu-id="e8517-106">如需如何調整節流值的資訊，請參閱[使用設定儀表板進行 BizTalk Server 效能微調](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)。</span><span class="sxs-lookup"><span data-stu-id="e8517-106">For information on how to adjust the throttling values, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8517-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="e8517-107">In This Section</span></span>  
  
-   [<span data-ttu-id="e8517-108">什麼是主控件節流？</span><span class="sxs-lookup"><span data-stu-id="e8517-108">What Is Host Throttling?</span></span>](../core/what-is-host-throttling.md)  
  
-   [<span data-ttu-id="e8517-109">BizTalk Server 如何實作主控件節流</span><span class="sxs-lookup"><span data-stu-id="e8517-109">How BizTalk Server Implements Host Throttling</span></span>](../core/how-biztalk-server-implements-host-throttling.md)  
  
-   [<span data-ttu-id="e8517-110">主控件節流效能計數器</span><span class="sxs-lookup"><span data-stu-id="e8517-110">Host Throttling Performance Counters</span></span>](../core/host-throttling-performance-counters.md)  
  
-   [<span data-ttu-id="e8517-111">節流設計建議</span><span class="sxs-lookup"><span data-stu-id="e8517-111">Throttling Design Recommendations</span></span>](../core/throttling-design-recommendations.md)