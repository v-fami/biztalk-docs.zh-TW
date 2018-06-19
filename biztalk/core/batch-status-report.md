---
title: 批次狀態報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04dad016-e7bb-45cd-b36a-a9c83d073501
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c033f58432c8ae5a2d87b87b56223b8f64a7201
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231798"
---
# <a name="batch-status-report"></a><span data-ttu-id="8e6e3-102">批次狀態報告</span><span class="sxs-lookup"><span data-stu-id="8e6e3-102">Batch Status Report</span></span>
<span data-ttu-id="8e6e3-103">這份報告會顯示批次協調流程的執行個體活動。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-103">This report shows the activity of instances of the batching orchestration.</span></span> <span data-ttu-id="8e6e3-104">報告中的每一列表示批次協調流程單一執行個體所處理的批次狀態。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-104">Each row in the report indicates the status of the batches being processed by a single instance of the batching orchestration.</span></span>  
  
 <span data-ttu-id="8e6e3-105">保留批次的狀態不會在「批次狀態報告」中提供，但「交換/通知狀態」報告中有提供其報告資料。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-105">The status of preserved batches is not reported in the Batch Status Report, but is reported in the Interchange/ACK Status report.</span></span>  
  
## <a name="fields-in-the-status-report"></a><span data-ttu-id="8e6e3-106">狀態報告中的欄位</span><span class="sxs-lookup"><span data-stu-id="8e6e3-106">Fields in the Status Report</span></span>  
 <span data-ttu-id="8e6e3-107">「批次狀態報告」會顯示批次交換的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="8e6e3-107">The Batch Status Report displays the following information for batched interchanges:</span></span>  
  
-   <span data-ttu-id="8e6e3-108">批次狀態</span><span class="sxs-lookup"><span data-stu-id="8e6e3-108">Batch Status</span></span>  
  
-   <span data-ttu-id="8e6e3-109">批次名稱</span><span class="sxs-lookup"><span data-stu-id="8e6e3-109">Batch Name</span></span>  
  
-   <span data-ttu-id="8e6e3-110">目的合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="8e6e3-110">Destination Party Name</span></span>  
  
-   <span data-ttu-id="8e6e3-111">啟動時間</span><span class="sxs-lookup"><span data-stu-id="8e6e3-111">Activation Time</span></span>  
  
-   <span data-ttu-id="8e6e3-112">批次發生次數</span><span class="sxs-lookup"><span data-stu-id="8e6e3-112">Batch Occurrence</span></span>  
  
-   <span data-ttu-id="8e6e3-113">EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="8e6e3-113">EDI Encoding Type</span></span>  
  
-   <span data-ttu-id="8e6e3-114">批次類型</span><span class="sxs-lookup"><span data-stu-id="8e6e3-114">Batch Type</span></span>  
  
-   <span data-ttu-id="8e6e3-115">批次目標</span><span class="sxs-lookup"><span data-stu-id="8e6e3-115">Batch Target</span></span>  
  
-   <span data-ttu-id="8e6e3-116">批次項目計數： 批次項目數目已經累積的批次處理協調流程執行個體</span><span class="sxs-lookup"><span data-stu-id="8e6e3-116">Batch Element Count: how many batch elements have been accumulated by the batching orchestration instance</span></span>  
  
-   <span data-ttu-id="8e6e3-117">已拒絕元素計數</span><span class="sxs-lookup"><span data-stu-id="8e6e3-117">Rejected Elements Count</span></span>  
  
-   <span data-ttu-id="8e6e3-118">批次已啟動、 排程釋放、 計數式釋放、 手動覆寫釋放、 批次終止/停止釋放、 新增項目，或外部釋放，可以是最新動作：</span><span class="sxs-lookup"><span data-stu-id="8e6e3-118">Latest Action: Can be Batch Activated, Scheduled Release, Count Based Release, Manual Override Release, Batch Terminated/Stop Release, Element Added, or External Release</span></span>  
  
-   <span data-ttu-id="8e6e3-119">交換控制編號</span><span class="sxs-lookup"><span data-stu-id="8e6e3-119">Interchange Control Number</span></span>  
  
-   <span data-ttu-id="8e6e3-120">交換日期時間</span><span class="sxs-lookup"><span data-stu-id="8e6e3-120">Interchange Date Time</span></span>  
  
