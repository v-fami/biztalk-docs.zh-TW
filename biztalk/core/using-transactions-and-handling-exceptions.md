---
title: 使用交易及處理例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions, orchestrations
- orchestrations, transactions
- orchestrations, errors
- transactions
- errors, orchestrations
- transactions, BizTalk Server Orchestration Engine
- errors, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], errors
- Scope shape [Orchestration Designer], transactions
ms.assetid: bb38f5eb-6641-4e7c-8e2a-c474fc739999
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab32729aa6b4f12aada623587f52728c6bd23240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288430"
---
# <a name="using-transactions-and-handling-exceptions"></a><span data-ttu-id="c7be3-102">使用交易和例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="c7be3-102">Using Transactions and Handling Exceptions</span></span>
<span data-ttu-id="c7be3-103">設計協調流程時，您應該仔細思考可能發生問題的地方，以及處理問題的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="c7be3-103">When you design an orchestration, you should consider carefully where problems might occur and how best to deal with them.</span></span> <span data-ttu-id="c7be3-104">許多協調流程都有多個潛在的失敗點。</span><span class="sxs-lookup"><span data-stu-id="c7be3-104">Many orchestrations have several potential points of failure.</span></span> <span data-ttu-id="c7be3-105">問題可能是由其他原因所引起；例如，伺服器可能當機，或是訊息格式不正確。</span><span class="sxs-lookup"><span data-stu-id="c7be3-105">Problems can arise for any number of other reasons; for example, a server might go down or a message might be badly formatted.</span></span>  
  
 <span data-ttu-id="c7be3-106">對於長時間執行或複雜的協調流程而言，持續追蹤狀態與即時報告錯誤尤其重要，因為這樣您才能夠以最少的精力正確解決問題。</span><span class="sxs-lookup"><span data-stu-id="c7be3-106">It is especially important for a long-running or complex orchestration to keep track of its state and to report errors as they occur, so that you can resolve problems accurately and with a minimum of effort.</span></span> <span data-ttu-id="c7be3-107">對於協調流程來說，維持一組關係緊密的動作保持完整也一樣重要，如此在執行交易的某一部分，而其他部分未執行的情況下，才能回復完整的交易 (即使該交易從未執行也一樣)。</span><span class="sxs-lookup"><span data-stu-id="c7be3-107">It is equally important for an orchestration to maintain the integrity of a set of closely related actions, so that if part of a transaction takes place but another does not, the entire transaction can be rolled back as though it never occurred.</span></span>  
  
 <span data-ttu-id="c7be3-108">即使有外部系統參與交易過程，BizTalk 協調流程也可讓您確保工作不可部分完成的特性，也就是相關動作的完整性。</span><span class="sxs-lookup"><span data-stu-id="c7be3-108">BizTalk Orchestration enables you to guarantee the atomicity of work, that is, the integrity of related actions, even when external systems are participating in transactions.</span></span> <span data-ttu-id="c7be3-109">它提供多項工具，供您處理錯誤、維護協調流程的狀態，以及透過交易、補償和例外狀況處理即時修正問題。</span><span class="sxs-lookup"><span data-stu-id="c7be3-109">It gives you tools to handle errors, to maintain the state of an orchestration, and to fix problems as they occur through transactions, compensation, and exception handling.</span></span>  
  
 <span data-ttu-id="c7be3-110">做為交易和例外狀況處理的架構，協調流程設計師 」 提供**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="c7be3-110">As a framework for transactions and exception handling, Orchestration Designer provides the **Scope** shape.</span></span> <span data-ttu-id="c7be3-111">範圍可以包含交易類型、補償和任何數目的例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="c7be3-111">A scope can have a transaction type, a compensation, and any number of exception handlers.</span></span>  
  
 <span data-ttu-id="c7be3-112">設定交易和例外狀況處理的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="c7be3-112">The steps for setting up a transaction and exception handling are:</span></span>  
  
