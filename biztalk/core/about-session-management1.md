---
title: 關於工作階段 Management1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d1848619-d97a-4f1e-ba94-59861bd7aedf
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 336deb34e5587e64c5177cd0a439c756cf0f2b61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22225646"
---
# <a name="about-session-management"></a><span data-ttu-id="1ea4b-102">關於工作階段管理</span><span class="sxs-lookup"><span data-stu-id="1ea4b-102">About Session Management</span></span>
<span data-ttu-id="1ea4b-103">Microsoft BizTalk Adapter for JD Edwards OneWorld 建立連線工作階段，以傳送呼叫給 JD Edwards OneWorld 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-103">The Microsoft BizTalk Adapter for JD Edwards OneWorld creates a connection session to send a call to the JD Edwards OneWorld server.</span></span> <span data-ttu-id="1ea4b-104">當呼叫終止時，工作階段會放在集區中，供後續呼叫重複使用。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-104">When the call terminates, the session is put in a pool to be re-used by a subsequent call.</span></span> <span data-ttu-id="1ea4b-105">配接器會建立多個連線工作階段，以處理對 JD Edwards OneWorld 伺服器的並行呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-105">The adapter creates multiple connection sessions to handle concurrent calls to the JD Edwards OneWorld server.</span></span> <span data-ttu-id="1ea4b-106">集區會定期清除，以移除不再需要的工作階段。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-106">The pool is periodically cleaned to remove sessions that are no longer necessary.</span></span>  
  
 <span data-ttu-id="1ea4b-107">Microsoft BizTalk Adapter for JD Edwards OneWorld 提供兩個訊息內容屬性來控制，必須發生呼叫相同的工作階段內。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-107">The Microsoft BizTalk Adapter for JD Edwards OneWorld provides two message context properties to control when calls must occur within the same session.</span></span>  
  
|<span data-ttu-id="1ea4b-108">名稱</span><span class="sxs-lookup"><span data-stu-id="1ea4b-108">Name</span></span>|<span data-ttu-id="1ea4b-109">類型</span><span class="sxs-lookup"><span data-stu-id="1ea4b-109">Type</span></span>|<span data-ttu-id="1ea4b-110">預設值</span><span class="sxs-lookup"><span data-stu-id="1ea4b-110">Default</span></span>|  
|----------|----------|-------------|  
|<span data-ttu-id="1ea4b-111">JDE.SessionID</span><span class="sxs-lookup"><span data-stu-id="1ea4b-111">JDE.SessionID</span></span>|<span data-ttu-id="1ea4b-112">int</span><span class="sxs-lookup"><span data-stu-id="1ea4b-112">Int</span></span>|<span data-ttu-id="1ea4b-113">0</span><span class="sxs-lookup"><span data-stu-id="1ea4b-113">0</span></span>|  
|<span data-ttu-id="1ea4b-114">JDE.ReserveSession</span><span class="sxs-lookup"><span data-stu-id="1ea4b-114">JDE.ReserveSession</span></span>|<span data-ttu-id="1ea4b-115">boolean</span><span class="sxs-lookup"><span data-stu-id="1ea4b-115">boolean</span></span>|<span data-ttu-id="1ea4b-116">false</span><span class="sxs-lookup"><span data-stu-id="1ea4b-116">false</span></span>|  
  
 <span data-ttu-id="1ea4b-117">如果商務功能只需呼叫 JD Edwards OneWorld 伺服器一單一工作階段管理。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-117">Session management is unnecessary if the business function requires a single call to the JD Edwards OneWorld server.</span></span> <span data-ttu-id="1ea4b-118">配接器可以取用任何可用的工作階段，而且工作階段仍然可供任何後續呼叫使用。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-118">The adapter can pick any available session and the session remains available for any following calls.</span></span> <span data-ttu-id="1ea4b-119">在這種情況下，您可以忽略訊息內容屬性，因為預設值都適用。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-119">In this scenario, you can ignore the message context properties as the defaults are appropriate.</span></span>  
  
 <span data-ttu-id="1ea4b-120">有些 JD Edwards OneWorld 功能需要多次呼叫 JD Edwards OneWorld 伺服器，例如在建立 SalesOrder 時。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-120">Some JD Edwards OneWorld functionality requires multiple calls to the JD Edwards OneWorld server; for example, the creation of a SalesOrder.</span></span> <span data-ttu-id="1ea4b-121">第一次呼叫 BeginDoc 時，會建立空白 SalesOrder。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-121">The first call to BeginDoc creates an empty SalesOrder.</span></span> <span data-ttu-id="1ea4b-122">接著，對 EditLine 的每個後續呼叫都會在 SalesOrder 中加入一個明細項目。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-122">Each subsequent call to EditLine adds one line item to the SalesOrder.</span></span> <span data-ttu-id="1ea4b-123">最後，對 EndDoc 的呼叫會關閉 SalesOrder。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-123">Finally the call to EndDoc closes the SalesOrder.</span></span>  
  
