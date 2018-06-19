---
title: ExceptionHandler 協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors, systems
- errors, applications
- applications, errors
- orchestrations, errors [process management solutions]
- process management solution tutorial, errors
ms.assetid: ac154e76-9dfe-433a-948b-e098df705fe5
caps.latest.revision: 27
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1b79a1c6d9e6fada206ba0298913fe8f369783c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22280022"
---
# <a name="the-exceptionhandler-orchestration"></a><span data-ttu-id="e93f0-102">ExceptionHandler 協調流程</span><span class="sxs-lookup"><span data-stu-id="e93f0-102">The ExceptionHandler Orchestration</span></span>
<span data-ttu-id="e93f0-103">商務程序管理解決方案會使用兩種類型的例外狀況： 系統例外狀況和應用程式例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e93f0-103">The Business Process Management solution uses two kinds of exceptions: system exceptions and application exceptions.</span></span> <span data-ttu-id="e93f0-104">系統例外狀況像是資源錯誤—例如網路連線失敗。</span><span class="sxs-lookup"><span data-stu-id="e93f0-104">System exceptions include things like resource errors—a network connection failing, for example.</span></span> <span data-ttu-id="e93f0-105">在一段時間後，這些問題有可能會自己解決，所以解決方案會重試造成系統例外狀況的所有作業。</span><span class="sxs-lookup"><span data-stu-id="e93f0-105">There is a chance that such a problem may resolve itself after an interval so that the solution retries all operations that produce system exceptions.</span></span> <span data-ttu-id="e93f0-106">應用程式例外狀況產生的問題較不易自行解決，如邏輯錯誤或某種形式的不一致。</span><span class="sxs-lookup"><span data-stu-id="e93f0-106">Application exceptions are produced by things less likely to resolve themselves, such as logical errors or some form of inconsistency.</span></span> <span data-ttu-id="e93f0-107">解決方案會使用**ExceptionHandlerOrch**協調流程來處理系統和應用程式錯誤。</span><span class="sxs-lookup"><span data-stu-id="e93f0-107">The solution uses the **ExceptionHandlerOrch** orchestration to process both system and application errors.</span></span>  
  
 <span data-ttu-id="e93f0-108">訂單處理階段 (**CableOrder1**， **CableOrder2**) 和其附屬協調流程 (**Activate**，**分析**， **取消**，**變更**，**完成**，**驗證**) 所有使用**ExceptionHandlerOrch**。</span><span class="sxs-lookup"><span data-stu-id="e93f0-108">The order processing stages (**CableOrder1**, **CableOrder2**) and their satellite orchestrations (**Activate**, **Analyze**, **Cancel**, **Change**, **Complete**, **Validate**) all use **ExceptionHandlerOrch**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e93f0-109">您可能想要閱讀本節**ExceptionHandlerOrch**協調流程開啟 microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="e93f0-109">You may want to read this section with the **ExceptionHandlerOrch** orchestration open in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="application-errors"></a><span data-ttu-id="e93f0-110">應用程式錯誤</span><span class="sxs-lookup"><span data-stu-id="e93f0-110">Application Errors</span></span>  
 <span data-ttu-id="e93f0-111">第一次呼叫來記錄錯誤的例外狀況處理常式**Utilities**方法**ErrorHandler**物件存放至**公用程式**組件。</span><span class="sxs-lookup"><span data-stu-id="e93f0-111">The exception handler first logs the error by calling the **PostError** method of the **ErrorHandler** object in the **Utilities** assembly.</span></span> <span data-ttu-id="e93f0-112">然後，例外狀況處理常式測試錯誤為系統錯誤或應用程式錯誤。</span><span class="sxs-lookup"><span data-stu-id="e93f0-112">The exception handler then tests whether the error was a system error or an application error.</span></span> <span data-ttu-id="e93f0-113">下列擷取畫面顯示處理應用程式例外狀況的協調流程分支：</span><span class="sxs-lookup"><span data-stu-id="e93f0-113">The following screenshot shows the orchestration branch that processes application exceptions:</span></span>  
  
 <span data-ttu-id="e93f0-114">![ExceptionHandler 協調流程的應用程式分支](../core/media/applicationerrorbranchofexceptionhandler.gif "ApplicationErrorBranchofExceptionHandler")</span><span class="sxs-lookup"><span data-stu-id="e93f0-114">![Application Branch of ExceptionHandler Orchestrati](../core/media/applicationerrorbranchofexceptionhandler.gif "ApplicationErrorBranchofExceptionHandler")</span></span>  
  
 <span data-ttu-id="e93f0-115">表示應用程式錯誤，協調流程會建構字串，描述錯誤並呼叫**ErrorHandlerOrch**協調流程。</span><span class="sxs-lookup"><span data-stu-id="e93f0-115">For an application error, the orchestration constructs a string describing the error and calls the **ErrorHandlerOrch** orchestration.</span></span> <span data-ttu-id="e93f0-116">此協調流程將錯誤傳送給作業，其中運算子決定要修復錯誤或終止作業。</span><span class="sxs-lookup"><span data-stu-id="e93f0-116">This orchestration sends the error to operations where an operator decides whether to fix the error or terminate the operation.</span></span> <span data-ttu-id="e93f0-117">若運算子修復錯誤，修復的訊息會從 ErrorHandlerOrch 協調流程傳回，並重試作業。</span><span class="sxs-lookup"><span data-stu-id="e93f0-117">If the operator fixes the error, the repaired message comes back from the ErrorHandlerOrch orchestration and the operation is retried.</span></span> <span data-ttu-id="e93f0-118">例外狀況處理常式會藉由呼叫**Invoke**方法**Recaller**物件存放至**公用程式**組件。</span><span class="sxs-lookup"><span data-stu-id="e93f0-118">The exception handler does this by calling the **Invoke** method of the **Recaller** object in the **Utilities** assembly.</span></span> <span data-ttu-id="e93f0-119">**Recaller**物件使用反映以呼叫造成錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e93f0-119">The **Recaller** object uses reflection to call the code that caused the error.</span></span>  
  
 <span data-ttu-id="e93f0-120">如果呼叫**Invoke**成功，例外狀況處理常式會結束。</span><span class="sxs-lookup"><span data-stu-id="e93f0-120">If the call to **Invoke** succeeds, the exception handler exits.</span></span> <span data-ttu-id="e93f0-121">否則，它回執行迴圈，並嘗試呼叫**Invoke**一次。</span><span class="sxs-lookup"><span data-stu-id="e93f0-121">Otherwise, it loops back and attempts the call to **Invoke** again.</span></span> <span data-ttu-id="e93f0-122">如需有關**Recaller**物件，請參閱[Recaller 物件](../core/the-recaller-object.md)。</span><span class="sxs-lookup"><span data-stu-id="e93f0-122">For more information about the **Recaller** object, see [The Recaller Object](../core/the-recaller-object.md).</span></span>  
  
