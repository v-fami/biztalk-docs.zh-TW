---
title: GetWorkflowEvent |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2534e0b8-26df-4554-b0df-742014deb64d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8dc753bd45452af6ab586a11f216bc65f9539fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246606"
---
# <a name="getworkflowevent"></a><span data-ttu-id="a48ea-102">GetWorkflowEvent</span><span class="sxs-lookup"><span data-stu-id="a48ea-102">GetWorkflowEvent</span></span>
<span data-ttu-id="a48ea-103">將目前工作流程事件的名稱推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="a48ea-103">Pushes the name of the current workflow event onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48ea-104">語法</span><span class="sxs-lookup"><span data-stu-id="a48ea-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetWorkflowEvent" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a48ea-105">參數</span><span class="sxs-lookup"><span data-stu-id="a48ea-105">Parameters</span></span>  
 <span data-ttu-id="a48ea-106">無。</span><span class="sxs-lookup"><span data-stu-id="a48ea-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="a48ea-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="a48ea-107">Pushed Value</span></span>  
 <span data-ttu-id="a48ea-108">包含目前工作流程事件的字串。</span><span class="sxs-lookup"><span data-stu-id="a48ea-108">String containing the current workflow event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a48ea-109">備註</span><span class="sxs-lookup"><span data-stu-id="a48ea-109">Remarks</span></span>  
 <span data-ttu-id="a48ea-110">工作流程執行個體可能會在其執行過程期間，經過好幾種狀態。</span><span class="sxs-lookup"><span data-stu-id="a48ea-110">A workflow instance can pass through several states during the course of its execution.</span></span> <span data-ttu-id="a48ea-111">例如，工作流程執行個體可能呈現閒置或是擱置的狀態。</span><span class="sxs-lookup"><span data-stu-id="a48ea-111">For example, a workflow instance may become idle, or it may be suspended.</span></span> <span data-ttu-id="a48ea-112">每當工作流程執行個體變更狀態時，就會發出工作流程狀態事件給執行階段追蹤基礎結構。</span><span class="sxs-lookup"><span data-stu-id="a48ea-112">Every time the workflow instance changes state, it emits a workflow status event to the runtime tracking infrastructure.</span></span> <span data-ttu-id="a48ea-113">Windows Workflow Foundation 的 BAM 攔截器支援 `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent` 列舉所定義的大多數事件，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a48ea-113">The Windows Workflow Foundation BAM interceptor supports most of the events defined by the `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent` enumeration, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a48ea-114">活動事件</span><span class="sxs-lookup"><span data-stu-id="a48ea-114">Activity event</span></span>|<span data-ttu-id="a48ea-115">Description</span><span class="sxs-lookup"><span data-stu-id="a48ea-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a48ea-116">已變更</span><span class="sxs-lookup"><span data-stu-id="a48ea-116">Changed</span></span>|<span data-ttu-id="a48ea-117">工作流程執行個體上已發生工作流程變更。</span><span class="sxs-lookup"><span data-stu-id="a48ea-117">A workflow change has occurred on the workflow instance.</span></span>|  
