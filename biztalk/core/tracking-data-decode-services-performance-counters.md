---
title: "追蹤資料解碼服務效能計數器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733450b1-71b5-48a4-9ac3-cd880324440c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99ec03138e455c671e9ccb69aa8bc4c5588d287c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-data-decode-services-performance-counters"></a><span data-ttu-id="f3bbd-102">追蹤資料解碼服務效能計數器</span><span class="sxs-lookup"><span data-stu-id="f3bbd-102">Tracking Data Decode Services Performance Counters</span></span>
<span data-ttu-id="f3bbd-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="f3bbd-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="f3bbd-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Tdds**效能物件類別：</span><span class="sxs-lookup"><span data-stu-id="f3bbd-105">The following performance counters are accessible for each host instance under the **BizTalk:TDDS** performance object category:</span></span>  
  
|<span data-ttu-id="f3bbd-106">**類別目錄**</span><span class="sxs-lookup"><span data-stu-id="f3bbd-106">**Category**</span></span>|<span data-ttu-id="f3bbd-107">**計數器**</span><span class="sxs-lookup"><span data-stu-id="f3bbd-107">**Counter**</span></span>|<span data-ttu-id="f3bbd-108">**說明**</span><span class="sxs-lookup"><span data-stu-id="f3bbd-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="f3bbd-109">BizTalk:TDDS</span><span class="sxs-lookup"><span data-stu-id="f3bbd-109">BizTalk:TDDS</span></span>|<span data-ttu-id="f3bbd-110">正在處理的批次</span><span class="sxs-lookup"><span data-stu-id="f3bbd-110">Batches being processed</span></span>|<span data-ttu-id="f3bbd-111">目前 SQL 交易正在處理的批次數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-111">The number of batches that are being processed inside the current SQL transaction.</span></span>|  
||<span data-ttu-id="f3bbd-112">認可的批次</span><span class="sxs-lookup"><span data-stu-id="f3bbd-112">Batches committed</span></span>|<span data-ttu-id="f3bbd-113">對目的資料庫認可的批次數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-113">The number of batches committed to the destination database.</span></span>|  
||<span data-ttu-id="f3bbd-114">正在處理的事件</span><span class="sxs-lookup"><span data-stu-id="f3bbd-114">Events being processed</span></span>|<span data-ttu-id="f3bbd-115">目前 SQL 交易正在處理的事件數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-115">The number of events that are being processed inside of the current SQL transaction.</span></span>|  
||<span data-ttu-id="f3bbd-116">認可的事件</span><span class="sxs-lookup"><span data-stu-id="f3bbd-116">Event Committed</span></span>|<span data-ttu-id="f3bbd-117">一秒內對目的資料庫確認的事件數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-117">The number of events committed to the destination database within this second.</span></span>|  
||<span data-ttu-id="f3bbd-118">正在處理的記錄</span><span class="sxs-lookup"><span data-stu-id="f3bbd-118">Records being processed</span></span>|<span data-ttu-id="f3bbd-119">目前 SQL 交易正在處理的記錄數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-119">The number of records that are being processed inside the current SQL transaction.</span></span>|  
||<span data-ttu-id="f3bbd-120">認可的記錄</span><span class="sxs-lookup"><span data-stu-id="f3bbd-120">Records Committed</span></span>|<span data-ttu-id="f3bbd-121">一秒內對目的資料庫確認的記錄數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-121">The number of records committed to the destination database during this second.</span></span>|  
||<span data-ttu-id="f3bbd-122">批次總數</span><span class="sxs-lookup"><span data-stu-id="f3bbd-122">Total Batches</span></span>|<span data-ttu-id="f3bbd-123">TDDS 已處理的批次總數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-123">Total batches processed by TDDS.</span></span>|  
||<span data-ttu-id="f3bbd-124">事件總數</span><span class="sxs-lookup"><span data-stu-id="f3bbd-124">Total Events</span></span>|<span data-ttu-id="f3bbd-125">TDDS 已處理的事件總數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-125">Total events processed by TDDS.</span></span>|  
||<span data-ttu-id="f3bbd-126">失敗的批次總數</span><span class="sxs-lookup"><span data-stu-id="f3bbd-126">Total Failed Batches</span></span>|<span data-ttu-id="f3bbd-127">TDDS 無法執行的批次總數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-127">Total batches failed to run by TDDS.</span></span>|  
||<span data-ttu-id="f3bbd-128">失敗的事件總數</span><span class="sxs-lookup"><span data-stu-id="f3bbd-128">Total Failed Events</span></span>|<span data-ttu-id="f3bbd-129">TDDS 無法執行的事件總數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-129">Total events failed to run by TDDS.</span></span>|  
||<span data-ttu-id="f3bbd-130">記錄總數</span><span class="sxs-lookup"><span data-stu-id="f3bbd-130">Total Records</span></span>|<span data-ttu-id="f3bbd-131">TDDS 已處理的記錄總數。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-131">Total records processed by TDDS.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="f3bbd-132">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="f3bbd-132">To access performance counters</span></span>  
 <span data-ttu-id="f3bbd-133">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-133">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="f3bbd-134">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="f3bbd-134">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="f3bbd-135">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-135">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="f3bbd-136">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-136">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="f3bbd-137">在**新增計數器**對話方塊中，從**可用的計數器**清單中，展開**biztalk: Tdds**效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="f3bbd-137">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:TDDS** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="f3bbd-138">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-138">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="f3bbd-139">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**>。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-139">To select all available counter instances, select \<**All instances**>.</span></span>  
  
5.  <span data-ttu-id="f3bbd-140">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-140">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="f3bbd-141">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="f3bbd-141">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bbd-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3bbd-142">See Also</span></span>  
 <span data-ttu-id="f3bbd-143">[效能秘訣和訣竅](../core/performance-tips-and-tricks.md) </span><span class="sxs-lookup"><span data-stu-id="f3bbd-143">[Performance Tips and Tricks](../core/performance-tips-and-tricks.md) </span></span>  
 <span data-ttu-id="f3bbd-144">[測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="f3bbd-144">[Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) </span></span>  
 <span data-ttu-id="f3bbd-145">[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="f3bbd-145">[Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md) </span></span>  
 [<span data-ttu-id="f3bbd-146">透過主控件節流將資源使用最佳化</span><span class="sxs-lookup"><span data-stu-id="f3bbd-146">Optimizing Resource Usage Through Host Throttling</span></span>](../core/optimizing-resource-usage-through-host-throttling.md)