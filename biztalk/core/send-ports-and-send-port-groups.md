---
title: 傳送埠與傳送埠群組 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- send ports, states
- send port groups
- send port groups, states
- send ports, about send ports
- send ports
- send port groups, about send port groups
- states, send ports
ms.assetid: 274bdd27-9098-46a2-8762-8b57bbfc95b8
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bad7bc94bd1721dcdf55dbf94af3b9ccc0e750d8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994807"
---
# <a name="send-ports-and-send-port-groups"></a><span data-ttu-id="68e57-102">傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="68e57-102">Send Ports and Send Port Groups</span></span>
<span data-ttu-id="68e57-103">A*傳送埠*是 Microsoft BizTalk Server 傳送訊息的位置，或從中 BizTalk Server 接收訊息。</span><span class="sxs-lookup"><span data-stu-id="68e57-103">A *send port* is the location to which Microsoft BizTalk Server sends messages or from which BizTalk Server receives messages.</span></span> <span data-ttu-id="68e57-104">它也提供 BizTalk Server 用來實作通訊動作的技術。</span><span class="sxs-lookup"><span data-stu-id="68e57-104">It also provides the technology that BizTalk Server uses to implement the communication action.</span></span> <span data-ttu-id="68e57-105">連接埠的名稱可指出唯一的位置。</span><span class="sxs-lookup"><span data-stu-id="68e57-105">The name of the port uniquely identifies the location.</span></span>  
  
 <span data-ttu-id="68e57-106">只要訊息傳送至傳送埠，就會建立新的傳送埠服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="68e57-106">Any time a message is sent to a send port a new instance of a send port service is created.</span></span> <span data-ttu-id="68e57-107">這稱為服務執行個體，也就是傳送埠執行個體。</span><span class="sxs-lookup"><span data-stu-id="68e57-107">This is called a service instance, also known as a Send Port Instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68e57-108">適當的傳遞傳送埠可以只有一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="68e57-108">There can only be one instance of an In-order delivery send port.</span></span>  
  
 <span data-ttu-id="68e57-109">A*傳送埠群組*是 BizTalk Server 可以使用相同的訊息傳送至一個組態中的多個目的地的傳送埠的具名的集合。</span><span class="sxs-lookup"><span data-stu-id="68e57-109">A *send port group* is a named collection of send ports that BizTalk Server can use to send the same message to multiple destinations in one configuration.</span></span>  
  
 <span data-ttu-id="68e57-110">BizTalk Server 可以直接將訊息從接收位置路由至傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="68e57-110">BizTalk Server can directly route messages from receive locations to a send port, or to a send port group.</span></span> <span data-ttu-id="68e57-111">BizTalk Server 將路由到傳送埠群組的訊息傳送到該群組中的所有傳送埠。</span><span class="sxs-lookup"><span data-stu-id="68e57-111">BizTalk Server sends messages routed to a send port group to all of the send ports in that group.</span></span>  
  
 <span data-ttu-id="68e57-112">屬於傳送埠群組成員的傳送埠以下列兩種方式處理訊息：</span><span class="sxs-lookup"><span data-stu-id="68e57-112">Send ports that are members of a send port group process messages in two ways:</span></span>  
  
-   <span data-ttu-id="68e57-113">做為傳送埠群組的成員</span><span class="sxs-lookup"><span data-stu-id="68e57-113">As a member of the send port group</span></span>  
  
-   <span data-ttu-id="68e57-114">如同 BizTalk Server 直接將訊息路由至傳送埠</span><span class="sxs-lookup"><span data-stu-id="68e57-114">As if BizTalk Server routed the messages to the send port directly</span></span>  
  
## <a name="send-port-and-send-port-group-states"></a><span data-ttu-id="68e57-115">傳送埠與傳送埠群組狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-115">Send Port and Send Port Group States</span></span>  
 <span data-ttu-id="68e57-116">BizTalk 管理主控台會以下列其中一種狀態來顯示傳送埠與傳送埠群組：</span><span class="sxs-lookup"><span data-stu-id="68e57-116">The BizTalk Administration Console displays send ports and send port groups in one of the following states:</span></span>  
  
- <span data-ttu-id="68e57-117">**繫結**。</span><span class="sxs-lookup"><span data-stu-id="68e57-117">**Bound**.</span></span> <span data-ttu-id="68e57-118">使用 BizTalk Server 管理主控台，系統管理員可以將傳送埠或傳送埠群組繫結至協調流程。</span><span class="sxs-lookup"><span data-stu-id="68e57-118">Using the BizTalk Server Administration Console, an administrator binds the send port or send port group to an orchestration.</span></span> <span data-ttu-id="68e57-119">在 BizTalk Server 將訊息路由至此傳送埠或傳送埠群組之前，系統管理員必須登錄並啟動繫結的傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="68e57-119">Before BizTalk Server routes messages to this send port or send port group, the administrator must enlist and start the bound send port or send port group.</span></span>  
  
