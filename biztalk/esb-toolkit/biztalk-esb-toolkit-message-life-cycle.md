---
title: BizTalk ESB 工具組訊息生命週期 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c72fdbda-b9ef-431a-8322-56dba98e9eab
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f93a4ee2024fcb9cfaf65e7cf33922784a47030
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979135"
---
# <a name="biztalk-esb-toolkit-message-life-cycle"></a><span data-ttu-id="b99d8-102">BizTalk ESB 工具組訊息生命週期</span><span class="sxs-lookup"><span data-stu-id="b99d8-102">BizTalk ESB Toolkit Message Life Cycle</span></span>
<span data-ttu-id="b99d8-103">以下是訊息的來自外部系統，並透過連線到其最終目的地 ESB 周遊生命週期：</span><span class="sxs-lookup"><span data-stu-id="b99d8-103">The following is the life cycle of a message that originates from an external system and traverses through the ESB to reach its final destination:</span></span>  

1. <span data-ttu-id="b99d8-104">匝道接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="b99d8-104">An on-ramp receives the message.</span></span> <span data-ttu-id="b99d8-105">根據提交的合作對象或用戶端上，訊息可能或可能不會包含定義訊息的處理指示的路線。</span><span class="sxs-lookup"><span data-stu-id="b99d8-105">Depending on the submitting party or client, the message may or may not contain an itinerary that defines the processing instructions for the message.</span></span>  

2. <span data-ttu-id="b99d8-106">ESB 管線元件複製路線 （如果有 SOAP 標頭中） 到訊息的內容為升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="b99d8-106">ESB pipeline components copy the itinerary (if present in the SOAP header) into the context of the message as promoted properties.</span></span> <span data-ttu-id="b99d8-107">路線沒有收到訊息時，可以設定特定的管線元件，以從資料庫中，根據訊息內容或內容中，選取適當的路線，，然後複製到訊息內容的 路線。</span><span class="sxs-lookup"><span data-stu-id="b99d8-107">If the message is received without an itinerary, a specific pipeline component can be configured to select the appropriate itinerary from a database, depending on message content or context, and then copy the itinerary into the context of the message.</span></span> <span data-ttu-id="b99d8-108">訊息的存留期期間，訊息內容中會保持路線。</span><span class="sxs-lookup"><span data-stu-id="b99d8-108">For the duration of the lifetime of the message, the itinerary is maintained within the message context.</span></span>  

3. <span data-ttu-id="b99d8-109">雖然仍會在管線中，評估路線，並且以訊息為基礎的路線服務可以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="b99d8-109">While still in the pipeline, the itinerary is evaluated and message-based itinerary services can process the message.</span></span> <span data-ttu-id="b99d8-110">這些路線服務可能會轉換該訊息，或設定路由的端點。</span><span class="sxs-lookup"><span data-stu-id="b99d8-110">These itinerary services may transform the message or configure routing endpoints.</span></span>  

4. <span data-ttu-id="b99d8-111">訊息會發佈到 Microsoft BizTalk Server Messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b99d8-111">The message is published to the Microsoft BizTalk Server Message Box database.</span></span>  

5. <span data-ttu-id="b99d8-112">BizTalk Server 的一或多個 「 訂閱者 」，訊息將評估的訊息和佇列的升級的屬性。</span><span class="sxs-lookup"><span data-stu-id="b99d8-112">BizTalk Server evaluates the promoted properties of the message and queues the message for one or more subscribers.</span></span>  

6. <span data-ttu-id="b99d8-113">訂閱者會處理訊息使用一般的 BizTalk Server 機制。</span><span class="sxs-lookup"><span data-stu-id="b99d8-113">The subscriber(s) process the message using typical BizTalk Server mechanisms.</span></span> <span data-ttu-id="b99d8-114">訂閱者可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b99d8-114">A subscriber can be either of the following:</span></span>  

   -   <span data-ttu-id="b99d8-115">使用篩選條件直接繫結上設定 BizTalk Server 協調流程接收埠</span><span class="sxs-lookup"><span data-stu-id="b99d8-115">A BizTalk Server orchestration with a filter configured on a direct-bound receive port</span></span>  

   -   <span data-ttu-id="b99d8-116">動態的 BizTalk Server 傳送埠，也稱為 ESB 出口匝。</span><span class="sxs-lookup"><span data-stu-id="b99d8-116">A dynamic BizTalk Server send port, which is also referred to as an ESB off-ramp.</span></span> <span data-ttu-id="b99d8-117">行程會判斷連接埠以繼續處理訊息的設定方式。</span><span class="sxs-lookup"><span data-stu-id="b99d8-117">The itinerary determines how the port will be configured to continue processing the message.</span></span>  

   <span data-ttu-id="b99d8-118">替代路線入口匝透過到達的訊息，BizTalk Server 協調流程也可以發佈訊息至 Messagebox 的 ESB 處理：</span><span class="sxs-lookup"><span data-stu-id="b99d8-118">As an alternative to a message arriving through an itinerary on-ramp, BizTalk Server orchestrations can also publish messages to the Message Box for ESB processing:</span></span>  

7. <span data-ttu-id="b99d8-119">BizTalk Server 協調流程內建立一則訊息。</span><span class="sxs-lookup"><span data-stu-id="b99d8-119">A message is created within a BizTalk Server orchestration.</span></span>  

8. <span data-ttu-id="b99d8-120">訊息的內容會填入 ESB 路線。</span><span class="sxs-lookup"><span data-stu-id="b99d8-120">The message's context is populated with the ESB itinerary.</span></span>  

9. <span data-ttu-id="b99d8-121">訊息會發佈到 Messagebox 資料庫直接繫結連接埠。</span><span class="sxs-lookup"><span data-stu-id="b99d8-121">The message is published through a direct-bound port to the Message Box database.</span></span>
