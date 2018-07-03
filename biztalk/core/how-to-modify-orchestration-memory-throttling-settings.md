---
title: 如何修改協調流程記憶體節流設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostInstanceOrchestration
ms.assetid: f6953c68-7809-4518-87ec-e75c98884af3
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444f0a53827f99bda3eeb2389c555e614c44fe04
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022156"
---
# <a name="how-to-modify-orchestration-memory-throttling-settings"></a><span data-ttu-id="0d9f1-102">如何修改協調流程記憶體節流設定</span><span class="sxs-lookup"><span data-stu-id="0d9f1-102">How to Modify Orchestration Memory Throttling Settings</span></span>
<span data-ttu-id="0d9f1-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 主控件執行個體記憶體節流機制可持續監控節流狀況、計算節流狀況的嚴重性，然後根據計算的嚴重性逐步套用主控件執行個體記憶體節流。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-103">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host instance memory throttling mechanism continuously monitors for a throttling condition, calculates the severity of the throttling condition, and applies host instance memory throttling progressively depending on the calculated severity.</span></span> <span data-ttu-id="0d9f1-104">本主題提供使用 [設定儀表板] 修改這些設定的逐步程序。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-104">This topic provides the step-by-step procedure to modify these settings using the Settings Dashboard.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="0d9f1-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="0d9f1-105">Prerequisites</span></span>  
 <span data-ttu-id="0d9f1-106">若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-106">To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  

### <a name="to-modify-the-orchestration-memory-throttling-settings-of-a-host-instance"></a><span data-ttu-id="0d9f1-107">若要修改主控件執行個體的協調流程記憶體節流設定</span><span class="sxs-lookup"><span data-stu-id="0d9f1-107">To modify the orchestration memory throttling settings of a host instance</span></span>  

1. <span data-ttu-id="0d9f1-108">在  **BizTalk Server 管理主控台**，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-108">In the **BizTalk Server Administration Console**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Settings**.</span></span>  

2. <span data-ttu-id="0d9f1-109">在  **BizTalk 設定儀表板**對話方塊的 **主控件執行個體**頁面上，按一下**協調流程記憶體節流** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-109">In the **BizTalk Settings Dashboard** dialog box, on the **Host Instances** page, click the **Orchestration Memory Throttling** tab.</span></span>  

