---
title: "XLANG s 陳述式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d0452-a8da-4285-b8b2-5a932ffcde28
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50f2ea904d134d22f08d86b1d600fdb3133a9c45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-statements"></a><span data-ttu-id="b06f9-102">XLANG s 陳述式</span><span class="sxs-lookup"><span data-stu-id="b06f9-102">XLANG-s Statements</span></span>
<span data-ttu-id="b06f9-103">XLANG/s 陳述式通常分為兩種類別： 簡單的陳述式會處理其本身，例如**接收**或**傳送**，和包含或是分組任一個簡單的陳述式的複雜陳述式或其他複雜的陳述式，例如**範圍**，**平行**，和**接聽**。</span><span class="sxs-lookup"><span data-stu-id="b06f9-103">XLANG/s statements generally fall into one of two categories: simple statements that act on their own, such as **receive** or **send**, and complex statements that contain or group either simple statements or other complex statements, such as **scope**, **parallel**, and **listen**.</span></span> <span data-ttu-id="b06f9-104">每個陳述式分別對應至「BizTalk 協調流程設計師」中的一個協調流程圖形。</span><span class="sxs-lookup"><span data-stu-id="b06f9-104">Each statement is corresponding to an orchestration shape in the BizTalk Orchestration Designer.</span></span> <span data-ttu-id="b06f9-105">XLANG/s 會定義下列陳述式：</span><span class="sxs-lookup"><span data-stu-id="b06f9-105">XLANG/s defines the following statements:</span></span>  
  
-   <span data-ttu-id="b06f9-106">**群組。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-106">**group.**</span></span> <span data-ttu-id="b06f9-107">將作業群組為單一可摺疊及可展開的單位用於視覺上的方便性。</span><span class="sxs-lookup"><span data-stu-id="b06f9-107">Used to group operations into a single collapsible and expandable unit for visual convenience.</span></span>  
  
-   <span data-ttu-id="b06f9-108">**傳送。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-108">**send.**</span></span> <span data-ttu-id="b06f9-109">將指定的訊息傳送到特定連接埠。</span><span class="sxs-lookup"><span data-stu-id="b06f9-109">Used to send a specified message to a specified port.</span></span>  
  
-   <span data-ttu-id="b06f9-110">**接收。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-110">**receive.**</span></span> <span data-ttu-id="b06f9-111">用來等待從特定連接埠接收特定訊息。</span><span class="sxs-lookup"><span data-stu-id="b06f9-111">Used to wait for the receipt of a specified message from a specified port.</span></span>  
  
-   <span data-ttu-id="b06f9-112">**連接埠。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-112">**port.**</span></span> <span data-ttu-id="b06f9-113">定義訊息的傳輸地點及方式。</span><span class="sxs-lookup"><span data-stu-id="b06f9-113">Defines where and how messages are transmitted.</span></span>  
  
-   <span data-ttu-id="b06f9-114">**角色連結。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-114">**role link.**</span></span> <span data-ttu-id="b06f9-115">用來建立與相同邏輯夥伴，可能是透過不同的傳輸或端點通訊的連接埠的集合</span><span class="sxs-lookup"><span data-stu-id="b06f9-115">Used to create a collection of ports that communicate with the same logical partner, perhaps through different transports or endpoints</span></span>  
  
-   <span data-ttu-id="b06f9-116">**轉換。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-116">**transform.**</span></span> <span data-ttu-id="b06f9-117">用來將現有訊息中的欄位對應到新訊息。</span><span class="sxs-lookup"><span data-stu-id="b06f9-117">Used to map the fields from existing messages into new messages.</span></span>  
  
-   <span data-ttu-id="b06f9-118">**訊息指派。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-118">**message assignment.**</span></span> <span data-ttu-id="b06f9-119">將指定的訊息傳送到特定連接埠。</span><span class="sxs-lookup"><span data-stu-id="b06f9-119">Used to send a specified message to a specified port.</span></span>  
  
-   <span data-ttu-id="b06f9-120">**建構訊息。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-120">**construct message.**</span></span> <span data-ttu-id="b06f9-121">定義訊息建立和初始化所在的 XLANG/s 程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="b06f9-121">Defines a block of XLANG/s code where a message is created and initialized.</span></span> <span data-ttu-id="b06f9-122">現有訊息可傳送至 XLANG/s 程式，但不可在建構之外建立。</span><span class="sxs-lookup"><span data-stu-id="b06f9-122">Existing messages can be sent to an XLANG/s program, but cannot be created outside of a construct.</span></span> <span data-ttu-id="b06f9-123">此機制提供訊息散佈和豐富的訊息追蹤，因為訊息狀態在所有時候都是已知的。</span><span class="sxs-lookup"><span data-stu-id="b06f9-123">This mechanism provides for message distribution and rich message tracking, because a message state is known at all times.</span></span>  
  
