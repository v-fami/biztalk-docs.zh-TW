---
title: 協調流程中使用的相互關聯 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, orchestrations
- messages, correlation sets
- correlation sets
- orchestrations, messages
- messages, validating
ms.assetid: d919afa9-bada-406a-bf4b-7b46c831c6d5
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3be56c2171205bb49d2ff1f589c77ac309ea188
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287366"
---
# <a name="using-correlations-in-orchestrations"></a><span data-ttu-id="d0150-102">使用協調流程中的相互關聯</span><span class="sxs-lookup"><span data-stu-id="d0150-102">Using Correlations in Orchestrations</span></span>
<span data-ttu-id="d0150-103">相互關聯是將內送訊息與適當協調流程執行個體相比對的程序。</span><span class="sxs-lookup"><span data-stu-id="d0150-103">Correlation is the process of matching an incoming message with the appropriate instance of an orchestration.</span></span> <span data-ttu-id="d0150-104">例如，協調流程會傳送訊息，並將回應接收到相同的協調流程中。</span><span class="sxs-lookup"><span data-stu-id="d0150-104">For example, orchestration sends out of a message and receives the response or responses back into the same orchestration.</span></span> <span data-ttu-id="d0150-105">相互關聯的訊息交換模式共有三種：</span><span class="sxs-lookup"><span data-stu-id="d0150-105">There are three correlated messages exchange patterns:</span></span>  
  
-   <span data-ttu-id="d0150-106">傳統交握</span><span class="sxs-lookup"><span data-stu-id="d0150-106">Traditional handshake</span></span>  
  
-   <span data-ttu-id="d0150-107">循序群組</span><span class="sxs-lookup"><span data-stu-id="d0150-107">Sequential convoy</span></span>  
  
-   <span data-ttu-id="d0150-108">平行群組</span><span class="sxs-lookup"><span data-stu-id="d0150-108">Parallel convoy</span></span>  
  
 <span data-ttu-id="d0150-109">在傳統交握模式中，交握存在協調流程或商務程序間的訊息交換之間，而您可以透過在協調流程中定義相互關聯集合來完成交握程序；協調流程中的相互關聯集合是一份具有特定值的升級屬性清單，您可以使用這些特定的值，將訊息路由到特定的協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="d0150-109">In the traditional handshake pattern, handshakes exist between the exchanges of the messages among the orchestrations or business processes, and you can achieve the handshakes by defining correlation sets in the orchestrations where a correlation set is a list of promoted properties with specific values that you use to route messages to a specific orchestration instance.</span></span>  
  
 <span data-ttu-id="d0150-110">例如，如果您的協調流程是設計用來發出訂單、接收發票及送出付款，您必須確定接收發票訊息的協調流程執行個體與傳送對應訂單的執行個體相同，因為當時可能已處理許多筆訂單。</span><span class="sxs-lookup"><span data-stu-id="d0150-110">If, for example, your orchestration is designed to issue a purchase order, receive an invoice, and send out the payment, you need to be sure that the invoice message is received by the same orchestration instance that the corresponding purchase order was sent from since numbers of purchase orders may be processed at the time.</span></span> <span data-ttu-id="d0150-111">在這個範例中，訂單識別碼可以當做相互關聯集合中的參數，以便使訂單訊息和發票訊息產生相互關聯。</span><span class="sxs-lookup"><span data-stu-id="d0150-111">In this example, the purchase order identification number can be used as a parameter in the correlation set for correlating the purchase order message and the invoice message.</span></span> <span data-ttu-id="d0150-112">此範例的實例流程如下：</span><span class="sxs-lookup"><span data-stu-id="d0150-112">The following is the scenario flow for this example,</span></span>  
  
1.  <span data-ttu-id="d0150-113">範例流程 A 將訂單訊息傳送至協調流程 B。相互關聯集合會在傳送訂單訊息之前初始化。</span><span class="sxs-lookup"><span data-stu-id="d0150-113">The Orchestration A sends out the purchase order message to the Orchestration B. Before sending out the purchase order message, the correlation set is initialized.</span></span>  
  
2.  <span data-ttu-id="d0150-114">協調流程 B 會處理訂單、產生並傳回發票；在這個協調流程中，第一個「接收」圖形會遵照同一個相互關聯集合來接收訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="d0150-114">In the Orchestration B, in which processes the purchase order, generates and sends back the invoice, the first Receive shape follows the same correlation set to receive the purchase order message.</span></span>  
  
3.  <span data-ttu-id="d0150-115">在處理訂單訊息之後，將發票傳回協調流程 A 時，也會遵照相同的相互關聯流程。</span><span class="sxs-lookup"><span data-stu-id="d0150-115">After processing the purchase order message, when sending back the invoice message to the Orchestration A, the same correlation set is also followed.</span></span>  
  