-   <span data-ttu-id="c7be3-113">建立範圍。</span><span class="sxs-lookup"><span data-stu-id="c7be3-113">Create a scope.</span></span>  
  
-   <span data-ttu-id="c7be3-114">識別您需要的交易種類。</span><span class="sxs-lookup"><span data-stu-id="c7be3-114">Identify the kind of transaction you need.</span></span>  
  
-   <span data-ttu-id="c7be3-115">判斷需要補償的部分。</span><span class="sxs-lookup"><span data-stu-id="c7be3-115">Determine what will need to be compensated.</span></span>  
  
-   <span data-ttu-id="c7be3-116">識別潛在的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c7be3-116">Identify potential errors.</span></span>  
  
-   <span data-ttu-id="c7be3-117">新增適當的例外狀況處理常式和補償程式碼。</span><span class="sxs-lookup"><span data-stu-id="c7be3-117">Add appropriate exception handlers and compensation code.</span></span>  
  
## <a name="examples-of-using-transactions-exception-handlings-and-compensations"></a><span data-ttu-id="c7be3-118">使用交易、例外狀況處理和補償的範例</span><span class="sxs-lookup"><span data-stu-id="c7be3-118">Examples of Using Transactions, Exception Handlings, and Compensations</span></span>  
  
-   [<span data-ttu-id="c7be3-119">錯誤處理 （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="c7be3-119">Error Handling (BizTalk Server Samples Folder)</span></span>](../core/error-handling-biztalk-server-samples-folder.md)  
  
-   [<span data-ttu-id="c7be3-120">補償 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="c7be3-120">Compensation (BizTalk Server Sample)</span></span>](../core/compensation-biztalk-server-sample.md)  
  
-   <span data-ttu-id="c7be3-121">下載 SDK 範例 「 不可部分完成交易與 COM + Serviced 元件中協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="c7be3-121">Download the SDK sample "Atomic Transactions with COM+ Serviced Components in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="c7be3-122">下載 SDK 範例 「 使用 SQL 配接器使用不可部分完成交易中協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="c7be3-122">Download the SDK sample "Using the SQL Adapter with Atomic Transactions in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="c7be3-123">下載 SDK 範例 「 使用長時間執行交易的協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="c7be3-123">Download the SDK sample "Using Long-Running Transactions in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="c7be3-124">下載 SDK 範例 「 例外狀況處理中協調流程 」 從[http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="c7be3-124">Download the SDK sample "Exception Handling in Orchestrations" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7be3-125">本節內容</span><span class="sxs-lookup"><span data-stu-id="c7be3-125">In This Section</span></span>  
  
-   [<span data-ttu-id="c7be3-126">範圍</span><span class="sxs-lookup"><span data-stu-id="c7be3-126">Scopes</span></span>](../core/scopes.md)  
  
-   [<span data-ttu-id="c7be3-127">如何設定 「 範圍 」 圖形</span><span class="sxs-lookup"><span data-stu-id="c7be3-127">How to Configure the Scope Shape</span></span>](../core/how-to-configure-the-scope-shape.md)  
  
-   [<span data-ttu-id="c7be3-128">建立交易式協調流程</span><span class="sxs-lookup"><span data-stu-id="c7be3-128">Making Orchestrations Transactional</span></span>](../core/making-orchestrations-transactional.md)  
  
-   [<span data-ttu-id="c7be3-129">例外狀況</span><span class="sxs-lookup"><span data-stu-id="c7be3-129">Exceptions</span></span>](../core/exceptions.md)  
  
-   [<span data-ttu-id="c7be3-130">補償</span><span class="sxs-lookup"><span data-stu-id="c7be3-130">Compensation</span></span>](../core/compensation.md)  
  
## <a name="see-also"></a><span data-ttu-id="c7be3-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7be3-131">See Also</span></span>  
 [<span data-ttu-id="c7be3-132">使用 「 BizTalk 傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="c7be3-132">Using the BizTalk Messaging Engine</span></span>](../core/using-the-biztalk-messaging-engine.md)