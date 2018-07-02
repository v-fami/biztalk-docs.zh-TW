---
title: 向外擴充 SQL Server 層 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, MessageBox database
- scaling, scaling out
- SQL Server, scaling
- MessageBox database, scaling
- scaling, strategies
ms.assetid: d5b2ebba-401e-4fde-8818-407fa626043a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8d8059f405907690f210191d60fee60af69f019
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972519"
---
# <a name="scaling-out-the-sql-server-tier"></a><span data-ttu-id="07378-102">向外擴充 SQL Server 層</span><span class="sxs-lookup"><span data-stu-id="07378-102">Scaling Out the SQL Server Tier</span></span>
<span data-ttu-id="07378-103">針對每個 BizTalk 群組，加入一個主要 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="07378-103">For each BizTalk group, you add one Master MessageBox database.</span></span> <span data-ttu-id="07378-104">所有之後加入的 MessageBox 資料庫都稱為次要 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="07378-104">All the subsequent MessageBox databases that you add are called secondary MessageBoxes.</span></span> <span data-ttu-id="07378-105">主要 MessageBox 會處理所有的訂閱和訊息路由，</span><span class="sxs-lookup"><span data-stu-id="07378-105">The Master MessageBox handles all subscriptions and message routing.</span></span> <span data-ttu-id="07378-106">而且還可以發佈訊息。</span><span class="sxs-lookup"><span data-stu-id="07378-106">It can also publish messages.</span></span> <span data-ttu-id="07378-107">次要 MessageBox 資料庫只有在經過特別設定時，才會發佈訊息。</span><span class="sxs-lookup"><span data-stu-id="07378-107">Secondary MessageBox databases will only publish messages when specifically configured to do so.</span></span>  
  
## <a name="how-to-add-a-secondary-messagebox-database"></a><span data-ttu-id="07378-108">如何加入次要 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="07378-108">How to Add a Secondary MessageBox Database</span></span>  
 <span data-ttu-id="07378-109">有兩個方式可以加入次要 MessageBox 資料庫：</span><span class="sxs-lookup"><span data-stu-id="07378-109">There are two ways to add secondary MessageBox databases:</span></span>  
  
- <span data-ttu-id="07378-110">在相同的實體伺服器上加入次要 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="07378-110">Add the secondary MessageBox database on the same physical server.</span></span>  
  
   <span data-ttu-id="07378-111">若現有的 MessageBox 實體伺服器有足夠的 CPU 與 I/O 資源，但是因鎖定爭用而遇到瓶頸。</span><span class="sxs-lookup"><span data-stu-id="07378-111">Do this if the existing MessageBox physical server has enough CPU and I/O resources and is only bottlenecked by lock contention.</span></span> <span data-ttu-id="07378-112">請在個別的 IO 磁碟機上建立次要 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="07378-112">Create the secondary MessageBox database on separate IO drives.</span></span>  
  
   <span data-ttu-id="07378-113">優點：</span><span class="sxs-lookup"><span data-stu-id="07378-113">Advantages:</span></span>  
  
  -   <span data-ttu-id="07378-114">另一個 message-box 可以利用額外的 CPU 空間</span><span class="sxs-lookup"><span data-stu-id="07378-114">The extra CPU headroom can be utilized by another message-box</span></span>  
  
  -   <span data-ttu-id="07378-115">需要的 SQL Server 授權數目較少</span><span class="sxs-lookup"><span data-stu-id="07378-115">Fewer SQL server licenses are required</span></span>  
  
  -   <span data-ttu-id="07378-116">網路躍點已排除</span><span class="sxs-lookup"><span data-stu-id="07378-116">Network hop is eliminated</span></span>  
  
- <span data-ttu-id="07378-117">在不同的實體伺服器上加入次要 MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="07378-117">Add the secondary MessageBox database on a different physical server</span></span>  
  
   <span data-ttu-id="07378-118">在此情況下，使用具有自己 IO 的專用實體伺服器做為額外的 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="07378-118">In this case, use a dedicated physical server with its own IO as the extra MessageBox database.</span></span>  
  
  <span data-ttu-id="07378-119">下圖顯示一個實例，其中 SQL 層從 MessageBox 資料庫向外擴充為三個 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="07378-119">The following figure shows a scenario where SQL tier is scaled-out from one MessageBox database to three MessageBoxes databases.</span></span>  
  
  <span data-ttu-id="07378-120">![向外擴充 MSGBOX](../core/media/scaleoutmsgbox.gif "ScaleOutMSGBOX")</span><span class="sxs-lookup"><span data-stu-id="07378-120">![Scale out MSGBOX](../core/media/scaleoutmsgbox.gif "ScaleOutMSGBOX")</span></span>  
  
## <a name="when-to-scale-out-the-messagebox-database"></a><span data-ttu-id="07378-121">向外擴充 MessageBox 資料庫的時機</span><span class="sxs-lookup"><span data-stu-id="07378-121">When to Scale-out the MessageBox database</span></span>  
  
