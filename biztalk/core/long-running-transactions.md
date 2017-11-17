---
title: "長時間執行交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- long-running transactions, about long-running transactions
- atomic transactions, long-running transactions
- long-running transactions, orchestrations
- long-running transactions, nesting
- scopes, examples
- orchestrations, transactions
- compensations, long-running transactions
- compensations, customizing
- transactions, long-running
- transactions, compensation blocks
- long-running transactions
- long-running transactions, timeouts
- compensations, examples
- fault tolerance, long-running transactions
- transactions, examples
- orchestrations, long-running transactions
- transactions, atomic
- transactions, fault tolerance
- scopes, long-running transactions
- long-running transactions, fault tolerance
- transactions, nesting
- examples, scopes
ms.assetid: 4bf4d0c8-903a-411f-963b-bd4cfdfc2958
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86c419c79b9de6287a0361dfe4e2e6b9dc555153
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="long-running-transactions"></a><span data-ttu-id="07ac2-102">長時間執行的交易</span><span class="sxs-lookup"><span data-stu-id="07ac2-102">Long-Running Transactions</span></span>
<span data-ttu-id="07ac2-103">長時間執行的交易是在 BizTalk 協調流程中重要並經常使用的建構。</span><span class="sxs-lookup"><span data-stu-id="07ac2-103">Long-running transactions are important, commonly used constructs in BizTalk orchestrations.</span></span> <span data-ttu-id="07ac2-104">這類交易提供您進行自訂範圍補償、自訂範圍例外狀況處理，以及巢狀交易能力的設備，這些全都會提供您設計健全交易架構的大量彈性。</span><span class="sxs-lookup"><span data-stu-id="07ac2-104">They provide you with facilities for custom scope-based compensation, custom scope-based exception handling, and the ability to nest transactions, all of which give you great flexibility in designing robust transaction architecture.</span></span>  
  
 <span data-ttu-id="07ac2-105">當交易需要執行極長的時間，而且您不需要完整的 ACID 屬性時 (也就是說，您不需要保證資料與其他交易隔離)，您就會使用長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="07ac2-105">You use a long-running transaction when the transaction might need to run for an extended time and you do not need full ACID properties (that is, you do not need to guarantee isolation of data from other transactions).</span></span> <span data-ttu-id="07ac2-106">長時間執行的交易可能會有長期無活動的情況，這通常都是因為在等候外部訊息抵達。</span><span class="sxs-lookup"><span data-stu-id="07ac2-106">A long-running transaction might have long periods of inactivity, often due to waiting for external messages to arrive.</span></span>  
  
 <span data-ttu-id="07ac2-107">長時間執行的交易具有一致性與持久性，不過卻沒有不可部分完成性與隔離性。</span><span class="sxs-lookup"><span data-stu-id="07ac2-107">Long-running transactions possess consistency, and durability, but not atomicity and isolation.</span></span> <span data-ttu-id="07ac2-108">長時間執行交易內的資料不會被鎖定，因此其他處理序或應用程式都能加以修改。</span><span class="sxs-lookup"><span data-stu-id="07ac2-108">The data within a long-running transaction is not locked; other processes or applications can modify it.</span></span> <span data-ttu-id="07ac2-109">由於長時間保留鎖定不切實際，因此不會維護狀態更新的隔離屬性。</span><span class="sxs-lookup"><span data-stu-id="07ac2-109">The isolation property for state updates is not maintained because holding locks for a long duration is impractical.</span></span>  
  
 <span data-ttu-id="07ac2-110">長時間執行交易的認可與不可部分執行交易的認可不同。</span><span class="sxs-lookup"><span data-stu-id="07ac2-110">Commitment of a long-running transaction is different than commitment of an atomic transaction.</span></span> <span data-ttu-id="07ac2-111">對於結果，並沒有分散式協調的隱含假設 (長時間執行的交易只會存在於單一的協調流程執行個體中)。</span><span class="sxs-lookup"><span data-stu-id="07ac2-111">There is no implicit assumption of distributed coordination regarding the outcome (a long-running transaction exists only within a single orchestration instance).</span></span> <span data-ttu-id="07ac2-112">而是在完成長時間執行交易的最後一個陳述式時，便會被視為已認可。</span><span class="sxs-lookup"><span data-stu-id="07ac2-112">Instead, a long-running transaction is considered committed when the last statement in it has completed.</span></span> <span data-ttu-id="07ac2-113">在交易中止的情況下，不會有狀態的「自動」復原。</span><span class="sxs-lookup"><span data-stu-id="07ac2-113">There is no "auto" rollback of state in case of a transaction abort.</span></span> <span data-ttu-id="07ac2-114">您可以透過例外狀況和補償處理常式，以程式設計方式來達成這點。</span><span class="sxs-lookup"><span data-stu-id="07ac2-114">You can achieve this programmatically through the exception and compensation handlers.</span></span>  
  
 <span data-ttu-id="07ac2-115">範圍可以藉由宣告變數、訊息和 .NET 組件，來定義自己的狀態。</span><span class="sxs-lookup"><span data-stu-id="07ac2-115">A scope can define its own state by declaring variables, messages, and .NET components.</span></span> <span data-ttu-id="07ac2-116">長時間執行的交易可存取自己範圍的狀態資訊、封閉該交易的任何範圍，以及在協調流程中全域定義的任何狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="07ac2-116">A long-running transaction has access to the state information of its own scope, any scope that encloses it, and any state information that is globally defined within the orchestration.</span></span> <span data-ttu-id="07ac2-117">對於未封閉該交易的任何範圍，則是無法存取其狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="07ac2-117">It does not have access to the state information of any scopes that do not enclose it.</span></span>  
  