## <a name="system-errors"></a><span data-ttu-id="e93f0-123">系統錯誤</span><span class="sxs-lookup"><span data-stu-id="e93f0-123">System Errors</span></span>  
 <span data-ttu-id="e93f0-124">下圖顯示的系統錯誤分支**ExceptionHandler**協調流程：</span><span class="sxs-lookup"><span data-stu-id="e93f0-124">The following diagram shows the system error branch of the **ExceptionHandler** orchestration:</span></span>  
  
 <span data-ttu-id="e93f0-125">![ExceptionHandler 協調流程的系統錯誤](../core/media/systemerrorbranchofexceptionhandler.gif "SystemErrorBranchofExceptionHandler")</span><span class="sxs-lookup"><span data-stu-id="e93f0-125">![System Error of ExceptionHandler Orchestration](../core/media/systemerrorbranchofexceptionhandler.gif "SystemErrorBranchofExceptionHandler")</span></span>  
  
 <span data-ttu-id="e93f0-126">針對系統錯誤，例外狀況處理常式會先呼叫**CheckInterrupt**協調流程，然後等候一分鐘。</span><span class="sxs-lookup"><span data-stu-id="e93f0-126">For a system error, the exception handler first calls the **CheckInterrupt** orchestration and then waits for one minute.</span></span> <span data-ttu-id="e93f0-127">等候的時間可先清除暫時短暫的錯誤 (如網路連線問題)，再進行重試。</span><span class="sxs-lookup"><span data-stu-id="e93f0-127">The wait allows for temporary, short-term errors such as network connection problems, to clear before trying again.</span></span> <span data-ttu-id="e93f0-128">在進行遠端呼叫時，常有可能會發生網路問題。</span><span class="sxs-lookup"><span data-stu-id="e93f0-128">When making remote calls there is always the chance of a network problem.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e93f0-129">在可中斷的設計中，一般的規則是在任何等待時間期間或之後立即測試是否有中斷的情形發生。</span><span class="sxs-lookup"><span data-stu-id="e93f0-129">In an interruptible design, as a general rule, you want to test for an interrupt during or immediately after any waiting period to see if an interrupt has occurred.</span></span>  
  
 <span data-ttu-id="e93f0-130">等候之後, 處理常式使用**Invoke**方法**Recaller**執行原始的程式碼的物件。</span><span class="sxs-lookup"><span data-stu-id="e93f0-130">After the wait, the handler uses the **Invoke** method of the **Recaller** object to run the original code.</span></span> <span data-ttu-id="e93f0-131">若呼叫成功，就會結束處理常式。</span><span class="sxs-lookup"><span data-stu-id="e93f0-131">If the call succeeds, the handler exits.</span></span> <span data-ttu-id="e93f0-132">否則，處理常式會再試著執行兩次原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="e93f0-132">Otherwise, the handler will try two more times to run the original code.</span></span> <span data-ttu-id="e93f0-133">如果所有的三次嘗試失敗，處理常式會建構錯誤字串，並呼叫**ErrorHandlerOrch**協調流程。</span><span class="sxs-lookup"><span data-stu-id="e93f0-133">If all three attempts fail, the handler constructs an error string and calls the **ErrorHandlerOrch** orchestration.</span></span>  
  
 <span data-ttu-id="e93f0-134">如果處理系統例外狀況時造成例外狀況，例外狀況區塊將會取得此例外狀況：</span><span class="sxs-lookup"><span data-stu-id="e93f0-134">If processing a system exception causes an exception, the exception block catches it:</span></span>  
  
 <span data-ttu-id="e93f0-135">![系統錯誤分支的例外狀況處理常式](../core/media/exceptionhandlerofsystemerrorbranch.gif "ExceptionHandlerofSystemErrorBranch")</span><span class="sxs-lookup"><span data-stu-id="e93f0-135">![Exception Handler for System Error Branch](../core/media/exceptionhandlerofsystemerrorbranch.gif "ExceptionHandlerofSystemErrorBranch")</span></span>  
  
 <span data-ttu-id="e93f0-136">例外狀況處理常式會測試例外狀況的類型；如果是系統例外狀況，就遞減重試計數器；否則，設定旗標以表示其為應用程式例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e93f0-136">The exception handler tests the type of the exception and either decrements the retry counter if it's a system exception, or sets a flag to indicate an application exception.</span></span>  
  
