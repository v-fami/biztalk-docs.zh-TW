---
title: MSMQ 配接器效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab8b0342-c6c2-4113-ae54-359df28e5d30
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be7580ae6551fca18ee0a3b9b14b194006efd62e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971844"
---
# <a name="msmq-adapter-performance-counters"></a><span data-ttu-id="fe2f5-102">MSMQ 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="fe2f5-102">MSMQ Adapter Performance Counters</span></span>
<span data-ttu-id="fe2f5-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="fe2f5-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="fe2f5-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Msmq 接收配接器**和**biztalk: Msmq 傳送配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="fe2f5-105">The following performance counters are accessible for each host instance under the **BizTalk:MSMQ Receive Adapter** and the **BizTalk:MSMQ Send Adapter** performance object categories:</span></span>  
  
|<span data-ttu-id="fe2f5-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="fe2f5-106">**Category**</span></span>|<span data-ttu-id="fe2f5-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="fe2f5-107">**Counter**</span></span>|<span data-ttu-id="fe2f5-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="fe2f5-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="fe2f5-109">BizTalk:MSMQ 接收配接器</span><span class="sxs-lookup"><span data-stu-id="fe2f5-109">BizTalk:MSMQ Receive Adapter</span></span>|<span data-ttu-id="fe2f5-110">接收位元組數</span><span class="sxs-lookup"><span data-stu-id="fe2f5-110">Bytes received</span></span>|<span data-ttu-id="fe2f5-111">MSMQ 接收配接器接收的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-111">Total number of bytes received by the MSMQ receive adapter.</span></span> <span data-ttu-id="fe2f5-112">此計數器會在 MSMQ 接收配接器從來源佇列完整讀取訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-112">The counter is incremented after a message is completely read by the MSMQ receive adapter from the source queue.</span></span>|  
||<span data-ttu-id="fe2f5-113">接收位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="fe2f5-113">Bytes received/Sec</span></span>|<span data-ttu-id="fe2f5-114">MSMQ 接收配接器每秒收到的位元組數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-114">Number of bytes received by the MSMQ receive adapter per second.</span></span> <span data-ttu-id="fe2f5-115">此計數器只適用於 MSMQ 接收配接器從來源佇列完整讀取的訊息。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-115">The counter applies only to messages that have been completely read by the MSMQ receive adapter from the source queue.</span></span>|  
||<span data-ttu-id="fe2f5-116">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="fe2f5-116">Messages received</span></span>|<span data-ttu-id="fe2f5-117">MSMQ 接收配接器接收的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-117">Total number of messages received by the MSMQ receive adapter.</span></span> <span data-ttu-id="fe2f5-118">此計數器會在 MSMQ 接收配接器從來源佇列完整讀取訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-118">The counter is incremented after a message is completely read by the MSMQ receive adapter from the source queue.</span></span>|  
||<span data-ttu-id="fe2f5-119">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="fe2f5-119">Messages received/Sec</span></span>|<span data-ttu-id="fe2f5-120">MSMQ 接收配接器每秒收到的訊息數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-120">Number of messages received by the MSMQ receive adapter per second.</span></span> <span data-ttu-id="fe2f5-121">此計數器只適用於 MSMQ 接收配接器從來源佇列完整讀取的訊息。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-121">The counter applies only to messages that have been completely read by the MSMQ receive adapter from the source queue.</span></span>|  
|<span data-ttu-id="fe2f5-122">BizTalk:MSMQ 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="fe2f5-122">BizTalk:MSMQ Send Adapter</span></span>|<span data-ttu-id="fe2f5-123">傳送位元組數</span><span class="sxs-lookup"><span data-stu-id="fe2f5-123">Bytes sent</span></span>|<span data-ttu-id="fe2f5-124">MSMQ 傳送配接器傳送的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-124">Total number of bytes sent by the MSMQ send adapter.</span></span> <span data-ttu-id="fe2f5-125">此計數器只會在訊息已到達目的地佇列後遞增。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-125">The counter is incremented only for messages that have reached the destination queue.</span></span>|  
||<span data-ttu-id="fe2f5-126">傳送位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="fe2f5-126">Bytes sent/Sec</span></span>|<span data-ttu-id="fe2f5-127">MSMQ 傳送配接器每秒傳送的位元組數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-127">Number of bytes sent by the MSMQ send adapter per second.</span></span> <span data-ttu-id="fe2f5-128">此計數器只適用於已到達目的地佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-128">The counter applies only to messages that have reached the destination queue.</span></span>|  
||<span data-ttu-id="fe2f5-129">Messages sent</span><span class="sxs-lookup"><span data-stu-id="fe2f5-129">Messages sent</span></span>|<span data-ttu-id="fe2f5-130">MSMQ 傳送配接器傳送的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-130">Total number of messages sent by the MSMQ send adapter.</span></span> <span data-ttu-id="fe2f5-131">此計數器只會在訊息已到達目的地佇列後遞增。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-131">The counter is incremented only for messages that have reached the destination queue.</span></span>|  
||<span data-ttu-id="fe2f5-132">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="fe2f5-132">Messages sent/Sec</span></span>|<span data-ttu-id="fe2f5-133">MSMQ 傳送配接器每秒傳送的訊息數。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-133">Number of messages sent by the MSMQ send adapter per second.</span></span> <span data-ttu-id="fe2f5-134">此計數器只適用於已到達目的地佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-134">The counter applies only to messages that have reached the destination queue.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="fe2f5-135">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="fe2f5-135">To access performance counters</span></span>  
 <span data-ttu-id="fe2f5-136">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-136">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="fe2f5-137">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="fe2f5-137">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="fe2f5-138">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-138">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="fe2f5-139">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-139">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="fe2f5-140">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Msmq**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="fe2f5-140">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:MSMQ** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="fe2f5-141">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-141">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="fe2f5-142">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-142">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="fe2f5-143">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-143">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="fe2f5-144">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="fe2f5-144">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe2f5-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe2f5-145">See Also</span></span>  
 <span data-ttu-id="fe2f5-146">[搭配 MSMQ 使用 LoadGen 2007](../core/using-loadgen-2007-with-msmq.md) </span><span class="sxs-lookup"><span data-stu-id="fe2f5-146">[Using LoadGen 2007 with MSMQ](../core/using-loadgen-2007-with-msmq.md) </span></span>  
 [<span data-ttu-id="fe2f5-147">最佳化 MSMQ 配接器的效能</span><span class="sxs-lookup"><span data-stu-id="fe2f5-147">Optimizing Performance of the MSMQ Adapter</span></span>](../core/optimizing-performance-of-the-msmq-adapter.md)