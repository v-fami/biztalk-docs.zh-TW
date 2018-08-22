---
title: 凍結預設屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68c59def-d73b-4880-9884-ccbe5d982f4b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 907bd9f9b47db10a199f5a93a828558dfb3ae210
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981959"
---
# <a name="dehydration-default-properties"></a><span data-ttu-id="b987c-102">凍結預設屬性</span><span class="sxs-lookup"><span data-stu-id="b987c-102">Dehydration Default Properties</span></span>
<span data-ttu-id="b987c-103">以下是凍結屬性名稱及其預設值。</span><span class="sxs-lookup"><span data-stu-id="b987c-103">Following are the names of the dehydration properties and their default values.</span></span> <span data-ttu-id="b987c-104">這些屬性可在 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 中設定，也可在 BTSNTSvc.exe.config 檔 (BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config) 中設定為 XML。</span><span class="sxs-lookup"><span data-stu-id="b987c-104">These properties are configurable in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or as XML in the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config).</span></span> <span data-ttu-id="b987c-105">BizTalk 組態檔中的值將先套用。</span><span class="sxs-lookup"><span data-stu-id="b987c-105">The values in the BizTalk configuration file are applied first.</span></span> <span data-ttu-id="b987c-106">然後 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 設定才會套用。</span><span class="sxs-lookup"><span data-stu-id="b987c-106">Then, the [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] settings are applied.</span></span> <span data-ttu-id="b987c-107">所有包含協調流程的主控件執行個體啟動時，將讀取凍結屬性。</span><span class="sxs-lookup"><span data-stu-id="b987c-107">The dehydration properties are read when all host instances containing an orchestration start.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b987c-108">[!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)]並未完全顯示所有的協調流程設定。</span><span class="sxs-lookup"><span data-stu-id="b987c-108">Not all orchestrations settings are exposed in [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)].</span></span> <span data-ttu-id="b987c-109">對於這些設定，將使用 BizTalk 組態檔 (BTSNTSvc.exe.config 或 BTSNTSvc64.exe.config)。</span><span class="sxs-lookup"><span data-stu-id="b987c-109">For these settings, the BizTalk configuration file (BTSNTSvc.exe.config or BTSNTSvc64.exe.config) is used.</span></span> <span data-ttu-id="b987c-110">使用 BizTalk 組態檔時，許多屬性並未列出。</span><span class="sxs-lookup"><span data-stu-id="b987c-110">When using the BizTalk configuration file, many properties are not listed.</span></span> <span data-ttu-id="b987c-111">即使組態檔未明確指定這些屬性及其預設值，仍將套用這些屬性及其預設值。</span><span class="sxs-lookup"><span data-stu-id="b987c-111">These properties and their default values are still applied, even if they are not explicitly specified in the configuration file.</span></span>  
  
 <span data-ttu-id="b987c-112">若要變更預設值，可以使用 [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] 或將預設值明確新增至 BizTalk 組態檔。</span><span class="sxs-lookup"><span data-stu-id="b987c-112">To change the default values, you can use [!INCLUDE[btsSettingsDashboard](../includes/btssettingsdashboard-md.md)] or explicitly add them to the BizTalk configuration file.</span></span> <span data-ttu-id="b987c-113">如需詳細資訊，請參閱 <<c0> [ 使用設定儀表板進行 BizTalk Server 效能調整](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md)並[BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)。</span><span class="sxs-lookup"><span data-stu-id="b987c-113">For more information, see [Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) and [BTSNTSvc.exe.config File](../core/btsntsvc-exe-config-file.md).</span></span>  
  
 <span data-ttu-id="b987c-114">**凍結**</span><span class="sxs-lookup"><span data-stu-id="b987c-114">**Dehydration**</span></span>  
  
- <span data-ttu-id="b987c-115">**MaxThreshold** = 1800年</span><span class="sxs-lookup"><span data-stu-id="b987c-115">**MaxThreshold** = 1800</span></span>  
  