-   <span data-ttu-id="07378-122">MessageBox 資料庫變成瓶頸。</span><span class="sxs-lookup"><span data-stu-id="07378-122">The MessageBox database becomes the bottleneck.</span></span> <span data-ttu-id="07378-123">這些瓶頸可能是：</span><span class="sxs-lookup"><span data-stu-id="07378-123">Those bottlenecks can be:</span></span>  
  
    -   <span data-ttu-id="07378-124">**CPU**非常昂貴和複雜的協調流程的情況下，如果 MessageBox 資料庫會耗用大量的 CPU 資源。</span><span class="sxs-lookup"><span data-stu-id="07378-124">**CPU** In case of very expensive and complex orchestration scenarios, the MessageBox database consumes heavy CPU resources.</span></span> <span data-ttu-id="07378-125">加入另一個發佈的 MessageBox 資料庫應該可以協助提升輸送量。</span><span class="sxs-lookup"><span data-stu-id="07378-125">Adding another publishing the MessageBox database should help increase the throughput.</span></span>  
  
    -   <span data-ttu-id="07378-126">**鎖定爭用**具有多個主控件執行個體或協調流程的複雜案例通常會建立 MessageBox 資料庫上的鎖定爭用。</span><span class="sxs-lookup"><span data-stu-id="07378-126">**Lock Contention** Complex scenarios with multiple host instances or orchestrations tend to create lock contention on the MessageBox database.</span></span> <span data-ttu-id="07378-127">同樣的，加入另一個發佈的 MessageBox 資料庫應該可以協助提升輸送量。</span><span class="sxs-lookup"><span data-stu-id="07378-127">Again, adding another publishing MessageBox database should help increase the throughput.</span></span>  
  
-   <span data-ttu-id="07378-128">擴大資料庫不能處理瓶頸。</span><span class="sxs-lookup"><span data-stu-id="07378-128">Scaling up doesn’t address the bottleneck.</span></span> <span data-ttu-id="07378-129">例如，如果主要 MessageBox 資料庫受限於鎖定爭用，唯一的選擇就是向外擴充。</span><span class="sxs-lookup"><span data-stu-id="07378-129">For example, if the Master MessageBox database is lock contention bound, scaling-out is the only option.</span></span>  
  
-   <span data-ttu-id="07378-130">擴大資料庫的成本太高。</span><span class="sxs-lookup"><span data-stu-id="07378-130">Scaling-up is too expensive.</span></span> <span data-ttu-id="07378-131">例如，如果升級現有的四處理器伺服器到 8 方式伺服器成本高於新增另一個四程序，向外延展是更好的選項。</span><span class="sxs-lookup"><span data-stu-id="07378-131">For example, if upgrading the existing quad proc server to 8 way server is more expensive than adding another quad proc, scale-out is better option.</span></span>  
  
## <a name="when-you-cant-scale-out-the-sql-tier"></a><span data-ttu-id="07378-132">無法向外擴充 SQL 層時</span><span class="sxs-lookup"><span data-stu-id="07378-132">When You Can’t Scale-out the SQL Tier</span></span>  
 <span data-ttu-id="07378-133">理論上，只要主要 MessageBox 資料庫不是瓶頸，SQL 層應該可以無限擴充。</span><span class="sxs-lookup"><span data-stu-id="07378-133">In theory, the SQL tier should scale indefinitely as long as the Master MessageBox database is not the bottleneck.</span></span> <span data-ttu-id="07378-134">為了達成此目標，請考慮讓主要 MessageBox 資料庫變成非發佈資料庫，使它只能處理路由作業。</span><span class="sxs-lookup"><span data-stu-id="07378-134">To achieve this, consider making the Master MessageBox database a non-publishing database so it only does routing.</span></span> <span data-ttu-id="07378-135">但是，如果主要資料庫因為鎖定爭用而產生瓶頸，您就再也不能向外擴充 SQL 層。</span><span class="sxs-lookup"><span data-stu-id="07378-135">But, once the Master is bottlenecked by lock contention, you cannot scale out the SQL tier any more.</span></span>  
  
## <a name="scale-out-strategies-and-considerations"></a><span data-ttu-id="07378-136">向外擴充策略與考量</span><span class="sxs-lookup"><span data-stu-id="07378-136">Scale-out Strategies and Considerations</span></span>  
  
-   <span data-ttu-id="07378-137">先擴大主要 MessageBox 資料庫然後再向外擴充。</span><span class="sxs-lookup"><span data-stu-id="07378-137">First scale-up the Master MessageBox database and then scale out.</span></span>  
  