|<span data-ttu-id="a48ea-118">已完成</span><span class="sxs-lookup"><span data-stu-id="a48ea-118">Completed</span></span>|<span data-ttu-id="a48ea-119">工作流程執行個體已完成。</span><span class="sxs-lookup"><span data-stu-id="a48ea-119">The workflow instance has completed.</span></span>|  
|<span data-ttu-id="a48ea-120">建立日期</span><span class="sxs-lookup"><span data-stu-id="a48ea-120">Created</span></span>|<span data-ttu-id="a48ea-121">工作流程執行個體已建立。</span><span class="sxs-lookup"><span data-stu-id="a48ea-121">The workflow instance has been created.</span></span>|  
|<span data-ttu-id="a48ea-122">Exception</span><span class="sxs-lookup"><span data-stu-id="a48ea-122">Exception</span></span>|<span data-ttu-id="a48ea-123">發生未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a48ea-123">An unhandled exception has occurred.</span></span>|  
|<span data-ttu-id="a48ea-124">Idle</span><span class="sxs-lookup"><span data-stu-id="a48ea-124">Idle</span></span>|<span data-ttu-id="a48ea-125">工作流程執行個體閒置中。</span><span class="sxs-lookup"><span data-stu-id="a48ea-125">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="a48ea-126">已載入</span><span class="sxs-lookup"><span data-stu-id="a48ea-126">Loaded</span></span>|<span data-ttu-id="a48ea-127">工作流程執行個體已載入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="a48ea-127">The workflow instance has been loaded into memory.</span></span>|  
|<span data-ttu-id="a48ea-128">已保存</span><span class="sxs-lookup"><span data-stu-id="a48ea-128">Persisted</span></span>|<span data-ttu-id="a48ea-129">工作流程執行個體已保存。</span><span class="sxs-lookup"><span data-stu-id="a48ea-129">The workflow instance has been persisted.</span></span>|  
|<span data-ttu-id="a48ea-130">繼續</span><span class="sxs-lookup"><span data-stu-id="a48ea-130">Resumed</span></span>|<span data-ttu-id="a48ea-131">先前擱置的工作流程執行個體已繼續執行。</span><span class="sxs-lookup"><span data-stu-id="a48ea-131">A previously suspended workflow instance has resumed running.</span></span>|  
|<span data-ttu-id="a48ea-132">Started</span><span class="sxs-lookup"><span data-stu-id="a48ea-132">Started</span></span>|<span data-ttu-id="a48ea-133">工作流程執行個體已啟動。</span><span class="sxs-lookup"><span data-stu-id="a48ea-133">The workflow instance has been started.</span></span>|  
|<span data-ttu-id="a48ea-134">已暫停</span><span class="sxs-lookup"><span data-stu-id="a48ea-134">Suspended</span></span>|<span data-ttu-id="a48ea-135">工作流程執行個體已擱置。</span><span class="sxs-lookup"><span data-stu-id="a48ea-135">The workflow instance has been suspended.</span></span>|  
|<span data-ttu-id="a48ea-136">已終止</span><span class="sxs-lookup"><span data-stu-id="a48ea-136">Terminated</span></span>|<span data-ttu-id="a48ea-137">工作流程執行個體已終止。</span><span class="sxs-lookup"><span data-stu-id="a48ea-137">The workflow instance has been terminated.</span></span>|  
|<span data-ttu-id="a48ea-138">已卸載</span><span class="sxs-lookup"><span data-stu-id="a48ea-138">Unloaded</span></span>|<span data-ttu-id="a48ea-139">工作流程執行個體已從記憶體中卸載。</span><span class="sxs-lookup"><span data-stu-id="a48ea-139">The workflow instance has been unloaded from memory.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a48ea-140">您不能在同一個 OnEvent 項目中同時使用 `GetWorkflowEvent` 和 `GetActivityEvent`。</span><span class="sxs-lookup"><span data-stu-id="a48ea-140">You cannot use both `GetWorkflowEvent` and `GetActivityEvent` in the same OnEvent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a48ea-141">範例</span><span class="sxs-lookup"><span data-stu-id="a48ea-141">Example</span></span>  
 <span data-ttu-id="a48ea-142">下列範例包含設定為找出特定活動的篩選條件 —"FoodAndDrinksPolicy"，工作流程中。</span><span class="sxs-lookup"><span data-stu-id="a48ea-142">The following sample contains a filter that is configured to find a specific activity—"FoodAndDrinksPolicy"—in a workflow.</span></span> <span data-ttu-id="a48ea-143">範例中的篩選條件是設定用來在結束的工作流程中尋找名為 "FoodAndDrinksPolicy" 的活動。</span><span class="sxs-lookup"><span data-stu-id="a48ea-143">In the sample, a filter is configured to find the activity named "FoodAndDrinksPolicy" in a closed workflow.</span></span> <span data-ttu-id="a48ea-144">這是藉由比較 `GetWorkflowEvent` 的傳回值和常數 "Created" 而達成的。</span><span class="sxs-lookup"><span data-stu-id="a48ea-144">This is done by comparing the value returned by `GetWorkflowEvent` to the constant "Created".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowEvent" />   
      <ic:Operation Name="Constant">  
        <ic:Argument>Created</ic:Argument>   
      </ic:Operation>  
    <ic:Operation Name="Equals" />   
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="a48ea-145">在追蹤工作流程的存留期間，以及偵測工作流程的例外狀況或其他問題時，這項作業就很有用。</span><span class="sxs-lookup"><span data-stu-id="a48ea-145">This operation is useful for tracking the lifetime of a workflow and for detecting exceptions or other problems with the workflow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48ea-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a48ea-146">See Also</span></span>  
 [<span data-ttu-id="a48ea-147">System.Workflow.Runtime.Tracking.TrackingWorkflowEvent 列舉</span><span class="sxs-lookup"><span data-stu-id="a48ea-147">System.Workflow.Runtime.Tracking.TrackingWorkflowEvent enumeration</span></span>](http://go.microsoft.com/fwlink/?LinkId=119568)