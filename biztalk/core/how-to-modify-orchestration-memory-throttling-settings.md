---
title: "如何修改協調流程記憶體節流設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Bts10.settings.HostInstanceOrchestration
ms.assetid: f6953c68-7809-4518-87ec-e75c98884af3
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c48f1ec5e74ae577a7c1d130e22f3b4a1b53874c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-orchestration-memory-throttling-settings"></a><span data-ttu-id="3e0df-102">如何修改協調流程記憶體節流設定</span><span class="sxs-lookup"><span data-stu-id="3e0df-102">How to Modify Orchestration Memory Throttling Settings</span></span>
<span data-ttu-id="3e0df-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體記憶體節流機制可持續監控節流狀況、計算節流狀況的嚴重性，然後根據計算的嚴重性逐步套用主控件執行個體記憶體節流。</span><span class="sxs-lookup"><span data-stu-id="3e0df-103">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instance memory throttling mechanism continuously monitors for a throttling condition, calculates the severity of the throttling condition, and applies host instance memory throttling progressively depending on the calculated severity.</span></span> <span data-ttu-id="3e0df-104">本主題提供使用 [設定儀表板] 修改這些設定的逐步程序。</span><span class="sxs-lookup"><span data-stu-id="3e0df-104">This topic provides the step-by-step procedure to modify these settings using the Settings Dashboard.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3e0df-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="3e0df-105">Prerequisites</span></span>  
 <span data-ttu-id="3e0df-106">若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="3e0df-106">To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-modify-the-orchestration-memory-throttling-settings-of-a-host-instance"></a><span data-ttu-id="3e0df-107">若要修改主控件執行個體的協調流程記憶體節流設定</span><span class="sxs-lookup"><span data-stu-id="3e0df-107">To modify the orchestration memory throttling settings of a host instance</span></span>  
  
1.  <span data-ttu-id="3e0df-108">在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="3e0df-108">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
2.  <span data-ttu-id="3e0df-109">在**BizTalk 設定儀表板**對話方塊**主控件執行個體**頁面上，按一下**協調流程記憶體節流** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3e0df-109">In the **BizTalk Settings Dashboard** dialog box, on the **Host Instances** page, click the **Orchestration Memory Throttling** tab.</span></span>  
  
