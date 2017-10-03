---
title: "HTTP 配接器效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d85473f1-1d67-4990-8d2f-fc7fe0e80108
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21ae11dfb3ecd9a2b5e63449961af70aa3bc6f7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-performance-counters"></a><span data-ttu-id="8e543-102">HTTP 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="8e543-102">HTTP Adapter Performance Counters</span></span>
<span data-ttu-id="8e543-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="8e543-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="8e543-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="8e543-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="8e543-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Http 接收配接器**和**biztalk: Http 傳送配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="8e543-105">The following performance counters are accessible for each host instance under the **BizTalk:HTTP Receive Adapter** and the **BizTalk:HTTP Send Adapter** performance object categories:</span></span>  
  
|<span data-ttu-id="8e543-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="8e543-106">**Category**</span></span>|<span data-ttu-id="8e543-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="8e543-107">**Counter**</span></span>|<span data-ttu-id="8e543-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="8e543-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="8e543-109">BizTalk:HTTP 接收配接器</span><span class="sxs-lookup"><span data-stu-id="8e543-109">BizTalk:HTTP Receive Adapter</span></span>|<span data-ttu-id="8e543-110">Memory queue size</span><span class="sxs-lookup"><span data-stu-id="8e543-110">Memory queue size</span></span>|<span data-ttu-id="8e543-111">HTTP 接收配接器的內部記憶體佇列中的內送訊息數。</span><span class="sxs-lookup"><span data-stu-id="8e543-111">Number of incoming messages in the HTTP receive adapter's internal memory queue.</span></span>|  
||<span data-ttu-id="8e543-112">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="8e543-112">Message received</span></span>|<span data-ttu-id="8e543-113">HTTP 接收配接器接收的 HTTP 要求總數。</span><span class="sxs-lookup"><span data-stu-id="8e543-113">Total number of HTTP requests received by the HTTP receive adapter.</span></span> <span data-ttu-id="8e543-114">此計數器會在 HTTP 接收配接器從 HTTP 用戶端完整讀取要求訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="8e543-114">The counter is incremented after a request message is completely read by the HTTP receive adapter from the HTTP client.</span></span>|  
||<span data-ttu-id="8e543-115">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="8e543-115">Messages received/Sec</span></span>|<span data-ttu-id="8e543-116">HTTP 接收配接器每秒接收的 HTTP 要求數。</span><span class="sxs-lookup"><span data-stu-id="8e543-116">Number of HTTP requests received by the HTTP receive adapter per second.</span></span> <span data-ttu-id="8e543-117">此計數器只適用於 HTTP 接收配接器從 HTTP 用戶端完整讀取的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="8e543-117">The counter applies only to request messages that have been completely read by the HTTP receive adapter from the HTTP client.</span></span>|  
||<span data-ttu-id="8e543-118">Messages sent</span><span class="sxs-lookup"><span data-stu-id="8e543-118">Messages sent</span></span>|<span data-ttu-id="8e543-119">HTTP 接收配接器傳送的 HTTP 回應總數。</span><span class="sxs-lookup"><span data-stu-id="8e543-119">Total number of HTTP responses sent by the HTTP receive adapter.</span></span> <span data-ttu-id="8e543-120">此計數器只會在回應訊息已成功傳送至 HTTP 用戶端後遞增。</span><span class="sxs-lookup"><span data-stu-id="8e543-120">The counter is incremented only for response messages that have been successfully sent to HTTP clients.</span></span>|  
||<span data-ttu-id="8e543-121">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="8e543-121">Messages sent/Sec</span></span>|<span data-ttu-id="8e543-122">HTTP 接收配接器每秒傳送的 HTTP 回應數。</span><span class="sxs-lookup"><span data-stu-id="8e543-122">Number of HTTP responses sent by the HTTP receive adapter per second.</span></span> <span data-ttu-id="8e543-123">此計數器只適用於已成功傳送至 HTTP 用戶端的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="8e543-123">The counter applies only to response messages that have been successfully sent to HTTP clients.</span></span>|  
||<span data-ttu-id="8e543-124">新增訊息至批次的時間</span><span class="sxs-lookup"><span data-stu-id="8e543-124">Time to add message to batch</span></span>|<span data-ttu-id="8e543-125">IIS 將訊息提供給 HTTP 接收配接器，到該訊息新增至某個批次之間的平均時間。</span><span class="sxs-lookup"><span data-stu-id="8e543-125">Average time between when a message is given to the HTTP receive adapter by IIS and when the message is added to a batch.</span></span>|  
||<span data-ttu-id="8e543-126">建置批次時間</span><span class="sxs-lookup"><span data-stu-id="8e543-126">Time to build batch</span></span>|<span data-ttu-id="8e543-127">HTTP 接收配接器建立訊息批次的平均時間。</span><span class="sxs-lookup"><span data-stu-id="8e543-127">Average time taken by the HTTP receive adapter to build a message batch.</span></span>|  
|<span data-ttu-id="8e543-128">BizTalk:HTTP 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="8e543-128">BizTalk:HTTP Send Adapter</span></span>|<span data-ttu-id="8e543-129">Memory queue size</span><span class="sxs-lookup"><span data-stu-id="8e543-129">Memory queue size</span></span>|<span data-ttu-id="8e543-130">HTTP 傳送配接器的內部記憶體佇列中的外寄訊息數。</span><span class="sxs-lookup"><span data-stu-id="8e543-130">Number of outgoing messages in the HTTP send adapter's internal memory queue.</span></span>|  
||<span data-ttu-id="8e543-131">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="8e543-131">Messages received</span></span>|<span data-ttu-id="8e543-132">HTTP 傳送配接器接收的 HTTP 回應訊息總數。</span><span class="sxs-lookup"><span data-stu-id="8e543-132">Total number of HTTP response messages received by the HTTP send adapter.</span></span> <span data-ttu-id="8e543-133">此計數器會在 HTTP 傳送配接器從 HTTP 伺服器完整讀取回應訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="8e543-133">The counter is incremented after a response message is completely read by the HTTP send adapter from HTTP servers.</span></span>|  
||<span data-ttu-id="8e543-134">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="8e543-134">Message received/Sec</span></span>|<span data-ttu-id="8e543-135">HTTP 傳送配接器每秒接收的 HTTP 回應數。</span><span class="sxs-lookup"><span data-stu-id="8e543-135">Number of HTTP responses received by the HTTP send adapter per second.</span></span> <span data-ttu-id="8e543-136">此計數器只適用於 HTTP 傳送配接器從 HTTP 伺服器完整讀取的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="8e543-136">The counter applies only to response messages that have been completely read by the HTTP send adapter from HTTP servers.</span></span>|  
||<span data-ttu-id="8e543-137">Messages sent</span><span class="sxs-lookup"><span data-stu-id="8e543-137">Messages sent</span></span>|<span data-ttu-id="8e543-138">HTTP 傳送配接器傳送的 HTTP 要求總數。</span><span class="sxs-lookup"><span data-stu-id="8e543-138">Total number of HTTP requests sent by the HTTP send adapter.</span></span> <span data-ttu-id="8e543-139">此計數器只會在要求訊息已到達目的地 URL 後遞增。</span><span class="sxs-lookup"><span data-stu-id="8e543-139">The counter is incremented only for request messages that have reached the destination URL.</span></span>|  
||<span data-ttu-id="8e543-140">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="8e543-140">Messages sent/Sec</span></span>|<span data-ttu-id="8e543-141">HTTP 傳送配接器每秒傳送的 HTTP 要求數。</span><span class="sxs-lookup"><span data-stu-id="8e543-141">Number of HTTP requests sent by the HTTP send adapter per second.</span></span> <span data-ttu-id="8e543-142">此計數器只適用於已到達目的地 URL 的要求訊息。</span><span class="sxs-lookup"><span data-stu-id="8e543-142">The counter applies only to request messages that have reached the destination URL.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="8e543-143">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="8e543-143">To access performance counters</span></span>  
 <span data-ttu-id="8e543-144">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="8e543-144">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="8e543-145">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="8e543-145">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="8e543-146">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="8e543-146">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="8e543-147">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="8e543-147">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="8e543-148">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Http**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="8e543-148">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:HTTP** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="8e543-149">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="8e543-149">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="8e543-150">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**>。</span><span class="sxs-lookup"><span data-stu-id="8e543-150">To select all available counter instances, select \<**All instances**>.</span></span>  
  
5.  <span data-ttu-id="8e543-151">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="8e543-151">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="8e543-152">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="8e543-152">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e543-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e543-153">See Also</span></span>  
 <span data-ttu-id="8e543-154">[監控 BizTalk Server](../core/monitoring-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="8e543-154">[Monitoring BizTalk Server](../core/monitoring-biztalk-server.md) </span></span>  
 <span data-ttu-id="8e543-155">[HTTP 配接器組態和調整參數](../core/http-adapter-configuration-and-tuning-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="8e543-155">[HTTP Adapter Configuration and Tuning Parameters](../core/http-adapter-configuration-and-tuning-parameters.md) </span></span>  
 [<span data-ttu-id="8e543-156">執行叢集主控件中的配接器處理常式的考量</span><span class="sxs-lookup"><span data-stu-id="8e543-156">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)