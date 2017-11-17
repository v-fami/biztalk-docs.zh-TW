---
title: "GetActivityEvent |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6fe824c9-4cea-44da-b830-5520d67988e0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9fb039c0e9946091214a52fbb605753a212c233c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityevent"></a><span data-ttu-id="a162a-102">GetActivityEvent</span><span class="sxs-lookup"><span data-stu-id="a162a-102">GetActivityEvent</span></span>
<span data-ttu-id="a162a-103">將目前活動事件的名稱推至堆疊上。</span><span class="sxs-lookup"><span data-stu-id="a162a-103">Pushes the name of the current activity event onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a162a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a162a-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetActivityEvent"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a162a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a162a-105">Parameters</span></span>  
 <span data-ttu-id="a162a-106">無。</span><span class="sxs-lookup"><span data-stu-id="a162a-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="a162a-107">推入的值</span><span class="sxs-lookup"><span data-stu-id="a162a-107">Pushed Value</span></span>  
 <span data-ttu-id="a162a-108">包含目前活動事件的字串。</span><span class="sxs-lookup"><span data-stu-id="a162a-108">String containing the current activity event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a162a-109">備註</span><span class="sxs-lookup"><span data-stu-id="a162a-109">Remarks</span></span>  
 <span data-ttu-id="a162a-110">工作流程活動可能會在工作流程存留期間，經過好幾種狀態。</span><span class="sxs-lookup"><span data-stu-id="a162a-110">A workflow activity can pass through several states during the lifetime of the workflow.</span></span> <span data-ttu-id="a162a-111">Windows Workflow Foundation 的 BAM 攔截器支援 `System.Workflow.ComponentModel.ActivityExecutionStatus` 列舉所定義的大多數執行狀態值，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a162a-111">The Windows Workflow Foundation BAM interceptor supports most of the execution status values defined by the `System.Workflow.ComponentModel.ActivityExecutionStatus` enumeration, as shown in the following table.</span></span>  
  
|<span data-ttu-id="a162a-112">執行狀態</span><span class="sxs-lookup"><span data-stu-id="a162a-112">Execution status</span></span>|<span data-ttu-id="a162a-113">說明</span><span class="sxs-lookup"><span data-stu-id="a162a-113">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a162a-114">Canceling</span><span class="sxs-lookup"><span data-stu-id="a162a-114">Canceling</span></span>|<span data-ttu-id="a162a-115">代表活動正在取消的狀態中。</span><span class="sxs-lookup"><span data-stu-id="a162a-115">Represents the status when an activity is in the process of being canceled.</span></span>|  
|<span data-ttu-id="a162a-116">Closed</span><span class="sxs-lookup"><span data-stu-id="a162a-116">Closed</span></span>|<span data-ttu-id="a162a-117">代表活動已結束的狀態。</span><span class="sxs-lookup"><span data-stu-id="a162a-117">Represents the status when an activity is closed.</span></span>|  
|<span data-ttu-id="a162a-118">Compensating</span><span class="sxs-lookup"><span data-stu-id="a162a-118">Compensating</span></span>|<span data-ttu-id="a162a-119">代表活動正在補償的狀態中。</span><span class="sxs-lookup"><span data-stu-id="a162a-119">Represents the status when an activity is compensating.</span></span>|  
|<span data-ttu-id="a162a-120">Executing</span><span class="sxs-lookup"><span data-stu-id="a162a-120">Executing</span></span>|<span data-ttu-id="a162a-121">代表活動正在執行的狀態中。</span><span class="sxs-lookup"><span data-stu-id="a162a-121">Represents the status when an activity is executing.</span></span>|  
|<span data-ttu-id="a162a-122">Faulting</span><span class="sxs-lookup"><span data-stu-id="a162a-122">Faulting</span></span>|<span data-ttu-id="a162a-123">代表活動正在失敗的狀態中。</span><span class="sxs-lookup"><span data-stu-id="a162a-123">Represents the status when an activity is faulting.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="a162a-124">您不能在同一個 OnEvent 項目中同時使用 `GetActivityEvent` 和 `GetWorkflowEvent`。</span><span class="sxs-lookup"><span data-stu-id="a162a-124">You cannot use both `GetActivityEvent` and `GetWorkflowEvent` in the same OnEvent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a162a-125">範例</span><span class="sxs-lookup"><span data-stu-id="a162a-125">Example</span></span>  
 <span data-ttu-id="a162a-126">下列範例包含一個事件篩選條件運算式，這是設定來尋找 Closed 工作流程中的特定活動，即 FoodAndDringPolicy。</span><span class="sxs-lookup"><span data-stu-id="a162a-126">The following sample contains an event filter expression configured to find a specific activity—FoodAndDringPolicy—in a Closed workflow.</span></span> <span data-ttu-id="a162a-127">這是使用包括 `GetActivityEvent`、`GetActivityName` 和邏輯運算等運算組合所完成。</span><span class="sxs-lookup"><span data-stu-id="a162a-127">This is done by using a combination of operations including `GetActivityEvent`, `GetActivityName`, and logical operations.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="a162a-128">這種篩選模式常見於 Windows Workflow Foundation 攔截器組態檔。</span><span class="sxs-lookup"><span data-stu-id="a162a-128">This filter pattern is common with Windows Workflow Foundation interceptor configuration files.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a162a-129">引數不需要引號，除非您很明確地要比對包含引號的字串。</span><span class="sxs-lookup"><span data-stu-id="a162a-129">Arguments do not require quotation marks unless you are explicitly trying to match a string that contains quotation marks.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a162a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a162a-130">See Also</span></span>  
 [<span data-ttu-id="a162a-131">System.Workflow.ComponentModel.ActivityExecutionStatus 列舉</span><span class="sxs-lookup"><span data-stu-id="a162a-131">System.Workflow.ComponentModel.ActivityExecutionStatus enumeration</span></span>](http://go.microsoft.com/fwlink/?LinkId=119570)