```  
BeginDoc  
   EditLine  
   EditLine  
   ...  
EndDoc  
```  
  
 <span data-ttu-id="1ea4b-124">若要成功，單一 SalesOrder 的所有呼叫都必須在相同的工作階段傳送。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-124">To be successful, all the calls for a single SalesOrder must be sent on the same session.</span></span> <span data-ttu-id="1ea4b-125">若要執行這項操作，請指派訊息內容屬性，以指示配接器如何處理工作階段。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-125">To do this, assign message context properties to instruct the adapter what to do with the session.</span></span> <span data-ttu-id="1ea4b-126">對於 SalesOrder 範例，下列值會指派給訊息內容屬性，以處理 JD OneWorld 工作階段：</span><span class="sxs-lookup"><span data-stu-id="1ea4b-126">For the SalesOrder example, these are the values that would be assigned to the message context properties to handle the JD OneWorld session:</span></span>  
  
|<span data-ttu-id="1ea4b-127">函數</span><span class="sxs-lookup"><span data-stu-id="1ea4b-127">Function</span></span>|<span data-ttu-id="1ea4b-128">SessionID</span><span class="sxs-lookup"><span data-stu-id="1ea4b-128">SessionID</span></span>|<span data-ttu-id="1ea4b-129">ReserveSession</span><span class="sxs-lookup"><span data-stu-id="1ea4b-129">ReserveSession</span></span>|  
|--------------|---------------|--------------------|  
|<span data-ttu-id="1ea4b-130">BeginDoc</span><span class="sxs-lookup"><span data-stu-id="1ea4b-130">BeginDoc</span></span>|<span data-ttu-id="1ea4b-131">0</span><span class="sxs-lookup"><span data-stu-id="1ea4b-131">0</span></span>|<span data-ttu-id="1ea4b-132">true</span><span class="sxs-lookup"><span data-stu-id="1ea4b-132">true</span></span>|  
|<span data-ttu-id="1ea4b-133">EditLine</span><span class="sxs-lookup"><span data-stu-id="1ea4b-133">EditLine</span></span>|<span data-ttu-id="1ea4b-134">從 BeginDoc 回覆複製</span><span class="sxs-lookup"><span data-stu-id="1ea4b-134">Copied from BeginDoc reply</span></span>|<span data-ttu-id="1ea4b-135">true</span><span class="sxs-lookup"><span data-stu-id="1ea4b-135">true</span></span>|  
|<span data-ttu-id="1ea4b-136">EditLine</span><span class="sxs-lookup"><span data-stu-id="1ea4b-136">EditLine</span></span>|<span data-ttu-id="1ea4b-137">從 BeginDoc 回覆複製</span><span class="sxs-lookup"><span data-stu-id="1ea4b-137">Copied from BeginDoc reply</span></span>|<span data-ttu-id="1ea4b-138">true</span><span class="sxs-lookup"><span data-stu-id="1ea4b-138">true</span></span>|  
|<span data-ttu-id="1ea4b-139">EndDoc</span><span class="sxs-lookup"><span data-stu-id="1ea4b-139">EndDoc</span></span>|<span data-ttu-id="1ea4b-140">從 BeginDoc 回覆複製</span><span class="sxs-lookup"><span data-stu-id="1ea4b-140">Copied from BeginDoc reply</span></span>|<span data-ttu-id="1ea4b-141">false</span><span class="sxs-lookup"><span data-stu-id="1ea4b-141">false</span></span>|  
  