## <a name="the-errorhandlerorch-orchestration"></a><span data-ttu-id="e93f0-137">ErrorHandlerOrch 協調流程</span><span class="sxs-lookup"><span data-stu-id="e93f0-137">The ErrorHandlerOrch Orchestration</span></span>  
 <span data-ttu-id="e93f0-138">下圖顯示的第一個部分**ErrorHandlerOrch**協調流程：</span><span class="sxs-lookup"><span data-stu-id="e93f0-138">The following diagram shows the first part of the **ErrorHandlerOrch** orchestration:</span></span>  
  
 <span data-ttu-id="e93f0-139">![錯誤處理常式協調流程中，第一個部分](../core/media/errorhandlerfirstpart.gif "ErrorHandlerFirstPart")</span><span class="sxs-lookup"><span data-stu-id="e93f0-139">![Error Handler Orchestration, First Part](../core/media/errorhandlerfirstpart.gif "ErrorHandlerFirstPart")</span></span>  
  
 <span data-ttu-id="e93f0-140">**ErrorHandlerOrch**協調流程會先測試**IsBadOrder**參數，以查看錯誤是錯誤的訂單 (**IsBadOrder**為 true) 或其他一些錯誤。</span><span class="sxs-lookup"><span data-stu-id="e93f0-140">The **ErrorHandlerOrch** orchestration first tests the **IsBadOrder** parameter to see if the error is a bad order (**IsBadOrder** is true) or some other error.</span></span> <span data-ttu-id="e93f0-141">若錯誤是錯誤的訂單，協調流程會從原始的訂單傳回位址以指定訊息的目的地，然後將訊息傳回到客戶服務系統。</span><span class="sxs-lookup"><span data-stu-id="e93f0-141">If the error is a bad order, it assigns the destination of the message from the original order return address and sends the message back to the customer service system.</span></span> <span data-ttu-id="e93f0-142">若錯誤不是錯誤的訂單，協調流程會建立訂單錯誤訊息，並將它傳送到作業系統。</span><span class="sxs-lookup"><span data-stu-id="e93f0-142">If the error is not a bad order, the orchestration creates an order error message and sends it to the operations system.</span></span>  
  
 <span data-ttu-id="e93f0-143">發生上述其中一種錯誤後，協調流程會接聽回應訊息或中斷訊息：</span><span class="sxs-lookup"><span data-stu-id="e93f0-143">After either error, the orchestration then listens for a response message or an interrupt message:</span></span>  
  
 <span data-ttu-id="e93f0-144">![錯誤處理常式的第二個部分](../core/media/errorhandlersecondpart.gif "ErrorHandlerSecondPart")</span><span class="sxs-lookup"><span data-stu-id="e93f0-144">![Error Handler Second Part](../core/media/errorhandlersecondpart.gif "ErrorHandlerSecondPart")</span></span>  
  
 <span data-ttu-id="e93f0-145">若協調流程收到回應，會將回應傳回呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e93f0-145">If the orchestration receives a response, it returns to the caller.</span></span> <span data-ttu-id="e93f0-146">如果協調流程收到中斷訊息，將訊息傳遞到中斷連接埠，並擲出自**InterruptException**。</span><span class="sxs-lookup"><span data-stu-id="e93f0-146">If the orchestration receives an interrupt message, it passes the message on to an interrupt port and throws a custom **InterruptException**.</span></span>  
  
 <span data-ttu-id="e93f0-147">如需解決方案如何使用和處理中斷的詳細資訊，請參閱[中斷商務程序管理解決方案中處理](../core/interrupt-handling-in-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="e93f0-147">For more information about how the solution uses and handles interrupts, see [Interrupt Handling in the Business Process Management Solution](../core/interrupt-handling-in-the-business-process-management-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e93f0-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e93f0-148">See Also</span></span>  
 <span data-ttu-id="e93f0-149">[在商務程序管理解決方案中處理的例外狀況](../core/exception-handling-in-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="e93f0-149">[Exception Handling in the Business Process Management Solution](../core/exception-handling-in-the-business-process-management-solution.md) </span></span>  
 <span data-ttu-id="e93f0-150">[自訂例外狀況](../core/custom-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="e93f0-150">[Custom Exceptions](../core/custom-exceptions.md) </span></span>  
 <span data-ttu-id="e93f0-151">[中斷商務程序管理解決方案中的處理](../core/interrupt-handling-in-the-business-process-management-solution.md) </span><span class="sxs-lookup"><span data-stu-id="e93f0-151">[Interrupt Handling in the Business Process Management Solution](../core/interrupt-handling-in-the-business-process-management-solution.md) </span></span>  
 [<span data-ttu-id="e93f0-152">Recaller 物件</span><span class="sxs-lookup"><span data-stu-id="e93f0-152">The Recaller Object</span></span>](../core/the-recaller-object.md)