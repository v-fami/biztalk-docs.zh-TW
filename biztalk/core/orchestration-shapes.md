---
title: 協調流程圖形 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer]
- Loop shape [Orchestration Designer]
- Throw Exception shape [Orchestration Designer]
- Expression shape [Orchestration Designer]
- Decide shape [Orchestration Designer]
- Receive shape [Orchestration Designer]
- Compensate shape [Orchestration Designer]
- orchestrations, shapes
- Suspend shape [Orchestration Designer]
- Send shape [Orchestration Designer]
- Group shape [Orchestration Designer]
- Listen shape [Orchestration Designer]
- shapes, about shapes
- Construct Message shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer]
- Call Rules shape [Orchestration Designer]
- Start Orchestration shape [Orchestration Designer]
- Transform shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Role Link shape [Orchestration Designer]
- Call Orchestration shape [Orchestration Designer]
- Port shape [Orchestration Designer]
- shapes
- Scope shape [Orchestration Designer]
- Terminate shape [Orchestration Designer]
- Orchestration Designer, shapes
- Insufficient Configuration Smart Tag [Orchestration Designer]
ms.assetid: a1d03baa-a267-499d-94fc-700b3e959458
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 181656208b757c595feb9d19ee786fe91f1b78f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264294"
---
# <a name="orchestration-shapes"></a><span data-ttu-id="b5b3a-102">協調流程圖形</span><span class="sxs-lookup"><span data-stu-id="b5b3a-102">Orchestration Shapes</span></span>
<span data-ttu-id="b5b3a-103">協調流程設計師是用來建立協調流程的視覺化工具，</span><span class="sxs-lookup"><span data-stu-id="b5b3a-103">Orchestration Designer is a visual tool for creating orchestrations.</span></span> <span data-ttu-id="b5b3a-104">它提供了幾個圖形，讓您以基礎動作的視覺化表示方式將這些圖形放在設計介面上，這些圖形也可讓您有效率地設計及實作協調流程。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-104">It provides several shapes that you can place on the design surface as visual representations of underlying actions, and they can help you to efficiently design and implement an orchestration.</span></span>  
  
 <span data-ttu-id="b5b3a-105">**組態不完整的動作**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-105">**Insufficient Configuration Action**</span></span>  
  
 ![](../core/media/ebiz-orch-insufficconfig.gif "ebiz_orch_insufficconfig")  
  
> [!NOTE]
>  <span data-ttu-id="b5b3a-106">當協調流程設計師偵測到關聯的圖形未完整設定時，會顯示協調流程設計師中不足，無法設定動作。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-106">The Insufficient Configuration Action is displayed in the Orchestration designer when the Orchestration Designer detects that the associated shape is not completely configured.</span></span> <span data-ttu-id="b5b3a-107">如果協調流程中的圖形未完整設定，則關聯的協調流程將不會編譯。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-107">If a shape in an Orchestration is not completely configured then the associated Orchestration will not compile.</span></span>  
  
 <span data-ttu-id="b5b3a-108">下表列出可用的圖形，連同每一個圖形功能的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-108">The following table lists the available shapes, along with a brief description of the function of each shape.</span></span>  
  
