---
title: "在協調流程中實作的設計模式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Aggregator pattern, orchestrations
- Error Handling pattern [orchestrations]
- patterns, orchestrations
- designing, orchestrations
- orchestrations, designing
- Exception Handling and Compensation pattern [orchestrations]
- Parallel Convoy pattern [orchestrations]
- Dynamic Router pattern [orchestrations]
- orchestrations, patterns
- patterns
- Composed Message Processor pattern [orchestrations]
- Suspend with Retry pattern, orchestrations
- Calling Pipelines from Orchestration pattern [orchestrations]
- Message Filter pattern [orchestrations]
- Message Broker pattern [orchestrations]
- Content-Based Router pattern [orchestrations]
- Sequential Convoy pattern [orchestrations]
- Scatter and Gather pattern [orchestrations]
- Splitter pattern, orchestrations
- Message Translator pattern [orchestrations]
ms.assetid: f62ba955-018a-40e7-b303-497acc906019
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a4837ddf1199425a76a6fa82bbfd6e44615b6c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="implementing-design-patterns-in-orchestrations"></a><span data-ttu-id="040fa-102">實作協調流程中的設計模式</span><span class="sxs-lookup"><span data-stu-id="040fa-102">Implementing Design Patterns in Orchestrations</span></span>
<span data-ttu-id="040fa-103">本節討論 BizTalk Server 程式設計的常見模式以及企業整合模式。</span><span class="sxs-lookup"><span data-stu-id="040fa-103">This section discusses the common patterns of BizTalk Server programming as well as enterprise integration patterns.</span></span> <span data-ttu-id="040fa-104">您可以利用單一模式或結合數個模式來設計您的商務程序，然後再使用 BizTalk 協調流程設計師中的圖形來實作設計。</span><span class="sxs-lookup"><span data-stu-id="040fa-104">You can leverage a single pattern or combine multiple patterns to design your business process and then implement the design by using shapes in BizTalk Orchestration Designer.</span></span>  
  
## <a name="design-patterns"></a><span data-ttu-id="040fa-105">設計模式</span><span class="sxs-lookup"><span data-stu-id="040fa-105">Design Patterns</span></span>  
 <span data-ttu-id="040fa-106">下列項目將簡短描述每個模式，並指向說明如何使用 BizTalk 協調流程設計師實作模式的主題或範例。</span><span class="sxs-lookup"><span data-stu-id="040fa-106">The following entries briefly describe each pattern and point to the topics or samples that show how to implement the patterns using BizTalk Orchestration Designer.</span></span>  
  
