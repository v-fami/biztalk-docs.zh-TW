---
title: "TIBCO Rendezvous 接收訊息內容屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f47e2a0-6ac8-404a-bc0a-c7739911af74
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36f4de92dbe7c4c235a1c9ebd092b28b3a198c92
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="biztalk-server-message-context-properties-receive-handlers"></a><span data-ttu-id="a263f-102">BizTalk Server 訊息內容屬性 （接收處理常式）</span><span class="sxs-lookup"><span data-stu-id="a263f-102">BizTalk Server Message Context Properties (Receive Handlers)</span></span>
<span data-ttu-id="a263f-103">在執行階段，必須可從 BizTalk Server 協調流程存取的，除了有訊息內容以外，還有組成訊息的補充資訊。</span><span class="sxs-lookup"><span data-stu-id="a263f-103">In addition to the message payload, the supplementary information that composes a message must be accessible from a BizTalk Server orchestration at run time.</span></span>  
  
## <a name="tibco-rv-message-information-promoted-as-message-context-properties"></a><span data-ttu-id="a263f-104">已升級為訊息內容屬性的 TIBCO RV 訊息資訊</span><span class="sxs-lookup"><span data-stu-id="a263f-104">TIBCO RV Message Information Promoted as Message Context Properties</span></span>  
 <span data-ttu-id="a263f-105">下表列出這些補充資訊：</span><span class="sxs-lookup"><span data-stu-id="a263f-105">The following table lists this supplementary information:</span></span>  
  
|<span data-ttu-id="a263f-106">資料識別</span><span class="sxs-lookup"><span data-stu-id="a263f-106">Data Identification</span></span>|<span data-ttu-id="a263f-107">型別</span><span class="sxs-lookup"><span data-stu-id="a263f-107">Type</span></span>|<span data-ttu-id="a263f-108">可路由傳送</span><span class="sxs-lookup"><span data-stu-id="a263f-108">Routable</span></span>|<span data-ttu-id="a263f-109">接收位置</span><span class="sxs-lookup"><span data-stu-id="a263f-109">Receive Location</span></span>|  
|-------------------------|----------|--------------|----------------------|  
|<span data-ttu-id="a263f-110">傳送主旨 [null]</span><span class="sxs-lookup"><span data-stu-id="a263f-110">Send Subject [null]</span></span>|<span data-ttu-id="a263f-111">string</span><span class="sxs-lookup"><span data-stu-id="a263f-111">string</span></span>|<span data-ttu-id="a263f-112">是</span><span class="sxs-lookup"><span data-stu-id="a263f-112">Yes</span></span>|<span data-ttu-id="a263f-113">告訴協調流程此訊息已傳送至哪個主旨。</span><span class="sxs-lookup"><span data-stu-id="a263f-113">Tells orchestration which subject this message was sent to.</span></span>|  
|<span data-ttu-id="a263f-114">回覆主旨 [null]</span><span class="sxs-lookup"><span data-stu-id="a263f-114">Reply Subject [null]</span></span>|<span data-ttu-id="a263f-115">string</span><span class="sxs-lookup"><span data-stu-id="a263f-115">string</span></span>|<span data-ttu-id="a263f-116">是</span><span class="sxs-lookup"><span data-stu-id="a263f-116">Yes</span></span>|<span data-ttu-id="a263f-117">告訴協調流程，如果有回覆的話，寄件者預期要讓回覆傳送至的位置。</span><span class="sxs-lookup"><span data-stu-id="a263f-117">Tells orchestration where the sender expects the reply to be sent, if one is expected.</span></span>|  
|<span data-ttu-id="a263f-118">欄位計數 [唯讀]</span><span class="sxs-lookup"><span data-stu-id="a263f-118">Field Count [read only]</span></span>|<span data-ttu-id="a263f-119">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="a263f-119">unsigned int</span></span>|<span data-ttu-id="a263f-120">否</span><span class="sxs-lookup"><span data-stu-id="a263f-120">No</span></span>|<span data-ttu-id="a263f-121">較上層 訊息中的欄位數目 。</span><span class="sxs-lookup"><span data-stu-id="a263f-121">Number of fields in upper level message.</span></span> <span data-ttu-id="a263f-122">TIBCO RV 所提供的屬性。</span><span class="sxs-lookup"><span data-stu-id="a263f-122">A property provided by TIBCO RV.</span></span>|  
|<span data-ttu-id="a263f-123">CM 寄件者名稱 [唯讀]</span><span class="sxs-lookup"><span data-stu-id="a263f-123">CM Sender Name [read-only]</span></span>|<span data-ttu-id="a263f-124">string</span><span class="sxs-lookup"><span data-stu-id="a263f-124">string</span></span>|<span data-ttu-id="a263f-125">是</span><span class="sxs-lookup"><span data-stu-id="a263f-125">Yes</span></span>|<span data-ttu-id="a263f-126">寄件者的 CM 對應名稱。</span><span class="sxs-lookup"><span data-stu-id="a263f-126">CM Correspondent name of the sender.</span></span>|  
|<span data-ttu-id="a263f-127">CM 序號 [唯讀]</span><span class="sxs-lookup"><span data-stu-id="a263f-127">CM Sequence Number [read only]</span></span>|<span data-ttu-id="a263f-128">long</span><span class="sxs-lookup"><span data-stu-id="a263f-128">long</span></span>|<span data-ttu-id="a263f-129">否</span><span class="sxs-lookup"><span data-stu-id="a263f-129">No</span></span>|<span data-ttu-id="a263f-130">由傳送 TIBCO 傳輸物件指派的序號。</span><span class="sxs-lookup"><span data-stu-id="a263f-130">Sequence number assigned by the sending TIBCO transport object.</span></span>|  
|<span data-ttu-id="a263f-131">CM 時間限制 [唯讀]</span><span class="sxs-lookup"><span data-stu-id="a263f-131">CM Time Limit [read-only]</span></span>|<span data-ttu-id="a263f-132">double</span><span class="sxs-lookup"><span data-stu-id="a263f-132">double</span></span>|<span data-ttu-id="a263f-133">否</span><span class="sxs-lookup"><span data-stu-id="a263f-133">No</span></span>|<span data-ttu-id="a263f-134">時間限制，過了此時間限制之後，傳送程式就不再預期其 CM 傳輸會認證訊息傳遞。</span><span class="sxs-lookup"><span data-stu-id="a263f-134">A time limit, after which the sending program no longer expects its CM transport to certify delivery of the message.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a263f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a263f-135">See Also</span></span>  
 <span data-ttu-id="a263f-136">[TIBCO Rendezvous 中的訊息對應](../core/message-mapping-in-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="a263f-136">[Message Mapping in TIBCO Rendezvous](../core/message-mapping-in-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="a263f-137">建立 TIBCO Rendezvous 接收處理常式</span><span class="sxs-lookup"><span data-stu-id="a263f-137">Creating TIBCO Rendezvous Receive Handlers</span></span>](../core/creating-tibco-rendezvous-receive-handlers.md)