- <span data-ttu-id="68e57-120">**啟動**。</span><span class="sxs-lookup"><span data-stu-id="68e57-120">**Started**.</span></span> <span data-ttu-id="68e57-121">此傳送埠或傳送埠群組的訂閱已存在或在作用中。</span><span class="sxs-lookup"><span data-stu-id="68e57-121">The subscription for this send port or send port group exists and is active.</span></span> <span data-ttu-id="68e57-122">當傳送埠或傳送埠群組為已啟動狀態時，BizTalk Server 會將訊息傳遞至傳送埠或傳送埠群組，讓傳送埠或傳送埠群組處理這些訊息。</span><span class="sxs-lookup"><span data-stu-id="68e57-122">When the send port or send port group is in the started state, BizTalk Server delivers messages to the send port or send port group, and the send port or send port group processes them.</span></span> <span data-ttu-id="68e57-123">在您啟動傳送埠或傳送埠群組之前，系統管理員必須使用 BizTalk 管理主控台登錄繫結的傳送埠或傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="68e57-123">Before you can start a send port or send port group, an administrator must use the BizTalk Administration Console to enlist the bound send port or send port group.</span></span>  
  
- <span data-ttu-id="68e57-124">**停止**。</span><span class="sxs-lookup"><span data-stu-id="68e57-124">**Stopped**.</span></span> <span data-ttu-id="68e57-125">傳送埠或傳送埠群組目前並未執行。</span><span class="sxs-lookup"><span data-stu-id="68e57-125">The send port or send port group is not currently running.</span></span> <span data-ttu-id="68e57-126">如果您已啟動傳送埠或傳送埠群組，然後將它停止，會在工作佇列中繼續處理。</span><span class="sxs-lookup"><span data-stu-id="68e57-126">If you started the send port or send port group and then stopped it, processing continues in the work queue.</span></span> <span data-ttu-id="68e57-127">BizTalk Server 將路由至已停止的傳送埠或傳送埠群組的所有新訊息都傳送至執行傳送處理常式之主控件的擱置佇列。</span><span class="sxs-lookup"><span data-stu-id="68e57-127">BizTalk Server sends all new messages routed to a stopped send port or send port group to the suspended queue of the host where the send handler is running.</span></span>  
  
  <span data-ttu-id="68e57-128">下表顯示每個狀態可用的動作及其結果。</span><span class="sxs-lookup"><span data-stu-id="68e57-128">The following table shows the actions available from each state, and the result of each.</span></span>  
  
||<span data-ttu-id="68e57-129">繫結</span><span class="sxs-lookup"><span data-stu-id="68e57-129">Bound</span></span>|<span data-ttu-id="68e57-130">Stopped</span><span class="sxs-lookup"><span data-stu-id="68e57-130">Stopped</span></span>|<span data-ttu-id="68e57-131">Started</span><span class="sxs-lookup"><span data-stu-id="68e57-131">Started</span></span>|  
|------|-----------|-------------|-------------|  
|<span data-ttu-id="68e57-132">**登錄**</span><span class="sxs-lookup"><span data-stu-id="68e57-132">**Enlist**</span></span>|<span data-ttu-id="68e57-133">Stopped</span><span class="sxs-lookup"><span data-stu-id="68e57-133">Stopped</span></span>|<span data-ttu-id="68e57-134">無法使用</span><span class="sxs-lookup"><span data-stu-id="68e57-134">Not available</span></span>|<span data-ttu-id="68e57-135">無法使用</span><span class="sxs-lookup"><span data-stu-id="68e57-135">Not available</span></span>|  
|<span data-ttu-id="68e57-136">**啟動**</span><span class="sxs-lookup"><span data-stu-id="68e57-136">**Start**</span></span>|<span data-ttu-id="68e57-137">Started</span><span class="sxs-lookup"><span data-stu-id="68e57-137">Started</span></span>|<span data-ttu-id="68e57-138">Started</span><span class="sxs-lookup"><span data-stu-id="68e57-138">Started</span></span>|<span data-ttu-id="68e57-139">無法使用</span><span class="sxs-lookup"><span data-stu-id="68e57-139">Not available</span></span>|  
|<span data-ttu-id="68e57-140">**停止**</span><span class="sxs-lookup"><span data-stu-id="68e57-140">**Stop**</span></span>|<span data-ttu-id="68e57-141">無法使用</span><span class="sxs-lookup"><span data-stu-id="68e57-141">Not available</span></span>|<span data-ttu-id="68e57-142">無法使用</span><span class="sxs-lookup"><span data-stu-id="68e57-142">Not available</span></span>|<span data-ttu-id="68e57-143">Stopped</span><span class="sxs-lookup"><span data-stu-id="68e57-143">Stopped</span></span>|  
|<span data-ttu-id="68e57-144">**取消登錄**</span><span class="sxs-lookup"><span data-stu-id="68e57-144">**Unenlist**</span></span>|<span data-ttu-id="68e57-145">無法使用</span><span class="sxs-lookup"><span data-stu-id="68e57-145">Not available</span></span>|<span data-ttu-id="68e57-146">繫結</span><span class="sxs-lookup"><span data-stu-id="68e57-146">Bound</span></span>|<span data-ttu-id="68e57-147">繫結</span><span class="sxs-lookup"><span data-stu-id="68e57-147">Bound</span></span>|  
  
 <span data-ttu-id="68e57-148">傳送埠與其所屬傳送埠群組的組合狀態可用於判斷傳送埠或傳送埠群組是否處理訊息。</span><span class="sxs-lookup"><span data-stu-id="68e57-148">The combined state of a send port and the send port group it belongs to determines if the send port or the send port group processes a message or not.</span></span>  
  
 <span data-ttu-id="68e57-149">下表描述傳送埠和傳送埠群組的可能狀態組合。</span><span class="sxs-lookup"><span data-stu-id="68e57-149">The following table describes the possible state combinations for send ports and send port groups.</span></span>  
  
