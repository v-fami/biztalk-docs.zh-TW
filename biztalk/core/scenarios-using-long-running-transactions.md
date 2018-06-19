---
title: 使用長時間執行交易的案例 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions, long-running
- long-running transactions, timeouts
- transactions, examples
- long-running transactions, examples
- long-running compensations
- examples, long-running transactions
- examples, custom compensations
ms.assetid: 76b3e0f8-44dc-419e-a73a-c2908b1d8795
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05ac14bc6e333f963dda7cb9b33d1ebf371c0546
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269918"
---
# <a name="scenarios-using-long-running-transactions"></a><span data-ttu-id="c1e5d-102">使用長時間執行交易的案例</span><span class="sxs-lookup"><span data-stu-id="c1e5d-102">Scenarios Using Long-Running Transactions</span></span>
<span data-ttu-id="c1e5d-103">下列案例說明長時間執行交易的用途。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-103">The following scenarios describe the use of long running transactions.</span></span>  
  
## <a name="scenario-1-using-long-running-transactions-with-timeouts"></a><span data-ttu-id="c1e5d-104">案例 1： 使用長時間執行交易的逾時</span><span class="sxs-lookup"><span data-stu-id="c1e5d-104">Scenario 1: Using Long Running Transactions with Timeouts</span></span>  
 <span data-ttu-id="c1e5d-105">長時間執行範圍可以和逾時相關聯，這是長時間執行工作必須完成的邏輯時間。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-105">Long running scopes can be associated with a timeout, which is a logical time within which the long-running work must complete.</span></span> <span data-ttu-id="c1e5d-106">如果指定的時間，預先定義的系統例外狀況內沒有完成範圍**TimeoutException** ，就會引發。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-106">If the scope does not complete within the specified time, a pre-defined system exception **TimeoutException** is raised.</span></span>  
  
 <span data-ttu-id="c1e5d-107">您可以將整個協調流程標示為長時間執行，或在外部長時間執行範圍中巢狀處理任何其他範圍，來建立長時間執行程序。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-107">You can create long running processes by either marking the entire orchestration as long running or having an outer long running scope nest any other scopes.</span></span> <span data-ttu-id="c1e5d-108">在前面的案例中，系統提供的例外狀況處理常式會執行，而在後面的案例中，則允許將特定例外狀況處理常式與外部範圍產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-108">In the former scenario, a system-provided exception handler runs, whereas the latter allows associating specific exception handlers to the outer scope.</span></span> <span data-ttu-id="c1e5d-109">系統提供的預設例外狀況處理常式會針對每個順利完成的巢狀交易式範圍 (如果有的話)，以其完成的相反順序，執行補償處理常式。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-109">The default system-provided exception handler will run the compensation handler for each of the successfully completed nested transactional scopes, if any, in reverse order of their completion.</span></span> <span data-ttu-id="c1e5d-110">您可以在長時間執行交易的例外狀況處理常式中使用 [補償] 圖形，透過自我補償達到相同結果。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-110">You can achieve the same through self compensating by using the Compensate shape in the exception handler for a long running transaction.</span></span>  
  
 <span data-ttu-id="c1e5d-111">下列協調流程說明如何將逾時與長時間執行交易產生關聯。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-111">The following orchestration is a representation of how to associate timeouts with long running transactions.</span></span>  
  
 <span data-ttu-id="c1e5d-112">**使用逾時的長時間執行交易**</span><span class="sxs-lookup"><span data-stu-id="c1e5d-112">**Long running transactions with timeouts**</span></span>  
  
 <span data-ttu-id="c1e5d-113">![長時間執行交易的逾時與](../core/media/bts-trans-orch-fig7.gif "BTS_Trans_Orch_Fig7")</span><span class="sxs-lookup"><span data-stu-id="c1e5d-113">![Long running transactions with timeouts](../core/media/bts-trans-orch-fig7.gif "BTS_Trans_Orch_Fig7")</span></span>  
  
 <span data-ttu-id="c1e5d-114">有時候您可能需要與透過批次方式運作的舊有系統互動。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-114">Sometimes you may need to interface with legacy systems that operate in a batch fashion.</span></span> <span data-ttu-id="c1e5d-115">這個案例顯示舊有系統收發訂單。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-115">This scenario shows a purchase order being received and sent to the legacy system.</span></span> <span data-ttu-id="c1e5d-116">舊有系統會處理訂單並傳回訂單通知。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-116">The legacy system processes the purchase order and sends back a purchase order acknowledgement.</span></span> <span data-ttu-id="c1e5d-117">傳送作業會使用訂單編號初始化相互關聯集，並且在該相互關聯集之後發生接收作業。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-117">The send operation initializes a correlation set using the purchase order number and the receive operation follows that correlation set.</span></span> <span data-ttu-id="c1e5d-118">接收作業也位在具有逾時值的長時間執行範圍內。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-118">The receive operation is also in a long running scope with a timeout value.</span></span>  
  
 <span data-ttu-id="c1e5d-119">協調流程引擎會凍結等待接收的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-119">The orchestration engine will dehydrate the orchestration instance waiting for the receive.</span></span> <span data-ttu-id="c1e5d-120">相互關聯會確保在接收訊息之後叫用相同的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-120">The correlation will ensure that the same orchestration instance is invoked after the message is received.</span></span> <span data-ttu-id="c1e5d-121">如果訂單通知未在逾時值，所指定的時間間隔內到達**TimeoutException**就會擲回。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-121">If the purchase order acknowledgement does not arrive within the time interval specified by the timeout values, a **TimeoutException** will be thrown.</span></span>  
  
