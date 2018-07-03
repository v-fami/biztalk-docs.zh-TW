---
title: 活動接續 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- continuation tokens
- activities [BAM], code samples
- activities [BAM], continuation tokens
- continuations, activities [BAM]
- code samples, activities [BAM]
ms.assetid: 47d91ae6-77c1-4efb-940f-a7b3a325e5bd
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91eadd02e3b0a8792b9b27ea6c913b847b534456
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981991"
---
# <a name="activity-continuation"></a><span data-ttu-id="27cfe-102">活動接續</span><span class="sxs-lookup"><span data-stu-id="27cfe-102">Activity Continuation</span></span>
<span data-ttu-id="27cfe-103">BAM 活動 (也稱為商務活動) 可以跨越多個異質應用程式 (例如，從某個管線進入兩個協調流程，再到某個商務營運系統應用程式，然後到另一個管線)。</span><span class="sxs-lookup"><span data-stu-id="27cfe-103">The BAM activity (also called the business activity) can span multiple heterogeneous applications (for example, a pipeline, two orchestrations, a line-of-business application, and then another pipeline).</span></span> <span data-ttu-id="27cfe-104">BAM 基礎結構可以相互關聯的稍加協助，為開發人員引進所謂的多個應用程式的事件 」*接續*，「 這會顯示在下圖中。</span><span class="sxs-lookup"><span data-stu-id="27cfe-104">The BAM infrastructure can correlate the events from multiple applications with a little help from the developer – a concept called "*Continuation*," which is shown in the following figure.</span></span>  
  
 <span data-ttu-id="27cfe-105">![](../core/media/ebiz-prog-bam-fig4-app-scopes-cont-tokens.gif "ebiz_prog_bam_fig4_app_scopes_cont_tokens")</span><span class="sxs-lookup"><span data-stu-id="27cfe-105">![](../core/media/ebiz-prog-bam-fig4-app-scopes-cont-tokens.gif "ebiz_prog_bam_fig4_app_scopes_cont_tokens")</span></span>  

## <a name="applications"></a><span data-ttu-id="27cfe-106">應用程式</span><span class="sxs-lookup"><span data-stu-id="27cfe-106">Applications</span></span>  
 <span data-ttu-id="27cfe-107">活動的第一個階段發生於 Sales (銷售) 應用程式，第二個階段則發生於 Packaging & Assembly (包裝和組裝) 應用程式，最後由 Shipping (送貨) 應用程式提供送貨進度。</span><span class="sxs-lookup"><span data-stu-id="27cfe-107">The first part of the activity happens in the Sales application, the second part of the activity happens in the Packaging & Assembly application, and finally, the delivery progress is available in the Shipping application.</span></span> <span data-ttu-id="27cfe-108">每個應用程式目前的工作單位使用不同的識別碼： 購買訂單號碼 (PO)、 銷售訂單號碼 (SO) 和送貨單號碼 (UPS)。</span><span class="sxs-lookup"><span data-stu-id="27cfe-108">Each application uses different IDs for the current work unit: purchase order number (PO), sales order number (SO), and shipping order number (UPS).</span></span> <span data-ttu-id="27cfe-109">若要將兩個不同應用程式的事件相互關聯，您必須：</span><span class="sxs-lookup"><span data-stu-id="27cfe-109">To correlate the events between two different applications, you must:</span></span>  
  
- <span data-ttu-id="27cfe-110">識別接續 Token，這是兩個應用程式都能使用的唯一資料片段 (例如，彼此交換的訊息部分)。</span><span class="sxs-lookup"><span data-stu-id="27cfe-110">Identify the continuation token – a unique piece of data that is available to both applications (for example, the part of the message being exchanged).</span></span>  
  
- <span data-ttu-id="27cfe-111">在第一個應用程式中呼叫 EnableContinuation，並傳遞接續 Token 和目前的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="27cfe-111">Call EnableContinuation in the first application and pass the continuation token along with the current ActivityID.</span></span>  
  
- <span data-ttu-id="27cfe-112">請勿在第二個應用程式中呼叫 BeginActivity。</span><span class="sxs-lookup"><span data-stu-id="27cfe-112">Do not call BeginActivity in the second application.</span></span>  
  
- <span data-ttu-id="27cfe-113">在第二個應用程式中使用接續 Token 代替 ActivityID，引發所有後續事件。</span><span class="sxs-lookup"><span data-stu-id="27cfe-113">Fire all subsequent events in the second application by using the continuation token instead of ActivityID.</span></span>  
  
  <span data-ttu-id="27cfe-114">下列程式碼範例示範如何在三個應用程式之間使用活動接續：</span><span class="sxs-lookup"><span data-stu-id="27cfe-114">The following code example illustrates the use of activity continuation among three applications:</span></span>  
  
  <span data-ttu-id="27cfe-115">**訂單應用程式**</span><span class="sxs-lookup"><span data-stu-id="27cfe-115">**Purchase Order Application**</span></span>  
  