-   <span data-ttu-id="1ea4b-142">對於第一個呼叫，配接器可以自由選取任何可用的工作階段 (因為 SessionID 是零)。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-142">For the first call, the adapter is free to choose any available session (because the SessionID is zero).</span></span>  
  
-   <span data-ttu-id="1ea4b-143">配接器會傳回 BeginDoc 回覆中所使用的 SessionID。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-143">The adapter returns the SessionID that was used in the BeginDoc reply.</span></span>  
  
-   <span data-ttu-id="1ea4b-144">ReserveSession 屬性會告知配接器保留此工作階段，以供明確要求此工作階段的後續呼叫使用。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-144">The ReserveSession property tells the adapter to reserve this session for following calls that explicitly requests this session.</span></span> <span data-ttu-id="1ea4b-145">其他呼叫都會刻意重複使用此工作階段，因為它是保留的工作階段。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-145">No other calls can accidentally re-use the session because it is reserved.</span></span>  
  
-   <span data-ttu-id="1ea4b-146">藉由將 SessionID 設定為 BeginDoc 中所傳回的值，後續呼叫便可以要求此工作階段。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-146">Subsequent calls request the session by setting the SessionID to the value returned in BeginDoc.</span></span>  
  
-   <span data-ttu-id="1ea4b-147">ReserveSession 屬性設定為 true (至少直到一系列呼叫中的最後一個呼叫為止)。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-147">The ReserveSession property is set to true, at least until the last call in the series.</span></span>  
  
-   <span data-ttu-id="1ea4b-148">最後一個呼叫會將 ReserveSession 設定為 false，讓任何後續呼叫都可以使用工作階段。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-148">The last call sets ReserveSession to false to make the session available to any following call.</span></span> <span data-ttu-id="1ea4b-149">不過，協調流程可以選擇保留工作階段給更多呼叫使用。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-149">However, the orchestration can elect to keep the session for more calls.</span></span>  
  
 <span data-ttu-id="1ea4b-150">如果有一段時間工作階段未使用，集區會對此工作階段進行記憶體回收，即使此工作階段仍然因為錯誤而遭保留也一樣。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-150">If the session is not used for a while, it will be garbage-collected by the pool, even if the session is still reserved by mistake.</span></span>  
  
 <span data-ttu-id="1ea4b-151">如需訊息內容屬性的詳細資料，請參閱 BizTalk Server 文件。</span><span class="sxs-lookup"><span data-stu-id="1ea4b-151">Refer to BizTalk Server documentation for more details on message context properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea4b-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea4b-152">See Also</span></span>  
 <span data-ttu-id="1ea4b-153">[使用訊息內容屬性](../core/using-message-context-properties2.md) </span><span class="sxs-lookup"><span data-stu-id="1ea4b-153">[Using Message Context Properties](../core/using-message-context-properties2.md) </span></span>  
 <span data-ttu-id="1ea4b-154">[如何指派訊息內容屬性值](../core/how-to-assign-message-context-property-values2.md) </span><span class="sxs-lookup"><span data-stu-id="1ea4b-154">[How to Assign Message Context Property Values](../core/how-to-assign-message-context-property-values2.md) </span></span>  
 [<span data-ttu-id="1ea4b-155">教學課程： 使用 BizTalk Adapter for JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="1ea4b-155">Tutorial: Using the BizTalk Adapter for JD Edwards OneWorld</span></span>](../core/tutorial-using-the-biztalk-adapter-for-jd-edwards-oneworld.md)