-   <span data-ttu-id="8e6e3-121">批次大小 (以字元為單位) (預設情況下不顯示)</span><span class="sxs-lookup"><span data-stu-id="8e6e3-121">Batch Size (in characters) (not displayed by default)</span></span>  
  
## <a name="view-related-interchanges-status-reports"></a><span data-ttu-id="8e6e3-122">檢視相關的交換狀態報告</span><span class="sxs-lookup"><span data-stu-id="8e6e3-122">View Related Interchanges Status Reports</span></span>  
 <span data-ttu-id="8e6e3-123">如果您以滑鼠右鍵按一下的交換或批次狀態報告中所列的通知，您可以顯示的批次相關之交換的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-123">If you right-click an interchange or acknowledgment listed in the Batch Status Report, you can display details about the interchanges related to the batch.</span></span>  
  
## <a name="fields-in-the-query-expression-for-the-status-report"></a><span data-ttu-id="8e6e3-124">狀態報告之查詢運算式中的欄位</span><span class="sxs-lookup"><span data-stu-id="8e6e3-124">Fields in the Query Expression for the Status Report</span></span>  
 <span data-ttu-id="8e6e3-125">您可以自訂「批次狀態報告」，藉由變更查詢運算式中的欄位，來決定要顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-125">You can customize the Batch Status Report by changing the fields in the query expression that determines the data displayed.</span></span> <span data-ttu-id="8e6e3-126">可用的欄位如下：</span><span class="sxs-lookup"><span data-stu-id="8e6e3-126">The following fields are available:</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="8e6e3-127">查詢運算式欄位</span><span class="sxs-lookup"><span data-stu-id="8e6e3-127">Query Expression Field</span></span>|<span data-ttu-id="8e6e3-128">可能的運算子</span><span class="sxs-lookup"><span data-stu-id="8e6e3-128">Potential Operators</span></span>|<span data-ttu-id="8e6e3-129">可能的值</span><span class="sxs-lookup"><span data-stu-id="8e6e3-129">Potential Values</span></span>|<span data-ttu-id="8e6e3-130">預設已包含？</span><span class="sxs-lookup"><span data-stu-id="8e6e3-130">Included By Default?</span></span>|  