## <a name="scenario-2-using-long-running-transactions-with-custom-compensation"></a><span data-ttu-id="c1e5d-122">案例 2： 使用長時間執行交易搭配自訂補償</span><span class="sxs-lookup"><span data-stu-id="c1e5d-122">Scenario 2: Using Long Running Transactions with Custom Compensation</span></span>  
 <span data-ttu-id="c1e5d-123">下列協調流程示範如何將自訂補償與整個協調流程產生關聯並叫用關聯的自訂補償。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-123">The following orchestrations demonstrate how to associate and invoke custom compensations associated with entire orchestrations.</span></span> <span data-ttu-id="c1e5d-124">這個案例會插入新客戶，並插入該客戶的訂單詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-124">This scenario inserts a new customer and inserts order details for the customer.</span></span> <span data-ttu-id="c1e5d-125">此協調流程的邏輯指出，如果訂單插入失敗，您應該回復客戶插入。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-125">The logic of the orchestration dictates that if the order insert fails, you should roll back the customer insert.</span></span> <span data-ttu-id="c1e5d-126">客戶插入無法做到舊有系統，因此，個別呼叫的協調流程中所示範。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-126">The customer insert could be done by a legacy system, and is therefore, demonstrated in a separate callable orchestration.</span></span> <span data-ttu-id="c1e5d-127">呼叫的協調流程**自訂**屬性集，以便提供個別的工作表，來執行補償程序的補償。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-127">The called orchestration has the **Custom** property set for compensation, which provides a separate sheet to do the compensation process.</span></span> <span data-ttu-id="c1e5d-128">補償將會刪除新插入的客戶。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-128">The compensation is to delete the newly inserted customer.</span></span>  
  
 <span data-ttu-id="c1e5d-129">呼叫端協調流程具有長時間執行範圍以執行訂單插入。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-129">The calling orchestration has a long running scope to do the order insert.</span></span> <span data-ttu-id="c1e5d-130">這個範圍是以巢狀方式放在外部長時間執行範圍內。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-130">This scope is nested within an outer long running scope.</span></span> <span data-ttu-id="c1e5d-131">外部範圍關聯的例外狀況處理常式會攔截任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-131">The outer scope has an exception handler associated to catch any exceptions.</span></span> <span data-ttu-id="c1e5d-132">此處理常式會使用 [補償] 圖形，叫用與被呼叫端協調流程關聯的自訂例外狀況，以回復對協調流程的呼叫中可能發生的任何變更。</span><span class="sxs-lookup"><span data-stu-id="c1e5d-132">The handler uses the Compensate shape to invoke the custom exception associated with the called orchestration to roll back any changes that might have occurred in the call to the orchestration.</span></span>  
  
 <span data-ttu-id="c1e5d-133">**自訂補償使用長時間執行交易**</span><span class="sxs-lookup"><span data-stu-id="c1e5d-133">**Long running transactions with custom compensation**</span></span>  
  
 <span data-ttu-id="c1e5d-134">![長時間執行交易搭配自訂補償](../core/media/bts-trans-orch-fig8.gif "BTS_Trans_Orch_Fig8")</span><span class="sxs-lookup"><span data-stu-id="c1e5d-134">![Long running transactions with custom compensation](../core/media/bts-trans-orch-fig8.gif "BTS_Trans_Orch_Fig8")</span></span>  
  
 <span data-ttu-id="c1e5d-135">**呼叫端協調流程 （主要）**</span><span class="sxs-lookup"><span data-stu-id="c1e5d-135">**Called orchestration (main)**</span></span>  
  
 <span data-ttu-id="c1e5d-136">![呼叫協調流程 &#40; 主要 &#41;] (../core/media/bts-trans-orch-fig9.gif "BTS_Trans_Orch_Fig9")</span><span class="sxs-lookup"><span data-stu-id="c1e5d-136">![Called orchestration &#40;main&#41;](../core/media/bts-trans-orch-fig9.gif "BTS_Trans_Orch_Fig9")</span></span>  
  
 <span data-ttu-id="c1e5d-137">**呼叫端協調流程 （補償）**</span><span class="sxs-lookup"><span data-stu-id="c1e5d-137">**Called orchestration (compensation)**</span></span>  
  
 <span data-ttu-id="c1e5d-138">![呼叫協調流程 &#40; 補償 &#41;] (../core/media/bts-trans-orch-fig10.gif "BTS_Trans_Orch_Fig10")</span><span class="sxs-lookup"><span data-stu-id="c1e5d-138">![Called orchestration &#40;compensation&#41;](../core/media/bts-trans-orch-fig10.gif "BTS_Trans_Orch_Fig10")</span></span>