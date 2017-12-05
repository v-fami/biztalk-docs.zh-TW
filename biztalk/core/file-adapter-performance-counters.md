---
title: "檔案配接器效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 343465b4-6b20-4a24-b4b1-138548c572cc
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d48cf2cf203ed001611bb30e3c9f1d5746a903e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="file-adapter-performance-counters"></a><span data-ttu-id="aef0f-102">FILE 配接器效能計數器</span><span class="sxs-lookup"><span data-stu-id="aef0f-102">File Adapter Performance Counters</span></span>
<span data-ttu-id="aef0f-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="aef0f-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="aef0f-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="aef0f-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="aef0f-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: File 接收配接器**和**biztalk: File 傳送配接器**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="aef0f-105">The following performance counters are accessible for each host instance under the **BizTalk:FILE Receive Adapter** and the **BizTalk:FILE Send Adapter** performance object categories:</span></span>  
  
|<span data-ttu-id="aef0f-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="aef0f-106">**Category**</span></span>|<span data-ttu-id="aef0f-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="aef0f-107">**Counter**</span></span>|<span data-ttu-id="aef0f-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="aef0f-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="aef0f-109">BizTalk:FILE 接收配接器</span><span class="sxs-lookup"><span data-stu-id="aef0f-109">BizTalk:FILE Receive Adapter</span></span>|<span data-ttu-id="aef0f-110">接收位元組數</span><span class="sxs-lookup"><span data-stu-id="aef0f-110">Bytes received</span></span>|<span data-ttu-id="aef0f-111">FILE 接收配接器接收的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-111">Total number of bytes received by the file receive adapter.</span></span> <span data-ttu-id="aef0f-112">此計數器會在配接器從檔案系統完整讀取訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="aef0f-112">The counter is incremented after a message is completely read by the adapter from the file system.</span></span>|  
||<span data-ttu-id="aef0f-113">接收位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="aef0f-113">Byte received/Sec</span></span>|<span data-ttu-id="aef0f-114">FILE 接收配接器每秒收到的位元組數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-114">Number of bytes received by the file receive adapter per second.</span></span> <span data-ttu-id="aef0f-115">此計數器只適用於 FILE 配接器從檔案系統完整讀取的訊息。</span><span class="sxs-lookup"><span data-stu-id="aef0f-115">The counter applies only to messages that have been completely read by the file adapter from the file system.</span></span>|  
||<span data-ttu-id="aef0f-116">刪除重試次數</span><span class="sxs-lookup"><span data-stu-id="aef0f-116">Delete retries</span></span>|<span data-ttu-id="aef0f-117">FILE 接收配接器嘗試刪除已讀取檔案的次數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-117">Number of times the file receive adapter attempts to delete a file that has been read.</span></span>|  
||<span data-ttu-id="aef0f-118">鎖定失敗次數</span><span class="sxs-lookup"><span data-stu-id="aef0f-118">Lock failures</span></span>|<span data-ttu-id="aef0f-119">FILE 接收配接器鎖定檔案失敗的次數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-119">Number of times the file receive adapter failed to lock the file.</span></span>|  
||<span data-ttu-id="aef0f-120">鎖定失敗次數/秒</span><span class="sxs-lookup"><span data-stu-id="aef0f-120">Lock failures/sec</span></span>|<span data-ttu-id="aef0f-121">FILE 接收配接器每秒鎖定檔案失敗的次數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-121">Number of times the file receive adapter failed to lock the file per second.</span></span>|  
||<span data-ttu-id="aef0f-122">接收訊息數</span><span class="sxs-lookup"><span data-stu-id="aef0f-122">Messages received</span></span>|<span data-ttu-id="aef0f-123">FILE 接收配接器接收的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-123">Total number of messages received by the file receive adapter.</span></span> <span data-ttu-id="aef0f-124">此計數器會在 FILE 接收配接器從檔案系統完整讀取訊息後遞增。</span><span class="sxs-lookup"><span data-stu-id="aef0f-124">The counter is incremented after a message is completely read by the file receive adapter from the file system.</span></span>|  
||<span data-ttu-id="aef0f-125">接收訊息數/秒</span><span class="sxs-lookup"><span data-stu-id="aef0f-125">Messages received/Sec</span></span>|<span data-ttu-id="aef0f-126">FILE 接收配接器每秒收到的訊息數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-126">Number of messages received by the file receive adapter per second.</span></span> <span data-ttu-id="aef0f-127">此計數器只適用於 FILE 接收配接器從檔案系統完整讀取的訊息。</span><span class="sxs-lookup"><span data-stu-id="aef0f-127">The counter applies only to messages that have been completely read by the file receive adapter from the file system.</span></span>|  
||<span data-ttu-id="aef0f-128">建置批次時間</span><span class="sxs-lookup"><span data-stu-id="aef0f-128">Time to build batch</span></span>|<span data-ttu-id="aef0f-129">FILE 接收配接器建立批次的平均時間。</span><span class="sxs-lookup"><span data-stu-id="aef0f-129">Average time taken by file receive adapter to build a batch.</span></span>|  
|<span data-ttu-id="aef0f-130">BizTalk:FILE 傳送配接器</span><span class="sxs-lookup"><span data-stu-id="aef0f-130">BizTalk:FILE Send Adapter</span></span>|<span data-ttu-id="aef0f-131">傳送位元組數</span><span class="sxs-lookup"><span data-stu-id="aef0f-131">Bytes sent</span></span>|<span data-ttu-id="aef0f-132">FILE 傳送配接器傳送的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-132">Total number of bytes sent by the file send adapter.</span></span> <span data-ttu-id="aef0f-133">此計數器只會在訊息已完整寫入檔案系統後遞增。</span><span class="sxs-lookup"><span data-stu-id="aef0f-133">The counter is incremented only for messages that have been completely written to file system.</span></span>|  
||<span data-ttu-id="aef0f-134">傳送位元組數/秒</span><span class="sxs-lookup"><span data-stu-id="aef0f-134">Bytes sent/Sec</span></span>|<span data-ttu-id="aef0f-135">FILE 傳送配接器每秒傳送的位元組數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-135">Number of bytes sent by the file send adapter per second.</span></span> <span data-ttu-id="aef0f-136">此計數器只適用於已完整寫入檔案系統的訊息。</span><span class="sxs-lookup"><span data-stu-id="aef0f-136">The counter applies only to messages that have been completely written to file system.</span></span>|  
||<span data-ttu-id="aef0f-137">Messages sent</span><span class="sxs-lookup"><span data-stu-id="aef0f-137">Messages sent</span></span>|<span data-ttu-id="aef0f-138">FILE 傳送配接器傳送的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-138">Total number of messages sent by the file send adapter.</span></span> <span data-ttu-id="aef0f-139">此計數器只會在訊息已完整寫入檔案系統後遞增。</span><span class="sxs-lookup"><span data-stu-id="aef0f-139">The counter is incremented only for messages that have been completely written to file system.</span></span>|  
||<span data-ttu-id="aef0f-140">Messages sent/Sec</span><span class="sxs-lookup"><span data-stu-id="aef0f-140">Messages sent/Sec</span></span>|<span data-ttu-id="aef0f-141">FILE 傳送配接器每秒傳送的訊息數。</span><span class="sxs-lookup"><span data-stu-id="aef0f-141">Number of messages sent by the file send adapter per second.</span></span> <span data-ttu-id="aef0f-142">此計數器只適用於已完整寫入檔案系統的訊息。</span><span class="sxs-lookup"><span data-stu-id="aef0f-142">The counter applies only to messages that have been completely written to file system.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="aef0f-143">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="aef0f-143">To access performance counters</span></span>  
 <span data-ttu-id="aef0f-144">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="aef0f-144">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="aef0f-145">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="aef0f-145">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="aef0f-146">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="aef0f-146">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="aef0f-147">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="aef0f-147">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="aef0f-148">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: File**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="aef0f-148">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:FILE** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="aef0f-149">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="aef0f-149">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="aef0f-150">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="aef0f-150">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="aef0f-151">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="aef0f-151">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="aef0f-152">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="aef0f-152">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef0f-153">請參閱</span><span class="sxs-lookup"><span data-stu-id="aef0f-153">See Also</span></span>  
 [<span data-ttu-id="aef0f-154">持續性效能的規劃</span><span class="sxs-lookup"><span data-stu-id="aef0f-154">Planning for Sustained Performance</span></span>](../core/planning-for-sustained-performance.md)