---
title: "使用協調流程為路線服務的訂閱者 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 278564f1-de9f-4fbf-8c7f-09b3e607c28b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f496884d0aed8d5f351f681ca8cfe59e05684240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-an-orchestration-as-an-itinerary-service-subscriber"></a><span data-ttu-id="5f8bb-102">使用協調流程為路線服務的訂閱者</span><span class="sxs-lookup"><span data-stu-id="5f8bb-102">Using an Orchestration as an Itinerary Service Subscriber</span></span>
<span data-ttu-id="5f8bb-103">協調流程也可以當做路線的服務。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-103">Orchestrations can also act as itinerary services.</span></span> <span data-ttu-id="5f8bb-104">若要加入的路線，您必須先設計將協調流程直接繫結。若要這樣做，請使用 類似上一個主題中的傳送埠的篩選條件訂閱[用作路線服務的訂閱者端的傳送埠](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md)。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-104">To participate in an itinerary, you must first design the orchestration as direct-bound; to do this, use a filter subscription similar to that of the send port in the previous topic, [Using a Send Port as an Itinerary Service Subscriber](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md).</span></span> <span data-ttu-id="5f8bb-105">圖 1 顯示適當的協調流程收取符合下列條件的任何訊息篩選條件運算式的範例：</span><span class="sxs-lookup"><span data-stu-id="5f8bb-105">Figure 1 shows an example of a filter expression for a suitable orchestration to pick up any message that meets the following conditions:</span></span>  
  
-   <span data-ttu-id="5f8bb-106">**ServiceName = Microsoft.Practices.ESB.Services.Transform**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-106">**ServiceName = Microsoft.Practices.ESB.Services.Transform**</span></span>  
  
-   <span data-ttu-id="5f8bb-107">**ServiceState = 暫止**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-107">**ServiceState = Pending**</span></span>  
  
-   <span data-ttu-id="5f8bb-108">**ServiceType = 協調流程**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-108">**ServiceType = Orchestration**</span></span>  
  
 <span data-ttu-id="5f8bb-109">![協調流程](../esb-toolkit/media/ch4-orchestration.jpg "第 4 章第協調流程")</span><span class="sxs-lookup"><span data-stu-id="5f8bb-109">![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "Ch4-Orchestration")</span></span>  
  
 <span data-ttu-id="5f8bb-110">**圖 1**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="5f8bb-111">**要參與行程為訂閱者的協調流程的範例篩選條件運算式**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-111">**Example filter expression for an orchestration that will participate in an itinerary as a subscriber**</span></span>  
  
 <span data-ttu-id="5f8bb-112">當訊息送達 Microsoft BizTalk Server 透過 ESB 上手時，ESB 管線中的驗證步驟會將篩選條件屬性的屬性值寫入至內送訊息; BizTalk 內容屬性這將其提升至訊息內容。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-112">When messages arrive in Microsoft BizTalk Server through an ESB on-ramp, the validation step in the ESB pipeline writes the property values for the filter properties into the BizTalk context properties of the incoming message; this promotes them to the message context.</span></span> <span data-ttu-id="5f8bb-113">路線服務永遠設定**ServiceName**目前作用中的服務，以處理接下來，並與服務的名稱屬性**ServiceState**屬性值為**暫止**。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-113">The itinerary service always sets the **ServiceName** property for the currently active service to the name of the service to process next, and with a **ServiceState** property value of **Pending**.</span></span> <span data-ttu-id="5f8bb-114">訂用帳戶，您必須設定至少第三個下列屬性：</span><span class="sxs-lookup"><span data-stu-id="5f8bb-114">For a subscription, you must set at least the first three of the following properties:</span></span>  
  
-   <span data-ttu-id="5f8bb-115">**ServiceName。**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-115">**ServiceName.**</span></span> <span data-ttu-id="5f8bb-116">這是存放在 ESB 行程中，服務的名稱，而且可以是任何名稱。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-116">This is the name of the service, as stored in the ESB itinerary, and can be any name.</span></span> <span data-ttu-id="5f8bb-117">路線會使用此名稱來識別要執行的服務。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-117">The itinerary uses this name to identify which service to execute.</span></span>  
  
-   <span data-ttu-id="5f8bb-118">**ServiceState。**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-118">**ServiceState.**</span></span> <span data-ttu-id="5f8bb-119">這是要執行之目前路線服務步驟的狀態。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-119">This is the state of the current itinerary service step to execute.</span></span> <span data-ttu-id="5f8bb-120">目前的服務步驟 （適用於處理下一步） 一定會值**暫止**、 任一 ESB 路線管線元件，ESB 行程選取器管線元件，來設定或程式碼呼叫**進階**路線應用程式開發介面的方法。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-120">The current service step (for processing next) will always have the value **Pending**, set by either the ESB itinerary pipeline component, the ESB Itinerary Selector pipeline component, or code that calls the **Advance** method of the itinerary API.</span></span>  
  
-   <span data-ttu-id="5f8bb-121">**ServiceType。**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-121">**ServiceType.**</span></span> <span data-ttu-id="5f8bb-122">此屬性會定義服務，指出它是否來自協調流程 」 或 「 biztalk 傳訊子系統的型別。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-122">This property defines the type of service, indicating whether it originates from the orchestration or the messaging subsystem in BizTalk.</span></span>  
  
-   <span data-ttu-id="5f8bb-123">**IsRequestResponse。**</span><span class="sxs-lookup"><span data-stu-id="5f8bb-123">**IsRequestResponse.**</span></span> <span data-ttu-id="5f8bb-124">這個選擇性屬性必須具有相同的值**IsRequestResponse**服務屬性。</span><span class="sxs-lookup"><span data-stu-id="5f8bb-124">This optional property must have the same value as the **IsRequestResponse** property of the service.</span></span>