### <a name="aggregator"></a><span data-ttu-id="040fa-107">彙總工具</span><span class="sxs-lookup"><span data-stu-id="040fa-107">Aggregator</span></span>  
 <span data-ttu-id="040fa-108">彙總工具模式可從多個來源接收資訊並將它併入單一訊息。</span><span class="sxs-lookup"><span data-stu-id="040fa-108">Aggregator is the pattern of receiving information from multiple sources and consolidating it into a single message.</span></span> <span data-ttu-id="040fa-109">如需此模式的範例，請參閱中的 Aggregate.odx[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-109">For an example of this pattern, see Aggregate.odx in [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).</span></span>  
  
### <a name="calling-pipelines-from-an-orchestration"></a><span data-ttu-id="040fa-110">從協調流程呼叫管線</span><span class="sxs-lookup"><span data-stu-id="040fa-110">Calling Pipelines from an Orchestration</span></span>  
 <span data-ttu-id="040fa-111">您可以從協調流程傳送及接收管線。</span><span class="sxs-lookup"><span data-stu-id="040fa-111">You can call send and receive pipelines from your orchestrations.</span></span> <span data-ttu-id="040fa-112">這允許重複使用管線並協助維護管線階段的協調流程解離。</span><span class="sxs-lookup"><span data-stu-id="040fa-112">This allows the reuse of pipelines and helps maintain the decoupling of an orchestration from the pipeline stages.</span></span> <span data-ttu-id="040fa-113">如需此模式的範例，請參閱中的 Aggregate.odx[彙總工具 （BizTalk Server 範例）](../core/aggregator-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-113">For an example of this pattern, see Aggregate.odx in [Aggregator (BizTalk Server Sample)](../core/aggregator-biztalk-server-sample.md).</span></span> <span data-ttu-id="040fa-114">另一個例子是中的 CMP.odx[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-114">Another example is CMP.odx in [Composed Message Processor (BizTalk Server Sample)](../core/composed-message-processor-biztalk-server-sample.md).</span></span> <span data-ttu-id="040fa-115">另請參閱[如何使用運算式執行管線](../core/how-to-use-expressions-to-execute-pipelines.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-115">See also [How to Use Expressions to Execute Pipelines](../core/how-to-use-expressions-to-execute-pipelines.md).</span></span>  
  
### <a name="composed-message-processor"></a><span data-ttu-id="040fa-116">撰寫訊息處理器</span><span class="sxs-lookup"><span data-stu-id="040fa-116">Composed Message Processor</span></span>  
 <span data-ttu-id="040fa-117">撰寫訊息處理器模式可從匯總的或批次的交換訊息來處理個別的項目。</span><span class="sxs-lookup"><span data-stu-id="040fa-117">Composed Message Processor is the pattern of processing individual items from an aggregated or batched interchange message.</span></span> <span data-ttu-id="040fa-118">如需此模式的範例，請參閱中的 CMP.odx[撰寫訊息處理器 （BizTalk Server 範例）](../core/composed-message-processor-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-118">For an example of this pattern, see CMP.odx in [Composed Message Processor (BizTalk Server Sample)](../core/composed-message-processor-biztalk-server-sample.md).</span></span>  
  
### <a name="content-based-router"></a><span data-ttu-id="040fa-119">以內容為基礎的路由</span><span class="sxs-lookup"><span data-stu-id="040fa-119">Content-Based Router</span></span>  
 <span data-ttu-id="040fa-120">以內容為基礎的路由模式可根據訊息內容的某些部分來決定訊息收件者。</span><span class="sxs-lookup"><span data-stu-id="040fa-120">Content-Based Router is the pattern of determining the recipient of a message based on some part of the message content.</span></span> <span data-ttu-id="040fa-121">如需此模式的範例，請參閱[CBRSample （BizTalk Server 範例）](../core/cbrsample-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-121">For an example of this pattern, see [CBRSample (BizTalk Server Sample)](../core/cbrsample-biztalk-server-sample.md).</span></span>  
  
### <a name="dynamic-router"></a><span data-ttu-id="040fa-122">動態路由器</span><span class="sxs-lookup"><span data-stu-id="040fa-122">Dynamic Router</span></span>  
 <span data-ttu-id="040fa-123">動態路由器模式可根據訊息處理的結果而決定目的地位址以及傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="040fa-123">Dynamic Router is the pattern of determining the destination address as well as the transport protocol based on the result of message processing.</span></span> <span data-ttu-id="040fa-124">您可以使用動態傳送埠或**角色連結**圖形來實作此模式。</span><span class="sxs-lookup"><span data-stu-id="040fa-124">You can use a dynamic send port or a **Role Link** shape to implement this pattern.</span></span> <span data-ttu-id="040fa-125">如需此模式的範例，請參閱中的 ReceiveSend.odx [SendMail](../core/sendmail.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-125">For an example of this pattern, see ReceiveSend.odx in [SendMail](../core/sendmail.md).</span></span> <span data-ttu-id="040fa-126">另一個例子是中的 SupplierProcess.odx [PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-126">Another example is SupplierProcess.odx in [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md).</span></span>  
  
### <a name="error-handling"></a><span data-ttu-id="040fa-127">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="040fa-127">Error Handling</span></span>  
 <span data-ttu-id="040fa-128">BizTalk Server 可讓您指定自動化處理傳訊失敗，做為在已擱置佇列中放置失敗訊息的預設行為替代解決方案。</span><span class="sxs-lookup"><span data-stu-id="040fa-128">BizTalk Server allows you to designate automated handling of messaging failures as an alternative to the default behavior of placing failed messages in the Suspended queue.</span></span> <span data-ttu-id="040fa-129">您可以將失敗的訊息路由至訂閱連接埠，以進行報告或處理。</span><span class="sxs-lookup"><span data-stu-id="040fa-129">You can route failed messages to a subscribing port for reporting or processing.</span></span> <span data-ttu-id="040fa-130">如需此模式的範例，請參閱中的 ResubmitLogic.odx[錯誤處理 （BizTalk Server 範例資料夾）](../core/error-handling-biztalk-server-samples-folder.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-130">For an example of this pattern, see ResubmitLogic.odx in [Error Handling (BizTalk Server Samples Folder)](../core/error-handling-biztalk-server-samples-folder.md).</span></span>  
  
### <a name="exception-handling-and-compensation"></a><span data-ttu-id="040fa-131">例外狀況處理和補償</span><span class="sxs-lookup"><span data-stu-id="040fa-131">Exception Handling and Compensation</span></span>  
 <span data-ttu-id="040fa-132">您可以使用例外狀況處理常式和**擲回的例外狀況**圖形或**運算式**例外狀況處理的圖形。</span><span class="sxs-lookup"><span data-stu-id="040fa-132">You can use an exception handler and a **Throw Exception** shape or an **Expression** shape for exception handling.</span></span> <span data-ttu-id="040fa-133">例如，您可以在其中放置中的下列程式碼**運算式**擲回例外狀況的圖形:，</span><span class="sxs-lookup"><span data-stu-id="040fa-133">For example, you can place the following code in the **Expression** shape to throw the exception:,</span></span>  
  
```  
excp = new System.Exception();  
throw(excp);  
```  
  
 <span data-ttu-id="040fa-134">您可以使用補償區塊和**補償**圖形上的已認可的交易執行補償。</span><span class="sxs-lookup"><span data-stu-id="040fa-134">You can use a compensation block and a **Compensate** shape to perform the compensation on the transactions that have been committed.</span></span> <span data-ttu-id="040fa-135">如需此模式的範例，請參閱中的 UpdateContact.odx[補償 （BizTalk Server 範例）](../core/compensation-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-135">For an example of this pattern, see UpdateContact.odx in [Compensation (BizTalk Server Sample)](../core/compensation-biztalk-server-sample.md).</span></span> <span data-ttu-id="040fa-136">另一個例子是在[自訂例外狀況](../core/custom-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-136">Another example is in [Custom Exceptions](../core/custom-exceptions.md).</span></span>  
  
### <a name="message-broker"></a><span data-ttu-id="040fa-137">訊息仲介</span><span class="sxs-lookup"><span data-stu-id="040fa-137">Message Broker</span></span>  
 <span data-ttu-id="040fa-138">訊息仲介模式可決定訊息的目的地，並保持對訊息流量的控制。</span><span class="sxs-lookup"><span data-stu-id="040fa-138">Message Broker is the pattern of determining the destination of a message and still maintaining control over the message flow.</span></span> <span data-ttu-id="040fa-139">如需詳細資訊，請參閱[OrderBroker 協調流程中處理](../core/processing-in-the-orderbroker-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-139">For more, see  [Processing in the OrderBroker Orchestration](../core/processing-in-the-orderbroker-orchestration.md).</span></span>  
  
### <a name="message-filter"></a><span data-ttu-id="040fa-140">訊息篩選</span><span class="sxs-lookup"><span data-stu-id="040fa-140">Message Filter</span></span>  
 <span data-ttu-id="040fa-141">訊息篩選模式會選取符合特殊準則的訊息，以進行處理。</span><span class="sxs-lookup"><span data-stu-id="040fa-141">The Message Filter pattern selects messages meeting particular criteria for processing.</span></span> <span data-ttu-id="040fa-142">您可以實作此模式的篩選運算式加入至啟動**接收**圖形。</span><span class="sxs-lookup"><span data-stu-id="040fa-142">You can implement this pattern by adding the filter expression to an activated **Receive** shape.</span></span> <span data-ttu-id="040fa-143">如需詳細資訊，請參閱[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-143">For more information, see [Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md).</span></span>  
  
### <a name="message-translator"></a><span data-ttu-id="040fa-144">訊息轉譯程式</span><span class="sxs-lookup"><span data-stu-id="040fa-144">Message Translator</span></span>  
 <span data-ttu-id="040fa-145">訊息轉譯程式模式可將訊息從一種形式轉換成另一種形式。</span><span class="sxs-lookup"><span data-stu-id="040fa-145">The Message Translator pattern converts a message from one form to another form.</span></span> <span data-ttu-id="040fa-146">您可以使用與 BizTalk 對應來實作此模式**轉換**使用協調流程。</span><span class="sxs-lookup"><span data-stu-id="040fa-146">You can implement this pattern by using a BizTalk map with a **Transform** shape in an orchestration.</span></span> <span data-ttu-id="040fa-147">如需此模式的範例，請參閱中的 HelloOrchestration.odx [HelloWorld （BizTalk Server 範例）](../core/helloworld-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="040fa-147">For an example of this pattern, see HelloOrchestration.odx in [HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md).</span></span>  
  
### <a name="parallel-convoy"></a><span data-ttu-id="040fa-148">平行群組</span><span class="sxs-lookup"><span data-stu-id="040fa-148">Parallel Convoy</span></span>  
 <span data-ttu-id="040fa-149">平行群組模式可以讓多個單一項目聯結在一起，達到個別項目無法完成的目標。</span><span class="sxs-lookup"><span data-stu-id="040fa-149">The Parallel Convoy pattern enables multiple single items to join together to achieve something that an individual item cannot accomplish by itself.</span></span> <span data-ttu-id="040fa-150">一組相關的項目會依任何順序抵達，但 BizTalk Server 必須收到所有的訊息，才能開始處理。</span><span class="sxs-lookup"><span data-stu-id="040fa-150">The set of related items can arrive in any order, but BizTalk Server must receive all of them before starting the process.</span></span> <span data-ttu-id="040fa-151">如需此模式的範例，請參閱[http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035)。</span><span class="sxs-lookup"><span data-stu-id="040fa-151">For an example of this pattern, see [http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035).</span></span>  
  
### <a name="scatter-and-gather"></a><span data-ttu-id="040fa-152">散佈和收集</span><span class="sxs-lookup"><span data-stu-id="040fa-152">Scatter and Gather</span></span>  
 <span data-ttu-id="040fa-153">散佈和收集模式可將訊息傳送至多個收件者，並從每個收件者接收回訊息。</span><span class="sxs-lookup"><span data-stu-id="040fa-153">The Scatter and Gather pattern enables messages to be sent to multiple recipients and messages to be received back from each recipient.</span></span> <span data-ttu-id="040fa-154">您可以使用分隔器模式和彙總工具模式來實作此模式。</span><span class="sxs-lookup"><span data-stu-id="040fa-154">You can implement this pattern by using the Splitter pattern and the Aggregator pattern.</span></span> <span data-ttu-id="040fa-155">您可以使用彙總工具模式來組合使用分隔器模式的結果，並放在**平行動作**圖形。</span><span class="sxs-lookup"><span data-stu-id="040fa-155">You use the Aggregator pattern to assemble the results from using the Splitter pattern and put them under a **Parallel Actions** shape.</span></span> <span data-ttu-id="040fa-156">如需分隔器模式的範例，請參閱 SDK 範例具名實作散佈和收集模式時[http://go.microsoft.com/fwlink/?LinkId=65185](http://go.microsoft.com/fwlink/?LinkId=65185)。</span><span class="sxs-lookup"><span data-stu-id="040fa-156">For an example of the Splitter pattern, see SDK sample named Implementing Scatter and Gather Pattern at [http://go.microsoft.com/fwlink/?LinkId=65185](http://go.microsoft.com/fwlink/?LinkId=65185).</span></span>  
  
### <a name="sequential-convoy"></a><span data-ttu-id="040fa-157">循序群組</span><span class="sxs-lookup"><span data-stu-id="040fa-157">Sequential Convoy</span></span>  
 <span data-ttu-id="040fa-158">循序群組模式可以讓多個單一項目聯結在一起，達到個別項目無法完成的目標。</span><span class="sxs-lookup"><span data-stu-id="040fa-158">The Sequential Convoy pattern enables multiple single items to join together to achieve something that an individual item cannot accomplish by itself.</span></span> <span data-ttu-id="040fa-159">循序群組是具有預先定義順序的相關項目組。</span><span class="sxs-lookup"><span data-stu-id="040fa-159">A sequential convoy is a set of related items that have a predefined order.</span></span> <span data-ttu-id="040fa-160">雖然項目不需要完全相同，但 BizTalk Server 必須以循序方式接收這些項目。</span><span class="sxs-lookup"><span data-stu-id="040fa-160">Although the items do not have to be exactly the same, BizTalk Server must receive the items in a sequential order.</span></span> <span data-ttu-id="040fa-161">如需此模式的範例，請參閱[http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035)。</span><span class="sxs-lookup"><span data-stu-id="040fa-161">For an example of this pattern, see [http://go.microsoft.com/fwlink/?LinkId=56035](http://go.microsoft.com/fwlink/?LinkId=56035).</span></span>  
  
### <a name="splitter"></a><span data-ttu-id="040fa-162">分隔器</span><span class="sxs-lookup"><span data-stu-id="040fa-162">Splitter</span></span>  
 <span data-ttu-id="040fa-163">分隔器模式會將單一訊息分割為多個訊息。</span><span class="sxs-lookup"><span data-stu-id="040fa-163">The Splitter pattern takes a single message and splits it into multiple messages.</span></span>  
  
### <a name="suspend-with-retry"></a><span data-ttu-id="040fa-164">重試擱置模式</span><span class="sxs-lookup"><span data-stu-id="040fa-164">Suspend with Retry</span></span>  
 <span data-ttu-id="040fa-165">重試擱置模式可讓協調流程在錯誤發生時擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="040fa-165">The Suspend with Retry pattern enables the orchestration to suspend a message when there is an error.</span></span> <span data-ttu-id="040fa-166">擱置會發生在迴圈中，讓協調流程擱置、要求操作人員介入、然後以固定次數重試作業。</span><span class="sxs-lookup"><span data-stu-id="040fa-166">The suspension occurs within a loop so that the orchestration suspends, asks for intervention, and then retries the operation a fixed number of times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="040fa-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="040fa-167">See Also</span></span>  
 [<span data-ttu-id="040fa-168">設計協調流程</span><span class="sxs-lookup"><span data-stu-id="040fa-168">Designing Orchestration Flow</span></span>](../core/designing-orchestration-flow.md)