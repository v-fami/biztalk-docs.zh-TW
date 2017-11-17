---
title: "交易 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, transactions
- Orchestration Designer, BizTalk Server Orchestration Engine
- BizTalk Server Orchestration Engine
- Orchestration Designer, transactions
ms.assetid: d9a748c7-be9f-4965-a30f-6b05bd6b42a3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74827beade56e6e54414371c9796454d3b48609e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="transactions"></a><span data-ttu-id="55fef-102">交易</span><span class="sxs-lookup"><span data-stu-id="55fef-102">Transactions</span></span>
<span data-ttu-id="55fef-103">BizTalk Server 協調流程引擎管理會管理狀態、套用商務規則，並叫用複雜處理序和 (或) 交易集合的支援應用程式。</span><span class="sxs-lookup"><span data-stu-id="55fef-103">The BizTalk Server Orchestration Engine manages the state, applies business logic, and invokes the supporting applications of complex processes and/or transaction sets.</span></span>  
  
 <span data-ttu-id="55fef-104">商務程序可以使用不可部分完成的交易而編輯為不連續的工作，此類交易會在發生錯誤或執行時間過長時自動回復所有的變更，其中可能包含巢狀交易，且會使用自訂的例外狀況處理來復原錯誤案例。</span><span class="sxs-lookup"><span data-stu-id="55fef-104">Business processes can be composed as discrete pieces of work using atomic transactions that automatically roll back all changes in case of errors or long running, which can contain nested transactions and use custom exception handling to recover from error scenarios.</span></span> <span data-ttu-id="55fef-105">通常會透過協調流程設計師中的範圍建構來管理這些交易語意。</span><span class="sxs-lookup"><span data-stu-id="55fef-105">These transactional semantics are typically managed through the Scope construct in the Orchestration Designer.</span></span>  
  
 <span data-ttu-id="55fef-106">長時間執行的處理序，其執行時間可能會長達數天、數週或更長。</span><span class="sxs-lookup"><span data-stu-id="55fef-106">The long running processes can span days, weeks, and longer time durations.</span></span> <span data-ttu-id="55fef-107">長時間執行的處理序通常會利用關聯，將接收到的訊息與可能會傳送的訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="55fef-107">The long running processes typically utilize correlation to correlate messages that are received to the messages that may be sent.</span></span> <span data-ttu-id="55fef-108">協調流程引擎管理通常會將這些執行個體凍結，以保留系統資源，然後在接到這些相關訊息時再將處理序解除凍結。</span><span class="sxs-lookup"><span data-stu-id="55fef-108">The orchestration engine typically dehydrates these instances to conserve system resources and re-hydrates the process upon receipt of these correlated messages.</span></span> <span data-ttu-id="55fef-109">協調流程引擎會在已知的檢查點將協調流程狀態保存到 MessageBox 資料庫，以從任何應用程式或系統例外狀況進行復原。</span><span class="sxs-lookup"><span data-stu-id="55fef-109">The orchestration engine persists the orchestration state to the MessageBox database at known checkpoints to recover from any application or system exceptions.</span></span>  
  
 <span data-ttu-id="55fef-110">為 BizTalk 協調流程引擎提供的交易程式設計模型包括下列項目的支援：例外狀況的處理以及從失敗交易復原、會在錯誤發生時自動回復其動作的不可部分完成的交易，或可能包含其他交易以及自訂例外狀況處理的長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="55fef-110">The transactional programming model provided for the BizTalk Orchestration engine includes support for exception handling and recovery from failed transactions, atomic transactions that automatically roll back their actions if an error occurs, or long-running transactions that can contain other transactions as well as custom exception handling.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="55fef-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="55fef-111">In This Section</span></span>  
  
-   [<span data-ttu-id="55fef-112">不可部分完成交易</span><span class="sxs-lookup"><span data-stu-id="55fef-112">Atomic Transactions</span></span>](../core/atomic-transactions.md)  
  
-   [<span data-ttu-id="55fef-113">使用不可部分完成交易的案例</span><span class="sxs-lookup"><span data-stu-id="55fef-113">Scenarios Using Atomic Transactions</span></span>](../core/scenarios-using-atomic-transactions.md)  
  
-   [<span data-ttu-id="55fef-114">長時間執行的交易</span><span class="sxs-lookup"><span data-stu-id="55fef-114">Long-Running Transactions</span></span>](../core/long-running-transactions.md)  
  
-   [<span data-ttu-id="55fef-115">使用長時間執行交易的案例</span><span class="sxs-lookup"><span data-stu-id="55fef-115">Scenarios Using Long-Running Transactions</span></span>](../core/scenarios-using-long-running-transactions.md)  
  
-   [<span data-ttu-id="55fef-116">在協調流程中的持續性</span><span class="sxs-lookup"><span data-stu-id="55fef-116">Persistence in Orchestrations</span></span>](../core/persistence-in-orchestrations.md)