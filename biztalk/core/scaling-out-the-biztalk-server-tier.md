---
title: 向外擴充 BizTalk Server 層 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, planning
- scaling, load balancing
- host instances, scaling
- scaling, examples
- fault tolerance
- scaling, scaling out
- scaling, fault tolerance
- NLB system, scaling
- scaling, host instances
ms.assetid: 01d1ab20-d7a9-4d0b-a61e-65e56fe5010e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35674e89d8f8104a35718531f2a87f95e8bc67e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271966"
---
# <a name="scaling-out-the-biztalk-server-tier"></a><span data-ttu-id="48796-102">向外擴充 BizTalk Server 層</span><span class="sxs-lookup"><span data-stu-id="48796-102">Scaling Out the BizTalk Server Tier</span></span>
<span data-ttu-id="48796-103">若要向外擴充 BizTalk 層，請新增更多硬體至現有的拓撲。</span><span class="sxs-lookup"><span data-stu-id="48796-103">To scale out the BizTalk tier, add more hardware to the existing topology.</span></span> <span data-ttu-id="48796-104">建議您在下列情況下新增硬體：</span><span class="sxs-lookup"><span data-stu-id="48796-104">It is recommended that you add hardware in the following scenarios:</span></span>  
  
-   <span data-ttu-id="48796-105">BizTalk Server 成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="48796-105">BizTalk Server becomes a bottleneck.</span></span> <span data-ttu-id="48796-106">瓶頸本身可能是由於以下其中一個問題所造成：</span><span class="sxs-lookup"><span data-stu-id="48796-106">The bottleneck itself may be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="48796-107">CPU：若實例使用大量 CPU 管線、對應或協調流程，BizTalk Server 將不會有額外的 CPU 空間。</span><span class="sxs-lookup"><span data-stu-id="48796-107">CPU: If the scenario uses CPU intensive pipelines, maps, or orchestrations, the BizTalk servers will not have any extra CPU headroom.</span></span>  
  
-   <span data-ttu-id="48796-108">記憶體和 I/O：若現有的電腦已經到達記憶體和 IO 的上限，增加資源的唯一方法是新增另一部實體電腦。</span><span class="sxs-lookup"><span data-stu-id="48796-108">Memory and I/O: If the existing computers have reached their maximum limit on memory and IO, the only way to add resources is to add another physical computer.</span></span>  
  
-   <span data-ttu-id="48796-109">擴充的成本太昂貴。</span><span class="sxs-lookup"><span data-stu-id="48796-109">Scaling up is too expensive.</span></span> <span data-ttu-id="48796-110">例如，考量一個 BizTalk CPU 處於最大容量的 BizTalk Server 拓撲。</span><span class="sxs-lookup"><span data-stu-id="48796-110">For example, consider the 1 BizTalk Server topology where the BizTalk CPU is at maximum capacity.</span></span> <span data-ttu-id="48796-111">若新增額外的雙處理器機器比將雙處理器升級為四處理器便宜，您應該向外擴充系統。</span><span class="sxs-lookup"><span data-stu-id="48796-111">If it is cheaper to add extra dual processor machines instead of upgrading the dual processor to a quad processor, you should instead scale-outyour system.</span></span>  
  
-   <span data-ttu-id="48796-112">擴充無法解決瓶頸。</span><span class="sxs-lookup"><span data-stu-id="48796-112">Scaling-up does not fix the bottleneck.</span></span> <span data-ttu-id="48796-113">下列情況下擴充可能無法解決問題：</span><span class="sxs-lookup"><span data-stu-id="48796-113">Scaling up may not work in the following scenarios:</span></span>  
  
    -   <span data-ttu-id="48796-114">BizTalk 電腦的 IO 已達最高層次，因此您需要另一台機器來擴充 IO。</span><span class="sxs-lookup"><span data-stu-id="48796-114">IO is at the maximum level for the BizTalk computer so you need another computer to scale the IO.</span></span>  
  
    -   <span data-ttu-id="48796-115">作業系統的記憶體已達最高層次。</span><span class="sxs-lookup"><span data-stu-id="48796-115">Memory is at the maximum level for your operating system.</span></span> <span data-ttu-id="48796-116">在此情況下，擴充系統的唯一方法是加入額外的 BizTalk 電腦到拓撲。</span><span class="sxs-lookup"><span data-stu-id="48796-116">In this scenario, the only way to scale your system is to add an extra BizTalk computermachine to the topology.</span></span>  
  
 <span data-ttu-id="48796-117">在某些情況下，您可能想要專用的伺服器來接收訊息、傳送訊息以及處理訊息。</span><span class="sxs-lookup"><span data-stu-id="48796-117">In some scenarios, you may want dedicated servers for receiving messages, sending messages, and processing them.</span></span> <span data-ttu-id="48796-118">當您擁有專用伺服器時，較容易在一台電腦上隔離問題和進行維護，不影響其他電腦。</span><span class="sxs-lookup"><span data-stu-id="48796-118">When you have dedicated servers, it is easier to isolate problems and do maintenance on one computer without impacting the others.</span></span> <span data-ttu-id="48796-119">您可以向外擴充 BizTalk 層來新增這些電腦。</span><span class="sxs-lookup"><span data-stu-id="48796-119">You can add these computers by scaling our the BizTalk tier.</span></span>  
  
