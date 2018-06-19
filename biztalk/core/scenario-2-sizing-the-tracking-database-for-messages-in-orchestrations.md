---
title: 案例 2： 在協調流程中的訊息調整追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: d1cfb8b9-d4e2-4069-8db3-18f72358652b
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62ea6e463dfb3a44e2628f57b632634d7a9bd212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269830"
---
# <a name="scenario-2-sizing-the-tracking-database--for-messages-in-orchestrations"></a><span data-ttu-id="1fe5e-102">實例 2：為協調流程中的訊息調整追蹤資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="1fe5e-102">Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations</span></span>
<span data-ttu-id="1fe5e-103">讓我們看一個包括協調流程的範例。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-103">Let's look at an example that includes an orchestration.</span></span> <span data-ttu-id="1fe5e-104">下圖顯示整個商務程序。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-104">The following figure displays the entire business process.</span></span> <span data-ttu-id="1fe5e-105">在此實例中，一個訊息進入 BizTalk Server，透過協調流程傳送，在協調流程中變更，然後透過傳送埠傳送出去。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-105">In this scenario, a message comes into BizTalk Server, is sent through an orchestration, is changed within the orchestration, and is then sent out through a send port.</span></span>  
  
 <span data-ttu-id="1fe5e-106">![BizTalk Server 訊息程序](../core/media/biztalk-server-message-process.gif "BizTalk_Server_Message_Process")</span><span class="sxs-lookup"><span data-stu-id="1fe5e-106">![BizTalk Server message process](../core/media/biztalk-server-message-process.gif "BizTalk_Server_Message_Process")</span></span>  
  
 <span data-ttu-id="1fe5e-107">**BizTalk Server 訊息程序**</span><span class="sxs-lookup"><span data-stu-id="1fe5e-107">**The BizTalk Server message process**</span></span>  
  
 <span data-ttu-id="1fe5e-108">以下是與此實例相關的事實：</span><span class="sxs-lookup"><span data-stu-id="1fe5e-108">Here are some of the facts concerning this scenario:</span></span>  
  
-   <span data-ttu-id="1fe5e-109">訊息大小為 5K。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-109">The message size is 5K.</span></span>  
  
-   <span data-ttu-id="1fe5e-110">我們未升級任何屬性。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-110">We are not promoting any properties.</span></span>  
  
-   <span data-ttu-id="1fe5e-111">我們一年內所接收的訊息數目為三百五十萬。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-111">The number of messages we receive in a year is 3.5 million.</span></span>  
  
-   <span data-ttu-id="1fe5e-112">開啟所有事件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-112">Tracking is turned on for all events.</span></span> <span data-ttu-id="1fe5e-113">在此實例中有 6 個事件：</span><span class="sxs-lookup"><span data-stu-id="1fe5e-113">There are six events in this scenario:</span></span>  
  
    -   <span data-ttu-id="1fe5e-114">收到訊息 M0</span><span class="sxs-lookup"><span data-stu-id="1fe5e-114">Receipt of message M0</span></span>  
  
    -   <span data-ttu-id="1fe5e-115">接收埠輸出訊息 M1</span><span class="sxs-lookup"><span data-stu-id="1fe5e-115">Output of message M1 from the receive port</span></span>  
  
    -   <span data-ttu-id="1fe5e-116">協調流程收到訊息 M1</span><span class="sxs-lookup"><span data-stu-id="1fe5e-116">Receipt of message M1 by the orchestration</span></span>  
  
    -   <span data-ttu-id="1fe5e-117">協調流程輸出訊息 M2</span><span class="sxs-lookup"><span data-stu-id="1fe5e-117">Output of message M2 from the orchestration</span></span>  
  
    -   <span data-ttu-id="1fe5e-118">傳送埠收到訊息 M2</span><span class="sxs-lookup"><span data-stu-id="1fe5e-118">Receipt of message M2 by the send port</span></span>  
  
    -   <span data-ttu-id="1fe5e-119">傳送管線輸出訊息 M3</span><span class="sxs-lookup"><span data-stu-id="1fe5e-119">Output of message M3 by the send pipeline</span></span>  
  
-   <span data-ttu-id="1fe5e-120">在此實例中建立了三個額外的訊息。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-120">Three additional messages are created in this scenario.</span></span> <span data-ttu-id="1fe5e-121">訊息 M0 是內送訊息，因此並不是由 BizTalk Server 所建立。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-121">Message M0 is the incoming message and is therefore not created by BizTalk Server.</span></span> <span data-ttu-id="1fe5e-122">訊息 M1 是來自接收埠的輸出訊息、M2 是來自協調流程的輸出訊息，而 M3 則是來自傳輸埠的輸出訊息。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-122">Message M1 is the output message from the receive port, M2 is the output message from the orchestration, and M3 is the output message from the transmit port.</span></span>  
  
 <span data-ttu-id="1fe5e-123">將此資訊套用至公式會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="1fe5e-123">Applying this information to the formula gives the following result:</span></span>  
  
```  
[(3*150 bytes) + (6*230 bytes) + (0*0(52 bytes + 0) * 3,500,000]/1024/1024  
[(450 + 1380 + 0) * 3,500,000]/1024/1024 = 6108 MB ~ 5.96 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-a-single-promoted-property"></a><span data-ttu-id="1fe5e-124">協調流程中含有單一升級屬性的訊息</span><span class="sxs-lookup"><span data-stu-id="1fe5e-124">Messages in orchestrations with a single promoted property</span></span>  
 <span data-ttu-id="1fe5e-125">現在讓我們來升級此實例中的單一欄位，就如先前範例所執行。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-125">Now let's promote a single field in this scenario, as in the earlier example.</span></span> <span data-ttu-id="1fe5e-126">升級的屬性約為 10 個位元組大小。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-126">The promoted property is approximately 10 bytes in size.</span></span> <span data-ttu-id="1fe5e-127">方程式現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="1fe5e-127">The equation now looks like this:</span></span>  
  
```  
[((3*150 bytes) + (6*230 bytes) + (1*3*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 186) * 3,500,000]/1024/1024 = 6729 MB ~ 6.57 GB per year  
```  
  
 <span data-ttu-id="1fe5e-128">若您需要升級 20 個位元組大小的其他屬性，則公式現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="1fe5e-128">If you need to promote an additional property that is 20 bytes in size, the formula now looks like this:</span></span>  
  
```  
[(3*150 bytes) + (6*230 bytes) + ((1*3*(52 bytes + 10 bytes) + (1*3*(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 372) * 3,500,000]/1024/1024 = 7350 MB ~ 7.18 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-message-body-tracking-activated"></a><span data-ttu-id="1fe5e-129">協調流程中已啟動訊息內文追蹤的訊息</span><span class="sxs-lookup"><span data-stu-id="1fe5e-129">Messages in orchestrations with message body tracking activated</span></span>  
 <span data-ttu-id="1fe5e-130">若您要啟動訊息追蹤，則計算所需額外空間的結果會與先前實例的結果相同，或為每年 50.1 GB。</span><span class="sxs-lookup"><span data-stu-id="1fe5e-130">If you want to accommodate message tracking, the result from calculating the additional space needed is identical to the result in the earlier scenario, or 50.1 GB per year.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fe5e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fe5e-131">See Also</span></span>  
 <span data-ttu-id="1fe5e-132">[使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="1fe5e-132">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="1fe5e-133">[追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="1fe5e-133">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="1fe5e-134">[案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1fe5e-134">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="1fe5e-135">[案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1fe5e-135">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="1fe5e-136">案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小</span><span class="sxs-lookup"><span data-stu-id="1fe5e-136">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)