- <span data-ttu-id="b987c-116">**MinThreshold** = 1</span><span class="sxs-lookup"><span data-stu-id="b987c-116">**MinThreshold** = 1</span></span>  
  
- <span data-ttu-id="b987c-117">**ConstantThreshold** =-1</span><span class="sxs-lookup"><span data-stu-id="b987c-117">**ConstantThreshold** = -1</span></span>  
  
  <span data-ttu-id="b987c-118">**VirtualMemoryThrottlingCriteria**</span><span class="sxs-lookup"><span data-stu-id="b987c-118">**VirtualMemoryThrottlingCriteria**</span></span>  
  
- <span data-ttu-id="b987c-119">**OptimalUsage** = 900</span><span class="sxs-lookup"><span data-stu-id="b987c-119">**OptimalUsage** = 900</span></span>  
  
- <span data-ttu-id="b987c-120">**MaximalUsage** = 1300年</span><span class="sxs-lookup"><span data-stu-id="b987c-120">**MaximalUsage** =  1300</span></span>  
  
- <span data-ttu-id="b987c-121">**IsActive** = true</span><span class="sxs-lookup"><span data-stu-id="b987c-121">**IsActive** = true</span></span>  
  
  <span data-ttu-id="b987c-122">**PrivateMemoryThrottlingCriteria**</span><span class="sxs-lookup"><span data-stu-id="b987c-122">**PrivateMemoryThrottlingCriteria**</span></span>  
  
- <span data-ttu-id="b987c-123">**OptimalUsage** = 50</span><span class="sxs-lookup"><span data-stu-id="b987c-123">**OptimalUsage** = 50</span></span>  
  
- <span data-ttu-id="b987c-124">**MaximalUsage** = 350</span><span class="sxs-lookup"><span data-stu-id="b987c-124">**MaximalUsage** =  350</span></span>  
  
- <span data-ttu-id="b987c-125">**IsActive** = true</span><span class="sxs-lookup"><span data-stu-id="b987c-125">**IsActive** = true</span></span>  
  
  <span data-ttu-id="b987c-126">**PhysicalMemoryThrottlingCriteria**</span><span class="sxs-lookup"><span data-stu-id="b987c-126">**PhysicalMemoryThrottlingCriteria**</span></span>  
  
- <span data-ttu-id="b987c-127">**OptimalUsage** = 90</span><span class="sxs-lookup"><span data-stu-id="b987c-127">**OptimalUsage** = 90</span></span>  
  
- <span data-ttu-id="b987c-128">**MaximalUsage**類別 = 95</span><span class="sxs-lookup"><span data-stu-id="b987c-128">**MaximalUsage** =  95</span></span>  
  
- <span data-ttu-id="b987c-129">**IsActive** = false</span><span class="sxs-lookup"><span data-stu-id="b987c-129">**IsActive** = false</span></span>  
  
  <span data-ttu-id="b987c-130">下文將詳細地描述每一個屬性。</span><span class="sxs-lookup"><span data-stu-id="b987c-130">Each of these properties is described in detail next.</span></span>  
  