3.  <span data-ttu-id="3e0df-110">執行下列命令，，然後按一下**套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用變更並結束 設定儀表板。</span><span class="sxs-lookup"><span data-stu-id="3e0df-110">Do the following, and then click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.</span></span>  
  
    |<span data-ttu-id="3e0df-111">使用</span><span class="sxs-lookup"><span data-stu-id="3e0df-111">Use this</span></span>|<span data-ttu-id="3e0df-112">動作</span><span class="sxs-lookup"><span data-stu-id="3e0df-112">To do this</span></span>|<span data-ttu-id="3e0df-113">界限值</span><span class="sxs-lookup"><span data-stu-id="3e0df-113">Boundary values</span></span>|<span data-ttu-id="3e0df-114">預設值</span><span class="sxs-lookup"><span data-stu-id="3e0df-114">Default value</span></span>|  
    |--------------|----------------|---------------------|-------------------|  
    |<span data-ttu-id="3e0df-115">**主控件執行個體**</span><span class="sxs-lookup"><span data-stu-id="3e0df-115">**Host Instance**</span></span>|<span data-ttu-id="3e0df-116">從下拉式方塊選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦上執行中的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="3e0df-116">From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine.</span></span>|-|-|  
  
     <span data-ttu-id="3e0df-117">**實體**</span><span class="sxs-lookup"><span data-stu-id="3e0df-117">**Physical**</span></span>  
  
    |<span data-ttu-id="3e0df-118">使用</span><span class="sxs-lookup"><span data-stu-id="3e0df-118">Use this</span></span>|<span data-ttu-id="3e0df-119">動作</span><span class="sxs-lookup"><span data-stu-id="3e0df-119">To do this</span></span>|<span data-ttu-id="3e0df-120">界限值</span><span class="sxs-lookup"><span data-stu-id="3e0df-120">Boundary values</span></span>|<span data-ttu-id="3e0df-121">預設值</span><span class="sxs-lookup"><span data-stu-id="3e0df-121">Default value</span></span>|  
    |--------------|----------------|---------------------|-------------------|  
    |<span data-ttu-id="3e0df-122">**最佳用量**</span><span class="sxs-lookup"><span data-stu-id="3e0df-122">**Optimal usage**</span></span>|<span data-ttu-id="3e0df-123">指定凍結節流生效時的實體記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="3e0df-123">Specify the percentage of physical memory usage at which dehydration throttling comes into effect.</span></span> <span data-ttu-id="3e0df-124">這是使用於主控件執行個體的實體記憶體最佳百分比。</span><span class="sxs-lookup"><span data-stu-id="3e0df-124">This is the optimum percentage of physical memory to use for the host instances.</span></span>|<span data-ttu-id="3e0df-125">[0 – 100]</span><span class="sxs-lookup"><span data-stu-id="3e0df-125">[0 – 100]</span></span>|<span data-ttu-id="3e0df-126">70</span><span class="sxs-lookup"><span data-stu-id="3e0df-126">70</span></span>|  
    |<span data-ttu-id="3e0df-127">**最大用量**</span><span class="sxs-lookup"><span data-stu-id="3e0df-127">**Maximal usage**</span></span>|<span data-ttu-id="3e0df-128">指定凍結節流達最大值時的實體記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="3e0df-128">Specify the percentage of physical memory usage at which dehydration throttling is maximum.</span></span> <span data-ttu-id="3e0df-129">這是使用於主控件執行個體的實體記憶體最大百分比。</span><span class="sxs-lookup"><span data-stu-id="3e0df-129">This is the maximum percentage of physical memory to use for the host instances.</span></span><br /><br /> <span data-ttu-id="3e0df-130">最小值**最大用量**應該**最佳用量**。</span><span class="sxs-lookup"><span data-stu-id="3e0df-130">The minimum value of **Maximal usage** should be **Optimal usage**.</span></span>|<span data-ttu-id="3e0df-131">(最佳用量 – 100]</span><span class="sxs-lookup"><span data-stu-id="3e0df-131">(Optimal usage – 100]</span></span><br /><br /> <span data-ttu-id="3e0df-132">當兩者都是 0 或 100 時例外。</span><span class="sxs-lookup"><span data-stu-id="3e0df-132">Except when both are 0 or 100.</span></span>|<span data-ttu-id="3e0df-133">85</span><span class="sxs-lookup"><span data-stu-id="3e0df-133">85</span></span>|  
  
     <span data-ttu-id="3e0df-134">**虛擬**</span><span class="sxs-lookup"><span data-stu-id="3e0df-134">**Virtual**</span></span>  
  
    |<span data-ttu-id="3e0df-135">使用</span><span class="sxs-lookup"><span data-stu-id="3e0df-135">Use this</span></span>|<span data-ttu-id="3e0df-136">動作</span><span class="sxs-lookup"><span data-stu-id="3e0df-136">To do this</span></span>|<span data-ttu-id="3e0df-137">界限值</span><span class="sxs-lookup"><span data-stu-id="3e0df-137">Boundary values</span></span>|<span data-ttu-id="3e0df-138">預設值</span><span class="sxs-lookup"><span data-stu-id="3e0df-138">Default value</span></span>|  
    |--------------|----------------|---------------------|-------------------|  
    |<span data-ttu-id="3e0df-139">**最佳用量**</span><span class="sxs-lookup"><span data-stu-id="3e0df-139">**Optimal usage**</span></span>|<span data-ttu-id="3e0df-140">指定凍結節流生效時的虛擬記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="3e0df-140">Specify the percentage of virtual memory usage at which dehydration throttling comes into effect.</span></span><br /><br /> <span data-ttu-id="3e0df-141">此時， **TestThreshold**值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**導致**TestThreshold**是小於**MaxThreshold**。</span><span class="sxs-lookup"><span data-stu-id="3e0df-141">At this point, **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.</span></span>|<span data-ttu-id="3e0df-142">[0 – 100]</span><span class="sxs-lookup"><span data-stu-id="3e0df-142">[0 – 100]</span></span>|<span data-ttu-id="3e0df-143">65</span><span class="sxs-lookup"><span data-stu-id="3e0df-143">65</span></span>|  
    |<span data-ttu-id="3e0df-144">**最大用量**</span><span class="sxs-lookup"><span data-stu-id="3e0df-144">**Maximal usage**</span></span>|<span data-ttu-id="3e0df-145">指定凍結節流達最大值時的虛擬記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="3e0df-145">Specify the percentage of virtual memory usage at which dehydration throttling is maximum.</span></span><br /><br /> <span data-ttu-id="3e0df-146">此時， **TestThreshold**值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**導致**TestThreshold**必須大於**MinThreshold**。</span><span class="sxs-lookup"><span data-stu-id="3e0df-146">At this point, **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.</span></span>|<span data-ttu-id="3e0df-147">(最佳用量 – 100]</span><span class="sxs-lookup"><span data-stu-id="3e0df-147">(Optimal usage – 100]</span></span><br /><br /> <span data-ttu-id="3e0df-148">當兩者都是 0 或 100 時例外。</span><span class="sxs-lookup"><span data-stu-id="3e0df-148">Except when both are 0 or 100.</span></span>|<span data-ttu-id="3e0df-149">85</span><span class="sxs-lookup"><span data-stu-id="3e0df-149">85</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="3e0df-150">若要還原預設設定，請按一下**還原預設值**。</span><span class="sxs-lookup"><span data-stu-id="3e0df-150">To restore the default settings, click **Restore Defaults**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e0df-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e0df-151">See Also</span></span>  
 [<span data-ttu-id="3e0df-152">如何修改主控件執行個體設定</span><span class="sxs-lookup"><span data-stu-id="3e0df-152">How to Modify Host Instance Settings</span></span>](../core/how-to-modify-host-instance-settings.md)