|<span data-ttu-id="b5b3a-109">形狀圖</span><span class="sxs-lookup"><span data-stu-id="b5b3a-109">Shape</span></span>|<span data-ttu-id="b5b3a-110">圖形名稱</span><span class="sxs-lookup"><span data-stu-id="b5b3a-110">Shape Name</span></span>|<span data-ttu-id="b5b3a-111">目的</span><span class="sxs-lookup"><span data-stu-id="b5b3a-111">Purpose</span></span>|  
|-----------|----------------|-------------|  
|![](../core/media/ebiz-orch-callorchestrat.gif "ebiz_orch_callorchestrat")|<span data-ttu-id="b5b3a-112">**呼叫協調流程**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-112">**Call Orchestration**</span></span>|<span data-ttu-id="b5b3a-113">可讓您的協調流程同步呼叫另一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-113">Enables your orchestration to call another orchestration synchronously.</span></span>|  
|![](../core/media/ebiz-orch-call-rules.gif "ebiz_orch_call_rules")|<span data-ttu-id="b5b3a-114">**呼叫規則**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-114">**Call Rules**</span></span>|<span data-ttu-id="b5b3a-115">可讓您設定要在協調流程中執行的商務規則原則。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-115">Enables you to configure a Business Rules policy to be executed in your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-compensate.gif "ebiz_orch_compensate")|<span data-ttu-id="b5b3a-116">**補償**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-116">**Compensate**</span></span>|<span data-ttu-id="b5b3a-117">可讓您呼叫程式碼，使其在發生錯誤時復原或補償已經由協調流程執行的作業。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-117">Enables you to call code to undo or compensate for operations already performed by the orchestration when an error occurs.</span></span>|  
|![](../core/media/ebiz-orch-constructmsg.gif "ebiz_orch_constructmsg")|<span data-ttu-id="b5b3a-118">**建構訊息**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-118">**Construct Message**</span></span>|<span data-ttu-id="b5b3a-119">可讓您建構訊息。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-119">Enables you to construct a message.</span></span>|  
|![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")|<span data-ttu-id="b5b3a-120">**決定**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-120">**Decide**</span></span>|<span data-ttu-id="b5b3a-121">可讓您在協調流程中進行條件式分支。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-121">Enables you to conditionally branch in your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")|<span data-ttu-id="b5b3a-122">**延遲**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-122">**Delay**</span></span>|<span data-ttu-id="b5b3a-123">可讓您根據逾時間隔在協調流程中建置延遲。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-123">Enables you to build delays in your orchestration based on a time-out interval.</span></span>|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|<span data-ttu-id="b5b3a-124">**運算式**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-124">**Expression**</span></span>|<span data-ttu-id="b5b3a-125">可讓您為變數指派值或發出 .NET 呼叫。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-125">Enables you to assign values to variables or make .NET calls.</span></span>|  
|![](../core/media/ebiz-orch-group.gif "ebiz_orch_group")|<span data-ttu-id="b5b3a-126">**群組**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-126">**Group**</span></span>|<span data-ttu-id="b5b3a-127">可讓您將作業群組成單一可摺疊及可展開的單位，以提供視覺上的方便性。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-127">Enables you to group operations into a single collapsible and expandable unit for visual convenience.</span></span>|  
|![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")|<span data-ttu-id="b5b3a-128">**接聽**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-128">**Listen**</span></span>|<span data-ttu-id="b5b3a-129">可讓您的協調流程根據收到的訊息或逾時期間過期進行條件式分支。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-129">Enables your orchestration to conditionally branch depending on messages received or the expiration of a timeout period.</span></span>|  
|![](../core/media/ebiz-orch-loop.gif "ebiz_orch_loop")|<span data-ttu-id="b5b3a-130">**迴圈**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-130">**Loop**</span></span>|<span data-ttu-id="b5b3a-131">可讓您的協調流程在遇到某個條件之前不斷循環。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-131">Enables your orchestration to loop until a condition is met.</span></span>|  
|![](../core/media/ebiz-orch-assign.gif "ebiz_orch_assign")|<span data-ttu-id="b5b3a-132">**訊息指派**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-132">**Message Assignment**</span></span>|<span data-ttu-id="b5b3a-133">可讓您指派訊息值。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-133">Enables you to assign message values.</span></span>|  
|![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")|<span data-ttu-id="b5b3a-134">**平行動作**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-134">**Parallel Actions**</span></span>|<span data-ttu-id="b5b3a-135">可讓您的協調流程執行兩個或多個彼此獨立的作業。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-135">Enables your orchestration to perform two or more operations independently of each other.</span></span>|  
|![](../core/media/ebiz-orch-port.gif "ebiz_orch_port")|<span data-ttu-id="b5b3a-136">**[通訊埠]**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-136">**Port**</span></span>|<span data-ttu-id="b5b3a-137">定義訊息的傳輸地點及方式。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-137">Defines where and how messages are transmitted.</span></span>|  
|![](../core/media/ebiz-orch-receive.gif "ebiz_orch_receive")|<span data-ttu-id="b5b3a-138">**接收**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-138">**Receive**</span></span>|<span data-ttu-id="b5b3a-139">可讓您接收協調流程中的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-139">Enables you to receive a message in your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-rolelink.gif "ebiz_orch_rolelink")|<span data-ttu-id="b5b3a-140">**角色連結**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-140">**Role Link**</span></span>|<span data-ttu-id="b5b3a-141">可讓您建立要與相同邏輯夥伴通訊的連接埠集合 (可能是透過不同的傳輸或端點)。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-141">Enables you to create a collection of ports that communicate with the same logical partner, perhaps through different transports or endpoints.</span></span>|  
|![](../core/media/ebiz-orch-scope.gif "ebiz_orch_scope")|<span data-ttu-id="b5b3a-142">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-142">**Scope**</span></span>|<span data-ttu-id="b5b3a-143">提供交易和例外處理的架構。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-143">Provides a framework for transactions and exception handling.</span></span>|  
|![](../core/media/ebiz-orch-send.gif "ebiz_orch_send")|<span data-ttu-id="b5b3a-144">**傳送**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-144">**Send**</span></span>|<span data-ttu-id="b5b3a-145">可讓您從協調流程傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-145">Enables you to send a message from your orchestration.</span></span>|  
|![](../core/media/ebiz-orch-strtorchestrat.gif "ebiz_orch_strtorchestrat")|<span data-ttu-id="b5b3a-146">**啟動協調流程**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-146">**Start Orchestration**</span></span>|<span data-ttu-id="b5b3a-147">可讓您的協調流程非同步呼叫另一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-147">Enables your orchestration to call another orchestration asynchronously.</span></span>|  
|![](../core/media/ebiz-orch-suspend.gif "ebiz_orch_suspend")|<span data-ttu-id="b5b3a-148">**暫止**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-148">**Suspend**</span></span>|<span data-ttu-id="b5b3a-149">當發生某個錯誤狀況時，擱置協調流程的作業來啟用介入。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-149">Suspends the operation of your orchestration to enable intervention in the event of some error condition.</span></span>|  
|![](../core/media/ebiz-orch-terminate.gif "ebiz_orch_terminate")|<span data-ttu-id="b5b3a-150">**終止**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-150">**Terminate**</span></span>|<span data-ttu-id="b5b3a-151">當發生某個錯誤狀況時，可讓您立即結束協調流程的作業。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-151">Enables you to immediately end the operation of your orchestration in the event of some error condition.</span></span>|  
|![](../core/media/ebiz-orch-throwexcept.gif "ebiz_orch_throwexcept")|<span data-ttu-id="b5b3a-152">**擲回例外狀況**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-152">**Throw Exception**</span></span>|<span data-ttu-id="b5b3a-153">可讓您在發生錯誤時明確地擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-153">Enables you to explicitly throw an exception in the event of an error.</span></span>|  
|![](../core/media/ebiz-orch-transform.gif "ebiz_orch_transform")|<span data-ttu-id="b5b3a-154">**轉換**</span><span class="sxs-lookup"><span data-stu-id="b5b3a-154">**Transform**</span></span>|<span data-ttu-id="b5b3a-155">可讓您將現有訊息中的欄位對應到新訊息中的欄位。</span><span class="sxs-lookup"><span data-stu-id="b5b3a-155">Enables you to map the fields from existing messages into new messages.</span></span>|