## <a name="dehydration"></a><span data-ttu-id="b987c-131">Dehydration</span><span class="sxs-lookup"><span data-stu-id="b987c-131">Dehydration</span></span>  
 <span data-ttu-id="b987c-132">**MaxThreshold**並**MinThreshold**是右上角，而範圍中，秒數的協調流程可能會封鎖在訂用帳戶 （也就，封鎖接收、 偵聽或延遲） 被凍結之前的時間。</span><span class="sxs-lookup"><span data-stu-id="b987c-132">**MaxThreshold** and **MinThreshold** are the upper and lower bounds, in seconds, of the time that an orchestration can be blocked at a subscription (that is, blocked by a receive, listen, or delay) before being dehydrated.</span></span> <span data-ttu-id="b987c-133">也會有值，計算在執行階段，稱為**TestThreshold**，且其值，以秒為單位測量之間**MinThreshold**並**MaxThreshold**。</span><span class="sxs-lookup"><span data-stu-id="b987c-133">There will also be a value calculated at run-time, called **TestThreshold**, and its value, measured in seconds, is between **MinThreshold** and **MaxThreshold**.</span></span>  
  
 <span data-ttu-id="b987c-134">如果您的設定值，預設值為-1 以外**ConstantThreshold**，則將不會有執行階段值**TestThreshold**。</span><span class="sxs-lookup"><span data-stu-id="b987c-134">If you set a value besides the default of -1 for **ConstantThreshold**, there will not be a run-time value **TestThreshold**.</span></span> <span data-ttu-id="b987c-135">當協調流程會封鎖在訂用帳戶，並多久該協調流程的所有執行個體已被封鎖在該訂用帳戶的歷程記錄的值大於**TestThreshold**，然後將協調流程凍結。</span><span class="sxs-lookup"><span data-stu-id="b987c-135">When an orchestration is blocked at a subscription, and the history of how long all instances of that orchestration have been blocked at that subscription is greater than the value of **TestThreshold**, then the orchestration will dehydrate.</span></span> <span data-ttu-id="b987c-136">否則，如果記錄是小於**TestThreshold**就不會凍結協調流程的值。</span><span class="sxs-lookup"><span data-stu-id="b987c-136">Otherwise, if the history is less than **TestThreshold** value the orchestration will not dehydrate.</span></span> <span data-ttu-id="b987c-137">此外，即使歷程記錄指出凍結不會進行，如果目前的封鎖時間達到 2<em>\**TestThreshold</em>*，則會發生凍結。</span><span class="sxs-lookup"><span data-stu-id="b987c-137">Also, even if the history indicates that dehydration will not take place, if the current blocking time reaches 2<em>\**TestThreshold</em>*, then the dehydration will take place.</span></span> <span data-ttu-id="b987c-138">歷程記錄是根據最後 10 次等候時間的平均 (以秒為單位)，或記錄中許多等候時間 (不到 10 次的等候時間) 的平均而定義。</span><span class="sxs-lookup"><span data-stu-id="b987c-138">The history is defined by the average of the last 10 waiting times in seconds, or the average of however many waiting times there are in the history if the waiting times are less than 10.</span></span>  
  
 <span data-ttu-id="b987c-139">當 windows 7 **TestThreshold**傾向**MinThreshold**隨著記憶體使用量增加，它會呼叫 「 記憶體基礎的凍結節流 」。</span><span class="sxs-lookup"><span data-stu-id="b987c-139">When the value of **TestThreshold** tends toward **MinThreshold** as memory usage increases, it is called "memory based dehydration throttling."</span></span> <span data-ttu-id="b987c-140">以記憶體為基礎的凍結節流允許啟動更多協調流程執行個體，因為當其中任何執行個體受阻並等待工作 (也就是說，等待訊息或延遲) 時，它們會遭凍結並從記憶體中移除。</span><span class="sxs-lookup"><span data-stu-id="b987c-140">Memory-based dehydration throttling allows more orchestration instances to be live because when any of them are blocked waiting for work (that is, waiting for a message or a delay), they can be dehydrated and taken out of memory.</span></span> <span data-ttu-id="b987c-141">**TestThreshold**是單純遞減的函式的記憶體使用量是記憶體使用量成反比。</span><span class="sxs-lookup"><span data-stu-id="b987c-141">**TestThreshold** is a monotonically decreasing function of memory usage, it is inversely proportional to memory usage.</span></span>  
  
 <span data-ttu-id="b987c-142">以下是個別 Dehydration 屬性的說明：</span><span class="sxs-lookup"><span data-stu-id="b987c-142">Following are descriptions of the individual Dehydration properties:</span></span>  
  
-   <span data-ttu-id="b987c-143">**MaxThreshold**： 上限，以秒為單位的時間，協調流程可能會封鎖在被凍結之前的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b987c-143">**MaxThreshold**: the upper bounds, in seconds, of the time that an orchestration can be blocked at a subscription before being dehydrated.</span></span>  
  
