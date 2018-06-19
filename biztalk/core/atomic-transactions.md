---
title: 不可部分完成交易 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- atomic transactions
- scopes, examples
- transactions, orchestrations
- orchestrations, transactions
- transactions, isolation levels
- transactions, ACID concept
- transactions, examples
- transactions, atomic
- scopes, transactions
- scopes
ms.assetid: 5030e1fd-943f-42bc-9296-4f315bd5f733
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc07f379c1f7aa1c846b2c20c19cbfb3393e8174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22233542"
---
# <a name="atomic-transactions"></a><span data-ttu-id="c1c54-102">不可部分完成交易</span><span class="sxs-lookup"><span data-stu-id="c1c54-102">Atomic Transactions</span></span>
<span data-ttu-id="c1c54-103">BizTalk 協調流程的設計按照傳統的 'ACID' 交易概念，可執行離散的工作片段。</span><span class="sxs-lookup"><span data-stu-id="c1c54-103">BizTalk orchestrations can be designed to run discrete pieces of work, following the classic 'ACID' concept of a transaction.</span></span> <span data-ttu-id="c1c54-104">當執行這些離散或不可部分完成的工作單位時，便會將商務程序從一個一致的狀態移到新的一致、耐用狀態，而且該狀態會是與其他工作單位隔離的。</span><span class="sxs-lookup"><span data-stu-id="c1c54-104">These discrete or atomic units of work, when performed, move the business process from one consistent state to a new, consistent and durable state that is isolated from other units of work.</span></span> <span data-ttu-id="c1c54-105">這通常是使用**範圍**建構封裝使用交易式語意的單位。</span><span class="sxs-lookup"><span data-stu-id="c1c54-105">This is typically done by using the **Scope** construct that encapsulates the units of work with the transactional semantics.</span></span> <span data-ttu-id="c1c54-106">整個協調流程也可以定義為不可部分完成的交易，而不需要使用範圍。</span><span class="sxs-lookup"><span data-stu-id="c1c54-106">The entire orchestration can also be defined as an atomic transaction without the use of scopes.</span></span> <span data-ttu-id="c1c54-107">不過，除非協調流程本身被標記為長時間執行或不可部分完成的交易類型，否則不能將範圍標記為交易式的。</span><span class="sxs-lookup"><span data-stu-id="c1c54-107">The scopes, however, cannot be marked as transactional unless the orchestration itself is marked as a long running or atomic transaction type.</span></span> <span data-ttu-id="c1c54-108">不可部分完成的交易可保證任何部分更新在交易更新期間作業失敗時都會自動復原，且會清除交易的結果 (在交易中進行的任何 .NET 呼叫結果除外)。</span><span class="sxs-lookup"><span data-stu-id="c1c54-108">Atomic transactions guarantee that any partial updates are rolled back automatically in the event of a failure during the transactional update, and that the effects of the transaction are erased (except for the effects of any .NET calls that are made in the transaction).</span></span> <span data-ttu-id="c1c54-109">在 BizTalk 協調流程中的不可部分完成交易與分散式交易協調器 (DTC) 交易的相似處在於，它們通常都是短時間的，而且都具有四個「ACID」屬性 (不可部分完成性、一致性、隔離性與耐用性)：</span><span class="sxs-lookup"><span data-stu-id="c1c54-109">Atomic transactions in BizTalk orchestrations are similar to distributed transaction coordinator (DTC) transactions in that they are generally short-lived and have the four "ACID" attributes (atomicity, consistency, isolation, and durability):</span></span>  
  
-   <span data-ttu-id="c1c54-110">**不可部分完成性**</span><span class="sxs-lookup"><span data-stu-id="c1c54-110">**Atomicity**</span></span>  
  
     <span data-ttu-id="c1c54-111">交易代表不可部分完成的工作單位。</span><span class="sxs-lookup"><span data-stu-id="c1c54-111">A transaction represents an atomic unit of work.</span></span> <span data-ttu-id="c1c54-112">會執行交易內的所有修改，或是不會執行任何修改。</span><span class="sxs-lookup"><span data-stu-id="c1c54-112">Either all modifications within a transaction are performed, or none of the modifications are performed.</span></span>  
  
