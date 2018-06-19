---
title: 調整節流閾值： 時間和原因 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9afb26c8-e5f4-4b78-9a45-a1263e3cb6ab
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b49ae78d4b2d0cf2dabfc69af9023b1e8676dea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229926"
---
# <a name="adjusting-throttling-thresholds-when-and-why"></a><span data-ttu-id="c0c96-102">調整節流閾值： 時間和原因</span><span class="sxs-lookup"><span data-stu-id="c0c96-102">Adjusting Throttling Thresholds: When and Why</span></span>
<span data-ttu-id="c0c96-103">當處理節流時，一個大小無法滿足所有的需要。</span><span class="sxs-lookup"><span data-stu-id="c0c96-103">When it comes to throttling, one size does not fit all.</span></span> <span data-ttu-id="c0c96-104">有各種因素，可決定最佳的設定應該是什麼。</span><span class="sxs-lookup"><span data-stu-id="c0c96-104">There are a range of factors that will determine what the optimal settings should be.</span></span> <span data-ttu-id="c0c96-105">有一個現成的方式，就是 BizTalk Server 提供了已經過測試證明的預設值，可有效保護系統不受待處理項目的傷害。</span><span class="sxs-lookup"><span data-stu-id="c0c96-105">Out of the box, BizTalk Server provides default values that have been proven through testing to effectively protect a system from things like backlog overages.</span></span> <span data-ttu-id="c0c96-106">但在某些情況下，這個作法可能太過激烈，</span><span class="sxs-lookup"><span data-stu-id="c0c96-106">However, for some scenarios, this may be too aggressive.</span></span> <span data-ttu-id="c0c96-107">下列範例將說明這一點。</span><span class="sxs-lookup"><span data-stu-id="c0c96-107">The following examples illustrate this point.</span></span>  
  
## <a name="example-1-peak-loads-and-database-size"></a><span data-ttu-id="c0c96-108">範例 1： 尖峰負載和資料庫大小</span><span class="sxs-lookup"><span data-stu-id="c0c96-108">Example 1: Peak Loads and Database Size</span></span>  
 <span data-ttu-id="c0c96-109">BizTalk Server 上所建置的每一個方案都有持續性輸送量上限 (MST)。</span><span class="sxs-lookup"><span data-stu-id="c0c96-109">Each solution built on BizTalk Server has a maximum sustainable throughput (MST).</span></span> <span data-ttu-id="c0c96-110">就定義上而言，只要負載維持在此上限以下，系統就可以永遠維持該負載。</span><span class="sxs-lookup"><span data-stu-id="c0c96-110">As long as load stays below this level, the system can sustain that load indefinitely, by definition.</span></span> <span data-ttu-id="c0c96-111">但就實際面而言，在負載設定檔中擁有尖峰和低峰要比擁有穩定且不會隨著時間變化的負載更為常見。</span><span class="sxs-lookup"><span data-stu-id="c0c96-111">In practice, however, it is more common to have peaks and valleys in the load profile than it is to have a steady load that doesn’t vary over time.</span></span>  
  
 <span data-ttu-id="c0c96-112">建置一個系統來處理尖峰負載下的某些待處理項目並在低峰時復原，是一個比較具成本效益的作法，而不要建置一個能夠處理永遠在最高尖峰負載的系統。</span><span class="sxs-lookup"><span data-stu-id="c0c96-112">Rather than build a system that is capable of sustaining the highest peak loads indefinitely, it is more cost effective to build a system that can handle some backlog under peak load, and recover during the valleys.</span></span> <span data-ttu-id="c0c96-113">但是，如果尖峰負載時所預期的待處理項目高於資料庫大小的預設節流值，則系統將會節流輸入來封鎖待處理項目。</span><span class="sxs-lookup"><span data-stu-id="c0c96-113">However, if the backlog expected during the peak loads is higher than the default throttling value for database size, then the system will block the backlog by throttling the input.</span></span> <span data-ttu-id="c0c96-114">如果這不是您想要的結果 (例如，因為您需要盡快消耗所有的輸入檔案)，則解決方案就是要增加資料庫大小閾值，以便在節流之前接受預期的待處理項目。</span><span class="sxs-lookup"><span data-stu-id="c0c96-114">If this is not desirable, for example, because you need all of the input files to be consumed as quickly as possible, then the solution is to raise the database size threshold to accept the expected backlog before throttling.</span></span>  
  
## <a name="example-2-memory-usage-optimization"></a><span data-ttu-id="c0c96-115">範例 2： 記憶體使用量最佳化</span><span class="sxs-lookup"><span data-stu-id="c0c96-115">Example 2: Memory Usage Optimization</span></span>  
 <span data-ttu-id="c0c96-116">為了要測量處理速度，節流所使用的另一個資源，就是測量主控件處理序可使用多少記憶體。</span><span class="sxs-lookup"><span data-stu-id="c0c96-116">Another resource that throttling uses in order to gauge processing speed is how much memory is available to host processes.</span></span> <span data-ttu-id="c0c96-117">如果與閾值相較之下，可用的記憶體變得太少，節流就會減少引擎從要處理之主控件佇列中擷取的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="c0c96-117">If the available memory gets too small compared to the threshold, throttling will slow down the number of messages the engine retrieves from the host queues to be worked on.</span></span> <span data-ttu-id="c0c96-118">在現今的企業等級伺服器中，記憶體的數量和可用性都可以有變化，特別是 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中提供了 x64 支援，所以可能需要增加或減少閾值，讓記憶體使用量最佳化。</span><span class="sxs-lookup"><span data-stu-id="c0c96-118">Given the variability in the amount and availability of memory on today’s enterprise class servers, especially with x64 support in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], the threshold may very well need to be raised or lowered to optimize memory usage.</span></span>  
  
## <a name="recommendation"></a><span data-ttu-id="c0c96-119">建議</span><span class="sxs-lookup"><span data-stu-id="c0c96-119">Recommendation</span></span>  
 <span data-ttu-id="c0c96-120">根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中會設定節流，為系統提供立即可用的完善保護。</span><span class="sxs-lookup"><span data-stu-id="c0c96-120">Throttling in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is configured by default to provide good protection for the system out of the box.</span></span> <span data-ttu-id="c0c96-121">但是，不應該理所當然地將預設設定視為最佳化設定。</span><span class="sxs-lookup"><span data-stu-id="c0c96-121">The default settings should not, however, be taken for granted as optimal.</span></span> <span data-ttu-id="c0c96-122">請監視效能計數器來瞭解節流狀態，看看是否正在進行節流，然後自行測量節流所依據的資源 (例如，資料庫大小或記憶體使用量) 是過度利用還是利用不足，然後據此來往上或往下調整閾值。</span><span class="sxs-lookup"><span data-stu-id="c0c96-122">Monitor the performance counters for throttling states to see if throttling is taking place, then gauge for yourself if the resource on which throttling is based (for example, database size or memory usage) is under or over utilized, then adjust the throttling thresholds up or down accordingly.</span></span>