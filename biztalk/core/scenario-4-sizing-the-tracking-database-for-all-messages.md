---
title: 案例 4： 所有訊息調整追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: db1126c7-0b86-4635-bfdc-3b69a82cc64b
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 327953843b2d9b70f500796f43302320924a330c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-4-sizing-the-tracking-database-for-all-messages"></a><span data-ttu-id="db3fb-102">實例 4：為所有訊息調整追蹤資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="db3fb-102">Scenario 4: Sizing the Tracking Database for all Messages</span></span>
<span data-ttu-id="db3fb-103">若您在 Microsoft® BizTalk Server® 2004 實作中共有三個訊息實例，您將需要將所有實例結果相加以決定 BizTalk 追蹤資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="db3fb-103">If you had all three message scenarios present in a Microsoft® BizTalk Server® 2004 implementation, you would need to add together all of the scenario results to determine the size of the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="db3fb-104">在上方所示的範例中：</span><span class="sxs-lookup"><span data-stu-id="db3fb-104">From the examples shown above:</span></span>  
  
|<span data-ttu-id="db3fb-105">狀況</span><span class="sxs-lookup"><span data-stu-id="db3fb-105">Scenario</span></span>|<span data-ttu-id="db3fb-106">每年所需的空間，以 GB 為單位</span><span class="sxs-lookup"><span data-stu-id="db3fb-106">Space required, per year, in GB</span></span>|  
|--------------|-------------------------------------|  
|<span data-ttu-id="db3fb-107">範例訊息</span><span class="sxs-lookup"><span data-stu-id="db3fb-107">Simple messages</span></span>|<span data-ttu-id="db3fb-108">4.78</span><span class="sxs-lookup"><span data-stu-id="db3fb-108">4.78</span></span>|  
|<span data-ttu-id="db3fb-109">協調流程中的訊息</span><span class="sxs-lookup"><span data-stu-id="db3fb-109">Messages in orchestrations</span></span>|<span data-ttu-id="db3fb-110">7.18</span><span class="sxs-lookup"><span data-stu-id="db3fb-110">7.18</span></span>|  
|<span data-ttu-id="db3fb-111">協調流程中傳送至通訊群組清單的訊息</span><span class="sxs-lookup"><span data-stu-id="db3fb-111">Messages in orchestrations sent out to distribution lists</span></span>|<span data-ttu-id="db3fb-112">10.8</span><span class="sxs-lookup"><span data-stu-id="db3fb-112">10.8</span></span>|  
|<span data-ttu-id="db3fb-113">**總計**</span><span class="sxs-lookup"><span data-stu-id="db3fb-113">**Total**</span></span>|<span data-ttu-id="db3fb-114">22.04</span><span class="sxs-lookup"><span data-stu-id="db3fb-114">22.04</span></span>|  
  
 <span data-ttu-id="db3fb-115">此外，若我們為所有三個實例開啟訊息內文追蹤，將取得以下結果：</span><span class="sxs-lookup"><span data-stu-id="db3fb-115">In addition, if we turn on message body tracking for all three scenarios, we would get the following results:</span></span>  
  
|<span data-ttu-id="db3fb-116">狀況</span><span class="sxs-lookup"><span data-stu-id="db3fb-116">Scenario</span></span>|<span data-ttu-id="db3fb-117">每年所需的空間，以 GB 為單位</span><span class="sxs-lookup"><span data-stu-id="db3fb-117">Space required, per year, in GB</span></span>|  
|--------------|-------------------------------------|  
|<span data-ttu-id="db3fb-118">範例訊息</span><span class="sxs-lookup"><span data-stu-id="db3fb-118">Simple messages</span></span>|<span data-ttu-id="db3fb-119">50.1</span><span class="sxs-lookup"><span data-stu-id="db3fb-119">50.1</span></span>|  
|<span data-ttu-id="db3fb-120">協調流程中的訊息</span><span class="sxs-lookup"><span data-stu-id="db3fb-120">Messages in orchestrations</span></span>|<span data-ttu-id="db3fb-121">50.1</span><span class="sxs-lookup"><span data-stu-id="db3fb-121">50.1</span></span>|  
|<span data-ttu-id="db3fb-122">協調流程中傳送至通訊群組清單的訊息</span><span class="sxs-lookup"><span data-stu-id="db3fb-122">Messages in orchestrations sent out to distribution lists</span></span>|<span data-ttu-id="db3fb-123">83.45</span><span class="sxs-lookup"><span data-stu-id="db3fb-123">83.45</span></span>|  
|<span data-ttu-id="db3fb-124">**總計**</span><span class="sxs-lookup"><span data-stu-id="db3fb-124">**Total**</span></span>|<span data-ttu-id="db3fb-125">183.65</span><span class="sxs-lookup"><span data-stu-id="db3fb-125">183.65</span></span>|  
  
 <span data-ttu-id="db3fb-126">BizTalk 追蹤資料庫總計每年將成長 205.69 GB。</span><span class="sxs-lookup"><span data-stu-id="db3fb-126">This would give you a grand total of 205.69 GB per year growth on the BizTalk Tracking database.</span></span> <span data-ttu-id="db3fb-127">此圖不包括任何偶發事件。</span><span class="sxs-lookup"><span data-stu-id="db3fb-127">This figure does not include any contingency.</span></span> <span data-ttu-id="db3fb-128">若您決定按照建議將 10% 的偶發事件加到此總計，則您應規劃 BizTalk 追蹤資料庫每年成長 227.94 GB。</span><span class="sxs-lookup"><span data-stu-id="db3fb-128">If you decided to add a contingency of 10 percent to this total, as is recommended, then you should plan on the BizTalk Tracking database growing 227.94 GB per year.</span></span> <span data-ttu-id="db3fb-129">在頂端，您應該考慮因 SQL 索引、 儲存體和其他內容的額外負荷。您應該盡可能執行中測試的測試案例後，根據相乘因素。</span><span class="sxs-lookup"><span data-stu-id="db3fb-129">On top of this, you should consider the overhead due to SQL indices, storage, etc. You should base your multiplying factor after running the test scenarios in test if possible.</span></span>  
  
