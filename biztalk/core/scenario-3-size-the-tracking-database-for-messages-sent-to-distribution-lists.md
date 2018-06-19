---
title: 案例 3： 調整追蹤資料庫大小的訊息傳送至通訊群組清單的 Out |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Tracking database, database size
ms.assetid: bc6e0da0-46d1-42d6-8ec9-29a28719fbb3
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dca1722e24e0c76c85699ea00fcf6ffc120b2e14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271102"
---
# <a name="scenario-3-sizing-the-tracking-database--for-messages-sent-out-to-distribution-lists"></a><span data-ttu-id="a98b1-102">實例 3：為外送到通訊群組清單之訊息的追蹤資料庫設定大小</span><span class="sxs-lookup"><span data-stu-id="a98b1-102">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>
<span data-ttu-id="a98b1-103">在下圖中，有一個透過協調流程繼續的訊息在協調流程中變更了，而且已透過通訊群組清單傳送到數個不同的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="a98b1-103">In the following figure, you have a message that proceeds through an orchestration, is changed within the orchestration, and is then sent out to several different send ports through a distribution list.</span></span>  
  
 <span data-ttu-id="a98b1-104">![透過多個連接埠至協調流程訊息](../core/media/biztalk-server-message-orch-multiple-ports.gif "BizTalk_Server_message_orch_multiple_ports")</span><span class="sxs-lookup"><span data-stu-id="a98b1-104">![Message through an orchestration to multiple ports](../core/media/biztalk-server-message-orch-multiple-ports.gif "BizTalk_Server_message_orch_multiple_ports")</span></span>  
  
 <span data-ttu-id="a98b1-105">**透過協調流程，並且在送出至數個不同的連接埠的 BizTalk Server 訊息**</span><span class="sxs-lookup"><span data-stu-id="a98b1-105">**BizTalk Server message that proceeds through an orchestration and is sent out to several different ports**</span></span>  
  
 <span data-ttu-id="a98b1-106">以下是與此實例相關的事實：</span><span class="sxs-lookup"><span data-stu-id="a98b1-106">Here are some of the facts concerning this scenario:</span></span>  
  
-   <span data-ttu-id="a98b1-107">訊息大小是 10 K。</span><span class="sxs-lookup"><span data-stu-id="a98b1-107">The message size is 10K.</span></span>  
  
-   <span data-ttu-id="a98b1-108">您未升級任何屬性。</span><span class="sxs-lookup"><span data-stu-id="a98b1-108">You are not promoting any properties.</span></span>  
  
-   <span data-ttu-id="a98b1-109">您一年內所接收的訊息數目為三百五十萬。</span><span class="sxs-lookup"><span data-stu-id="a98b1-109">The number of messages you receive in a year is 3.5 million.</span></span>  
  
-   <span data-ttu-id="a98b1-110">開啟所有事件的追蹤。</span><span class="sxs-lookup"><span data-stu-id="a98b1-110">Tracking is turned on for all events.</span></span> <span data-ttu-id="a98b1-111">在此實例中有 5 個事件：</span><span class="sxs-lookup"><span data-stu-id="a98b1-111">There are five events in this scenario:</span></span>  
  
    -   <span data-ttu-id="a98b1-112">收到訊息 M0</span><span class="sxs-lookup"><span data-stu-id="a98b1-112">Receipt of message M0</span></span>  
  
    -   <span data-ttu-id="a98b1-113">接收埠輸出訊息 M1</span><span class="sxs-lookup"><span data-stu-id="a98b1-113">Output of message M1 from the receive port</span></span>  
  
    -   <span data-ttu-id="a98b1-114">傳送埠輸出訊息 M3</span><span class="sxs-lookup"><span data-stu-id="a98b1-114">Output of message M3 by the send port</span></span>  
  
    -   <span data-ttu-id="a98b1-115">傳送埠輸出訊息 M4</span><span class="sxs-lookup"><span data-stu-id="a98b1-115">Output of message M4 by the send port</span></span>  
  
    -   <span data-ttu-id="a98b1-116">傳送埠輸出訊息 M5</span><span class="sxs-lookup"><span data-stu-id="a98b1-116">Output of message M5 by the send port</span></span>  
  
 <span data-ttu-id="a98b1-117">將此資訊套用至方程式會產生下列結果：</span><span class="sxs-lookup"><span data-stu-id="a98b1-117">Applying this information to the equation gives the following:</span></span>  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-a-single-promoted-property"></a><span data-ttu-id="a98b1-118">傳送至通訊群組清單的協調流程中具有單一升級屬性的訊息</span><span class="sxs-lookup"><span data-stu-id="a98b1-118">Messages in an orchestration that are sent out to a distribution list with a single promoted property</span></span>  
 <span data-ttu-id="a98b1-119">在此範例中，將升級單一屬性，大約 10 個位元組的大小，就如先前的實例所執行。</span><span class="sxs-lookup"><span data-stu-id="a98b1-119">In this example, let's promote a single property, approximately 10 bytes in size, as we did in an earlier scenario.</span></span> <span data-ttu-id="a98b1-120">方程式現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="a98b1-120">The equation now looks like this:</span></span>  
  
```  
[((5*150 bytes) + (10*230 bytes) + (1*5(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 260) * 3,500,000]/1024/1024 = 11048 MB ~ 10.79 GB per year  
```  
  
 <span data-ttu-id="a98b1-121">若升級 20 個位元組大小的其他屬性，則方程式現在看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="a98b1-121">If we promote an additional property that is 20 bytes in size the equation now looks like this:</span></span>  
  
```  
[((5*150 bytes) + (10*230 bytes) + ((1*5(52 bytes + 10 bytes) + (1*5(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 670) * 3,500,000]/1024/1024 = 12417 MB ~ 12.13 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-message-body-tracking-activated"></a><span data-ttu-id="a98b1-122">傳送至通訊群組清單的協調流程中已啟動訊息內文追蹤的訊息</span><span class="sxs-lookup"><span data-stu-id="a98b1-122">Messages in an orchestration that are sent out to a distribution list with message body tracking activated</span></span>  
 <span data-ttu-id="a98b1-123">若您要啟動訊息追蹤，則此範例的方程式看起來如下：</span><span class="sxs-lookup"><span data-stu-id="a98b1-123">If you want to accommodate message tracking, the equation will look like the following for this example:</span></span>  
  
```  
[3,500,000 * 6 * 5KB]/1024 = 102539.06 MB ~ 100.14 GB per year  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="a98b1-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a98b1-124">See Also</span></span>  
 <span data-ttu-id="a98b1-125">[使用訊息變數調整追蹤資料庫的大小](../core/using-message-variables-to-size-the-tracking-database.md) </span><span class="sxs-lookup"><span data-stu-id="a98b1-125">[Using Message Variables to Size the Tracking Database](../core/using-message-variables-to-size-the-tracking-database.md) </span></span>  
 <span data-ttu-id="a98b1-126">[追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="a98b1-126">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="a98b1-127">[案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="a98b1-127">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="a98b1-128">[案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="a98b1-128">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="a98b1-129">案例 4： 所有訊息調整追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="a98b1-129">Scenario 4: Sizing the Tracking Database for all Messages</span></span>](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)