-   <span data-ttu-id="c1c54-113">**一致性**</span><span class="sxs-lookup"><span data-stu-id="c1c54-113">**Consistency**</span></span>  
  
     <span data-ttu-id="c1c54-114">在認可時，交易必須保持系統內資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="c1c54-114">When committed, a transaction must preserve the integrity of the data within the system.</span></span> <span data-ttu-id="c1c54-115">如果交易對資料庫執行資料修改，而在交易開始前該資料庫的內部是一致的，在交易認可後，該資料庫內部必須依然是一致的。</span><span class="sxs-lookup"><span data-stu-id="c1c54-115">If a transaction performs a data modification on a database that was internally consistent before the transaction started, the database must still be internally consistent when the transaction is committed.</span></span> <span data-ttu-id="c1c54-116">確認這個屬性大部分都是應用程式開發人員的責任。</span><span class="sxs-lookup"><span data-stu-id="c1c54-116">Ensuring this property is largely the responsibility of the application developer.</span></span>  
  
-   <span data-ttu-id="c1c54-117">**隔離性**</span><span class="sxs-lookup"><span data-stu-id="c1c54-117">**Isolation**</span></span>  
  
     <span data-ttu-id="c1c54-118">由並行的交易所做的修改，都必須與其他並行交易所做的修改隔離。</span><span class="sxs-lookup"><span data-stu-id="c1c54-118">Modifications made by concurrent transactions must be isolated from the modifications made by other concurrent transactions.</span></span> <span data-ttu-id="c1c54-119">並行執行的隔離交易會保留內部資料庫的一致性，使其與依序執行交易的情況完全相同。</span><span class="sxs-lookup"><span data-stu-id="c1c54-119">Isolated transactions that run concurrently perform modifications that preserve internal database consistency exactly as they would if the transactions were run serially.</span></span>  
  
-   <span data-ttu-id="c1c54-120">**持久性**</span><span class="sxs-lookup"><span data-stu-id="c1c54-120">**Durability**</span></span>  
  
     <span data-ttu-id="c1c54-121">根據預設，在認可交易後，所有的修改便會永遠留在系統中。</span><span class="sxs-lookup"><span data-stu-id="c1c54-121">After a transaction is committed, all modifications are permanently in place in the system by default.</span></span> <span data-ttu-id="c1c54-122">即使發生系統故障，這些修改依然會保存。</span><span class="sxs-lookup"><span data-stu-id="c1c54-122">The modifications persist even if a system failure occurs.</span></span>  
  
 <span data-ttu-id="c1c54-123">在 BizTalk 協調流程中使用的不可部分完成交易支援下列隔離等級：</span><span class="sxs-lookup"><span data-stu-id="c1c54-123">The following isolation levels are supported by the atomic transactions used in BizTalk Orchestrations:</span></span>  
  
-   <span data-ttu-id="c1c54-124">**讀取認可**</span><span class="sxs-lookup"><span data-stu-id="c1c54-124">**Read Committed**</span></span>  
  
     <span data-ttu-id="c1c54-125">當正在讀取資料以避免修改讀取時，會保留共用鎖定，但是在交易結束之前可以變更資料，這會造成非重複讀取或虛設資料。</span><span class="sxs-lookup"><span data-stu-id="c1c54-125">Shared locks are held while the data is being read to avoid dirty reads, but the data can be changed before the end of the transaction, resulting in non-repeatable reads or phantom data.</span></span>  
  
-   <span data-ttu-id="c1c54-126">**可重複讀取**</span><span class="sxs-lookup"><span data-stu-id="c1c54-126">**Repeatable Read**</span></span>  
  
     <span data-ttu-id="c1c54-127">鎖定會放置在查詢中使用的所有資料上，以防止其他使用者更新資料。</span><span class="sxs-lookup"><span data-stu-id="c1c54-127">Locks are placed on all data that is used in a query, preventing other users from updating the data.</span></span> <span data-ttu-id="c1c54-128">這樣便會防止非重複的讀取，但虛設資料列仍有可能發生。</span><span class="sxs-lookup"><span data-stu-id="c1c54-128">This prevents non-repeatable reads, but phantom rows are still possible.</span></span>  
  