## <a name="nesting"></a><span data-ttu-id="07ac2-118">巢狀</span><span class="sxs-lookup"><span data-stu-id="07ac2-118">Nesting</span></span>  
 <span data-ttu-id="07ac2-119">長時間執行的交易可以包含不可部分完成的交易和其他長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="07ac2-119">Long-running transactions can contain atomic transactions or other long-running transactions.</span></span> <span data-ttu-id="07ac2-120">它們也可以位於任意深度的巢狀中。</span><span class="sxs-lookup"><span data-stu-id="07ac2-120">They can be nested to arbitrary depths.</span></span> <span data-ttu-id="07ac2-121">例如，您的交易可能包含兩個其他的長時間執行交易，其中每個都包含不可部分完成的交易。</span><span class="sxs-lookup"><span data-stu-id="07ac2-121">For example, your transaction might contain two other long-running transactions, each of which might contain atomic transactions.</span></span>  
  
 <span data-ttu-id="07ac2-122">當整體交易的一個或多個元件需要是不可部分完成，而整體交易則需要是長時間執行時，巢狀尤其有用。</span><span class="sxs-lookup"><span data-stu-id="07ac2-122">Nesting is particularly useful when one or more components of the overall transaction need to be atomic while the overall transaction needs to be long-running.</span></span> <span data-ttu-id="07ac2-123">請考量接收和履行採購單的範例。</span><span class="sxs-lookup"><span data-stu-id="07ac2-123">Consider the example of receiving and fulfilling a purchase order.</span></span> <span data-ttu-id="07ac2-124">採購單可以在任何時刻抵達，而且履行採購單的各種步驟都需要花費時間進行，不過您仍然會將整個程序視為交易。</span><span class="sxs-lookup"><span data-stu-id="07ac2-124">The purchase order can arrive at any time, and the various steps in fulfilling the order might take time to occur, but you still want to treat the entire process as a transaction.</span></span> <span data-ttu-id="07ac2-125">在此情況下，整體的交易很清楚地必須是長時間執行的，不過個別的步驟 (例如，付款的通知)，則需要是不可部分完成的。</span><span class="sxs-lookup"><span data-stu-id="07ac2-125">The overall transaction in this case clearly needs to be long-running, but an individual step, such as acknowledging a payment, might need to be atomic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07ac2-126">您無法將交易範圍放在非交易式範圍或協調流程的巢狀中。</span><span class="sxs-lookup"><span data-stu-id="07ac2-126">You cannot nest a transactional scope within a scope or orchestration that is not transactional.</span></span> <span data-ttu-id="07ac2-127">非交易式的封閉範圍或協調流程將不會管理狀態，因為它必須適當地處理其中任何範圍的狀態管理。</span><span class="sxs-lookup"><span data-stu-id="07ac2-127">An enclosing scope or orchestration that is not transactional will not manage state, as it must to properly handle the state management of any scopes within it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07ac2-128">已同步的交易不得包含其他任何交易或已同步的範圍。</span><span class="sxs-lookup"><span data-stu-id="07ac2-128">A synchronized transaction cannot include any other transactions or synchronized scopes.</span></span>  
  
