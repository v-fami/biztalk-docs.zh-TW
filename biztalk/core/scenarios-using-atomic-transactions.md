---
title: 使用不可部分完成交易的案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], examples
- Scope shape [Orchestration Designer], atomic transactions
- transactions, examples
- transactions, atomic
- atomic transactions, examples
- examples, atomic transactions
ms.assetid: f3481b4e-7e7e-47f0-b8f4-6012a2fc5310
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e73cfea7a99e2fafbf115a367dbf0840de3369c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270942"
---
# <a name="scenarios-using-atomic-transactions"></a><span data-ttu-id="e3acf-102">使用不可部分完成交易的案例</span><span class="sxs-lookup"><span data-stu-id="e3acf-102">Scenarios Using Atomic Transactions</span></span>
<span data-ttu-id="e3acf-103">下列案例將描述不可部分完成交易的用法。</span><span class="sxs-lookup"><span data-stu-id="e3acf-103">The following scenarios describe the use of atomic transactions.</span></span>  
  
## <a name="scenario-1-an-atomic-transaction-with-com-servicedcomponent"></a><span data-ttu-id="e3acf-104">案例 1: 不可部分完成交易具有 COM + ServicedComponent</span><span class="sxs-lookup"><span data-stu-id="e3acf-104">Scenario 1: An Atomic Transaction with COM+ ServicedComponent</span></span>  
 <span data-ttu-id="e3acf-105">下列的協調流程示範如何使用**RetryTransactionException**不可部分完成交易。</span><span class="sxs-lookup"><span data-stu-id="e3acf-105">The following orchestration shows how to use the **RetryTransactionException** with atomic transactions.</span></span> <span data-ttu-id="e3acf-106">雖然在不可部分完成的範圍中無法直接包含例外狀況處理常式，但該範圍可以包含非交易式的範圍，非交易式的範圍中就可以具備例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="e3acf-106">Although exception handlers cannot be directly included for an atomic scope, the scope can include a non-transactional scope that can have an exception handler.</span></span> <span data-ttu-id="e3acf-107">**ServicedComponent**在相同的 DTC 交易中登記和元件所引發的例外狀況會遭到攔截並重新擲回為**RetryTransactionException**。</span><span class="sxs-lookup"><span data-stu-id="e3acf-107">The **ServicedComponent** enlists in the same DTC transaction and any exception raised by the component is caught and re-thrown as **RetryTransactionException**.</span></span> <span data-ttu-id="e3acf-108">(這是假設**重試**屬性設定為**True**不可部分完成的範圍)。</span><span class="sxs-lookup"><span data-stu-id="e3acf-108">(This assumes that the **Retry** property is set to **True** for the atomic scope).</span></span>  
  
 <span data-ttu-id="e3acf-109">請注意，擱置協調流程會而 MessageAssignment 圖形中的動作會回復即使**RetryTransactionException**不會擲回。</span><span class="sxs-lookup"><span data-stu-id="e3acf-109">Note that the orchestration would have been suspended and the action in the MessageAssignment shape would have been rolled back even if the **RetryTransactionException** is not thrown.</span></span> <span data-ttu-id="e3acf-110">不過，這種模式可以使自動產生重試作業的應用程式更有恢復力。</span><span class="sxs-lookup"><span data-stu-id="e3acf-110">This pattern, however, allows building resilience in the application where the retries occur automatically.</span></span>  
  
 <span data-ttu-id="e3acf-111">**具有 COM + ServicedComponent 的不可部分完成交易**</span><span class="sxs-lookup"><span data-stu-id="e3acf-111">**An atomic transaction with COM+ ServicedComponent**</span></span>  
  
 <span data-ttu-id="e3acf-112">![與 COM &#43; 不可部分完成交易ServicedComponent](../core/media/bts-trans-orch-fig5.gif "BTS_Trans_Orch_Fig5")</span><span class="sxs-lookup"><span data-stu-id="e3acf-112">![An atomic transaction with COM&#43; ServicedComponent](../core/media/bts-trans-orch-fig5.gif "BTS_Trans_Orch_Fig5")</span></span>  
  
## <a name="scenario-2-using-transacted-adapters-with-atomic-transactions"></a><span data-ttu-id="e3acf-113">案例 2： 將交易配接器使用不可部分完成交易</span><span class="sxs-lookup"><span data-stu-id="e3acf-113">Scenario 2: Using Transacted Adapters with Atomic Transactions</span></span>  
 <span data-ttu-id="e3acf-114">下列的協調流程顯示如何以 SQL 配接器使用不可部分完成的交易。</span><span class="sxs-lookup"><span data-stu-id="e3acf-114">The following orchestration shows how to use the atomic transactions with the SQL adapter.</span></span> <span data-ttu-id="e3acf-115">整個協調流程標示為長時間執行個別的不可部分完成交易的兩個邏輯部分的工作： 客戶 插入新的 「 客戶 」 和 「 插入訂單詳細資料。</span><span class="sxs-lookup"><span data-stu-id="e3acf-115">The whole orchestration is marked as long running with individual atomic transactions for the two logical pieces of work: Inserting a new Customer and Insert Order details for the customer.</span></span>  
  
 <span data-ttu-id="e3acf-116">如果訂單插入工作因為任何原因而失敗，則客戶插入工作將會回復。</span><span class="sxs-lookup"><span data-stu-id="e3acf-116">If, for whatever reason, the Order Insert fails, the Customer Insert should be rolled back.</span></span> <span data-ttu-id="e3acf-117">此範例使用 SQL 配接器來執行資料庫作業。</span><span class="sxs-lookup"><span data-stu-id="e3acf-117">The sample uses the SQL adapter to do the database work.</span></span> <span data-ttu-id="e3acf-118">如前所述，與不可部分完成之交易相關的範圍，會在訊息傳送至 MessageBox 資料庫時完成。</span><span class="sxs-lookup"><span data-stu-id="e3acf-118">As mentioned earlier, the scope associated with an atomic transaction completes when the message is sent to the MessageBox database.</span></span> <span data-ttu-id="e3acf-119">這代表當引擎成功傳送 Scope_InsertCustomer 和 Scope_InsertOrder 範圍中的訊息之後，各範圍就會認可。</span><span class="sxs-lookup"><span data-stu-id="e3acf-119">This implies that after the engine is successful in sending the message in the Scope_InsertCustomer and Scope_InsertOrder scopes, each one of the scopes commits.</span></span> <span data-ttu-id="e3acf-120">SQL 配接器會針對客戶或訂單的實際插入工作建立新的交易。</span><span class="sxs-lookup"><span data-stu-id="e3acf-120">The SQL adapter creates a new transaction for the actual Insert of the Customer or the order.</span></span>  
  
 <span data-ttu-id="e3acf-121">連接埠擁有 Delivery Notification 屬性，可驗證訊息已透過傳送埠而成功傳送。</span><span class="sxs-lookup"><span data-stu-id="e3acf-121">The Ports have a property “Delivery Notification” for validating that the message has been successfully sent via the Sent Port.</span></span> <span data-ttu-id="e3acf-122">當 Delivery Notification 屬性設定為 "Transmitted" 時，會在傳送作業的交易認可點之前放置接收訂閱。</span><span class="sxs-lookup"><span data-stu-id="e3acf-122">When the Delivery Notification property is set to “Transmitted”, a receive subscription is placed before the Transactional commit point of the Send Operation.</span></span> <span data-ttu-id="e3acf-123">不過，以不可部分完成的範圍來說，接收訂閱會放在包含此範圍的父範圍中。</span><span class="sxs-lookup"><span data-stu-id="e3acf-123">However, in case of Atomic Scopes, the receive subscription is placed in the enclosing Parent scope.</span></span>  
  
 <span data-ttu-id="e3acf-124">在 InsertOrder SQL 交易失敗的案例中，會傳回 "Nack" 並認可 "Scope_InsertOrder"。</span><span class="sxs-lookup"><span data-stu-id="e3acf-124">In the scenario where the InsertOrder SQL transaction fails, a "Nack" will be sent back and the "Scope_InsertOrder" commits.</span></span> <span data-ttu-id="e3acf-125">在傳送埠耗盡設定的重試次數後，就會引發 DeliveryFailureException。</span><span class="sxs-lookup"><span data-stu-id="e3acf-125">After the Sent Port exhausts the configured retries, a DeliveryFailureException will be raised.</span></span> <span data-ttu-id="e3acf-126">此例外狀況會由預設的例外狀況處理常式所攔截 (該處理常式將執行預設的補償程序)。</span><span class="sxs-lookup"><span data-stu-id="e3acf-126">This exception will be caught by the default exception handler, which will run the default compensation process.</span></span> <span data-ttu-id="e3acf-127">如此將引發與 Scope_InsertCustomer 和 Scope_InsertOrder 相關聯的補償處理常式，導致客戶資訊插入作業復原。</span><span class="sxs-lookup"><span data-stu-id="e3acf-127">This will invoke the compensation handlers associated with the Scope_InsertCustomer and Scope_InsertOrder, causing the undo operation of inserting the customer information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3acf-128">將這兩個範圍巢狀化於長時間執行的範圍中，以及從例外狀況處理常式叫用長時間執行範圍的補償圖形 (目標為長時間執行的交易)，會導致與上述相同的行為。</span><span class="sxs-lookup"><span data-stu-id="e3acf-128">Nesting the two scopes in a long running scope and invoking the Compensate shape (targeting the long running transaction) from the exception handler for the long running scope will result in the same behavior as described above.</span></span> <span data-ttu-id="e3acf-129">您不能將整個協調流程標示為不可部分完成，因為不可部分完成的交易不允許巢狀化交易。</span><span class="sxs-lookup"><span data-stu-id="e3acf-129">The whole orchestration could not be marked atomic as atomic transactions do not allow nested transactions.</span></span>  
  
 <span data-ttu-id="e3acf-130">**不可部分完成交易的交易配接器**</span><span class="sxs-lookup"><span data-stu-id="e3acf-130">**Transacted adapters with atomic transactions**</span></span>  
  
 <span data-ttu-id="e3acf-131">![交易式配接器使用不可部分完成交易](../core/media/bts-trans-orch-fig6.gif "BTS_Trans_Orch_Fig6")</span><span class="sxs-lookup"><span data-stu-id="e3acf-131">![Transacted adapters with atomic transactions](../core/media/bts-trans-orch-fig6.gif "BTS_Trans_Orch_Fig6")</span></span>