```  
string oID="PO#123";  
string soID="SO#265";  
es.BeginActivity("PurchaseOrder",poID);  
es.UpdateActivity("PurchaseOrder",poID,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
"CustomerCity","Seattle");  
es.EnableContinuation(  
   "PurchaseOrder",poId,soID);  
es.EndActivity("PurchaseOrder",poID);  
```  
  
 <span data-ttu-id="27cfe-116">**履行應用程式**</span><span class="sxs-lookup"><span data-stu-id="27cfe-116">**Fulfillment Application**</span></span>  
  
```  
string soID="SO#265";  
string upsID="UPS#97892";  
es.UpdateActivity("PurchaseOrder",soID,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","ProductA");  
es.EnableContinuation(  
   "PurchaseOrder",soID,upsID);  
es.EndActivity("PurchaseOrder",soID);  
```  
  
 <span data-ttu-id="27cfe-117">**傳送應用程式**</span><span class="sxs-lookup"><span data-stu-id="27cfe-117">**Shipping Application**</span></span>  
  
```  
string upsID="UPS#97892"  
es.UpdateActivity("PurchaseOrder", upsID,  
"POShipped",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",upsID)  
  
```  
  
 <span data-ttu-id="27cfe-118">請依循下列指導方針，在程式碼中使用活動接續：</span><span class="sxs-lookup"><span data-stu-id="27cfe-118">Follow these guidelines to use activity continuation in your code:</span></span>  
  
-   <span data-ttu-id="27cfe-119">除非使用者必須將不同應用程式的工作視為相同活動的一部分，否則切勿使用接續。</span><span class="sxs-lookup"><span data-stu-id="27cfe-119">Only use continuation when the end user must treat the work of different applications as part of the same activity.</span></span> <span data-ttu-id="27cfe-120">如果每個應用程式的工作對使用者而言是各有其意義的活動，每個應用程式均應使用不同的活動，然後建立活動關係。</span><span class="sxs-lookup"><span data-stu-id="27cfe-120">Use separate activities for each application and create an activity relationship if the end user views the work in each applications as meaningful activities.</span></span>  
  
-   <span data-ttu-id="27cfe-121">如果應用程式的工作單位並非一對一關係，則可使用活動關係但不應使用接續，例如，一張銷售訂單有數個送貨地點時。</span><span class="sxs-lookup"><span data-stu-id="27cfe-121">If the work units in the applications do not have a one-to-one relationship, you can use activity relationships but not continuation, for example, when multiple shipments exist for a sales order.</span></span>  
  
-   <span data-ttu-id="27cfe-122">若以同步方式將資料傳送至 BAM (使用 DirectEventStream)，且 ActivityID 傳遞至所有參與的元件，就不需要使用接續。</span><span class="sxs-lookup"><span data-stu-id="27cfe-122">If you send data to BAM synchronously (using DirectEventStream) and the ActivityID is propagated to all involved components, then you do not need to use continuation.</span></span>  
  
-   <span data-ttu-id="27cfe-123">若以非同步方式將資料傳送至 BAM (使用 BufferedEventStream 或透過協調流程)，則即使 ActivityID 傳遞至所有元件，仍然必須使用接續。</span><span class="sxs-lookup"><span data-stu-id="27cfe-123">If you send data to BAM asynchronously (using BufferedEventStream or from orchestrations), then you must use continuation even if the ActivityID is propagated to all components.</span></span> <span data-ttu-id="27cfe-124">在此情況下，每個應用程式必須使用不同的 ActivityID，所以請用唯一字串做為字首 (例如，加上應用程式名稱)。</span><span class="sxs-lookup"><span data-stu-id="27cfe-124">In this case, you need to use a different ActivityID in each application by prefixing it with a unique string (for example, Application Name).</span></span> <span data-ttu-id="27cfe-125">需要這麼做是因為，不同的應用程式可能以隨機順序將資料送達 BAM，而 BAM 必須隱藏失序的事件以確保查詢和彙總結果正確。</span><span class="sxs-lookup"><span data-stu-id="27cfe-125">This is necessary because the data from different applications may arrive to BAM in random order and BAM has to hide the out-of-order events to ensure correct query and aggregation results.</span></span>  
  
-   <span data-ttu-id="27cfe-126">使用接續的應用程式不需要重新撰寫就能交換更多資料。</span><span class="sxs-lookup"><span data-stu-id="27cfe-126">Continuation does not require rewriting your applications to exchange more data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27cfe-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27cfe-127">See Also</span></span>  
  
 <span data-ttu-id="27cfe-128">[BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="27cfe-128">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="27cfe-129">[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md) </span><span class="sxs-lookup"><span data-stu-id="27cfe-129">[BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md) </span></span>  
 [<span data-ttu-id="27cfe-130">BAM 端對端 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="27cfe-130">BAM End-to-End (BizTalk Server Sample)</span></span>](../core/bam-end-to-end-biztalk-server-sample.md)