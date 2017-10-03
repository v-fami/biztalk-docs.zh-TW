---
title: "BizTalk ESB Toolkit 訊息生命週期 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c72fdbda-b9ef-431a-8322-56dba98e9eab
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cb15a4c87a497a5595327b65019ca95b3201664
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-esb-toolkit-message-life-cycle"></a><span data-ttu-id="86274-102">BizTalk ESB Toolkit 訊息生命週期</span><span class="sxs-lookup"><span data-stu-id="86274-102">BizTalk ESB Toolkit Message Life Cycle</span></span>
<span data-ttu-id="86274-103">以下是訊息的來自外部系統，並透過連線到其最終目的地 ESB 周遊週期：</span><span class="sxs-lookup"><span data-stu-id="86274-103">The following is the life cycle of a message that originates from an external system and traverses through the ESB to reach its final destination:</span></span>  
  
1.  <span data-ttu-id="86274-104">上手接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="86274-104">An on-ramp receives the message.</span></span> <span data-ttu-id="86274-105">根據正在提交的合作對象或用戶端，訊息可能或可能不包含會定義訊息的處理指示的路線。</span><span class="sxs-lookup"><span data-stu-id="86274-105">Depending on the submitting party or client, the message may or may not contain an itinerary that defines the processing instructions for the message.</span></span>  
  
2.  <span data-ttu-id="86274-106">ESB 管線元件複製路線 （如果有 SOAP 標頭中） 的訊息內容做為升級屬性。</span><span class="sxs-lookup"><span data-stu-id="86274-106">ESB pipeline components copy the itinerary (if present in the SOAP header) into the context of the message as promoted properties.</span></span> <span data-ttu-id="86274-107">如果路線沒有收到訊息時，可以設定特定的管線元件以從資料庫中，根據訊息內容或內容中，選取適當的路線，然後複製到訊息內容的 路線。</span><span class="sxs-lookup"><span data-stu-id="86274-107">If the message is received without an itinerary, a specific pipeline component can be configured to select the appropriate itinerary from a database, depending on message content or context, and then copy the itinerary into the context of the message.</span></span> <span data-ttu-id="86274-108">訊息的存留期間，會維護訊息內容中的路線。</span><span class="sxs-lookup"><span data-stu-id="86274-108">For the duration of the lifetime of the message, the itinerary is maintained within the message context.</span></span>  
  
3.  <span data-ttu-id="86274-109">雖然仍在管線中，會評估路線，且訊息為基礎的路線服務可以處理訊息。</span><span class="sxs-lookup"><span data-stu-id="86274-109">While still in the pipeline, the itinerary is evaluated and message-based itinerary services can process the message.</span></span> <span data-ttu-id="86274-110">這些路線服務可能會將訊息轉換，或設定路由的端點。</span><span class="sxs-lookup"><span data-stu-id="86274-110">These itinerary services may transform the message or configure routing endpoints.</span></span>  
  
4.  <span data-ttu-id="86274-111">訊息會發佈到 Microsoft BizTalk Server Messagebox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="86274-111">The message is published to the Microsoft BizTalk Server Message Box database.</span></span>  
  
5.  <span data-ttu-id="86274-112">BizTalk Server 評估一個或多個 「 訂閱者 」 的升級的屬性的訊息和佇列訊息。</span><span class="sxs-lookup"><span data-stu-id="86274-112">BizTalk Server evaluates the promoted properties of the message and queues the message for one or more subscribers.</span></span>  
  
6.  <span data-ttu-id="86274-113">訂閱者會處理訊息使用一般的 BizTalk Server 機制。</span><span class="sxs-lookup"><span data-stu-id="86274-113">The subscriber(s) process the message using typical BizTalk Server mechanisms.</span></span> <span data-ttu-id="86274-114">「 訂閱者 」 可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="86274-114">A subscriber can be either of the following:</span></span>  
  
    -   <span data-ttu-id="86274-115">使用直接繫結上設定篩選的 BizTalk Server 協調流程接收埠</span><span class="sxs-lookup"><span data-stu-id="86274-115">A BizTalk Server orchestration with a filter configured on a direct-bound receive port</span></span>  
  
    -   <span data-ttu-id="86274-116">動態的 BizTalk Server 傳送埠，也稱為 ESB 匝道。</span><span class="sxs-lookup"><span data-stu-id="86274-116">A dynamic BizTalk Server send port, which is also referred to as an ESB off-ramp.</span></span> <span data-ttu-id="86274-117">路線判斷連接埠設定來繼續處理訊息的方式。</span><span class="sxs-lookup"><span data-stu-id="86274-117">The itinerary determines how the port will be configured to continue processing the message.</span></span>  
  
 <span data-ttu-id="86274-118">或者透過路線上手抵達的訊息，BizTalk Server 協調流程也發佈訊息至訊息槽 ESB 處理：</span><span class="sxs-lookup"><span data-stu-id="86274-118">As an alternative to a message arriving through an itinerary on-ramp, BizTalk Server orchestrations can also publish messages to the Message Box for ESB processing:</span></span>  
  
1.  <span data-ttu-id="86274-119">BizTalk Server 協調流程內建立一則訊息。</span><span class="sxs-lookup"><span data-stu-id="86274-119">A message is created within a BizTalk Server orchestration.</span></span>  
  
2.  <span data-ttu-id="86274-120">訊息的內容填入 ESB 行程。</span><span class="sxs-lookup"><span data-stu-id="86274-120">The message's context is populated with the ESB itinerary.</span></span>  
  
3.  <span data-ttu-id="86274-121">訊息會發佈到 Messagebox 資料庫的直接繫結連接埠。</span><span class="sxs-lookup"><span data-stu-id="86274-121">The message is published through a direct-bound port to the Message Box database.</span></span>