---
title: 使用訊息變數調整追蹤資料庫的大小 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message variables [Tracking database], CMsgs
- message variables [Tracking database], Events
- message variables [Tracking database], Properties
- Tracking database, database size
- message variables [Tracking database], Nserv
- message variables [Tracking database], Msgs
- message variables [Tracking database], PropSize
- message variables [Tracking database]
- message variables [Tracking database], MsgSize
- message variables [Tracking database], MsgNum
- Tracking database, messages
ms.assetid: 2d31ae25-3d16-4002-b5a5-dca25e764ecd
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5418cdf79499302e6127db7fb66f108825a0d8c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22287838"
---
# <a name="using-message-variables-to-size-the-tracking-database"></a><span data-ttu-id="f47ab-102">使用訊息變數調整追蹤資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="f47ab-102">Using Message Variables to Size the Tracking Database</span></span>
<span data-ttu-id="f47ab-103">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您可以使用一些變數來決定 BizTalk 追蹤 (BizTalkDTADb) 資料庫在經過一段指定時間後的大小。</span><span class="sxs-lookup"><span data-stu-id="f47ab-103">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can use a number of variables to determine how large the BizTalk Tracking (BizTalkDTADb) database will become over a given period of time.</span></span> <span data-ttu-id="f47ab-104">這些變數是：</span><span class="sxs-lookup"><span data-stu-id="f47ab-104">These variables are:</span></span>  
  
-   <span data-ttu-id="f47ab-105">使用的管線數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-105">Number of pipelines used</span></span>  
  
-   <span data-ttu-id="f47ab-106">相關的協調流程數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-106">Number of orchestrations involved</span></span>  
  
-   <span data-ttu-id="f47ab-107">產生的事件數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-107">Number of events generated</span></span>  
  
-   <span data-ttu-id="f47ab-108">追蹤的訊息屬性數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-108">Number of message properties tracked</span></span>  
  
-   <span data-ttu-id="f47ab-109">建立的其他訊息數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-109">Number of additional messages created</span></span>  
  
-   <span data-ttu-id="f47ab-110">在指定的一段時間中所接收訊息的預估數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-110">Estimated number of messages received in the specified timeframe</span></span>  
  
 <span data-ttu-id="f47ab-111">雖然您用來預估 BizTalk 追蹤資料庫大小的方程式很明確，不過您必須將它套用到每個使用 BizTalk Server 實作的內送和外寄訊息程序。</span><span class="sxs-lookup"><span data-stu-id="f47ab-111">While the equation you use to estimate the size of the BizTalk Tracking database is straightforward, you must apply it to each incoming and outgoing message process that uses the BizTalk Server implementation.</span></span> <span data-ttu-id="f47ab-112">換句話說，您必須為每個不同的訊息實例套用此方程式，然後加總這些結果以取得最後預估的資料庫大小。</span><span class="sxs-lookup"><span data-stu-id="f47ab-112">In other words, you will need to apply this equation for every distinct message scenario and then add up the results to obtain the final estimated database size.</span></span> <span data-ttu-id="f47ab-113">在此文件中，我們將研究兩個實例。</span><span class="sxs-lookup"><span data-stu-id="f47ab-113">In this document we will look at two scenarios.</span></span> <span data-ttu-id="f47ab-114">實例為：</span><span class="sxs-lookup"><span data-stu-id="f47ab-114">The scenarios are:</span></span>  
  
1.  <span data-ttu-id="f47ab-115">接收訊息、轉換訊息，然後傳送結果訊息</span><span class="sxs-lookup"><span data-stu-id="f47ab-115">Receiving a message, transforming the message, and then sending the resulting message</span></span>  
  
2.  <span data-ttu-id="f47ab-116">接收訊息、執行使用訊息的商務程序，然後傳送結果訊息。</span><span class="sxs-lookup"><span data-stu-id="f47ab-116">Receiving a message, running a business process using the message, and then sending the resulting message.</span></span>  
  
 <span data-ttu-id="f47ab-117">這兩個實例可能會出現在 BizTalk Server 安裝中，而且每個實例都會產生不同的追蹤資料量。</span><span class="sxs-lookup"><span data-stu-id="f47ab-117">Both of these scenarios may be present in a BizTalk Server installation, and each scenario generates a different amount of tracking data.</span></span> <span data-ttu-id="f47ab-118">產生的 BizTalk Server 安裝總追蹤資料是所有實例的總和。</span><span class="sxs-lookup"><span data-stu-id="f47ab-118">The total tracking data generated for the BizTalk Server installation is the sum of all the scenarios.</span></span>  
  
 <span data-ttu-id="f47ab-119">下列項目是用於方程式的部分變數：</span><span class="sxs-lookup"><span data-stu-id="f47ab-119">The following are some variables used in the equation:</span></span>  
  
