---
title: "使用協調流程偵錯工具時的考量 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, modified orchestrations
- Orchestration Debugger, planning
- atomic scopes
- planning, Orchestration Debugger
- Orchestration Debugger, atomic scopes
- Orchestration Debugger, simple types
- orchestrations, modifying
ms.assetid: 55bfef48-08bd-48bb-abd5-7264e683da46
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2815da55bc74d822cb5fe2540347855db75b3a8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="considerations-when-using-orchestration-debugger"></a><span data-ttu-id="e981c-102">使用協調流程偵錯工具時的考量</span><span class="sxs-lookup"><span data-stu-id="e981c-102">Considerations when Using Orchestration Debugger</span></span>
<span data-ttu-id="e981c-103">以下為使用協調流程偵錯工具時需考量的事項。</span><span class="sxs-lookup"><span data-stu-id="e981c-103">Following are some things to consider when you work with the Orchestration Debugger.</span></span>  
  
## <a name="tracking-atomic-scopes"></a><span data-ttu-id="e981c-104">追蹤不可部分完成的範圍</span><span class="sxs-lookup"><span data-stu-id="e981c-104">Tracking atomic scopes</span></span>  
 <span data-ttu-id="e981c-105">協調流程會包含不可部分完成的範圍，以包含對規則引擎的呼叫。</span><span class="sxs-lookup"><span data-stu-id="e981c-105">An orchestration can contain atomic scopes to include calls to the Rule Engine.</span></span> <span data-ttu-id="e981c-106">當您連接至協調流程偵錯工具中的執行個體時，協調流程執行個體中不可部分完成的範圍將會導致追蹤的事件清單中出現間距。</span><span class="sxs-lookup"><span data-stu-id="e981c-106">When you attach to an instance in the orchestration debugger, any atomic scopes in the orchestration instance will cause gaps to appear in the tracked events list.</span></span> <span data-ttu-id="e981c-107">發生的原因有兩個：</span><span class="sxs-lookup"><span data-stu-id="e981c-107">This happens for two reasons:</span></span>  
  
-   <span data-ttu-id="e981c-108">因為直到範圍認可之前，不可部分完成交易中圖形的事件都不會持續。</span><span class="sxs-lookup"><span data-stu-id="e981c-108">Because events for the shapes inside atomic transactions do not get persisted until the scope commits</span></span>  
  
-   <span data-ttu-id="e981c-109">偵錯工具會將事件重新載入至清單結尾，因此在即時工作階段，所有的間距都還沒有填滿。</span><span class="sxs-lookup"><span data-stu-id="e981c-109">The debugger reloads events onto the end of the list, so any gaps remain unfilled during the live session.</span></span>  
  
 <span data-ttu-id="e981c-110">若您重新整理檢視即可消除間距。</span><span class="sxs-lookup"><span data-stu-id="e981c-110">You can eliminate the gaps if you refresh the view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e981c-111">您無法在不可部分完成範圍內的圖形上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="e981c-111">You cannot set a breakpoint on shapes inside an atomic scope.</span></span>  
  
## <a name="setting-breakpoints-in-the-exception-handler-scope"></a><span data-ttu-id="e981c-112">在例外處理常式範圍內設定中斷點</span><span class="sxs-lookup"><span data-stu-id="e981c-112">Setting breakpoints in the exception handler scope</span></span>  
 <span data-ttu-id="e981c-113">如果在例外狀況 Catch 處理常式設定中斷點，例外狀況類型必須標示為可序列化，否則協調流程偵錯工具便不會在設定的中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="e981c-113">If the breakpoint is set at the exception catch handler, the exception types must be marked as serializable, or the orchestration debugger will not stop at the breakpoints you set.</span></span> <span data-ttu-id="e981c-114">這是因為協調流程偵錯工具會在中斷點持續，因此，當不可序列化物件處於協調流程執行個體狀態中時，便會擲回持續性例外狀況。在此情況下，您也會收到 DebugBreakPointFailedException 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e981c-114">This is because of that the orchestration debugger does persistence at the breakpoint, therefore, when there is a non-serializable object in the orchestration instance state, a persistence exception will be thrown, and in this case, you will also receive a DebugBreakPointFailedException exception.</span></span>  
  