3. <span data-ttu-id="0d9f1-110">執行下列命令，，然後按一下**套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用所做的修改並結束 設定儀表板。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-110">Do the following, and then click **Apply** to apply the modifications and proceed to another tab. Or click **OK** to apply the modifications and exit the Settings Dashboard.</span></span>  


   |     <span data-ttu-id="0d9f1-111">使用</span><span class="sxs-lookup"><span data-stu-id="0d9f1-111">Use this</span></span>      |                                                                                <span data-ttu-id="0d9f1-112">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0d9f1-112">To do this</span></span>                                                                                | <span data-ttu-id="0d9f1-113">界限值</span><span class="sxs-lookup"><span data-stu-id="0d9f1-113">Boundary values</span></span> | <span data-ttu-id="0d9f1-114">預設值</span><span class="sxs-lookup"><span data-stu-id="0d9f1-114">Default value</span></span> |
   |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------|
   | <span data-ttu-id="0d9f1-115">**主控件執行個體**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-115">**Host Instance**</span></span> | <span data-ttu-id="0d9f1-116">從下拉式方塊選取 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段電腦上執行中的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-116">From the drop-down box, select the running instance of a host on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime machine.</span></span> |        -        |       -       |

    <span data-ttu-id="0d9f1-117">**實體**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-117">**Physical**</span></span>  

   |<span data-ttu-id="0d9f1-118">使用</span><span class="sxs-lookup"><span data-stu-id="0d9f1-118">Use this</span></span>|<span data-ttu-id="0d9f1-119">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0d9f1-119">To do this</span></span>|<span data-ttu-id="0d9f1-120">界限值</span><span class="sxs-lookup"><span data-stu-id="0d9f1-120">Boundary values</span></span>|<span data-ttu-id="0d9f1-121">預設值</span><span class="sxs-lookup"><span data-stu-id="0d9f1-121">Default value</span></span>|  
   |--------------|----------------|---------------------|-------------------|  
   |<span data-ttu-id="0d9f1-122">**最佳使用量**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-122">**Optimal usage**</span></span>|<span data-ttu-id="0d9f1-123">指定凍結節流生效時的實體記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-123">Specify the percentage of physical memory usage at which dehydration throttling comes into effect.</span></span> <span data-ttu-id="0d9f1-124">這是使用於主控件執行個體的實體記憶體最佳百分比。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-124">This is the optimum percentage of physical memory to use for the host instances.</span></span>|<span data-ttu-id="0d9f1-125">[0 – 100]</span><span class="sxs-lookup"><span data-stu-id="0d9f1-125">[0 – 100]</span></span>|<span data-ttu-id="0d9f1-126">70</span><span class="sxs-lookup"><span data-stu-id="0d9f1-126">70</span></span>|  
   |<span data-ttu-id="0d9f1-127">**最大用量**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-127">**Maximal usage**</span></span>|<span data-ttu-id="0d9f1-128">指定凍結節流達最大值時的實體記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-128">Specify the percentage of physical memory usage at which dehydration throttling is maximum.</span></span> <span data-ttu-id="0d9f1-129">這是使用於主控件執行個體的實體記憶體最大百分比。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-129">This is the maximum percentage of physical memory to use for the host instances.</span></span><br /><br /> <span data-ttu-id="0d9f1-130">最小值**最大用量**應該**最佳使用量**。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-130">The minimum value of **Maximal usage** should be **Optimal usage**.</span></span>|<span data-ttu-id="0d9f1-131">(最佳用量 – 100]</span><span class="sxs-lookup"><span data-stu-id="0d9f1-131">(Optimal usage – 100]</span></span><br /><br /> <span data-ttu-id="0d9f1-132">當兩者都是 0 或 100 時例外。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-132">Except when both are 0 or 100.</span></span>|<span data-ttu-id="0d9f1-133">85</span><span class="sxs-lookup"><span data-stu-id="0d9f1-133">85</span></span>|  

    <span data-ttu-id="0d9f1-134">**虛擬**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-134">**Virtual**</span></span>  

   |<span data-ttu-id="0d9f1-135">使用</span><span class="sxs-lookup"><span data-stu-id="0d9f1-135">Use this</span></span>|<span data-ttu-id="0d9f1-136">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="0d9f1-136">To do this</span></span>|<span data-ttu-id="0d9f1-137">界限值</span><span class="sxs-lookup"><span data-stu-id="0d9f1-137">Boundary values</span></span>|<span data-ttu-id="0d9f1-138">預設值</span><span class="sxs-lookup"><span data-stu-id="0d9f1-138">Default value</span></span>|  
   |--------------|----------------|---------------------|-------------------|  
   |<span data-ttu-id="0d9f1-139">**最佳使用量**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-139">**Optimal usage**</span></span>|<span data-ttu-id="0d9f1-140">指定凍結節流生效時的虛擬記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-140">Specify the percentage of virtual memory usage at which dehydration throttling comes into effect.</span></span><br /><br /> <span data-ttu-id="0d9f1-141">在此時**TestThreshold**具有值**MaxThreshold**和任何的記憶體使用量大於**OptimalUsage**會導致**TestThreshold**為小於**MaxThreshold**。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-141">At this point, **TestThreshold** has the value **MaxThreshold** and any memory usage greater than **OptimalUsage** causes **TestThreshold** to be less than **MaxThreshold**.</span></span>|<span data-ttu-id="0d9f1-142">[0 – 100]</span><span class="sxs-lookup"><span data-stu-id="0d9f1-142">[0 – 100]</span></span>|<span data-ttu-id="0d9f1-143">65</span><span class="sxs-lookup"><span data-stu-id="0d9f1-143">65</span></span>|  
   |<span data-ttu-id="0d9f1-144">**最大用量**</span><span class="sxs-lookup"><span data-stu-id="0d9f1-144">**Maximal usage**</span></span>|<span data-ttu-id="0d9f1-145">指定凍結節流達最大值時的虛擬記憶體用量百分比。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-145">Specify the percentage of virtual memory usage at which dehydration throttling is maximum.</span></span><br /><br /> <span data-ttu-id="0d9f1-146">在此時**TestThreshold**具有值**MinThreshold**和任何的記憶體使用量小於**MaximalUsage**會導致**TestThreshold**必須大於**MinThreshold**。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-146">At this point, **TestThreshold** has the value **MinThreshold** and any memory usage less than **MaximalUsage** causes **TestThreshold** to be greater than **MinThreshold**.</span></span>|<span data-ttu-id="0d9f1-147">(最佳用量 – 100]</span><span class="sxs-lookup"><span data-stu-id="0d9f1-147">(Optimal usage – 100]</span></span><br /><br /> <span data-ttu-id="0d9f1-148">當兩者都是 0 或 100 時例外。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-148">Except when both are 0 or 100.</span></span>|<span data-ttu-id="0d9f1-149">85</span><span class="sxs-lookup"><span data-stu-id="0d9f1-149">85</span></span>|  

   > [!NOTE]
   >  <span data-ttu-id="0d9f1-150">若要還原預設設定，請按一下**還原預設值**。</span><span class="sxs-lookup"><span data-stu-id="0d9f1-150">To restore the default settings, click **Restore Defaults**.</span></span>  

## <a name="see-also"></a><span data-ttu-id="0d9f1-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d9f1-151">See Also</span></span>  
 [<span data-ttu-id="0d9f1-152">如何修改主控件執行個體設定</span><span class="sxs-lookup"><span data-stu-id="0d9f1-152">How to Modify Host Instance Settings</span></span>](../core/how-to-modify-host-instance-settings.md)