-   <span data-ttu-id="b987c-144">**MinThreshold**： 下限，以秒為單位的時間，協調流程可能會封鎖在被凍結之前的訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="b987c-144">**MinThreshold**: the lower bounds, in seconds, of the time that an orchestration can be blocked at a subscription before being dehydrated.</span></span>  
  
-   <span data-ttu-id="b987c-145">**ConstantThreshold**： 通常指定的最小和最大值之間波動的動態臨界值。</span><span class="sxs-lookup"><span data-stu-id="b987c-145">**ConstantThreshold**: the dynamic threshold, which usually fluctuates between the minimum and maximum values specified.</span></span> <span data-ttu-id="b987c-146">不過，您可以設定這個屬性，將閾值固定。</span><span class="sxs-lookup"><span data-stu-id="b987c-146">However, you can make the threshold a fixed value by setting this property.</span></span> <span data-ttu-id="b987c-147">值 -1 會告知引擎不要使用常數閾值。</span><span class="sxs-lookup"><span data-stu-id="b987c-147">A value of -1 tells the engine not to use a constant threshold.</span></span> <span data-ttu-id="b987c-148">請勿將這個屬性設為 -1 以外的值，因為這會停用以凍結為基礎的節流。</span><span class="sxs-lookup"><span data-stu-id="b987c-148">Don't set this property to a value other than -1 because it will disable dehydration based throttling.</span></span>  
  
## <a name="virtualmemorythrottlingcriteria"></a><span data-ttu-id="b987c-149">VirtualMemoryThrottlingCriteria</span><span class="sxs-lookup"><span data-stu-id="b987c-149">VirtualMemoryThrottlingCriteria</span></span>  
 <span data-ttu-id="b987c-150">目前在 32 位元電腦上，由於 Unmanaged 堆積分割，虛擬記憶體可能成為瓶頸，所以您也應該依據這項資源進行節流。</span><span class="sxs-lookup"><span data-stu-id="b987c-150">Currently, virtual memory can become a bottleneck on 32-bit machines due to unmanaged heap fragmentation, so you should throttle by this resource as well.</span></span> <span data-ttu-id="b987c-151">如果已設定 /3GB，或在 64 位元平台上執行主控件，您應該重新設定這個屬性。</span><span class="sxs-lookup"><span data-stu-id="b987c-151">You should re-configure if /3GB is set or if the hosts are running on a 64-bit platform.</span></span> <span data-ttu-id="b987c-152">最佳和最大使用量都是以 MB 為單位。</span><span class="sxs-lookup"><span data-stu-id="b987c-152">Optimal and maximal usages are in MB.</span></span>  
  
 <span data-ttu-id="b987c-153">以下是個別 VirtualMemoryThrottlingCriteria 屬性的說明：</span><span class="sxs-lookup"><span data-stu-id="b987c-153">Following are descriptions of the individual VirtualMemoryThrottlingCriteria properties:</span></span>  
  
-   <span data-ttu-id="b987c-154">**OptimalUsage**： 的凍結節流開始生效的虛擬記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="b987c-154">**OptimalUsage**: The amount of virtual memory usage at which dehydration throttling begins to take effect.</span></span> <span data-ttu-id="b987c-155">在此時**TestThreshold**具有值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**會導致**TestThreshold**為小於**MaxThreshold**。</span><span class="sxs-lookup"><span data-stu-id="b987c-155">At this point, **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.</span></span>  
  
-   <span data-ttu-id="b987c-156">**MaximalUsage**： 的凍結節流時最多的虛擬記憶體使用量。</span><span class="sxs-lookup"><span data-stu-id="b987c-156">**MaximalUsage**: The amount of virtual memory usage at which dehydration throttling is at a maximum.</span></span> <span data-ttu-id="b987c-157">在此時**TestThreshold**具有值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**會導致**TestThreshold**必須大於**MinThreshold**。</span><span class="sxs-lookup"><span data-stu-id="b987c-157">At this point, **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.</span></span>  
  
-   <span data-ttu-id="b987c-158">**IsActive**： 布林值，指出虛擬記憶體節流是否為作用。</span><span class="sxs-lookup"><span data-stu-id="b987c-158">**IsActive**: A boolean value indicating if virtual memory throttling is active.</span></span>  
  
