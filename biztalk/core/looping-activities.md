---
title: 迴圈活動 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- activities [BAM], looping activities
- activities [BAM], orchestrations
- orchestrations, looping
- orchestrations, activities
ms.assetid: fb40fdd0-ac8f-486a-b3d0-9d2200a87cda
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18cf2b768deca72b281bc189431b01f5e63a4887
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005065"
---
# <a name="looping-activities"></a><span data-ttu-id="19483-102">迴圈活動</span><span class="sxs-lookup"><span data-stu-id="19483-102">Looping Activities</span></span>
<span data-ttu-id="19483-103">迴圈活動是指，在協調流程中迴圈的動作。</span><span class="sxs-lookup"><span data-stu-id="19483-103">Looping activities refers to actions that loop within an orchestration.</span></span> <span data-ttu-id="19483-104">您也許可以從協調流程內迴圈的動作擷取事件。</span><span class="sxs-lookup"><span data-stu-id="19483-104">It is possible to capture the events from actions that loop within an orchestration.</span></span> <span data-ttu-id="19483-105">若要執行這項操作，請建立其他活動，並對應迴圈內所有的新活動里程碑和資料。</span><span class="sxs-lookup"><span data-stu-id="19483-105">To do this, you create another activity and map all of the new activity milestones and data inside the loop.</span></span> <span data-ttu-id="19483-106">請務必這麼做，因為迴圈中的資料處理將會在每個排程執行發生一次以上。</span><span class="sxs-lookup"><span data-stu-id="19483-106">This is necessary because the data processing in the loop will occur more than once per scheduled execution.</span></span> <span data-ttu-id="19483-107">下圖顯示此情況的範例。</span><span class="sxs-lookup"><span data-stu-id="19483-107">The following figure shows an example of this situation.</span></span>  
  
 <span data-ttu-id="19483-108">![](../core/media/handlingloops2.gif "handlingloops2")</span><span class="sxs-lookup"><span data-stu-id="19483-108">![](../core/media/handlingloops2.gif "handlingloops2")</span></span>  
  
 <span data-ttu-id="19483-109">如圖所示，如果您有 「 訂單處理迴圈中的多個明細項目使用，像是 「 哪個訂單有項目價格為 $100？ 」</span><span class="sxs-lookup"><span data-stu-id="19483-109">As shown in the figure, if you have a Purchase Order with multiple Line Items that process in a loop, questions like "Which purchase orders have item prices of $100?"</span></span> <span data-ttu-id="19483-110">是模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="19483-110">are ambiguous.</span></span> <span data-ttu-id="19483-111">明確的問題如下：</span><span class="sxs-lookup"><span data-stu-id="19483-111">Unambiguous questions are:</span></span>  
  
- <span data-ttu-id="19483-112">哪個訂單的明細項目價格為 $100?</span><span class="sxs-lookup"><span data-stu-id="19483-112">Which purchase orders have line items with a price of $100?</span></span>  
  
- <span data-ttu-id="19483-113">哪個訂單的總計/最小/最大項目價格為 $100?</span><span class="sxs-lookup"><span data-stu-id="19483-113">Which purchase orders have Total/Min/Max item prices of $100?</span></span>  
  
  <span data-ttu-id="19483-114">建立明確的問題必須將明細項目與訂單當做兩回事來思考。</span><span class="sxs-lookup"><span data-stu-id="19483-114">Creating unambiguous questions requires thinking of the line items as something separate from the purchase order.</span></span> <span data-ttu-id="19483-115">在追蹤設定檔編輯器中，根活動 (例如訂單) 會對應至迴圈外的所有動作。</span><span class="sxs-lookup"><span data-stu-id="19483-115">In the Tracking Profile Editor, the root activity (for example, a purchase order) maps to all actions outside the loop.</span></span> <span data-ttu-id="19483-116">子活動 (例如明細項目) 會對應至迴圈內的動作。</span><span class="sxs-lookup"><span data-stu-id="19483-116">The child activity (for example, line item) maps to the actions inside the loop.</span></span>  
  
  <span data-ttu-id="19483-117">您需要使用內容項目當做根活動的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="19483-117">You need to use a payload item as ActivityID for the root activity.</span></span> <span data-ttu-id="19483-118">讓這個內容項目可以用在迴圈內部的某些訊息中。</span><span class="sxs-lookup"><span data-stu-id="19483-118">Have this payload item available in some of the messages inside the loop.</span></span> <span data-ttu-id="19483-119">請將活動對應至子活動底下顯示的關係節點，並將該活動命名為根活動。</span><span class="sxs-lookup"><span data-stu-id="19483-119">Map the activity to the Relationship node that displays under the child activity and name it as the root activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19483-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19483-120">See Also</span></span>  
 [<span data-ttu-id="19483-121">使用事件資料流實作 BAM 活動</span><span class="sxs-lookup"><span data-stu-id="19483-121">Implementing BAM Activities with Event Streams</span></span>](../core/implementing-bam-activities-with-event-streams.md)