-   <span data-ttu-id="c1c54-129">**可序列化**</span><span class="sxs-lookup"><span data-stu-id="c1c54-129">**Serializable**</span></span>  
  
     <span data-ttu-id="c1c54-130">會放置範圍鎖定，以防止其他使用者在交易完成前將資料列更新或插入資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1c54-130">A range lock is placed preventing other users from updating or inserting rows into the database until the transaction is complete.</span></span>  
  
 <span data-ttu-id="c1c54-131">BizTalk Server 會確認不可部分完成交易內的狀態變更 (例如變數、訊息及物件的修改) 只有在認可交易時，才會在不可部分完成交易的範圍外看到。</span><span class="sxs-lookup"><span data-stu-id="c1c54-131">BizTalk Server ensures that state changes within an atomic transaction—such as modifications to variables, messages, and objects—are visible outside the scope of the atomic transaction only upon commitment of the transaction.</span></span> <span data-ttu-id="c1c54-132">中繼狀態變更是與協調流程的其他部分隔離的。</span><span class="sxs-lookup"><span data-stu-id="c1c54-132">The intermediate state changes are isolated from other parts of an orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c54-133">如果不可部分完成交易包含**接收**圖形，**傳送**圖形，或**啟動協調流程**圖形，對應的動作不會進行直到已認可交易。</span><span class="sxs-lookup"><span data-stu-id="c1c54-133">If an atomic transaction contains a **Receive** shape, a **Send** shape, or a **Start Orchestration** shape, the corresponding actions will not take place until the transaction has committed.</span></span>  
  
 <span data-ttu-id="c1c54-134">如果您需要資料具有完整的 ACID 屬性 (例如，當資料必須與其他交易隔離時)，您必須專門使用不可部分完成的交易。</span><span class="sxs-lookup"><span data-stu-id="c1c54-134">If you require full ACID properties on the data—for example, when the data must be isolated from other transactions—you must use atomic transactions exclusively.</span></span>  
  
 <span data-ttu-id="c1c54-135">當不可部分完成的交易失敗時，所有的狀態都會重設，就像是協調流程執行個體從未進入範圍。</span><span class="sxs-lookup"><span data-stu-id="c1c54-135">When an atomic transaction fails, all states are reset as if the orchestration instance never entered the scope.</span></span> <span data-ttu-id="c1c54-136">BizTalk 對於不可部分完成交易所施加的規則為：所有的變數 (不只是範圍的區域變數) 都會參與交易。</span><span class="sxs-lookup"><span data-stu-id="c1c54-136">The rule BizTalk has for atomic transactions is that all variables (not just local to the scope) participate in the transaction.</span></span> <span data-ttu-id="c1c54-137">在不可部分完成交易中使用的所有不可序列化變數和訊息，都應該在範圍的區域內宣告。否則，編譯器就會顯示「變數….未標記為可序列化」錯誤。</span><span class="sxs-lookup"><span data-stu-id="c1c54-137">All non-serializable variables and messages used in an atomic transaction should be declared local to the scope; otherwise, the compiler will give the "variable….is not marked as serializable" error.</span></span> <span data-ttu-id="c1c54-138">對於所有不可部分完成的範圍都會假定為「已同步」，如果的確會在不可部分完成的範圍使用 Synchronized 關鍵字，協調流程編譯器便會提供多餘使用的警告。</span><span class="sxs-lookup"><span data-stu-id="c1c54-138">All atomic scopes are assumed to be "synchronized" and the orchestration compiler will provide a warning for redundant usage, if indeed the synchronized keyword is used for atomic scopes.</span></span> <span data-ttu-id="c1c54-139">共用資料的同步處理會從範圍的開頭延伸，直到範圍的成功完成 (包括在範圍結尾的狀態持續性)，或是直到例外狀況處理常式的完成部分 (如果發生錯誤)。</span><span class="sxs-lookup"><span data-stu-id="c1c54-139">The synchronization for the shared data extends from the beginning of the scope until the successful completion of the scope (including the state persistence at the end of the scope) or to the completion of the exception handler (in case of errors).</span></span> <span data-ttu-id="c1c54-140">同步處理的網域不會延伸到補償處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1c54-140">The synchronization domain does not extend to the compensation handler.</span></span>  
  
 <span data-ttu-id="c1c54-141">不可部分完成的交易可以與逾時值關聯，協調流程會在該點停止交易，並且會擱置執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1c54-141">Atomic transactions can be associated with timeout values at which point the orchestration will stop the transaction and the instance will be suspended.</span></span> <span data-ttu-id="c1c54-142">如果不可部分完成交易包含「接收」 圖形、「傳送」圖形或「啟動協調流程」圖形，在已經認可交易之前，不會發生對應的動作。</span><span class="sxs-lookup"><span data-stu-id="c1c54-142">If an atomic transaction contains a Receive shape, a Send shape, or a Start Orchestration shape, the corresponding actions will not take place until the transaction has committed.</span></span>  
  
 <span data-ttu-id="c1c54-143">不可部分完成的交易重試時使用者蓄意擲回**RetryTransactionException**或**PersistenceException**在不可部分完成交易嘗試認可的時間時引發。</span><span class="sxs-lookup"><span data-stu-id="c1c54-143">An atomic transaction retries when the user deliberately throws a **RetryTransactionException** or if a **PersistenceException** is raised at the time that the atomic transaction tries to commit.</span></span> <span data-ttu-id="c1c54-144">例如，如果不可部分完成的交易是分散式 DTC 交易的一部分，而且該交易的其他一些參與者已經停止交易時，後者便有可能發生。</span><span class="sxs-lookup"><span data-stu-id="c1c54-144">The latter could happen if for instance, the atomic transaction was part of a distributed DTC transaction and some other participant in that transaction stopped the transaction.</span></span> <span data-ttu-id="c1c54-145">同樣地，如果有個資料庫連線問題，當交易嘗試認可時，也有**PersistenceException**引發。</span><span class="sxs-lookup"><span data-stu-id="c1c54-145">Likewise, if there were database connectivity problems at the time when the transaction was trying to commit, there would also be a **PersistenceException** raised.</span></span> <span data-ttu-id="c1c54-146">如果這種情況具有不可部分完成範圍**重試 = True**，便會重試多達 21 次。</span><span class="sxs-lookup"><span data-stu-id="c1c54-146">If this happens for an atomic scope that has **Retry=True**, then it will retry up to 21 times.</span></span> <span data-ttu-id="c1c54-147">根據預設，每次重試之間的延遲為兩秒鐘 (不過該值是可修改的)。</span><span class="sxs-lookup"><span data-stu-id="c1c54-147">The delay between each retry is two seconds by default (but that is modifiable).</span></span> <span data-ttu-id="c1c54-148">在耗盡 21 次重試之後，如果依然無法認可交易，便會擱置整個協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1c54-148">After 21 retries are exhausted, if the transaction is still unable to commit, the whole orchestration instance is suspended.</span></span> <span data-ttu-id="c1c54-149">使用手動方式即可繼續協調流程，而且協調流程會用全新的計數器，在產生問題的不可部分完成範圍從頭開始。</span><span class="sxs-lookup"><span data-stu-id="c1c54-149">It can be manually resumed and it will start over again, with a fresh counter, from the beginning of the offending atomic scope.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c54-150">只有**RetryTransactionException**和**PersistenceException**可能會造成不可部分完成的範圍重試。</span><span class="sxs-lookup"><span data-stu-id="c1c54-150">Only the **RetryTransactionException** and **PersistenceException** can cause an atomic scope to retry.</span></span> <span data-ttu-id="c1c54-151">在不可部分完成的範圍中引發的其他任何例外狀況不會導致重試，即使**重試**屬性設定為**True**。</span><span class="sxs-lookup"><span data-stu-id="c1c54-151">Any other exception raised in an atomic scope cannot cause it to retry, even if the **Retry** property is set to **True**.</span></span> <span data-ttu-id="c1c54-152">每兩個連續重試之間的兩秒預設延遲會覆寫上使用的公用屬性**RetryTransactionException** （如果這是用來造成重試的例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="c1c54-152">The two-second default delay between each two consecutive retries can be overridden by using a public property on **RetryTransactionException** (if that is the exception that is being used to cause the retries).</span></span>  
  
 <span data-ttu-id="c1c54-153">不可部分完成的範圍有限制其他交易無法巢狀其他交易，或包含巢狀方式置於**Catch-Exception**區塊。</span><span class="sxs-lookup"><span data-stu-id="c1c54-153">The atomic scopes have restrictions on nesting other transactions that cannot nest other transactions or include **Catch - Exception** blocks.</span></span>  
  