## <a name="privatememorythrottlingcriteria"></a><span data-ttu-id="b987c-159">PrivateMemoryThrottlingCriteria</span><span class="sxs-lookup"><span data-stu-id="b987c-159">PrivateMemoryThrottlingCriteria</span></span>  
 <span data-ttu-id="b987c-160">這個屬性是節流的實用準則，但根據電腦是否正在執行其他 Windows 服務，適用值會不同。</span><span class="sxs-lookup"><span data-stu-id="b987c-160">This property is a useful criterion for throttling, but appropriate values depend on whether the computer is running other windows services.</span></span> <span data-ttu-id="b987c-161">如果電腦有許多記憶體，而且不與其他 Windows 服務共用，您就可以大幅增加這些值。</span><span class="sxs-lookup"><span data-stu-id="b987c-161">If the computer has a lot of memory and is not being shared with other windows services, then you can increase these values significantly.</span></span>  
  
 <span data-ttu-id="b987c-162">以下是個別 PrivateMemoryThrottlingCriteria 屬性的說明：</span><span class="sxs-lookup"><span data-stu-id="b987c-162">Following are descriptions of the individual PrivateMemoryThrottlingCriteria properties:</span></span>  
  
-   <span data-ttu-id="b987c-163">**OptimalUsage**： 的私用記憶體使用量，以 mb 為單位，凍結節流開始生效。</span><span class="sxs-lookup"><span data-stu-id="b987c-163">**OptimalUsage**: the amount of private memory usage, in MB, at which dehydration throttling begins to take effect.</span></span> <span data-ttu-id="b987c-164">此時**TestThreshold**具有值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**造成**TestThreshold**為小於**MaxThreshold**。</span><span class="sxs-lookup"><span data-stu-id="b987c-164">At this point **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.</span></span>  
  
-   <span data-ttu-id="b987c-165">**MaximalUsage**： 的私用記憶體使用量，以 mb 為單位，凍結節流是最大值。</span><span class="sxs-lookup"><span data-stu-id="b987c-165">**MaximalUsage**: the amount of private memory usage, in MB, at which dehydration throttling is at a maximum.</span></span> <span data-ttu-id="b987c-166">此時**TestThreshold**具有值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**造成**TestThreshold**必須大於**MinThreshold**。</span><span class="sxs-lookup"><span data-stu-id="b987c-166">At this point **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.</span></span>  
  
-   <span data-ttu-id="b987c-167">**IsActive**： 布林值，指出私用記憶體節流是否為作用。</span><span class="sxs-lookup"><span data-stu-id="b987c-167">**IsActive**: a boolean value indicating if private memory throttling is active.</span></span>  
  
## <a name="physicalmemorythrottlingcriteria"></a><span data-ttu-id="b987c-168">PhysicalMemoryThrottlingCriteria</span><span class="sxs-lookup"><span data-stu-id="b987c-168">PhysicalMemoryThrottlingCriteria</span></span>  
 <span data-ttu-id="b987c-169">除此之外，也有實體記憶體節流，其數字是以使用的記憶體百分比為單位，而不以 MB 為單位。</span><span class="sxs-lookup"><span data-stu-id="b987c-169">There is also a physical memory throttling where numbers are measured in percentage of memory used rather than MB.</span></span> <span data-ttu-id="b987c-170">預設不會啟用這個屬性，但在必要時您可以啟用它。</span><span class="sxs-lookup"><span data-stu-id="b987c-170">This property is disabled by default, but you can enable if needed.</span></span>  
  
 <span data-ttu-id="b987c-171">以下是個別 PhysicalMemoryThrottlingCriteria 屬性的說明：</span><span class="sxs-lookup"><span data-stu-id="b987c-171">Following are descriptions of the individual PhysicalMemoryThrottlingCriteria properties:</span></span>  
  