|<span data-ttu-id="68e57-150">訊息已傳送</span><span class="sxs-lookup"><span data-stu-id="68e57-150">Message Sent</span></span>|<span data-ttu-id="68e57-151">傳送埠群組的狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-151">State of Send Port Group</span></span>|<span data-ttu-id="68e57-152">傳送埠的狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-152">State of Send Port</span></span>|<span data-ttu-id="68e57-153">結果</span><span class="sxs-lookup"><span data-stu-id="68e57-153">Outcome</span></span>|  
|------------------|------------------------------|------------------------|-------------|  
|<span data-ttu-id="68e57-154">直接至傳送埠</span><span class="sxs-lookup"><span data-stu-id="68e57-154">Directly to the send port</span></span>|<span data-ttu-id="68e57-155">任何狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-155">Any state</span></span>|<span data-ttu-id="68e57-156">Started</span><span class="sxs-lookup"><span data-stu-id="68e57-156">Started</span></span>|<span data-ttu-id="68e57-157">訊息已處理</span><span class="sxs-lookup"><span data-stu-id="68e57-157">Message is processed</span></span>|  
|<span data-ttu-id="68e57-158">直接至傳送埠</span><span class="sxs-lookup"><span data-stu-id="68e57-158">Directly to the send port</span></span>|<span data-ttu-id="68e57-159">任何狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-159">Any state</span></span>|<span data-ttu-id="68e57-160">Stopped</span><span class="sxs-lookup"><span data-stu-id="68e57-160">Stopped</span></span>|<span data-ttu-id="68e57-161">訊息已擱置</span><span class="sxs-lookup"><span data-stu-id="68e57-161">Message is suspended</span></span>|  
|<span data-ttu-id="68e57-162">透過傳送埠群組到傳送埠</span><span class="sxs-lookup"><span data-stu-id="68e57-162">To the send port by means of a send port group</span></span>|<span data-ttu-id="68e57-163">Started</span><span class="sxs-lookup"><span data-stu-id="68e57-163">Started</span></span>|<span data-ttu-id="68e57-164">Started</span><span class="sxs-lookup"><span data-stu-id="68e57-164">Started</span></span>|<span data-ttu-id="68e57-165">訊息已處理</span><span class="sxs-lookup"><span data-stu-id="68e57-165">Message is processed</span></span>|  
|<span data-ttu-id="68e57-166">透過傳送埠群組到傳送埠</span><span class="sxs-lookup"><span data-stu-id="68e57-166">To the send port by means of a send port group</span></span>|<span data-ttu-id="68e57-167">任何狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-167">Any state</span></span>|<span data-ttu-id="68e57-168">Stopped</span><span class="sxs-lookup"><span data-stu-id="68e57-168">Stopped</span></span>|<span data-ttu-id="68e57-169">訊息已擱置</span><span class="sxs-lookup"><span data-stu-id="68e57-169">Message is suspended</span></span>|  
|<span data-ttu-id="68e57-170">透過傳送埠群組到傳送埠</span><span class="sxs-lookup"><span data-stu-id="68e57-170">To the send port by means of a send port group</span></span>|<span data-ttu-id="68e57-171">Stopped</span><span class="sxs-lookup"><span data-stu-id="68e57-171">Stopped</span></span>|<span data-ttu-id="68e57-172">任何狀態</span><span class="sxs-lookup"><span data-stu-id="68e57-172">Any state</span></span>|<span data-ttu-id="68e57-173">訊息已擱置</span><span class="sxs-lookup"><span data-stu-id="68e57-173">Message is suspended</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68e57-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68e57-174">See Also</span></span>  
 [<span data-ttu-id="68e57-175">成品</span><span class="sxs-lookup"><span data-stu-id="68e57-175">Artifacts</span></span>](../core/artifacts.md)