4.  <span data-ttu-id="d0150-116">在協調流程 A 中，從協調流程 B 接收發票訊息的「接收」圖形，也會遵照同一個相互關聯集合，以確實依據預先定義的相互關聯集合來接收相互關聯發票訊息。</span><span class="sxs-lookup"><span data-stu-id="d0150-116">In the Orchestration A, at the Receive shape which receives the invoice message back from the orchestration B, the same correlation set is also followed to ensure that receiving the correlated invoice message based on the predefined correlation set.</span></span>  
  
 <span data-ttu-id="d0150-117">每當多個單一項目必須相互關聯，以達到個別項目無法單獨完成的工作時，都可以使用循序群組和平行群組模式。</span><span class="sxs-lookup"><span data-stu-id="d0150-117">The sequential convoy and parallel convoy patterns exist in the world any time multiple single items must be related together in order to achieve something that the individual item cannot accomplish by itself.</span></span> <span data-ttu-id="d0150-118">如需詳細資訊，請參閱[使用群組實例](../core/working-with-convoy-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="d0150-118">For more information, see [Working with Convoy Scenarios](../core/working-with-convoy-scenarios.md).</span></span>  
  
 <span data-ttu-id="d0150-119">除了相互關聯訊息交換模式之外，協調流程中還有兩種相互關聯類型：</span><span class="sxs-lookup"><span data-stu-id="d0150-119">In addition to the correlated message exchange patterns, there are two types of correlations in orchestration:</span></span>  
  
-   <span data-ttu-id="d0150-120">手動相互關聯</span><span class="sxs-lookup"><span data-stu-id="d0150-120">Manual correlation</span></span>  
  
-   <span data-ttu-id="d0150-121">自動相互關聯</span><span class="sxs-lookup"><span data-stu-id="d0150-121">Automatic correlation</span></span>  
  
 <span data-ttu-id="d0150-122">在手動相互關聯實例中，您可手動設定協調流程，以初始化並遵照相互關聯集合，使訊息與適當的執行個體產生關聯。</span><span class="sxs-lookup"><span data-stu-id="d0150-122">In the manual correlation scenario, you manually configure the orchestrations to initialize and follow the correlation set to associate the messages with proper instances.</span></span> <span data-ttu-id="d0150-123">在自動相互關聯實例中，傳訊引擎會代替您建立訊息與執行個體的相互關聯，例如，當您在自己的協調流程中設定要求-回應連接埠或自我相互關聯連接埠時。</span><span class="sxs-lookup"><span data-stu-id="d0150-123">In the automatic correlation scenario, the messaging engine will correlate the messages with the instances for you, for example, when you set up Request-Response port or Self-Correlating port in your orchestrations.</span></span>  
  
 <span data-ttu-id="d0150-124">只要您的協調流程沒有可以讓訊息與執行個體產生關聯的明確途徑，例如啟動接收、要求-回應或自我相互關聯連接埠，您就必須使用相互關聯。</span><span class="sxs-lookup"><span data-stu-id="d0150-124">You must use correlation whenever your orchestration does not have an explicit way of associating a message with an instance, such as an activate receive, a request-response, or a self-correlating port.</span></span>  
  
## <a name="examples-of-using-correlations"></a><span data-ttu-id="d0150-125">相互關聯的使用範例</span><span class="sxs-lookup"><span data-stu-id="d0150-125">Examples of Using Correlations</span></span>  
  
-   [<span data-ttu-id="d0150-126">PartyResolution （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="d0150-126">PartyResolution (BizTalk Server Sample)</span></span>](../core/partyresolution-biztalk-server-sample.md)  
  
-   <span data-ttu-id="d0150-127">從下載 SDK 範例 < 相互關聯訊息與協調流程執行個體 > [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="d0150-127">Download the SDK sample "Correlating Messages with Orchestration Instances" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
-   <span data-ttu-id="d0150-128">從下載 SDK 範例 「 平行群組 」 [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703)。</span><span class="sxs-lookup"><span data-stu-id="d0150-128">Download the SDK sample "Parallel Convoy" from [http://go.microsoft.com/fwlink/?LinkId=73703](http://go.microsoft.com/fwlink/?LinkId=73703).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0150-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="d0150-129">In This Section</span></span>  
  
-   [<span data-ttu-id="d0150-130">相互關聯集</span><span class="sxs-lookup"><span data-stu-id="d0150-130">Correlation Sets</span></span>](../core/correlation-sets.md) 
  
-   [<span data-ttu-id="d0150-131">相互關聯類型</span><span class="sxs-lookup"><span data-stu-id="d0150-131">Correlation Types</span></span>](../core/correlation-types.md) 
  
-   [<span data-ttu-id="d0150-132">如何新增及移除相互關聯集</span><span class="sxs-lookup"><span data-stu-id="d0150-132">How to Add and Remove Correlation Sets</span></span>](../core/how-to-add-and-remove-correlation-sets.md) 
  
-   [<span data-ttu-id="d0150-133">如何設定相互關聯集</span><span class="sxs-lookup"><span data-stu-id="d0150-133">How to Configure Correlation Sets</span></span>](../core/how-to-configure-correlation-sets.md)  
  
-   [<span data-ttu-id="d0150-134">如何設定相互關聯類型</span><span class="sxs-lookup"><span data-stu-id="d0150-134">How to Configure Correlation Types</span></span>](../core/how-to-configure-correlation-types.md)  
  
-   [<span data-ttu-id="d0150-135">使用群組實例</span><span class="sxs-lookup"><span data-stu-id="d0150-135">Working with Convoy Scenarios</span></span>](../core/working-with-convoy-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="d0150-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0150-136">See Also</span></span>  
 [<span data-ttu-id="d0150-137">如何使用自我相互關聯直接繫結連接埠</span><span class="sxs-lookup"><span data-stu-id="d0150-137">How to Use Self-Correlating Direct Bound Ports</span></span>](../core/how-to-use-self-correlating-direct-bound-ports.md)