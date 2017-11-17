---
title: "範圍 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scopes, exception handling
- Scope shape [Orchestration Designer], nesting
- scopes, variables
- scopes, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], exception handling
- scopes, transactions
- scopes, synchronization
- scopes, nesting
- Scope shape [Orchestration Designer], transactions
ms.assetid: 51d81ce4-0034-4415-b6ab-4c952737c1bd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc4d1b5d926540477293591ade8123126be1b84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scopes"></a><span data-ttu-id="ab514-102">範圍</span><span class="sxs-lookup"><span data-stu-id="ab514-102">Scopes</span></span>
<span data-ttu-id="ab514-103">範圍是群組動作的架構。</span><span class="sxs-lookup"><span data-stu-id="ab514-103">A scope is a framework for grouping actions.</span></span> <span data-ttu-id="ab514-104">範圍主要用於交易式執行和例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="ab514-104">It is primarily used for transactional execution and exception handling.</span></span>  
  
 <span data-ttu-id="ab514-105">範圍可以包含一個或多個區塊。</span><span class="sxs-lookup"><span data-stu-id="ab514-105">A scope contains one or more blocks.</span></span> <span data-ttu-id="ab514-106">範圍具有一個本文，並且可以選擇性地附加任何數目的例外狀況處理區塊。</span><span class="sxs-lookup"><span data-stu-id="ab514-106">It has a body and can optionally have appended to it any number of exception-handling blocks.</span></span> <span data-ttu-id="ab514-107">取決於範圍的本質，範圍也可以具有選擇性的補償區塊。</span><span class="sxs-lookup"><span data-stu-id="ab514-107">It may have an optional compensation block as well, depending on the nature of the scope.</span></span> <span data-ttu-id="ab514-108">有些範圍會單純用於例外狀況處理，而不需要任何的補償。</span><span class="sxs-lookup"><span data-stu-id="ab514-108">Some scopes will be purely for exception handling, and will not require compensation.</span></span> <span data-ttu-id="ab514-109">其他的範圍則是明確交易式的，而且永遠會有預設的補償處理常式，以及您可以為其建立的選擇性補償處理常式。</span><span class="sxs-lookup"><span data-stu-id="ab514-109">Other scopes will be explicitly transactional, and will always have a default compensation handler, along with an optional compensation handler that you create for it.</span></span> <span data-ttu-id="ab514-110">交易式範圍也有一個預設的例外狀況處理常式，以及由您為其建立之任何數目的其他例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="ab514-110">A transactional scope will also have a default exception handler and any number of additional exception handlers that you create for it.</span></span>  
  
## <a name="synchronized-scopes"></a><span data-ttu-id="ab514-111">同步處理的範圍</span><span class="sxs-lookup"><span data-stu-id="ab514-111">Synchronized scopes</span></span>  
 <span data-ttu-id="ab514-112">您可以將範圍指定為同步處理或非同步處理。</span><span class="sxs-lookup"><span data-stu-id="ab514-112">You can specify that scopes are synchronized or not synchronized.</span></span> <span data-ttu-id="ab514-113">藉由同步處理某個範圍，您可以確保在其中存取的任何共用資料，都不會寫入協調流程中的一個或多個平行動作，或是在由其他動作讀取時寫入。</span><span class="sxs-lookup"><span data-stu-id="ab514-113">By synchronizing a scope, you ensure that any shared data that is accessed within it will not be written to by one or more parallel actions in your orchestration, nor will it be written to while another action is reading it.</span></span>  
  
 <span data-ttu-id="ab514-114">不可部分完成的交易範圍永遠都會是同步處理的。</span><span class="sxs-lookup"><span data-stu-id="ab514-114">Atomic transaction scopes are always synchronized.</span></span> <span data-ttu-id="ab514-115">同步處理之範圍內的所有動作，以及在其任何例外狀況處理常式中的所有動作，都會被視為已同步。</span><span class="sxs-lookup"><span data-stu-id="ab514-115">All actions within a synchronized scope are considered synchronized, as are all actions in any of its exception handlers.</span></span> <span data-ttu-id="ab514-116">交易式範圍之補償處理常式中的動作，則不會同步。</span><span class="sxs-lookup"><span data-stu-id="ab514-116">Actions in the compensation handler for a transactional scope are not synchronized.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="ab514-117">請注意，如果沒有小心設計您的處理序，您依然可能會碰到鎖死的狀況。</span><span class="sxs-lookup"><span data-stu-id="ab514-117">Note that you can still run into a deadlock condition if you do not design your processes carefully.</span></span> <span data-ttu-id="ab514-118">例如：協調流程 A 中的兩個平行分支存取相同的訊息，一個傳送該訊息，另一個則接收該訊息，兩者都需要同步處理的範圍。</span><span class="sxs-lookup"><span data-stu-id="ab514-118">For example: two branches of a parallel in orchestration A access the same message, one to send it and one to receive it, so both must have a synchronized scope.</span></span> <span data-ttu-id="ab514-119">第二個協調流程則會接收該訊息，並且將其傳回。</span><span class="sxs-lookup"><span data-stu-id="ab514-119">A second orchestration receives the message and sends it back.</span></span> <span data-ttu-id="ab514-120">這樣在協調流程 A 中的傳送分支，就有可能會在接收分支之前收到鎖定，而您將會面臨鎖死的狀況。</span><span class="sxs-lookup"><span data-stu-id="ab514-120">It is possible that the sending branch in orchestration A will receive its locks before the receiving branch, and you will end up with a deadlock.</span></span>  
  