-   <span data-ttu-id="b987c-172">**OptimalUsage**： 使用於主控件執行個體的實體記憶體最佳百分比。</span><span class="sxs-lookup"><span data-stu-id="b987c-172">**OptimalUsage**: the optimum percentage of physical memory to use for the host instances.</span></span>  
  
-   <span data-ttu-id="b987c-173">**MaximalUsage**： 使用於主控件執行個體的實體記憶體的最大百分比。</span><span class="sxs-lookup"><span data-stu-id="b987c-173">**MaximalUsage**: the maximum percentage of physical memory to use for the host instances.</span></span>  
  
-   <span data-ttu-id="b987c-174">**IsActive**： 布林值，指出實體記憶體節流是否為作用。</span><span class="sxs-lookup"><span data-stu-id="b987c-174">**IsActive**: boolean value indicating if physical memory throttling is active.</span></span>  
  
## <a name="dehydration-properties-behavior"></a><span data-ttu-id="b987c-175">凍結屬性行為</span><span class="sxs-lookup"><span data-stu-id="b987c-175">Dehydration Properties Behavior</span></span>  
 <span data-ttu-id="b987c-176">BizTalk Server 會使用這些凍結屬性，決定何時凍結和解除凍結協調流程。</span><span class="sxs-lookup"><span data-stu-id="b987c-176">BizTalk Server uses these dehydration properties to decide when to dehydrate and rehydrate orchestrations.</span></span> <span data-ttu-id="b987c-177">在正常負載下，預設的凍結值就足夠，但在負載過重時，若要變更效能特性，您應該自行微調。</span><span class="sxs-lookup"><span data-stu-id="b987c-177">Under normal load, the default dehydration values are sufficient, but if you are running under heavy load and want to change performance characteristics, you should do the tuning yourself.</span></span>  
  
 <span data-ttu-id="b987c-178">BizTalk Server 的凍結行為主要取決於可用和使用中的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="b987c-178">The dehydration behavior of BizTalk Server depends entirely on how much memory is available and how much memory is being used.</span></span> <span data-ttu-id="b987c-179">根據不同的記憶體數量，以及 32 位元和 64 位元主控件之間的記憶體使用差異，凍結行為會不同。</span><span class="sxs-lookup"><span data-stu-id="b987c-179">The dehydration behavior is different with different amounts of memory and differences in memory use between 32-bit and 64-bit hosts.</span></span>  
  
 <span data-ttu-id="b987c-180">凍結屬性會區分協調流程主控件的「私用位元組」和「虛擬位元組」：</span><span class="sxs-lookup"><span data-stu-id="b987c-180">The dehydration properties distinguish between Private Bytes and Virtual Bytes for the orchestration host:</span></span>  
  
-   <span data-ttu-id="b987c-181">**虛擬位元組**。</span><span class="sxs-lookup"><span data-stu-id="b987c-181">**Virtual Bytes**.</span></span> <span data-ttu-id="b987c-182">這是其中將填入目前的大小，以位元組為單位的處理序正在使用的虛擬位址空間。</span><span class="sxs-lookup"><span data-stu-id="b987c-182">This is thecurrent size, in bytes, of the virtual address space the process is using.</span></span> <span data-ttu-id="b987c-183">虛擬位址空間的使用不一定表示磁碟或主記憶體頁面的對應使用。</span><span class="sxs-lookup"><span data-stu-id="b987c-183">Use of virtual address space does not necessarily imply corresponding use of either disk or main memory pages.</span></span> <span data-ttu-id="b987c-184">虛擬空間是有限的，而且程序可以限制其載入程式庫的能力。</span><span class="sxs-lookup"><span data-stu-id="b987c-184">Virtual space is finite, and the process can limit its ability to load libraries.</span></span>  
  
-   <span data-ttu-id="b987c-185">**私用位元組**。</span><span class="sxs-lookup"><span data-stu-id="b987c-185">**Private Bytes**.</span></span> <span data-ttu-id="b987c-186">這是目前配置給程序、不能與其他程序共用的記憶體大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="b987c-186">This is the current size, in bytes, of memory that this process has allocated that cannot be shared with other processes.</span></span>