-   <span data-ttu-id="07378-138">相應放大 1 至 3 的 SQL MessageBox 資料庫，而不是 1 到 2。</span><span class="sxs-lookup"><span data-stu-id="07378-138">Scaling-out from 1 to 3 SQL MessageBox databases instead of 1 to 2.</span></span> <span data-ttu-id="07378-139">請考慮 1 如上圖所示的 SQL server 拓樸標題為"4 的 BizTalk Server，1 的 SQL Server 拓撲中，"，並假設 SQL server 是受 CPU 限制，也就是說，CPU 處理是瓶頸。</span><span class="sxs-lookup"><span data-stu-id="07378-139">Consider the 1 SQL server topology illustrated in the figure above titled "4 BizTalk Server, 1 SQL Server Topology," and assume that the SQL server is CPU bound, in other words, the CPU processing is a bottleneck.</span></span> <span data-ttu-id="07378-140">如果您只在這個拓樸中加入一個 MessageBox 資料庫，主要 Messagebox 仍然會受限於 CPU 處理能力，而且次要 MessageBox 資料庫的利用率也會偏低。</span><span class="sxs-lookup"><span data-stu-id="07378-140">If you add only one MessageBox database to this topology, the Master Messagebox will still be CPU bound and the secondary MessageBox database will be under-utilized.</span></span> <span data-ttu-id="07378-141">因此，縮放比例是幾近於 1。</span><span class="sxs-lookup"><span data-stu-id="07378-141">So, the scaling factor is almost 1.</span></span> <span data-ttu-id="07378-142">如果您停用主要 MessageBox 資料庫的發行，並設定專用主要 MessageBox 資料庫只是用來進行路由，次要 MessageBox 資料庫會處理發佈。</span><span class="sxs-lookup"><span data-stu-id="07378-142">If you disable publishing on the Master MessageBox database and dedicate the Master MessageBox database only to do routing, the secondary MessageBox database will do the publishing.</span></span> <span data-ttu-id="07378-143">不過由於次要 MessageBox 資料庫是唯一的發佈者，而且仍然會成為瓶頸，因此這種方法對於提高整體輸送量並無任何幫助。</span><span class="sxs-lookup"><span data-stu-id="07378-143">This will not help increase overall throughput though since the secondary MessageBox database is the only publisher and still becomes the bottleneck.</span></span> <span data-ttu-id="07378-144">因此，在這個案例中，建議的向外擴充方法為加入 2 個次要 MessageBox 資料庫，並停用主要 MessageBox 資料庫的發佈功能。</span><span class="sxs-lookup"><span data-stu-id="07378-144">So, adding 2 secondary MessageBox databases and disabling the publishing on the Master MessageBox database would be the recommended way to scale-out in this scenario.</span></span>  
  
-   <span data-ttu-id="07378-145">主要 MessageBox 資料庫最後都會變成瓶頸。</span><span class="sxs-lookup"><span data-stu-id="07378-145">The Master MessageBox database will eventually be the bottleneck.</span></span> <span data-ttu-id="07378-146">因此，裝載主要 MessageBox 資料庫的實體電腦應該具有較快的執行速度與較大的容量。</span><span class="sxs-lookup"><span data-stu-id="07378-146">So, the physical computer hosting the Master MessageBox database should be faster and bigger.</span></span>  
  
-   <span data-ttu-id="07378-147">為了讓透過網路傳送的資料量 (以及相關的 DTC 負擔) 降到最低，請考慮將多個 MessageBox 資料庫放在具有專用磁碟機的同一部實體電腦上。</span><span class="sxs-lookup"><span data-stu-id="07378-147">To minimize sending data over the network (and the associated DTC overhead), consider placing multiple MessageBox databases on the same physical computer with dedicated drives.</span></span> <span data-ttu-id="07378-148">同時，請確定儲存這些多個資料庫的電腦未遇到瓶頸，因為多個 MessageBox 資料庫會共用資源。</span><span class="sxs-lookup"><span data-stu-id="07378-148">At the same time, make sure that the computer holding these multiple databases is not bottlenecked as the resources are being shared by multiple MessageBox databases.</span></span>  
  
-   <span data-ttu-id="07378-149">所有的次要 MessageBox 資料庫都應該使用同等級的硬體，因為工作量會平均分配給這些 MessageBox 發佈資料庫。</span><span class="sxs-lookup"><span data-stu-id="07378-149">All secondary MessageBox databases should use comparable hardware because work is evenly distributed among the publishing MessageBox databases.</span></span>  
  
-   <span data-ttu-id="07378-150">只要主要 MessageBox 資料庫沒有產生瓶頸，您就可以向外擴充次要 MessageBox 資料庫，因此在執行次要 MessageBox 資料庫的電腦上，其 CPU 資源可以低於主要 MessageBox 資料庫伺服器的需求。</span><span class="sxs-lookup"><span data-stu-id="07378-150">Since you can scale out secondary MessageBox databases as long as the master MessageBox database is not bottlenecked, secondary MessageBox databases can run on computers with less CPU resources than is required by the master MessageBox database server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07378-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07378-151">See Also</span></span>  
 <span data-ttu-id="07378-152">[向外擴充 BizTalk Server 層](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="07378-152">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="07378-153">[向上擴充 BizTalk Server 層](../core/scaling-up-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="07378-153">[Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="07378-154">[向上擴充 SQL Server 層](../core/scaling-up-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="07378-154">[Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="07378-155">[相應放大的接收主控件](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="07378-155">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="07378-156">[相應放大處理主控件](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="07378-156">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="07378-157">[向外傳送主控件](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="07378-157">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="07378-158">[使用 Windows Server 叢集為 BizTalk Server Hosts2 提供高可用性](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="07378-158">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="07378-159">[相應放大的資料庫](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="07378-159">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="07378-160">叢集 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="07378-160">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)