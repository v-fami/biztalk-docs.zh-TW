---
title: 訊息方塊效能計數器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eafbd7b-f5fc-4942-a975-18154e6a7ee2
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 584cad0c850b85ef7c920da1611adbdc464d7250
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25972780"
---
# <a name="message-box-performance-counters"></a><span data-ttu-id="9ae23-102">MessageBox 效能計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-102">Message Box Performance Counters</span></span>
<span data-ttu-id="9ae23-103">效能計數器可讓您監視網站或系統上，服務所執行之工作的特定層面。</span><span class="sxs-lookup"><span data-stu-id="9ae23-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="9ae23-104">效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。</span><span class="sxs-lookup"><span data-stu-id="9ae23-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="9ae23-105">下列效能計數器會在每個主控件執行個體可存取**biztalk: Message Box： 一般計數器**和**biztalk: Message Box： 主控件計數器**效能物件類別:</span><span class="sxs-lookup"><span data-stu-id="9ae23-105">The following performance counters are accessible for each host instance under the **BizTalk:Message Box:General Counters** and the **BizTalk:Message Box:Host Counters** performance object categories:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ae23-106">若要啟用參照 SQL 代理程式工作的計數器，用於執行 BizTalk 主控件/NT 服務的服務帳戶必須隸屬 SQLAgentUserRole 角色。</span><span class="sxs-lookup"><span data-stu-id="9ae23-106">To enable counters that refer to the SQL Agent job, you must include the role SQLAgentUserRole to the service account used to run the BizTalk host/NT Service.</span></span> <span data-ttu-id="9ae23-107">或者，您也可以使用其他角色來授與權限，或授與該帳戶讀取 MSDB 資料庫的明確權限。</span><span class="sxs-lookup"><span data-stu-id="9ae23-107">Alternatively, you can grant permission using other roles or by granting explicit permission to read the MSDB database.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ae23-108">如果您已經加入新 MessageBox 至 BizTalk Server 群組，下列計數器方可將無法使用為此新 MessageBox 之前**快取重新整理**BizTalk Server 群組的間隔已經耗盡 （預設值為 60秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="9ae23-108">If you have added a new MessageBox to your BizTalk Server group, the counters listed below will not be available for the new MessageBox until the configured **Cache Refresh** interval for the BizTalk Server group has elapsed (default of 60 seconds).</span></span>  
  