## <a name="dtc-transactions"></a><span data-ttu-id="c1c54-154">DTC 交易</span><span class="sxs-lookup"><span data-stu-id="c1c54-154">DTC transactions</span></span>  
 <span data-ttu-id="c1c54-155">儘管不可部分完成交易的行為與 DTC 交易相像，根據預設，這類交易卻不是明確的 DTC 交易。</span><span class="sxs-lookup"><span data-stu-id="c1c54-155">While atomic transactions behave like DTC transactions, they are not explicitly DTC transactions by default.</span></span> <span data-ttu-id="c1c54-156">您可以使這類交易明確成為 DTC 交易，其條件為交易中使用的任何物件都是衍生自 System.EnterpriseServices.ServicedComponents 的 COM+ 物件，而且在交易元件之間的隔離層級也都相符。</span><span class="sxs-lookup"><span data-stu-id="c1c54-156">You can explicitly make them DTC transactions, provided that any objects being used in the transaction are COM+ objects derived from System.EnterpriseServices.ServicedComponents, and that isolation levels agree between transaction components.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c54-157">不可部分完成的交易無法在內部包含其他任何交易，也無法包含例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1c54-157">An atomic transaction cannot contain any other transactions within it, nor can it contain exception handlers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c54-158">如果不可部分完成的交易包含相符的傳送與接收動作，也就是「要求-回應」組，或是使用相同相互關聯集合的傳送與接收。</span><span class="sxs-lookup"><span data-stu-id="c1c54-158">An atomic transaction cannot contain matching send and receive actions—that is, a request-response pair or a send and receive that use the same correlation set.</span></span>  
  
