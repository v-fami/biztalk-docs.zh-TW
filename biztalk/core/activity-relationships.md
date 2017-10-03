---
title: "活動關係 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: activities [BAM], relationships
ms.assetid: da7c7205-18c6-44df-af03-3140214c84e6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3709ad02ed082595665c68485502847b52e5a1d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="activity-relationships"></a><span data-ttu-id="d6e8d-102">活動關係</span><span class="sxs-lookup"><span data-stu-id="d6e8d-102">Activity Relationships</span></span>
<span data-ttu-id="d6e8d-103">當活動與一或多個其他活動相關聯時，便存在活動關係，</span><span class="sxs-lookup"><span data-stu-id="d6e8d-103">An activity relationship exists when an activity relates to one or more other activities.</span></span> <span data-ttu-id="d6e8d-104">例如，多個「出貨」活動與單一「訂單」活動相關聯，或者一個「出貨」活動包含兩個「訂單」活動的項目。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-104">An example of this is having multiple Shipment activities related to a single Purchase Order activity, or one Shipment activity containing items from two Purchase Order activities.</span></span>  
  
 <span data-ttu-id="d6e8d-105">若要指示兩個相關的活動，您必須知道兩個活動的名稱，並且在記憶體中具有對應的 ActivityID 以便呼叫 AddRelatedActivity。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-105">To indicate that two activities are related, you need to know both names and have the corresponding ActivityIDs in memory in order to call AddRelatedActivity.</span></span> <span data-ttu-id="d6e8d-106">這個 API 會在對應的活動記錄之間建立連結。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-106">This API creates the link between the corresponding activity records.</span></span>  
  
 <span data-ttu-id="d6e8d-107">在下圖中，反白的程式碼行說明您可以用何種方式在「訂單」活動執行個體 #123 以及「出貨」活動 #1549、1550 和 1551 之間建立關係。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-107">In the following figure, the highlighted lines of code show how you make a relationship between Purchase Order activity instance #123, and Shipment activities #1549, 1550, and 1551.</span></span>  
  
 ![](../core/media/activity-relationships-example.gif "activity_relationships_example")  
  
 <span data-ttu-id="d6e8d-108">商務使用者會查看一個顯示訂單歷程記錄的網頁。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-108">The business end user looks at one Web page that shows the history of a purchase order.</span></span> <span data-ttu-id="d6e8d-109">它可能表示上午 10</span><span class="sxs-lookup"><span data-stu-id="d6e8d-109">It may indicate that at 10 A.M.</span></span> <span data-ttu-id="d6e8d-110">到達時加以、 兩天後收到核准，和頁面會提供實際文件的連結。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-110">it arrives, two days later it receives approval, and the page provides a link to the actual documents.</span></span> <span data-ttu-id="d6e8d-111">網頁也會因為上圖中的程式碼，提供可將商務使用者導向對應的出貨網頁的超連結。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-111">Because of the code in the previous figure, the page will also provide hyperlinks that take the business end user to the corresponding shipment Web pages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6e8d-112">所有呼叫`AddRelatedActivity`之間應該發生`BeginActivity`和`EndActivity`。</span><span class="sxs-lookup"><span data-stu-id="d6e8d-112">All calls to `AddRelatedActivity` should happen between `BeginActivity` and `EndActivity`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6e8d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6e8d-113">See Also</span></span>  
  
 <span data-ttu-id="d6e8d-114">[活動接續](../core/activity-continuation.md) </span><span class="sxs-lookup"><span data-stu-id="d6e8d-114">[Activity Continuation](../core/activity-continuation.md) </span></span>  
 <span data-ttu-id="d6e8d-115">[BAM 動態基礎結構](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="d6e8d-115">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="d6e8d-116">[BAM API （BizTalk Server 範例）](../core/bam-api-biztalk-server-sample.md) </span><span class="sxs-lookup"><span data-stu-id="d6e8d-116">[BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md) </span></span>  
 [<span data-ttu-id="d6e8d-117">BAM API，從協調流程運算式 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="d6e8d-117">BAM API from an Orchestration Expression (BizTalk Server Sample)</span></span>](../core/bam-api-from-an-orchestration-expression-biztalk-server-sample.md)