|<span data-ttu-id="9ae23-109">類別目錄</span><span class="sxs-lookup"><span data-stu-id="9ae23-109">Category</span></span>|<span data-ttu-id="9ae23-110">計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-110">Counter</span></span>|<span data-ttu-id="9ae23-111">Description</span><span class="sxs-lookup"><span data-stu-id="9ae23-111">Description</span></span>|  
|--------------|-------------|-----------------|  
|<span data-ttu-id="9ae23-112">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-112">General Counters</span></span>|<span data-ttu-id="9ae23-113">執行個體 - 總數</span><span class="sxs-lookup"><span data-stu-id="9ae23-113">Instances-Total Number</span></span>|<span data-ttu-id="9ae23-114">追蹤每個主控件存在特定 MessageBox 中的所有執行個體總和。</span><span class="sxs-lookup"><span data-stu-id="9ae23-114">Tracks the sum of all the instances of each host, which exist within a particular Message Box.</span></span>|  
|<span data-ttu-id="9ae23-115">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-115">General Counters</span></span>|<span data-ttu-id="9ae23-116">MsgBox 終止程序清理 (清除工作)</span><span class="sxs-lookup"><span data-stu-id="9ae23-116">MsgBox Dead Processes Cleanup (Purge Jobs)</span></span>|<span data-ttu-id="9ae23-117">最近執行的 SQL 代理程式工作 (釋放與已終止的 BizTalk 程序關聯的資料庫資料列) 所花的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="9ae23-117">Time in seconds for most recent run of SQL agent job which releases database rows associated with dead BizTalk processes.</span></span>|  
|<span data-ttu-id="9ae23-118">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-118">General Counters</span></span>|<span data-ttu-id="9ae23-119">MsgBox 訊息清理 (清除工作)</span><span class="sxs-lookup"><span data-stu-id="9ae23-119">MsgBox Msg Cleanup (Purge Jobs)</span></span>|<span data-ttu-id="9ae23-120">最近執行的 SQL 代理程式工作 (清除與已移除之訊息關聯的 MessageBox 表格) 所花的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="9ae23-120">Time in seconds for most recent run of SQL agent job which cleans up message box tables associated with removed messages.</span></span>|  
|<span data-ttu-id="9ae23-121">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-121">General Counters</span></span>|<span data-ttu-id="9ae23-122">MsgBox 部分清理 (清除工作)</span><span class="sxs-lookup"><span data-stu-id="9ae23-122">MsgBox Parts Cleanup (Purge Jobs)</span></span>|<span data-ttu-id="9ae23-123">最近執行的 SQL 代理程式工作 (清除與已移除之訊息部分關聯的 MessageBox 表格) 所花的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="9ae23-123">Time in seconds for most recent run of SQL agent job which clean up message box tables associated with removed message parts.</span></span>|  
|<span data-ttu-id="9ae23-124">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-124">General Counters</span></span>|<span data-ttu-id="9ae23-125">MsgBox 清除訂閱工作 (清除工作)</span><span class="sxs-lookup"><span data-stu-id="9ae23-125">MsgBox Purge Subscriptions Job (Purge Jobs)</span></span>|<span data-ttu-id="9ae23-126">最近執行的 SQL 代理程式工作 (清除不再使用的訂閱) 所花的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="9ae23-126">Time in seconds for most recent run of SQL agent job which purges subscriptions which are no longer in use.</span></span>|  
|<span data-ttu-id="9ae23-127">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-127">General Counters</span></span>|<span data-ttu-id="9ae23-128">多工緩衝處理大小</span><span class="sxs-lookup"><span data-stu-id="9ae23-128">Spool Size</span></span>|<span data-ttu-id="9ae23-129">追蹤特定伺服器上特定 MessageBox 的多工緩衝處理大小。</span><span class="sxs-lookup"><span data-stu-id="9ae23-129">Tracks the size of the spool on a particular message box on a particular server.</span></span>|  
|<span data-ttu-id="9ae23-130">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-130">General Counters</span></span>|<span data-ttu-id="9ae23-131">追蹤訊息複製 (清除工作)</span><span class="sxs-lookup"><span data-stu-id="9ae23-131">Tracked Msgs Copy (Purge Jobs)</span></span>|<span data-ttu-id="9ae23-132">最近執行的 SQL 代理程式工作 (針對追蹤的訊息複製追蹤的訊息內文) 所花的時間 (秒)。</span><span class="sxs-lookup"><span data-stu-id="9ae23-132">Time in seconds for most recent run of SQL agent job which copies tracked message bodies for tracked messages.</span></span>|  
|<span data-ttu-id="9ae23-133">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-133">General Counters</span></span>|<span data-ttu-id="9ae23-134">追蹤資料大小</span><span class="sxs-lookup"><span data-stu-id="9ae23-134">Tracking data size</span></span>|<span data-ttu-id="9ae23-135">追蹤特定伺服器上特定 MessageBox 中的追蹤資料表大小。</span><span class="sxs-lookup"><span data-stu-id="9ae23-135">Tracks the size of the tracking data table on a particular message box on a particular server.</span></span>|  
|<span data-ttu-id="9ae23-136">一般計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-136">General Counters</span></span>|<span data-ttu-id="9ae23-137">追蹤多工緩衝處理清理 (清除工作)</span><span class="sxs-lookup"><span data-stu-id="9ae23-137">Tracking Spool Cleanup (Purge Jobs)</span></span>|<span data-ttu-id="9ae23-138">時間 （秒） 最近執行的清除非作用中的 SQL 代理程式作業追蹤多工緩衝處理資料表。</span><span class="sxs-lookup"><span data-stu-id="9ae23-138">Time in seconds for the most recent run of the SQL agent job which purges the inactive tracking spool tables.</span></span>|  
|<span data-ttu-id="9ae23-139">主控件計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-139">Host Counters</span></span>|<span data-ttu-id="9ae23-140">主控件佇列 - 執行個體狀態訊息參考 - 長度</span><span class="sxs-lookup"><span data-stu-id="9ae23-140">Host Queue - Instance State Msg Refs - Length</span></span>|<span data-ttu-id="9ae23-141">追蹤此特定主控件的執行個體狀態佇列中的訊息參考數。</span><span class="sxs-lookup"><span data-stu-id="9ae23-141">Tracks the number of message references in the instance state queue for this particular host.</span></span>|  
|<span data-ttu-id="9ae23-142">主控件計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-142">Host Counters</span></span>|<span data-ttu-id="9ae23-143">主控件佇列 - 長度</span><span class="sxs-lookup"><span data-stu-id="9ae23-143">Host Queue - Length</span></span>|<span data-ttu-id="9ae23-144">追蹤特定主控件佇列中的訊息總數。</span><span class="sxs-lookup"><span data-stu-id="9ae23-144">Tracks the total number of messages in the particular host queue.</span></span>|  
|<span data-ttu-id="9ae23-145">主控件計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-145">Host Counters</span></span>|<span data-ttu-id="9ae23-146">主控件佇列 - 執行個體數</span><span class="sxs-lookup"><span data-stu-id="9ae23-146">Host Queue - Number of Instances</span></span>|<span data-ttu-id="9ae23-147">追蹤此特定主控件的執行個體數。</span><span class="sxs-lookup"><span data-stu-id="9ae23-147">Tracks the number of instances of this particular host.</span></span>|  
|<span data-ttu-id="9ae23-148">主控件計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-148">Host Counters</span></span>|<span data-ttu-id="9ae23-149">主控件佇列 - 擱置的訊息 - 長度</span><span class="sxs-lookup"><span data-stu-id="9ae23-149">Host Queue - Suspended Msgs - Length</span></span>|<span data-ttu-id="9ae23-150">追蹤特定主控件的擱置訊息總數。</span><span class="sxs-lookup"><span data-stu-id="9ae23-150">Tracks the total number of suspended messages for the particular host.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="9ae23-151">存取效能計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-151">To access performance counters</span></span>  
 <span data-ttu-id="9ae23-152">使用下列步驟來存取效能計數器。</span><span class="sxs-lookup"><span data-stu-id="9ae23-152">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="9ae23-153">若是使用 Windows 2008</span><span class="sxs-lookup"><span data-stu-id="9ae23-153">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="9ae23-154">按一下**啟動**，指向 **系統管理工具**，然後按一下 **效能監視器**。</span><span class="sxs-lookup"><span data-stu-id="9ae23-154">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="9ae23-155">在**效能監視器**對話方塊方塊中，展開 **監視工具**，選取**效能監視器**，然後按一下 **新增**。</span><span class="sxs-lookup"><span data-stu-id="9ae23-155">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="9ae23-156">在**新增計數器**對話方塊中，從**可用的計數器**清單中，選取**biztalk: Message Box： 一般計數器**或**biztalk： 訊息方塊： 裝載計數器**。</span><span class="sxs-lookup"><span data-stu-id="9ae23-156">In the **Add Counters** dialog box, from the **Available Counters** list, select either **BizTalk:Message Box:General Counters** or  **BizTalk:Message box:Host Counters**.</span></span> <span data-ttu-id="9ae23-157">展開選取的效能計數器物件，然後選取要監視的計數器</span><span class="sxs-lookup"><span data-stu-id="9ae23-157">Expand the selected performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="9ae23-158">在**選取執行個體的物件**清單中，選取要監視針對所選取計數器，然後按一下 特定的執行個體**新增**。</span><span class="sxs-lookup"><span data-stu-id="9ae23-158">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="9ae23-159">若要選取所有可用的計數器執行個體，請選取\<**所有執行個體**\>。</span><span class="sxs-lookup"><span data-stu-id="9ae23-159">To select all available counter instances, select \<**All instances**\>.</span></span>  
  
5.  <span data-ttu-id="9ae23-160">新增計數器後, 按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="9ae23-160">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="9ae23-161">選取的效能計數器隨即出現在**效能監視器**螢幕。</span><span class="sxs-lookup"><span data-stu-id="9ae23-161">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ae23-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="9ae23-162">See Also</span></span>  
 <span data-ttu-id="9ae23-163">[效能秘訣和訣竅](../core/performance-tips-and-tricks.md) </span><span class="sxs-lookup"><span data-stu-id="9ae23-163">[Performance Tips and Tricks](../core/performance-tips-and-tricks.md) </span></span>  
 <span data-ttu-id="9ae23-164">[測量最大持續性引擎輸送量](../core/measuring-maximum-sustainable-engine-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="9ae23-164">[Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) </span></span>  
 <span data-ttu-id="9ae23-165">[測量最大持續性追蹤輸送量](../core/measuring-maximum-sustainable-tracking-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="9ae23-165">[Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md) </span></span>  
 [<span data-ttu-id="9ae23-166">透過主控件節流將資源使用最佳化</span><span class="sxs-lookup"><span data-stu-id="9ae23-166">Optimizing Resource Usage Through Host Throttling</span></span>](../core/optimizing-resource-usage-through-host-throttling.md)