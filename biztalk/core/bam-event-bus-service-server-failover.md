---
title: BAM 事件匯流排服務伺服器容錯移轉 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f12378c8-09bb-45c1-ade1-d9b20131461f
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5c1fafc3e97d9905a6efd0de8ff0f389c2a389bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230638"
---
# <a name="bam-event-bus-service-server-failover"></a><span data-ttu-id="3ff64-102">BAM 事件匯流排服務伺服器容錯移轉</span><span class="sxs-lookup"><span data-stu-id="3ff64-102">BAM Event Bus Service Server Failover</span></span>
<span data-ttu-id="3ff64-103">BAM 事件匯流排服務包含容錯邏輯，可讓它從意外的失敗中復原和重新啟動，而不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="3ff64-103">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span>  
  
 <span data-ttu-id="3ff64-104">當您在多部電腦上啟用 BAM 事件匯流排服務時，如果服務發生錯誤，容錯移轉邏輯將會偵測到 BAM 事件匯流排服務已經終止，並自動在另一部電腦上啟動新的 BAM 事件匯流排服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ff64-104">When you enable the BAM Event Bus service on multiple computers, and the service fails, failover logic will detect that a BAM Event Bus service has terminated, and the logic automatically starts a new instance of the BAM Event Bus service on another computer.</span></span>  
  
 <span data-ttu-id="3ff64-105">下圖顯示 BAM 事件匯流排如何執行簡單負載平衡以處理電腦或網路的錯誤情況。</span><span class="sxs-lookup"><span data-stu-id="3ff64-105">The following figure displays how the BAM Event Bus handles computer or network failures by performing simple load balancing.</span></span> <span data-ttu-id="3ff64-106">在 BAM 事件匯流排服務啟動前，先設定好兩個來源與一個目的地。</span><span class="sxs-lookup"><span data-stu-id="3ff64-106">Two sources and one destination were configured before the BAM Event Bus service starts.</span></span>  
  
 ![](../core/media/ebiz-bam-admin-evntbuspoolfail.gif "ebiz_bam_admin_evntbuspoolfail")  
<span data-ttu-id="3ff64-107">BAM 事件匯流排服務進行負載平衡</span><span class="sxs-lookup"><span data-stu-id="3ff64-107">How the BAM Event Bus service load balances</span></span>  
  
 <span data-ttu-id="3ff64-108">BAM 事件匯流排服務執行下列動作以進行負載平衡：</span><span class="sxs-lookup"><span data-stu-id="3ff64-108">The BAM Event Bus service load balances by performing the following:</span></span>  
  
-   <span data-ttu-id="3ff64-109">**答： Server1 處理來自 2 個來源 （工作階段） 的事件資料**。</span><span class="sxs-lookup"><span data-stu-id="3ff64-109">**A: Server1 processes the event data from 2 sources (sessions)**.</span></span> <span data-ttu-id="3ff64-110">在 BAM 事件匯流排服務的執行個體建立在 Server2 之前，BAM 事件匯流排協調流程執行個體會先建立在 Server1 上。</span><span class="sxs-lookup"><span data-stu-id="3ff64-110">Before an instance of the BAM Event Bus service is created on Server2, a BAM Event Bus orchestration instance is created on Server1.</span></span> <span data-ttu-id="3ff64-111">伺服器會發現已經沒有其他可用的伺服器，於是為 Src1 和 Src2 收取這兩個工作階段。</span><span class="sxs-lookup"><span data-stu-id="3ff64-111">The server finds that there are no other servers available, and therefore picks up both sessions for Src1 and Src2.</span></span>  
  
-   <span data-ttu-id="3ff64-112">**B: Server2 上線，並加入 BAM 事件匯流排集區**。</span><span class="sxs-lookup"><span data-stu-id="3ff64-112">**B: Server2 is brought online and joins the BAM Event Bus pool**.</span></span> <span data-ttu-id="3ff64-113">當一個 BAM 事件匯流排服務執行個體建立在 Server2 上之後，Server1 會捨棄一個工作階段，而 Server2 會收取該工作階段。</span><span class="sxs-lookup"><span data-stu-id="3ff64-113">After an instance of the BAM Event Bus service is created on Server2, Server1 drops one BAM Event Bus service session and Server2 picks it up.</span></span>  
  
-   <span data-ttu-id="3ff64-114">**C: Server1 失敗**。</span><span class="sxs-lookup"><span data-stu-id="3ff64-114">**C: Server1 fails**.</span></span> <span data-ttu-id="3ff64-115">Server1 在 Server2 加入 BAM 事件匯流排集區後發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="3ff64-115">Server1 fails after Server2 joins the BAM Event Bus pool.</span></span>  
  
-   <span data-ttu-id="3ff64-116">**D: Server2 處理來自 2 個來源 （工作階段） 的事件資料**。</span><span class="sxs-lookup"><span data-stu-id="3ff64-116">**D: Server2 processes the event data from 2 sources (sessions)**.</span></span> <span data-ttu-id="3ff64-117">Server2 為 Src1 和 Src2 收取這兩個工作階段。</span><span class="sxs-lookup"><span data-stu-id="3ff64-117">Server2 picks up both sessions for Src1 and Src2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ff64-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ff64-118">See Also</span></span>  
 <span data-ttu-id="3ff64-119">[管理 BAM 事件匯流排服務](../core/managing-the-bam-event-bus-service.md) </span><span class="sxs-lookup"><span data-stu-id="3ff64-119">[Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md) </span></span>  
 <span data-ttu-id="3ff64-120">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="3ff64-120">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="3ff64-121">商務活動監控 (BAM)</span><span class="sxs-lookup"><span data-stu-id="3ff64-121">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)