---
title: 案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: 5b8fed48-d9c9-4d1f-a320-d3e23b8b1ec9
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9c99c99485e34f95c6f6a75b86170d73678518
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-1-sizing-the-tracking-database--for-simple-biztalk-messages"></a><span data-ttu-id="25671-102">實例 1：針對範例 BizTalk 訊息調整追蹤資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="25671-102">Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages</span></span>
<span data-ttu-id="25671-103">在下圖中，簡易 BizTalk Server 訊息不需經過任何訊息轉換即可在 BizTalk Server 傳入和傳出。</span><span class="sxs-lookup"><span data-stu-id="25671-103">In the following figure, a simple BizTalk Server message passes in and out of BizTalk Server without undergoing any message transformation.</span></span>  
  
 <span data-ttu-id="25671-104">![簡易 BizTalk Server 訊息 &#45;不需轉換](../core/media/simple-bts-message.gif "Simple_BTS_Message")</span><span class="sxs-lookup"><span data-stu-id="25671-104">![Simple BizTalk Server message &#45; no transformation](../core/media/simple-bts-message.gif "Simple_BTS_Message")</span></span>  
  
 <span data-ttu-id="25671-105">**簡單的 BizTalk Server 訊息-不需轉換**</span><span class="sxs-lookup"><span data-stu-id="25671-105">**A simple BizTalk Server message - no transformation**</span></span>  
  
 <span data-ttu-id="25671-106">在您套用前一節的公式之前，需要收集此實例的一些相關事實。</span><span class="sxs-lookup"><span data-stu-id="25671-106">Before you apply the formula in the previous section, you will need to gather some facts about this scenario.</span></span> <span data-ttu-id="25671-107">在此範例中，將使用下列項目：</span><span class="sxs-lookup"><span data-stu-id="25671-107">In this example, we use the following:</span></span>  
  
-   <span data-ttu-id="25671-108">訊息大小為 5K。</span><span class="sxs-lookup"><span data-stu-id="25671-108">The message size is 5K.</span></span>  
  
-   <span data-ttu-id="25671-109">不會升級屬性。</span><span class="sxs-lookup"><span data-stu-id="25671-109">No properties will be promoted.</span></span>  
  
-   <span data-ttu-id="25671-110">您一年內所接收的訊息數目為三百五十萬。</span><span class="sxs-lookup"><span data-stu-id="25671-110">The number of messages you receive in a year is 3.5 million.</span></span>  
  
-   <span data-ttu-id="25671-111">開啟所有事件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="25671-111">Tracking is turned on for all events.</span></span> <span data-ttu-id="25671-112">在此實例中有 4 個事件。</span><span class="sxs-lookup"><span data-stu-id="25671-112">There are four events in this scenario.</span></span> <span data-ttu-id="25671-113">這些事件為：</span><span class="sxs-lookup"><span data-stu-id="25671-113">The events are:</span></span>  
  
    -   <span data-ttu-id="25671-114">收到訊息 M0</span><span class="sxs-lookup"><span data-stu-id="25671-114">Receipt of message M0</span></span>  
  
    -   <span data-ttu-id="25671-115">接收埠輸出訊息 M1</span><span class="sxs-lookup"><span data-stu-id="25671-115">Output of message M1 from the receive port</span></span>  
  
    -   <span data-ttu-id="25671-116">傳輸管線收到訊息 M1</span><span class="sxs-lookup"><span data-stu-id="25671-116">Receipt of message M1 by the transmit pipeline</span></span>  
  
    -   <span data-ttu-id="25671-117">傳送管線輸出訊息 M2</span><span class="sxs-lookup"><span data-stu-id="25671-117">Output of message M2 by the send pipeline</span></span>  
  
-   <span data-ttu-id="25671-118">在此實例中建立了兩個額外的訊息。</span><span class="sxs-lookup"><span data-stu-id="25671-118">Two additional messages are created in this scenario.</span></span> <span data-ttu-id="25671-119">訊息 M0 是內送訊息，因此並不是由 BizTalk Server 所建立。</span><span class="sxs-lookup"><span data-stu-id="25671-119">Message M0 is the incoming message and is therefore not created by BizTalk Server.</span></span> <span data-ttu-id="25671-120">訊息 M1 是來自接收埠的輸出訊息，而 M2 是來自傳輸埠的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="25671-120">Message M1 is the output message from the receive port and M2 is the output from the transmit port.</span></span> <span data-ttu-id="25671-121">M1 和 M2 是由 BizTalk Server 所建立。</span><span class="sxs-lookup"><span data-stu-id="25671-121">M1 and M2 are created by BizTalk Server.</span></span>  
  
 <span data-ttu-id="25671-122">將此資訊套用至公式會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="25671-122">Applying this information to the formula gives the following:</span></span>  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-with-a-single-promoted-property"></a><span data-ttu-id="25671-123">含有單一升級屬性的訊息</span><span class="sxs-lookup"><span data-stu-id="25671-123">Messages with a single promoted property</span></span>  
 <span data-ttu-id="25671-124">請再看一次這個範例，並新增另一個事實到實例中。</span><span class="sxs-lookup"><span data-stu-id="25671-124">Let's take another look at this example and add one additional fact to the scenario.</span></span> <span data-ttu-id="25671-125">您想要從原始訊息升級單一欄位，欄位大小約為 10 個位元組。</span><span class="sxs-lookup"><span data-stu-id="25671-125">You want to promote a single field, approximately 10 bytes in size, from the original message.</span></span> <span data-ttu-id="25671-126">升級的欄位大小上限為 256 個字元，或大約 256 個位元組 (若字元是 Unicode，則為 512 個位元組)。</span><span class="sxs-lookup"><span data-stu-id="25671-126">The maximum size of a promoted field is 256 characters, or approximately 256 bytes (512 bytes if the characters are Unicode).</span></span>  
  
 <span data-ttu-id="25671-127">新增此額外的事實後，方程式現在看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="25671-127">With this additional fact, the equation now appears as follows:</span></span>  
  
```  
[(2*150 bytes) + (4*230 bytes) + (1*2(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 124) * 3,500,000]/1024/1024 = 4486 MB ~ 4.38 GB per year  
```  
  
 <span data-ttu-id="25671-128">若您要升級 10 個位元組大小的額外欄位，方程式將如下所示：</span><span class="sxs-lookup"><span data-stu-id="25671-128">If you wanted to promote an additional field that is 10 bytes in size, the equation would be:</span></span>  
  
```  
[(2*150 bytes) + (4*230 bytes) + ((1*2*(52 bytes + 10 bytes) + (1*2*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(300 + 920 + 248) * 3,500,000]/1024/1024 = 4899 MB ~ 4.78 GB per year  
```  
  
 <span data-ttu-id="25671-129">如您所見，若您在此實例中升級一個 10 個位元組的屬性，將會使 BizTalk 追蹤資料庫每年增加 333.79 MB 到 0.33 GB 的大小。</span><span class="sxs-lookup"><span data-stu-id="25671-129">As you can see, if you promote a single 10-byte property in this scenario, it will add an additional 333.79 MB ~ 0.33 GB per year to the size of the BizTalk Tracking database.</span></span>  
  
 <span data-ttu-id="25671-130">若升級兩個 10 個位元組的屬性，將會使 BizTalk 追蹤資料庫每年增加 667.58 MB 到 0.65 GB 的額外空間大小。</span><span class="sxs-lookup"><span data-stu-id="25671-130">Promoting two 10-byte properties will add an additional 667.58 MB ~ 0.65 GB of additional space per year to the size of the BizTalk Tracking database.</span></span>  
  
## <a name="messages-with-message-body-tracking-activated"></a><span data-ttu-id="25671-131">已啟動訊息內文追蹤的訊息</span><span class="sxs-lookup"><span data-stu-id="25671-131">Messages with message body tracking activated</span></span>  
 <span data-ttu-id="25671-132">在此範例中，假設我們正計劃啟動訊息內文追蹤。</span><span class="sxs-lookup"><span data-stu-id="25671-132">In this example, let us also assume that we are planning on activating message body tracking.</span></span> <span data-ttu-id="25671-133">這將需要新增第二個訊息追蹤方程式，如上一節所示。</span><span class="sxs-lookup"><span data-stu-id="25671-133">We will need to add the second equation for message tracking, shown in the previous section.</span></span> <span data-ttu-id="25671-134">此範例的方程式看起來將如下所示：</span><span class="sxs-lookup"><span data-stu-id="25671-134">The equation will look like the following for this example:</span></span>  
  
```  
[3,500,000 * 4 * 5KB]/1024 = 68359.375 MB ~ 66.75 GB per year  
  
```  
  
 <span data-ttu-id="25671-135">在新增兩個方程式的結果後，可以預估 BizTalk 追蹤資料庫每年將成長大約 54.48 GB 到 54.88 GB。</span><span class="sxs-lookup"><span data-stu-id="25671-135">By adding the results of the two equations, we can estimate that the BizTalk Tracking database will grow approximately 54.48 GB to 54.88 GB per year.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25671-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25671-136">See Also</span></span>  
 <span data-ttu-id="25671-137">[使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="25671-137">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="25671-138">[追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="25671-138">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="25671-139">[案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="25671-139">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 <span data-ttu-id="25671-140">[案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="25671-140">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="25671-141">案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小</span><span class="sxs-lookup"><span data-stu-id="25671-141">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)