## <a name="nesting-of-scopes"></a><span data-ttu-id="ab514-121">巢狀範圍</span><span class="sxs-lookup"><span data-stu-id="ab514-121">Nesting of scopes</span></span>  
 <span data-ttu-id="ab514-122">您可以巢狀**範圍**圖形內部其他**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="ab514-122">You can nest **Scope** shapes inside other **Scope** shapes.</span></span> <span data-ttu-id="ab514-123">巢狀範圍的規則如下：</span><span class="sxs-lookup"><span data-stu-id="ab514-123">The rules for nesting scopes are as follows:</span></span>  
  
-   <span data-ttu-id="ab514-124">交易式和 (或) 同步處理的範圍，都不能放在同步處理範圍 (包括同步處理範圍的例外狀況處理常式) 的巢狀內。</span><span class="sxs-lookup"><span data-stu-id="ab514-124">Transactional and/or synchronized scopes cannot be nested inside synchronized scopes, including the exception handlers of synchronized scopes.</span></span>  
  
-   <span data-ttu-id="ab514-125">不可部分完成的交易範圍無法在其中具有其他任何巢狀的交易式範圍。</span><span class="sxs-lookup"><span data-stu-id="ab514-125">Atomic transaction scopes cannot have any other transactional scopes nested inside them.</span></span>  
  
-   <span data-ttu-id="ab514-126">交易式範圍不能位於非交易式範圍或協調流程內的巢狀。</span><span class="sxs-lookup"><span data-stu-id="ab514-126">Transactional scopes cannot be nested inside nontransactional scopes or orchestrations.</span></span>  
  
-   <span data-ttu-id="ab514-127">您可以巢狀範圍最多 21 個層級深度。</span><span class="sxs-lookup"><span data-stu-id="ab514-127">You can nest scopes up to 21 levels deep.</span></span>  
  
-   <span data-ttu-id="ab514-128">**呼叫協調流程**圖形可以包含在範圍內，但呼叫的協調流程會被視為與任何其他相同巢狀交易，並套用相同的規則。</span><span class="sxs-lookup"><span data-stu-id="ab514-128">**Call Orchestration** shapes can be included inside scopes, but the called orchestrations are treated the same as any other nested transaction, and the same rules apply.</span></span>  
  
-   <span data-ttu-id="ab514-129">**啟動協調流程**圖形可以包含在範圍內。</span><span class="sxs-lookup"><span data-stu-id="ab514-129">**Start Orchestration** shapes can be included inside scopes.</span></span> <span data-ttu-id="ab514-130">巢狀限制並不適用於啟動的協調流程。</span><span class="sxs-lookup"><span data-stu-id="ab514-130">Nesting limitations do not apply to started orchestrations.</span></span>  
  
## <a name="scope-variables"></a><span data-ttu-id="ab514-131">範圍變數</span><span class="sxs-lookup"><span data-stu-id="ab514-131">Scope variables</span></span>  
 <span data-ttu-id="ab514-132">您可以在範圍層級宣告如訊息和相互關聯集合一類的變數。</span><span class="sxs-lookup"><span data-stu-id="ab514-132">You can declare variables such as messages and correlation sets at the scope level.</span></span> <span data-ttu-id="ab514-133">您不能對範圍變數使用與協調流程變數相同的名稱，而且，也不允許隱藏名稱。</span><span class="sxs-lookup"><span data-stu-id="ab514-133">You cannot use the same name for a scope variable as for an orchestration variable, however; name hiding is not allowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab514-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab514-134">See Also</span></span>  
 <span data-ttu-id="ab514-135">[使用交易和例外狀況處理](../core/using-transactions-and-handling-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="ab514-135">[Using Transactions and Handling Exceptions](../core/using-transactions-and-handling-exceptions.md) </span></span>  
 [<span data-ttu-id="ab514-136">不可部分完成交易</span><span class="sxs-lookup"><span data-stu-id="ab514-136">Atomic Transactions</span></span>](../core/atomic-transactions.md)