## <a name="non-serializable-objects"></a><span data-ttu-id="c1c54-159">不可序列化物件</span><span class="sxs-lookup"><span data-stu-id="c1c54-159">Non-serializable objects</span></span>  
 <span data-ttu-id="c1c54-160">如果您要在協調流程內使用不可序列化物件，就必須只在不可部分完成的交易內使用該物件。</span><span class="sxs-lookup"><span data-stu-id="c1c54-160">If you want to use a non-serializable object within an orchestration, you must use it only within an atomic transaction.</span></span> <span data-ttu-id="c1c54-161">每當協調流程由引擎所保存時，在不可部分完成交易外使用任何這類物件都必須承擔資料損失的風險。</span><span class="sxs-lookup"><span data-stu-id="c1c54-161">Any use of such an object outside of an atomic transaction risks data loss whenever the orchestration is persisted by the engine.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c1c54-162">每個「不可部分完成」的範圍都代表一個持續點，而且這表示在每個持續點都會將協調流程的狀態儲存到資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c1c54-162">Each Atomic scope represents a persistence point and what that means is the state of the orchestration is saved to the database at each persistence point.</span></span> <span data-ttu-id="c1c54-163">「不可部分完成」範圍的大量使用，將會增加協調流程中的延遲情況。</span><span class="sxs-lookup"><span data-stu-id="c1c54-163">Extensive use of Atomic scope will increase the latency in the orchestration.</span></span> <span data-ttu-id="c1c54-164">與其使用「不可部分完成」範圍以建立不可序列化物件，您可以使用不需要「不可部分完成」範圍的「靜態」方法呼叫，進而排除持續點的需要。</span><span class="sxs-lookup"><span data-stu-id="c1c54-164">Instead of using Atomic scope for the purpose of creating non-serializable objects, you can use Static method calls which they don not require Atomic scopes, thus eliminating the need for the persistence points.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c54-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1c54-165">See Also</span></span>  
 <span data-ttu-id="c1c54-166">[使用不可部分完成交易的案例](../core/scenarios-using-atomic-transactions.md) </span><span class="sxs-lookup"><span data-stu-id="c1c54-166">[Scenarios Using Atomic Transactions](../core/scenarios-using-atomic-transactions.md) </span></span>  
 [<span data-ttu-id="c1c54-167">長時間執行的交易</span><span class="sxs-lookup"><span data-stu-id="c1c54-167">Long-Running Transactions</span></span>](../core/long-running-transactions.md)