-   <span data-ttu-id="b06f9-124">**呼叫協調流程。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-124">**call orchestration.**</span></span> <span data-ttu-id="b06f9-125">從一個協調流程同步呼叫另一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="b06f9-125">Synchronously calls from one orchestration to another orchestration.</span></span> <span data-ttu-id="b06f9-126">可傳送和傳回參數。</span><span class="sxs-lookup"><span data-stu-id="b06f9-126">Parameters can be passed and returned.</span></span>  
  
-   <span data-ttu-id="b06f9-127">**啟動協調流程。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-127">**start orchestration.**</span></span> <span data-ttu-id="b06f9-128">用來啟用您的協調流程非同步呼叫另一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="b06f9-128">Used to enable your orchestration to call another orchestration asynchronously.</span></span>  
  
-   <span data-ttu-id="b06f9-129">**呼叫規則。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-129">**call rules.**</span></span> <span data-ttu-id="b06f9-130">可讓您設定要在協調流程中執行的商務規則原則。</span><span class="sxs-lookup"><span data-stu-id="b06f9-130">Enables you to configure a Business Rules policy to be executed in your orchestration.</span></span>  
  
-   <span data-ttu-id="b06f9-131">**運算式。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-131">**expression.**</span></span> <span data-ttu-id="b06f9-132">XLANG/s 支援豐富的運算式語法，可用於通訊協定定義的廣泛實例中。</span><span class="sxs-lookup"><span data-stu-id="b06f9-132">XLANG/s supports rich expression syntax to support the wide variety of usage scenarios required for protocol definition.</span></span> <span data-ttu-id="b06f9-133">這個陳述式可用來指定連接埠屬性、服務連結屬性、訊息、變數和物件，並且可用來叫用方法、屬性或靜態資料欄位。</span><span class="sxs-lookup"><span data-stu-id="b06f9-133">This statement is used to assign port properties, service-link properties, messages, variables, and objects, and to invoke methods, properties, or static data fields.</span></span>  
  
-   <span data-ttu-id="b06f9-134">**決定。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-134">**decide.**</span></span> <span data-ttu-id="b06f9-135">根據其關聯的條件值，條件式執行數個執行路徑之一。</span><span class="sxs-lookup"><span data-stu-id="b06f9-135">Used to conditionally execute one of several paths of execution, depending on the value of its associated conditions.</span></span>  
  
-   <span data-ttu-id="b06f9-136">**延遲。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-136">**delay.**</span></span> <span data-ttu-id="b06f9-137">用來等待，直到達到絕對時間或相對時間為止。</span><span class="sxs-lookup"><span data-stu-id="b06f9-137">Used to wait until an absolute time is reached or a relative time is reached.</span></span>  
  
-   <span data-ttu-id="b06f9-138">**接聽。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-138">**listen.**</span></span> <span data-ttu-id="b06f9-139">如同**平行**陳述式，**接聽**陳述式具有多個執行分支的路徑。</span><span class="sxs-lookup"><span data-stu-id="b06f9-139">As with a **parallel** statement, the **listen** statement has multiple paths of execution branches.</span></span> <span data-ttu-id="b06f9-140">不過，必須以開始分支**延遲**陳述式或**接收**陳述式。</span><span class="sxs-lookup"><span data-stu-id="b06f9-140">However, the branches must begin with a **delay** statement or a **receive** statement.</span></span> <span data-ttu-id="b06f9-141">只執行接收第一個叫用的分支，</span><span class="sxs-lookup"><span data-stu-id="b06f9-141">The branch that receives the first invocation is executed.</span></span> <span data-ttu-id="b06f9-142">其他的分支**接聽**絕對不會執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="b06f9-142">The other branches of the **listen** statement are never executed.</span></span>  
  
-   <span data-ttu-id="b06f9-143">**平行動作。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-143">**parallel actions.**</span></span> <span data-ttu-id="b06f9-144">並行執行商務程序的多個分支。</span><span class="sxs-lookup"><span data-stu-id="b06f9-144">Executes multiple branches of a business process concurrently.</span></span> <span data-ttu-id="b06f9-145">所有分支都必須完成處理，才能執行此 parallel 陳述式之後的任何陳述式。</span><span class="sxs-lookup"><span data-stu-id="b06f9-145">All branches must complete processing before any statements following the parallel statement are executed.</span></span>  
  