## <a name="when-you-cant-scale-out-the-biztalk-tier"></a><span data-ttu-id="48796-120">當您無法向外擴充 BizTalk 層時</span><span class="sxs-lookup"><span data-stu-id="48796-120">When You Can’t Scale Out the BizTalk Tier</span></span>  
  
-   <span data-ttu-id="48796-121">MessageBox 資料庫成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="48796-121">The MessageBox database is the bottleneck.</span></span>  
  
-   <span data-ttu-id="48796-122">配接器成為瓶頸。</span><span class="sxs-lookup"><span data-stu-id="48796-122">An adapter becomes the bottleneck.</span></span> <span data-ttu-id="48796-123">例如，若使用的是 SQL 配接器，則在增加 BizTalk 接收器的數量之後，BizTalk SQL 配接器從中提取資料之 SQL 資料庫上的鎖定爭用會增加。</span><span class="sxs-lookup"><span data-stu-id="48796-123">For example, if you are using the SQL adapter, after you increase the number of BizTalk receivers, lock contention increases on the SQL database where the BizTalk SQL adapter is pulling data from.</span></span> <span data-ttu-id="48796-124">這樣會限制您向外擴充 SQL 配接器的能力。</span><span class="sxs-lookup"><span data-stu-id="48796-124">This limits your ability to scale out the SQL adapter.</span></span>  
  
 <span data-ttu-id="48796-125">下表顯示如何向外擴充 BizTalk 層的範例。</span><span class="sxs-lookup"><span data-stu-id="48796-125">The following figure shows an example of how you might scale out the BizTalk tier.</span></span>  
  
 <span data-ttu-id="48796-126">![向外擴充 BTS](../core/media/scaleoutbts.gif "ScaleOutBTS")</span><span class="sxs-lookup"><span data-stu-id="48796-126">![Scaleout BTS](../core/media/scaleoutbts.gif "ScaleOutBTS")</span></span>  
  
 <span data-ttu-id="48796-127">下表顯示一個向外擴充的 BizTalk 拓撲，從一台 BizTalk Server 擴充成兩台 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="48796-127">This figure shows a scaled-out BizTalk topology, scaling from one BizTalk server to 2 BizTalk servers.</span></span> <span data-ttu-id="48796-128">在一台 BizTalk Server 拓撲中，三個主控件執行個體共用 BizTalk 電腦資源。</span><span class="sxs-lookup"><span data-stu-id="48796-128">In the one BizTalk server topology, three host instances are sharing the BizTalk computer resources.</span></span> <span data-ttu-id="48796-129">在兩台 BizTalk Server 拓撲中，傳輸主控件分別在不同伺服器上，以獲得更大的輸送量。</span><span class="sxs-lookup"><span data-stu-id="48796-129">In the two BizTalk server topology, the transmit host is separated onto a different server, which achieves more throughput.</span></span>  
  
## <a name="considerations-when-scaling-out-the-biztalk-tier"></a><span data-ttu-id="48796-130">向外擴充 BizTalk Server 層的考量</span><span class="sxs-lookup"><span data-stu-id="48796-130">Considerations When Scaling Out the BizTalk Tier</span></span>  
 <span data-ttu-id="48796-131">在您新增其他 BizTalk Server 電腦之前，必須考慮下列問題：</span><span class="sxs-lookup"><span data-stu-id="48796-131">You must consider the following questions before you add another BizTalk Server computer:</span></span>  
  
