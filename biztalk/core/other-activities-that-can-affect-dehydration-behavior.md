---
title: 其他可能影響凍結行為的活動 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed940448-d3b1-4308-9b38-887904e03bd0
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed8c37dbcca5c15e777cf6a98e50227f8752e324
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979295"
---
# <a name="other-activities-that-can-affect-dehydration-behavior"></a><span data-ttu-id="dd186-102">可能影響凍結行為的其他活動</span><span class="sxs-lookup"><span data-stu-id="dd186-102">Other Activities That Can Affect Dehydration Behavior</span></span>
<span data-ttu-id="dd186-103">下列活動會直接或間接影響凍結及整體效能，所以應該列入任何測試案例的考量項目。</span><span class="sxs-lookup"><span data-stu-id="dd186-103">The following activities directly or indirectly impact dehydration and overall performance and so should be factored into any testing scenarios.</span></span>  
  
- <span data-ttu-id="dd186-104">**BizTalk Server 管理主控台查詢。**</span><span class="sxs-lookup"><span data-stu-id="dd186-104">**BizTalk Server Administration Console queries.**</span></span> <span data-ttu-id="dd186-105">這些查詢會依據查詢的類型及頻率，耗用資源並影響整體輸送量。</span><span class="sxs-lookup"><span data-stu-id="dd186-105">These queries consume resources and affect overall throughput depending on the type and frequency of the query.</span></span>  
  
- <span data-ttu-id="dd186-106">**備份、 封存和清理活動。**</span><span class="sxs-lookup"><span data-stu-id="dd186-106">**Backup, archiving, and purging activities.**</span></span> <span data-ttu-id="dd186-107">這些活動也會耗用資源，而應該納入任何測試實例的考量。</span><span class="sxs-lookup"><span data-stu-id="dd186-107">These activities also consume resources and should be factored into any testing scenarios.</span></span>  
  
- <span data-ttu-id="dd186-108">**混合的 32 位元和 64 位元主控件。**</span><span class="sxs-lookup"><span data-stu-id="dd186-108">**Mixed 32-bit and 64-bit hosts.**</span></span> <span data-ttu-id="dd186-109">以下是在使用混合 32 位元及 64 位元的主控件時要考量的一些事項：</span><span class="sxs-lookup"><span data-stu-id="dd186-109">Here are some things to consider when using mixed 32-bit and 64-bit hosts:</span></span>  
  
  - <span data-ttu-id="dd186-110">在使用量很大時，我們要測量消耗的虛擬及實體記憶體，並將其與特定閾值進行比較。</span><span class="sxs-lookup"><span data-stu-id="dd186-110">Under stress we measure consumed virtual and physical memory and compare that against certain thresholds.</span></span> <span data-ttu-id="dd186-111">在 64 位元的系統中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序會使用較多的記憶體，所以凍結原則會與使用相同系統及相同預設值的 32 位元系統不同。</span><span class="sxs-lookup"><span data-stu-id="dd186-111">In 64 bit systems the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] process uses more memory so there will be a difference in dehydration policy from 32-bits using the same system and the same default values.</span></span> <span data-ttu-id="dd186-112">請確定分隔協調流程、接收、傳送和訊息方塊主控件。</span><span class="sxs-lookup"><span data-stu-id="dd186-112">Be sure to separate orchestration, receive, send and message box hosts.</span></span>  
  
     <span data-ttu-id="dd186-113">在 64 位元系統上使用預設的 32 位元閥值時，並不會有明顯的差別，只要 64 位元方塊上只有協調流程主控件。</span><span class="sxs-lookup"><span data-stu-id="dd186-113">There is not an obvious difference when using the default 32-bit thresholds for 64-bit systems, as long as only the orchestration host is on the 64 bit box.</span></span> <span data-ttu-id="dd186-114">不過，在壓力各種**MemoryThrottlingCriteria**設定應該至少會加倍或使用量 （只要您有足夠的記憶體），但應該調整案例以最大化輸送量，因為有許多派上用場的因素。</span><span class="sxs-lookup"><span data-stu-id="dd186-114">However, under stress the various **MemoryThrottlingCriteria** settings should be at least doubled or tripled (as long as you have enough memory), but the scenario should be tuned for maximizing throughput because there are many factors that come into play.</span></span> <span data-ttu-id="dd186-115">您應該在使用量很大時調整凍結閥值，以找出最佳的設定。</span><span class="sxs-lookup"><span data-stu-id="dd186-115">You should tune the dehydration thresholds under stress to find what is optimal for them.</span></span>  
  
  - <span data-ttu-id="dd186-116">凍結行為是依據每個訂閱的傳遞時間歷程記錄而定；不同訂閱的歷程記錄可能會不同，所以在調整凍結屬性值時，請將這點列入考慮。</span><span class="sxs-lookup"><span data-stu-id="dd186-116">Dehydration behavior depends on delivery time history of every subscription; the histories could be different for different subscriptions so consider this in tuning your dehydration property values.</span></span>  
  
  - <span data-ttu-id="dd186-117">當協調流程主控件服務在一個主控件上進行回收，但未在另一個主控件上回收時，歷程記錄就會不同。</span><span class="sxs-lookup"><span data-stu-id="dd186-117">When the orchestration host service is recycled on one host, but not on another, the histories will be different.</span></span>  
  
  - <span data-ttu-id="dd186-118">當伺服器使用不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，將會是中的凍結原則兩者之間的差異。</span><span class="sxs-lookup"><span data-stu-id="dd186-118">When servers are using different versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], there will be a difference in dehydration policy between the two.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd186-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd186-119">See Also</span></span>  
 [<span data-ttu-id="dd186-120">BTSNTSvc.exe.config 檔案</span><span class="sxs-lookup"><span data-stu-id="dd186-120">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)