|<span data-ttu-id="8e6e3-131">搜尋</span><span class="sxs-lookup"><span data-stu-id="8e6e3-131">Search for</span></span>|<span data-ttu-id="8e6e3-132">等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-132">Equals</span></span>|<span data-ttu-id="8e6e3-133">批次狀態</span><span class="sxs-lookup"><span data-stu-id="8e6e3-133">Batch Status</span></span>|<span data-ttu-id="8e6e3-134">是 (必要)</span><span class="sxs-lookup"><span data-stu-id="8e6e3-134">Yes (required)</span></span>|  
|<span data-ttu-id="8e6e3-135">批次狀態</span><span class="sxs-lookup"><span data-stu-id="8e6e3-135">Batch Status</span></span>|<span data-ttu-id="8e6e3-136">等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-136">Equals</span></span><br /><br /> <span data-ttu-id="8e6e3-137">不等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-137">Not Equals</span></span>|<span data-ttu-id="8e6e3-138">定義： 批次的執行個體已設定但開始日期時間晚於目前日期時間。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-138">Defined: The batch instance is configured but the start date time is later than the current date time.</span></span><br /><br /> <span data-ttu-id="8e6e3-139">作用中 （預設值）： 批次執行個體已設定且正在收集批次的交易集。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-139">Active (default): The batch instance is configured and is collecting transaction sets for a batch.</span></span> <span data-ttu-id="8e6e3-140">開始日期時間早於目前日期時間。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-140">The start date time is earlier than the current date time.</span></span><br /><br /> <span data-ttu-id="8e6e3-141">發行日期： 已符合釋放準則，並傳送批次，或批次協調流程已停止處理任何訊息之前。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-141">Released: The release criteria has been met, and the batch has been sent, or that the batch orchestration was stopped before any messages were processed.</span></span><br /><br /> <span data-ttu-id="8e6e3-142">完成： 已符合釋放準則，但尚未傳送批次。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-142">Completed: The release criteria has been met, but the batch has not been sent.</span></span><br /><br /> <span data-ttu-id="8e6e3-143">All： 顯示狀態為上述其中任何批次執行個體。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-143">All: Display any batch instance that is in one of the above states.</span></span>|<span data-ttu-id="8e6e3-144">是</span><span class="sxs-lookup"><span data-stu-id="8e6e3-144">Yes</span></span>|  
|<span data-ttu-id="8e6e3-145">相符記錄上限</span><span class="sxs-lookup"><span data-stu-id="8e6e3-145">Maximum Matches</span></span>|<span data-ttu-id="8e6e3-146">等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-146">Equals</span></span>|<span data-ttu-id="8e6e3-147">整數 (預設為 50)</span><span class="sxs-lookup"><span data-stu-id="8e6e3-147">Integer (default of 50)</span></span>|<span data-ttu-id="8e6e3-148">是</span><span class="sxs-lookup"><span data-stu-id="8e6e3-148">Yes</span></span>|  
|<span data-ttu-id="8e6e3-149">啟動日期時間</span><span class="sxs-lookup"><span data-stu-id="8e6e3-149">Activation Date Time</span></span>|<span data-ttu-id="8e6e3-150">小於或等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-150">Less Than or Equals</span></span><br /><br /> <span data-ttu-id="8e6e3-151">大於或等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-151">Greater Than or Equals</span></span>|<span data-ttu-id="8e6e3-152">日期時間</span><span class="sxs-lookup"><span data-stu-id="8e6e3-152">Date Time</span></span><br /><br /> <span data-ttu-id="8e6e3-153">今天</span><span class="sxs-lookup"><span data-stu-id="8e6e3-153">Today</span></span><br /><br /> <span data-ttu-id="8e6e3-154">今天-5</span><span class="sxs-lookup"><span data-stu-id="8e6e3-154">Today - 5</span></span>|<span data-ttu-id="8e6e3-155">否</span><span class="sxs-lookup"><span data-stu-id="8e6e3-155">No</span></span><br /><br /> <span data-ttu-id="8e6e3-156">附註： 可以包含超過一次在查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="8e6e3-156">Note: Can be included more than once in the query expression.</span></span>|  
|<span data-ttu-id="8e6e3-157">批次名稱</span><span class="sxs-lookup"><span data-stu-id="8e6e3-157">Batch Name</span></span>|<span data-ttu-id="8e6e3-158">等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-158">Equals</span></span>|<span data-ttu-id="8e6e3-159">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="8e6e3-159">All (Default)</span></span><br /><br /> <span data-ttu-id="8e6e3-160">特定批次名稱</span><span class="sxs-lookup"><span data-stu-id="8e6e3-160">Specific batch name</span></span>|<span data-ttu-id="8e6e3-161">否</span><span class="sxs-lookup"><span data-stu-id="8e6e3-161">No</span></span>|  
|<span data-ttu-id="8e6e3-162">目的合作對象</span><span class="sxs-lookup"><span data-stu-id="8e6e3-162">Destination Party</span></span>|<span data-ttu-id="8e6e3-163">等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-163">Equals</span></span>|<span data-ttu-id="8e6e3-164">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="8e6e3-164">All (default)</span></span><br /><br /> <span data-ttu-id="8e6e3-165">特定合作對象名稱</span><span class="sxs-lookup"><span data-stu-id="8e6e3-165">Specific party name</span></span>|<span data-ttu-id="8e6e3-166">否</span><span class="sxs-lookup"><span data-stu-id="8e6e3-166">No</span></span>|  
|<span data-ttu-id="8e6e3-167">EDI 編碼類型</span><span class="sxs-lookup"><span data-stu-id="8e6e3-167">EDI encoding type</span></span>|<span data-ttu-id="8e6e3-168">等於</span><span class="sxs-lookup"><span data-stu-id="8e6e3-168">Equals</span></span>|<span data-ttu-id="8e6e3-169">X12</span><span class="sxs-lookup"><span data-stu-id="8e6e3-169">X12</span></span><br /><br /> <span data-ttu-id="8e6e3-170">EDIFACT</span><span class="sxs-lookup"><span data-stu-id="8e6e3-170">EDIFACT</span></span><br /><br /> <span data-ttu-id="8e6e3-171">全部 (預設)</span><span class="sxs-lookup"><span data-stu-id="8e6e3-171">All (default)</span></span>|<span data-ttu-id="8e6e3-172">否</span><span class="sxs-lookup"><span data-stu-id="8e6e3-172">No</span></span>|  
  