#### <a name="how-do-i-configure-the-system-for-load-balancing-and-fault-tolerance-when-i-scale-out-the-biztalk-tier"></a><span data-ttu-id="48796-132">向外擴充 BizTalk 層時，如何設定系統以達負載平衡和容錯？</span><span class="sxs-lookup"><span data-stu-id="48796-132">How do I configure the system for load balancing and fault tolerance when I scale out the BizTalk tier?</span></span>  
 <span data-ttu-id="48796-133">負載平衡和容錯技術的選擇取決於實例中使用的配接器。</span><span class="sxs-lookup"><span data-stu-id="48796-133">The selection of load balancing and fault tolerance technology depends on the adapter that is being used in the scenario.</span></span> <span data-ttu-id="48796-134">對於 SOAP 和 HTTP 配接器，建議的方式是使用 NLB。</span><span class="sxs-lookup"><span data-stu-id="48796-134">For SOAP and HTTP adapters, the recommended way is to use NLB.</span></span> <span data-ttu-id="48796-135">請參閱 NLB 文件以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="48796-135">Refer to NLB documentation for more details.</span></span>  
  
#### <a name="how-do-i-refactor-the-host-instances"></a><span data-ttu-id="48796-136">如何重整主控件執行個體？</span><span class="sxs-lookup"><span data-stu-id="48796-136">How do I refactor the host instances?</span></span>  
 <span data-ttu-id="48796-137">當您向外擴充 BizTalk 層時，並沒有一定的規則可決定應如何重整主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="48796-137">There is no one rule to determine how you should refactor the host instances when you scale out the BizTalk tier.</span></span> <span data-ttu-id="48796-138">建構主控件執行個體的時機取決於實例的複雜性。</span><span class="sxs-lookup"><span data-stu-id="48796-138">When you factor the host instances depends on the complexity of scenario.</span></span> <span data-ttu-id="48796-139">以下是如何建構主控件執行個體的一些範例。</span><span class="sxs-lookup"><span data-stu-id="48796-139">Following are some examples how to factor the host instances.</span></span>  
  
##### <a name="scenario-1"></a><span data-ttu-id="48796-140">實例 1</span><span class="sxs-lookup"><span data-stu-id="48796-140">Scenario 1</span></span>  
 <span data-ttu-id="48796-141">一個 BizTalk Server 組態，接收和傳輸主控件執行個體在同一台電腦上。</span><span class="sxs-lookup"><span data-stu-id="48796-141">One BizTalk server configuration, and receive and transmit host instances are on the same computer.</span></span>  
  
 <span data-ttu-id="48796-142">假設有 CPU 瓶頸存在。</span><span class="sxs-lookup"><span data-stu-id="48796-142">Assume there is a CPU bottleneck.</span></span> <span data-ttu-id="48796-143">您新增另一部相同的 BizTalk 電腦到群組以向外擴充，如此可有兩種方式來建構主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="48796-143">You add another identical BizTalk computer to the group to scale-out, giving you two ways to factor the host instances.</span></span>  
  
 <span data-ttu-id="48796-144">此問題有兩個解決方案：</span><span class="sxs-lookup"><span data-stu-id="48796-144">Here are two solutions to this problem:</span></span>  
  
-   <span data-ttu-id="48796-145">**解決方案 1**： 的建構在此案例中的最簡單方式是複製主控件執行個體建構從第一部電腦至第二部電腦。</span><span class="sxs-lookup"><span data-stu-id="48796-145">**Solution 1**: The easiest way of factoring in this scenario is to clone the host instance factoring from first computer to second computer.</span></span> <span data-ttu-id="48796-146">這樣，就功能而言，第二台電腦就完全是第一台電腦的複本；也有接收和傳送主控件。</span><span class="sxs-lookup"><span data-stu-id="48796-146">So, the second computer is an exact copy of the first in term of functionality; it can also have both receive and send hosts.</span></span> <span data-ttu-id="48796-147">假設沒有其他瓶頸，CPU 資源加倍，您便得到兩倍的擴充。</span><span class="sxs-lookup"><span data-stu-id="48796-147">Assuming there is no other bottleneck, you may get a scaling factor of 2 as the CPU resources are doubled.</span></span>  
  