## <a name="compensation"></a><span data-ttu-id="07ac2-129">補償</span><span class="sxs-lookup"><span data-stu-id="07ac2-129">Compensation</span></span>  
 <span data-ttu-id="07ac2-130">長時間執行的交易可以指定補償區塊，在認可後便會呼叫該區塊以補償交易的活動。</span><span class="sxs-lookup"><span data-stu-id="07ac2-130">A long-running transaction can specify a compensation block that will be called to compensate for the transaction's activities, after it commits.</span></span> <span data-ttu-id="07ac2-131">這樣可能會在可行時使交易復原，或是執行其他功能 (例如通知)，以協助用某些方式緩和交易的效果。</span><span class="sxs-lookup"><span data-stu-id="07ac2-131">It might simply undo the transaction where feasible, or perform some other function, such as notification, that helps mitigate the effects of the transaction in some way.</span></span> <span data-ttu-id="07ac2-132">如果您沒有新增自己的補償程式碼，執行階段引擎便會根據預設，以相反的順序，從最後認可的交易開始，並在第一個認可的交易結束，呼叫內部交易的補償區塊 (包括長時間執行與不可部分執行的區塊)。</span><span class="sxs-lookup"><span data-stu-id="07ac2-132">If you do not add your own compensation code, the runtime engine will by default call the compensation blocks of the inner transactions, both long-running and atomic, in reverse order, starting with the last transaction committed and finishing with the first transaction committed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07ac2-133">補償只能在已經成功認可的交易上進行。</span><span class="sxs-lookup"><span data-stu-id="07ac2-133">Compensation can only be done on a transaction that has committed successfully.</span></span>  
  
## <a name="fault-tolerance"></a><span data-ttu-id="07ac2-134">容錯</span><span class="sxs-lookup"><span data-stu-id="07ac2-134">Fault tolerance</span></span>  
 <span data-ttu-id="07ac2-135">交易支援容錯，以便從內部錯誤 (例如電腦故障和軟體錯誤) 和外部錯誤 (例如取消訊息) 復原。</span><span class="sxs-lookup"><span data-stu-id="07ac2-135">Transactions support fault tolerance for recovery from both internal faults (such as machine failures and software faults) and external faults (such as cancel messages).</span></span> <span data-ttu-id="07ac2-136">發生交易失敗時，長時間執行交易的部份更新並不會自動復原，因為這些都在 ACID 交易中。</span><span class="sxs-lookup"><span data-stu-id="07ac2-136">Partial updates within long-running transactions are not rolled back automatically when a transaction failure occurs, as they are in ACID transactions.</span></span>  
  
 <span data-ttu-id="07ac2-137">當發生錯誤時，便會呼叫長時間執行交易的例外狀況程式碼區塊。</span><span class="sxs-lookup"><span data-stu-id="07ac2-137">The exception code block for the long-running transaction is called when a fault occurs.</span></span> <span data-ttu-id="07ac2-138">例外狀況程式碼區塊包含一組錯誤的處理常式，讓您能夠撰寫以處理可能在執行交易期間引發的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="07ac2-138">The exception code block contains a set of fault handlers that you write to deal with any of the faults that can arise during the execution of the transaction.</span></span> <span data-ttu-id="07ac2-139">在處理錯誤時，您可以依靠訊息、變數和物件的最後已知狀態。</span><span class="sxs-lookup"><span data-stu-id="07ac2-139">You can rely on the last known state of the messages, variables, and objects in handling the fault.</span></span>  
  
 <span data-ttu-id="07ac2-140">當例外狀況發生時，您通常會讓例外狀況處理常式評估協調流程的狀態，根據該狀態採取任何所需的動作，並呼叫任何巢狀交易的補償。</span><span class="sxs-lookup"><span data-stu-id="07ac2-140">You will typically want your exception handler to evaluate the state of the orchestration at the time the exception occurs, take any necessary action based on that state, and call the compensations of any nested transactions.</span></span>  
  
 <span data-ttu-id="07ac2-141">發生錯誤時，會中斷長時間執行之交易的執行。</span><span class="sxs-lookup"><span data-stu-id="07ac2-141">The execution of the long-running transaction is interrupted when a fault occurs.</span></span> <span data-ttu-id="07ac2-142">發生錯誤後便無法繼續執行。</span><span class="sxs-lookup"><span data-stu-id="07ac2-142">It cannot be resumed after a fault occurs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ac2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07ac2-143">See Also</span></span>  
 <span data-ttu-id="07ac2-144">[使用長時間執行交易的案例](../core/scenarios-using-long-running-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="07ac2-144">[Scenarios Using Long-Running Transactions](../core/scenarios-using-long-running-transactions.md) </span></span>  
 <span data-ttu-id="07ac2-145">[不可部分完成交易](../core/atomic-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="07ac2-145">[Atomic Transactions](../core/atomic-transactions.md) </span></span>  
 [<span data-ttu-id="07ac2-146">使用交易和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="07ac2-146">Using Transactions and Handling Exceptions</span></span>](../core/using-transactions-and-handling-exceptions.md)