|<span data-ttu-id="f47ab-120">變數</span><span class="sxs-lookup"><span data-stu-id="f47ab-120">Variable</span></span>|<span data-ttu-id="f47ab-121">Description</span><span class="sxs-lookup"><span data-stu-id="f47ab-121">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f47ab-122">**Nserv**</span><span class="sxs-lookup"><span data-stu-id="f47ab-122">**Nserv**</span></span>|<span data-ttu-id="f47ab-123">服務的數目 (管線數目 + 協調流程數目)</span><span class="sxs-lookup"><span data-stu-id="f47ab-123">Number of services (number of pipelines + number of orchestrations)</span></span>|  
|<span data-ttu-id="f47ab-124">**事件**</span><span class="sxs-lookup"><span data-stu-id="f47ab-124">**Events**</span></span>|<span data-ttu-id="f47ab-125">產生的訊息事件數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-125">Number of generated message events</span></span>|  
|<span data-ttu-id="f47ab-126">**屬性**</span><span class="sxs-lookup"><span data-stu-id="f47ab-126">**Properties**</span></span>|<span data-ttu-id="f47ab-127">追蹤的訊息屬性數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-127">Number of message properties tracked</span></span>|  
|<span data-ttu-id="f47ab-128">**PropSize**</span><span class="sxs-lookup"><span data-stu-id="f47ab-128">**PropSize**</span></span>|<span data-ttu-id="f47ab-129">升級屬性 (欄位) 的大小 (以位元組為單位)</span><span class="sxs-lookup"><span data-stu-id="f47ab-129">Size (in bytes) of the promoted property (field)</span></span>|  
|<span data-ttu-id="f47ab-130">**CMsgs**</span><span class="sxs-lookup"><span data-stu-id="f47ab-130">**CMsgs**</span></span>|<span data-ttu-id="f47ab-131">每個內送訊息建立的額外訊息數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-131">Number of additional messages created per incoming message</span></span>|  
|<span data-ttu-id="f47ab-132">**訊息的上限數**</span><span class="sxs-lookup"><span data-stu-id="f47ab-132">**Msgs**</span></span>|<span data-ttu-id="f47ab-133">在指定的一段時間中的預估內送訊息數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-133">Number of estimated incoming messages in a given time period</span></span>|  
|<span data-ttu-id="f47ab-134">**MsgSize**</span><span class="sxs-lookup"><span data-stu-id="f47ab-134">**MsgSize**</span></span>|<span data-ttu-id="f47ab-135">訊息大小</span><span class="sxs-lookup"><span data-stu-id="f47ab-135">Message size</span></span>|  
|<span data-ttu-id="f47ab-136">**MsgNum**</span><span class="sxs-lookup"><span data-stu-id="f47ab-136">**MsgNum**</span></span>|<span data-ttu-id="f47ab-137">每個內送訊息的已追蹤訊息數目</span><span class="sxs-lookup"><span data-stu-id="f47ab-137">Number of messages tracked for each incoming message</span></span>|  
  
 <span data-ttu-id="f47ab-138">方程式如下：</span><span class="sxs-lookup"><span data-stu-id="f47ab-138">The equation is as follows:</span></span>  
  
```  
[((Nserv * 150 bytes) + (Events * 230 bytes) + (Properties * CMsgs*(52 bytes + PropSize))) * Msgs]/1024/1024 = Data size in MB  
```  
  
 <span data-ttu-id="f47ab-139">此方程式僅計算訊息所產生的追蹤資料，不包括為「協調流程偵錯工具」所產生的追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="f47ab-139">This equation calculates only the tracking data generated by the messages and does not include the tracking data generated for the Orchestration Debugger.</span></span> <span data-ttu-id="f47ab-140">您必須將此公式套用到每個訊息程序以預估 BizTalk 追蹤資料庫的大小。</span><span class="sxs-lookup"><span data-stu-id="f47ab-140">You must apply this formula to each message process to estimate the size of the BizTalk Tracking database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f47ab-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f47ab-141">See Also</span></span>  
 <span data-ttu-id="f47ab-142">[追蹤訊息內文追蹤資料庫設定大小](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span><span class="sxs-lookup"><span data-stu-id="f47ab-142">[Sizing the Tracking Database to Track Message Bodies](../core/sizing-the-tracking-database-to-track-message-bodies.md) </span></span>  
 <span data-ttu-id="f47ab-143">[案例 1： 針對簡單 BizTalk 訊息調整追蹤資料庫](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span><span class="sxs-lookup"><span data-stu-id="f47ab-143">[Scenario 1: Sizing the Tracking Database  for Simple BizTalk Messages](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md) </span></span>  
 <span data-ttu-id="f47ab-144">[案例 2： 在協調流程中的訊息調整追蹤資料庫](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="f47ab-144">[Scenario 2: Sizing the Tracking Database  for Messages in Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md) </span></span>  
 <span data-ttu-id="f47ab-145">[案例 4： 所有訊息調整追蹤資料庫](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span><span class="sxs-lookup"><span data-stu-id="f47ab-145">[Scenario 4: Sizing the Tracking Database for all Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md) </span></span>  
 [<span data-ttu-id="f47ab-146">案例 3： 調整追蹤資料庫外送到通訊群組清單之訊息的大小</span><span class="sxs-lookup"><span data-stu-id="f47ab-146">Scenario 3: Sizing the Tracking Database  for Messages Sent Out to Distribution Lists</span></span>](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)