## <a name="tracking-a-modified-orchestration"></a><span data-ttu-id="e981c-115">追蹤修改的協調流程</span><span class="sxs-lookup"><span data-stu-id="e981c-115">Tracking a modified orchestration</span></span>  
 <span data-ttu-id="e981c-116">若您不變更版本編號而想追蹤修改的協調流程，則必須重新啟動已登錄協調流程的所有主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="e981c-116">If you track an orchestration modified without changing the version number, you must restart all the host instances to which the orchestration is enlisted.</span></span> <span data-ttu-id="e981c-117">如此即可在您逐步完成協調流程偵錯工具時，確保新部署版本中的圖形變更可正確顯示。</span><span class="sxs-lookup"><span data-stu-id="e981c-117">This insures that any shape change in the newly deployed version displays correctly, as you step through the Orchestration Debugger.</span></span>  
  
## <a name="tracking-simple-types"></a><span data-ttu-id="e981c-118">追蹤簡單型別</span><span class="sxs-lookup"><span data-stu-id="e981c-118">Tracking simple types</span></span>  
 <span data-ttu-id="e981c-119">協調流程偵錯工具僅支援簡單型別。</span><span class="sxs-lookup"><span data-stu-id="e981c-119">The Orchestration Debugger only supports simple types.</span></span> <span data-ttu-id="e981c-120">例如，若您追蹤包含 .NET 物件的多個訊息，您可以檢視所有訊息部分的屬性，但是 .NET 物件屬性為例外。</span><span class="sxs-lookup"><span data-stu-id="e981c-120">For example, if you track a multipart message that contains a .NET object you can view the properties of all message parts, with the exception of the .NET object properties.</span></span>  
  
 <span data-ttu-id="e981c-121">當協調流程顯示為「在中斷點」狀態，且協調流程偵錯工具已啟動時，您可以執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="e981c-121">When an orchestration appears in the In Breakpoint state and the Orchestration Debugger starts, you can perform the following actions:</span></span>  
  
-   <span data-ttu-id="e981c-122">使用**附加**服務選項。</span><span class="sxs-lookup"><span data-stu-id="e981c-122">Use the **Attach** service option.</span></span>  
  
-   <span data-ttu-id="e981c-123">檢視已完成的步驟。</span><span class="sxs-lookup"><span data-stu-id="e981c-123">Review the steps that have already completed.</span></span>  
  
-   <span data-ttu-id="e981c-124">檢視變數和訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="e981c-124">View the state of variables and messages.</span></span>  
  
-   <span data-ttu-id="e981c-125">設定其他中斷點。</span><span class="sxs-lookup"><span data-stu-id="e981c-125">Set additional breakpoints.</span></span>  
  
-   <span data-ttu-id="e981c-126">選取**繼續服務**選項。</span><span class="sxs-lookup"><span data-stu-id="e981c-126">Select the **Continue Service** option.</span></span>  
  
-   <span data-ttu-id="e981c-127">視需要重複任何步驟。</span><span class="sxs-lookup"><span data-stu-id="e981c-127">Repeat any steps as required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e981c-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e981c-128">See Also</span></span>  
 <span data-ttu-id="e981c-129">[協調流程偵錯工具中的互動模式](../core/interactive-mode-in-orchestration-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="e981c-129">[Interactive Mode in Orchestration Debugger](../core/interactive-mode-in-orchestration-debugger.md) </span></span>  
 [<span data-ttu-id="e981c-130">偵錯協調流程</span><span class="sxs-lookup"><span data-stu-id="e981c-130">Debugging an Orchestration</span></span>](../core/debugging-an-orchestration.md)