-   <span data-ttu-id="48796-148">**解決方案 2**： 建構主控件執行個體的另一個方式是將接收和傳送功能分置在不同的電腦。</span><span class="sxs-lookup"><span data-stu-id="48796-148">**Solution 2**: Another way to factor the host instances is to isolate the receive and send functions onto different computers.</span></span> <span data-ttu-id="48796-149">如此，一台 BizTalk Server 專用於接收，而另一台專用於傳送。</span><span class="sxs-lookup"><span data-stu-id="48796-149">So, one of the BizTalk servers is dedicated for receiving and other for sending.</span></span>  
  
 <span data-ttu-id="48796-150">**比較解決方案 1 與解決方案 2**</span><span class="sxs-lookup"><span data-stu-id="48796-150">**Comparing Solution 1 and Solution 2**</span></span>  
  
 <span data-ttu-id="48796-151">在解決方案 1 中，主控件執行個體的數目比 1 BTS 組態增加一倍。</span><span class="sxs-lookup"><span data-stu-id="48796-151">In solution 1, the number of host instances is doubled from 1 BTS configuration.</span></span> <span data-ttu-id="48796-152">這表示 SQL 伺服器上的鎖定爭用會增加。</span><span class="sxs-lookup"><span data-stu-id="48796-152">This means that lock contention on the SQL server will increase.</span></span> <span data-ttu-id="48796-153">鎖定爭用增加的量決定擴充比例。</span><span class="sxs-lookup"><span data-stu-id="48796-153">How much it increases in lock contention will determine the scaling factor.</span></span> <span data-ttu-id="48796-154">若鎖定爭用剛好在變成瓶頸的限制內，您會看到兩倍的擴充。</span><span class="sxs-lookup"><span data-stu-id="48796-154">If the lock contention is well within limits of becoming a bottleneck, you can see a scaling factor of 2.</span></span>  
  
 <span data-ttu-id="48796-155">解決方案 2 的優點是，您擁有只有兩個主控件執行個體，因此 SQL server 上的鎖定爭用應該小於比解決方案 1。</span><span class="sxs-lookup"><span data-stu-id="48796-155">The advantage of solution 2 is that you have only two host instances, so the lock contention on the SQL server should be less compared to solution 1.</span></span> <span data-ttu-id="48796-156">但是，擴充比例完全取決於接收的複雜性和傳送主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="48796-156">But, the scaling factor depends completely on the complexity of the receive and send host instances.</span></span> <span data-ttu-id="48796-157">考慮解決方案 2 的下列情況：</span><span class="sxs-lookup"><span data-stu-id="48796-157">Consider the following cases in solution 2:</span></span>  
  
 <span data-ttu-id="48796-158">假設接收和傳輸主控件執行個體使用同樣大量的 CPU，各使用一個 BizTalk Server 拓撲上 50% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="48796-158">Assume that both the receive and transmit host instances are equally intensive and they each use 50% of the CPU in the one BizTalk server topology.</span></span> <span data-ttu-id="48796-159">在兩個 BizTalk Server 拓撲中，您將傳輸主控件執行個體移動到不同電腦，現在接收和傳輸都得到雙倍的資源。</span><span class="sxs-lookup"><span data-stu-id="48796-159">In the two BizTalk server topology, you move the transmit host instance to different computer, and now both receive and transmit get double the resources.</span></span> <span data-ttu-id="48796-160">假設沒有其他瓶頸，這樣應該會提供兩倍的擴充。</span><span class="sxs-lookup"><span data-stu-id="48796-160">This should provide a scaling factor of 2, assuming that there is no other bottleneck.</span></span> <span data-ttu-id="48796-161">此實例比解決方案 1 為佳，因為只有兩個主控件執行個體，因此鎖定爭用較少。</span><span class="sxs-lookup"><span data-stu-id="48796-161">This case is better than Solution 1 because there are only two host instances and hence les lock contention.</span></span>  
  
 <span data-ttu-id="48796-162">假設傳輸耗費的資源比接收多，它使用一個 BizTalk Server 拓撲上 80% 的 CPU。</span><span class="sxs-lookup"><span data-stu-id="48796-162">Assume that transmit is way more intensive than receive, and uses 80% CPU resources in the one BizTalk server topology.</span></span> <span data-ttu-id="48796-163">將傳輸主控件執行個體移動到另一台機器，您只會多取得 20% 的 CPU 資源，因此最大擴充比例是 1.2。</span><span class="sxs-lookup"><span data-stu-id="48796-163">By moving the transmit host instance to another machine, you gain only 20% more CPU resources so the maximum scaling factor will be 1.2.</span></span> <span data-ttu-id="48796-164">此外，擁有接收主控件執行個體的電腦僅使用 20-30% CPU 資源，因此向外擴充的優點少很多。</span><span class="sxs-lookup"><span data-stu-id="48796-164">Moreover, the computer with the receive host instance will use only 20-30% CPU resources so the advantage of scaling-out is much less.</span></span>  
  
 <span data-ttu-id="48796-165">考慮下圖有四台 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="48796-165">Consider the following figure that has four BizTalk servers.</span></span> <span data-ttu-id="48796-166">每個電腦都有接收方與傳送方，就有四個屬於各種類型的主控件執行個體 (接收和傳輸)。</span><span class="sxs-lookup"><span data-stu-id="48796-166">Each computer is both receiver and sender, giving you a  total of four host instances of each type (receive and transmit).</span></span>  
  
 <span data-ttu-id="48796-167">![&#45; 建構主控件執行個體](../core/media/refactoringhostinstances.gif "RefactoringHostinstances")</span><span class="sxs-lookup"><span data-stu-id="48796-167">![Re&#45;factoring host instances](../core/media/refactoringhostinstances.gif "RefactoringHostinstances")</span></span>  
  
 <span data-ttu-id="48796-168">此拓撲或許不是最好的。</span><span class="sxs-lookup"><span data-stu-id="48796-168">This topology might not be the best possible one possible.</span></span> <span data-ttu-id="48796-169">您也應該測試其他建構排列，視實例的複雜性而定。</span><span class="sxs-lookup"><span data-stu-id="48796-169">You should also test other factoring permutations, depending on the complexity of scenario.</span></span> <span data-ttu-id="48796-170">例如：</span><span class="sxs-lookup"><span data-stu-id="48796-170">For example:</span></span>  
  
-   <span data-ttu-id="48796-171">兩台電腦專門用於接收、兩台用於傳輸。</span><span class="sxs-lookup"><span data-stu-id="48796-171">Dedicate two computers for receiving and  two for transmitting.</span></span> <span data-ttu-id="48796-172">這樣可在接收和傳送等量時，提供您最佳的可能擴充。</span><span class="sxs-lookup"><span data-stu-id="48796-172">This will give you the best possible scaling when both receive and send are equally intensive.</span></span>  
  
-   <span data-ttu-id="48796-173">若接收量較傳輸量大，三台電腦專門用於接收、一台用於傳輸。</span><span class="sxs-lookup"><span data-stu-id="48796-173">Dedicate three computersfor receiving and one for transmitting, if receiving is more intensive than transmit.</span></span>  
  
-   <span data-ttu-id="48796-174">若傳輸量較接收量大，三台電腦專門用於傳輸、一台用於接收。</span><span class="sxs-lookup"><span data-stu-id="48796-174">Dedicate one computer for receive and three for transmitting if transmitting is more intensive than receive.</span></span>  
  
 <span data-ttu-id="48796-175">在所有實例中，建議您將各個主控件的主控件執行個體數目減至最少，如此可減少 MessageBox 資料庫上的爭用，同時最充分的使用電腦資源。</span><span class="sxs-lookup"><span data-stu-id="48796-175">In all scenarios, it is recommended that you minimize the number of host instances of each host so that contention on the MessageBox database is reduced and at the same time use the computer resources are use to the fullest.</span></span> <span data-ttu-id="48796-176">最佳建構排列取決於實例的複雜性以及瓶頸的類型。</span><span class="sxs-lookup"><span data-stu-id="48796-176">The best factoring permutation depends on the complexity of scenario and type of bottleneck.</span></span> <span data-ttu-id="48796-177">在完成排列之前，請永遠要測試您的建構。</span><span class="sxs-lookup"><span data-stu-id="48796-177">Always test your factoring before you finalize a permutation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48796-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="48796-178">See Also</span></span>  
 <span data-ttu-id="48796-179">[向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="48796-179">[Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="48796-180">[向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="48796-180">[Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="48796-181">[向外擴充 SQL Server 層](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="48796-181">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="48796-182">[向外擴充接收主控件](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="48796-182">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="48796-183">[向外延展處理主控件](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="48796-183">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="48796-184">[向外延展傳送主控件](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="48796-184">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="48796-185">[使用 Windows 伺服器叢集以提供高可用性的 BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="48796-185">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="48796-186">[向外延展資料庫](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="48796-186">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="48796-187">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="48796-187">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)