-   <span data-ttu-id="b06f9-146">**迴圈。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-146">**loop.**</span></span> <span data-ttu-id="b06f9-147">在其關聯的條件維持 true 期間，重複執行。</span><span class="sxs-lookup"><span data-stu-id="b06f9-147">Repeatedly executes while its associated condition remains true.</span></span>  
  
-   <span data-ttu-id="b06f9-148">**範圍。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-148">**scope.**</span></span> <span data-ttu-id="b06f9-149">針對程式碼區塊，提供定義適用於該程式碼區塊之變數和交易式語意的內容。</span><span class="sxs-lookup"><span data-stu-id="b06f9-149">Provides a context for a block of code that defines variables and transactional semantics that apply to that block of code.</span></span> <span data-ttu-id="b06f9-150">變數存留期間受限於該範圍內。</span><span class="sxs-lookup"><span data-stu-id="b06f9-150">Variable lifetime can be restricted to that scope.</span></span> <span data-ttu-id="b06f9-151">交易式語意 (例如長時間執行、不可部分完成或無) 可套用至範圍，影響其行為。</span><span class="sxs-lookup"><span data-stu-id="b06f9-151">Transactional semantics, such as long-running, atomic, or none can be applied to a scope to affect its behavior.</span></span>  
  
-   <span data-ttu-id="b06f9-152">**擲回例外狀況。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-152">**throw exception.**</span></span> <span data-ttu-id="b06f9-153">用於在目前程式碼區塊中明確叫用例外狀況/錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="b06f9-153">Used to explicitly invoke an exception/fault handler in the current code block.</span></span>  
  
-   <span data-ttu-id="b06f9-154">**補償。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-154">**compensate.**</span></span> <span data-ttu-id="b06f9-155">用來明確叫用與指定範圍關聯的補償區塊。</span><span class="sxs-lookup"><span data-stu-id="b06f9-155">Used to explicitly invoke a compensation block associated with a given scope.</span></span> <span data-ttu-id="b06f9-156">A**範圍**陳述式可以有一或多個與其相關聯的補償區塊。</span><span class="sxs-lookup"><span data-stu-id="b06f9-156">A **scope** statement may have one or more compensation blocks associated with it.</span></span> <span data-ttu-id="b06f9-157">**補償**陳述式將執行導向至選取的補償區塊。</span><span class="sxs-lookup"><span data-stu-id="b06f9-157">The **compensate** statement directs execution to the selected compensation block.</span></span>  
  
-   <span data-ttu-id="b06f9-158">**暫止。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-158">**suspend.**</span></span> <span data-ttu-id="b06f9-159">暫時終止程序的執行，但可由操作員或應用程式重新啟動它。</span><span class="sxs-lookup"><span data-stu-id="b06f9-159">Temporarily halts execution of a process, but can be restarted by an operator or application.</span></span> <span data-ttu-id="b06f9-160">與相關聯的字串運算式**終止**陳述式都可以提供給操作員/系統管理員透過適當記錄或使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b06f9-160">A string expression associated with the **terminate** statement is made available to operators/administrators through appropriate logs or through a user interface.</span></span>  
  
-   <span data-ttu-id="b06f9-161">**終止。**</span><span class="sxs-lookup"><span data-stu-id="b06f9-161">**terminate.**</span></span> <span data-ttu-id="b06f9-162">以強制、不可逆轉的方式停止排程中的所有處理。</span><span class="sxs-lookup"><span data-stu-id="b06f9-162">Forcibly and irrevocably stops all processing in a schedule.</span></span> <span data-ttu-id="b06f9-163">與相關聯的字串運算式**終止**陳述式可供操作員和系統管理員透過適當記錄或使用者介面。</span><span class="sxs-lookup"><span data-stu-id="b06f9-163">A string expression associated with the **terminate** statement is made available to operators and administrators through appropriate logs or through a user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b06f9-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b06f9-164">See Also</span></span>  
 <span data-ttu-id="b06f9-165">[協調流程圖形](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="b06f9-165">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 <span data-ttu-id="b06f9-166">[XLANG 的資料型別](../core/xlang-s-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="b06f9-166">[XLANG-s Data Types](../core/xlang-s-data-types.md) </span></span>  
 <span data-ttu-id="b06f9-167">[XLANG 的變數和運算子](../core/xlang-s-variables-and-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b06f9-167">[XLANG-s Variables and Operators](../core/xlang-s-variables-and-operators.md) </span></span>  
 <span data-ttu-id="b06f9-168">[XLANG 的運算式](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b06f9-168">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="b06f9-169">[XLANG s 保留字](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="b06f9-169">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="b06f9-170">XLANG-s 至 BPEL4WS 型別轉換</span><span class="sxs-lookup"><span data-stu-id="b06f9-170">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)