## <a name="other-factors-affecting-biztalk-tracking-database-size"></a><span data-ttu-id="db3fb-130">其他影響 BizTalk 追蹤資料庫大小的因素</span><span class="sxs-lookup"><span data-stu-id="db3fb-130">Other factors affecting BizTalk Tracking database size</span></span>  
 <span data-ttu-id="db3fb-131">有一些其他項目 (例如協調流程中所使用的圖形) 也會影響 BizTalk 追蹤資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="db3fb-131">There are other items, such as the shapes used within an orchestration that also affect the size of the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="db3fb-132">若您已開啟協調流程偵錯工具選項 (預設為開啟)，協調流程中每個圖形的狀態會儲存到 BizTalk 追蹤資料庫。</span><span class="sxs-lookup"><span data-stu-id="db3fb-132">If the orchestration debugger option is turned on, which it is by default, the status of each shape in the orchestration is saved to the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="db3fb-133">決定追蹤圖形狀態所需大小的公式為：</span><span class="sxs-lookup"><span data-stu-id="db3fb-133">The formula to determine the size needed to track shape status is:</span></span>  
  
```  
[(# of object shapes ] * 76 bytes  
```  
  
 <span data-ttu-id="db3fb-134">例如，在下圖中，您將使用下列公式來決定 BizTalk 追蹤資料庫的大小：</span><span class="sxs-lookup"><span data-stu-id="db3fb-134">For example, in the following figure, you would use the following formula to determine the BizTalk Tracking size:</span></span>  
  
```  
((4) * 76 bytes = 304 bytes  
```  
  
 <span data-ttu-id="db3fb-135">![協調流程範例](../core/media/sample-orchestration.gif "Sample_orchestration")</span><span class="sxs-lookup"><span data-stu-id="db3fb-135">![Orchestration Example](../core/media/sample-orchestration.gif "Sample_orchestration")</span></span>  
  
 <span data-ttu-id="db3fb-136">假設此協調流程處理了三百五十萬個訊息，則追蹤此協調流程所需的額外空間為：</span><span class="sxs-lookup"><span data-stu-id="db3fb-136">If we assume that this orchestration processes 3.5 million messages, the additional space needed to track this orchestration would be:</span></span>  
  
```  
304 bytes * 3,500,000/1024/1024 = 1015 MB ~ 0.99 GB.  
```  
  
 <span data-ttu-id="db3fb-137">您需要將每個協調流程偵錯工具設為 [開啟] 的協調流程納入計算，才能決定 BizTalk 追蹤資料庫的大約大小。</span><span class="sxs-lookup"><span data-stu-id="db3fb-137">You will need to account for each orchestration that has the orchestration debugger set to "on" to get an approximate size for the BizTalk Tracking database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db3fb-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db3fb-138">See Also</span></span>  
 <span data-ttu-id="db3fb-139">[使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="db3fb-139">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="db3fb-140">[追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="db3fb-140">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="db3fb-141">[案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="db3fb-141">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="db3fb-142">[案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="db3fb-142">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="db3fb-143">案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小</span><span class="sxs-lookup"><span data-stu-id="db3fb-143">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)